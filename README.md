Using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace RangeIpvalidation
{
    class Program
    {
        static void Main(string[] args)
        {
            string ip = "10.1.2.12";

            string ip_ini = "10.1.2.11";
            string ip_end = "10.1.2.40";
            
            long long_ip = IP2Long(ip);
            long long_ip_ini = IP2Long(ip_ini);
            long long_ip_end = IP2Long(ip_end);

            if (long_ip >= long_ip_ini && long_ip <= long_ip_end)
            {
                Console.WriteLine("Direccion ip en rago valido.");
            }
            else {
                Console.WriteLine("Direccion ip fuera de rango.");
            }
            Console.ReadKey();
        }

        public static long IP2Long(string ip)
        {
            string[] ipBytes;
            double num = 0;
            if (!string.IsNullOrEmpty(ip))
            {
                ipBytes = ip.Split('.');
                for (int i = ipBytes.Length - 1; i >= 0; i--)
                {
                    num += ((int.Parse(ipBytes[i]) % 256) * Math.Pow(256, (3 - i)));
                }
            }
            return (long)num;
        }
    }
}

