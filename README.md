toplama-islemi
==============

sınırsız uzunlukta girilen iki farklı sayıyı iki farklı diziye atarak boyutlarını karşılaştırır. Daha sonra her indis kendi arasında toplama işlemi yaptırılır.


using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace toplama
{
    class Program
    {
        static void Main(string[] args)
        {

            int a, b;
            Console.Write("Bir sayi giriniz : ");
            a = Convert.ToInt32(Console.ReadLine());
            Console.Write("Bir sayi giriniz:");
            b = Convert.ToInt32(Console.ReadLine());

            int gecici;
            bool aBuyuk = false;
            string[] sayi1;
            string[] sayi2;
            int length = 0;

            if (a.ToString().Length > b.ToString().Length)
            {
                sayi1 = new string[a.ToString().Length];
                sayi2 = new string[a.ToString().Length];
                gecici = a.ToString().Length - b.ToString().Length;
                aBuyuk = true;
                length = a.ToString().Length;
            }

            else
            {
                sayi1 = new string[b.ToString().Length];
                sayi2 = new string[b.ToString().Length];
                gecici = b.ToString().Length - a.ToString().Length;
                length = b.ToString().Length;
            }

            for (int i = 0; i < length; i++)
            {
                if (!aBuyuk)
                {
                    if (i >= gecici)
                    {
                        sayi1[i] = a.ToString().Substring(i - gecici, 1);
                    }
                    else
                    {
                        sayi1[i] = "0";
                    }
                }
                else
                {
                    sayi1[i] = a.ToString().Substring(i, 1);
                }
            }
            for (int i = 0; i < length; i++)
            {

                if (aBuyuk)
                {
                    if (i >= gecici)
                    {
                        sayi2[i] = b.ToString().Substring(i - gecici, 1);
                    }
                    else
                    {
                        sayi2[i] = "0";
                    }
                }
                else
                {
                    sayi2[i] = b.ToString().Substring(i, 1);
                }
            }

            string[] dizi;

            if (a.ToString().Length < b.ToString().Length)
            {
                dizi = new string[b.ToString().Length + 1];
            }
            else
            {
                dizi = new string[a.ToString().Length + 1];
            }


            int toplam;
            string elde = "0";
            string toplam1;

            for (int i = 1; i <= sayi1.Length; i++)
            {
                toplam = Convert.ToInt32(sayi1[sayi1.Length - i]) + Convert.ToInt32(sayi2[sayi2.Length - i]) +
                    Convert.ToInt32(elde);
                toplam1 = toplam.ToString();
                if (toplam > 9)
                {
                    elde = toplam1.Substring(0, 1);
                    dizi[i - 1] = toplam1.Substring(1, 1);
                }

                else
                {
                    elde = "0";
                    dizi[i - 1] = toplam1;
                }

            }
            string sonuc = "";
            if (elde == "1")
            {
                sonuc = "1";
            }

            for (int i = 0; i < dizi.Length; i++)
            {
                sonuc = sonuc + dizi[dizi.Length - i - 1];

            }

            Console.WriteLine("\nSonuç : "+sonuc);
            Console.ReadLine();
        }
    }
}
