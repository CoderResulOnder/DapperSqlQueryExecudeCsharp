       
       //Postgresql database operatinos
       //C# class dapper execute
       //
       public class Kullanicilar
       {
        #region FIELDS
        public int id { get; set; }
        public string KullaniciAdi { get; set; }
        public string ParolaMD5 { get; set; }
        public string Adi { get; set; }
        public string Soyadi { get; set; }
        public string CepTelefonu { get; set; }
        public string Telefon2 { get; set; }
        public string EPosta { get; set; }
        #endregion

        #region METHODS
        public static bool KullaniciAdiKontrol(string KullaniciAdi)
        {
            // Kullanici adinin veri tabanında olup olmaması
            Kullanicilar sonuc = DatabaseOperations.QueryExecute<Kullanicilar>(
                "SELECT * FROM \"Kullanicilar\" where lower(\"KullaniciAdi\")='" + KullaniciAdi.ToLower() + "'"
                ).FirstOrDefault();
            return (sonuc != null);
        }

        public static Kullanicilar getKullanicilar(int id)
        {
            //id istenen kullaniciyi listeler
            Kullanicilar sonuc = null;
            if (id > 0)
            {
                sonuc = DatabaseOperations.QueryExecute<Kullanicilar>(
                    "Select * from \"Kullanicilar\" where id=" + id
                    ).FirstOrDefault();
            }
            return sonuc;
        }

        public static List<Kullanicilar> getKullanicilar()
        {
            //tüm kullanicilari listeler
            List<Kullanicilar> sonuc = null;
            sonuc = DatabaseOperations.QueryExecute<Kullanicilar>(
                "Select * from \"Kullanicilar\" order by \"KullaniciAdi\""
                ).ToList();
            return sonuc;
        }

        public static Kullanicilar getKullanicilar(string KullaniciAdi)
        {
            //kullanici adi ile istenen kullaniciyi listeler
            Kullanicilar sonuc = null;
            if (KullaniciAdi != "")
            {
                sonuc = DatabaseOperations.QueryExecute<Kullanicilar>(
                    "Select * from \"Kullanicilar\" where lower(\"KullaniciAdi\")='" + KullaniciAdi.ToLower()+"'"
                    ).FirstOrDefault();
            }
            return sonuc;
        }
        #endregion
        }    
           
       //Data insert
       //DatabaseOperations.QueryExecute("insert into \"Kullanicilar\" (\"KullaniciAdi\",\"ParolaMD5\",\"Adi\",\"Soyadi\") 
       //Values ('" + KullaniciAdi + "','" + Parola + "','" + KullaniciAdi + "','" + KullaniciAdi + "')");
       //Data Update
       //bool sonuc = DatabaseOperations.QueryExecute("update \"Kullanicilar\" set " +
       //                                 " \"KullaniciAdi\" ='" + kullanicis.KullaniciAdi + "'," +
       //                                 " \"ParolaMD5\" ='" + kullanicis.ParolaMD5 + "'," +
       //                                 " \"Adi\" ='" + kullanicis.Adi + "'," +
       //                                 " \"Soyadi\" ='" + kullanicis.Soyadi + "'," +
       //                                 " \"CepTelefonu\" ='" + kullanicis.CepTelefonu + "'," +
       //                                 " \"EPosta\" ='" + kullanicis.EPosta + "'," +
       //                                 " \"Guncelleyen\" ='" + CurrentUser.ID + "'," +
       //                                 " \"GuncellemeZamani\" ='" + DateTime.Now + "' where id="+kullanicis.id
       //                                 );
                                
        
        
        public static IEnumerable<T> QueryExecute<T>(string query) where T : class
        {
            using (IDbConnection db =(IDbConnection) new NpgsqlConnection(GetConnectionString()))
            {
                return db.Query<T>(query);
            }
        }
        
        public static bool QueryExecute(string query) 
        {
            using (IDbConnection db = (IDbConnection)new NpgsqlConnection(GetConnectionString()))
            {
                var sonuc = db.Execute(query);
                return Convert.ToBoolean(sonuc);
            }
        }
