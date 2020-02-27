// гитхабом пользуюсь 1 раз, не очень понимиаю как тут указывать, что код, а что нет
//код библиотеки
// с c# работаю мало и после университета многое не помню, так что писал задачу с помощью гугла

 	using System;
	namespace ClassLibrary1
	{
    public static class Class1
    {
        public static double circle1(double r)
        {
            return Math.PI * (r * r);
        }
        public static double tre(double a, double b, double c)
        {
            return Math.Sqrt(((a+b+c)/2) * ((a + b + c)/2 - a)  * ((a + b + c) / 2 - b) * ((a + b + c) / 2 - c));
        }
        public static double all(double[,] a)
        {
            double b = 0;
            double c = 0;
            int e = 0;
            for (int i = 0; i < (a.Length / 2) - 1; i++)
            {
                b = b + (a[0, i] * a[1, i + 1]);
                e = i;
            }
            b = b + (a[0, e+1] * a[1, 0]);
           
            for (int i = 0; i < (a.Length / 2) - 1; i++)
            {
                c = c + (a[0, i + 1] * a[1, i]);
                e = i;
            }
            c = c + (a[0, 0] * a[1, e + 1]);
            return (b - c) / 2;
        }
    }
	}


	//код тестов
	using NUnit.Framework;
	using System;
	using ClassLibrary1;
	namespace ClassLibrary1test
	{
    public class Tests
    {

        [Test] //Круг
        public void Test1()
        {

            double r = 2;
            var res = Class1.circle1(r);
            Assert.AreEqual(12.566, Math.Round(res, 3));
        }

        [Test]//неизвестная фигура по точкам
        public void Test2()
        {

            double[,] a = new double[2, 5];
            a[0, 0] = -3; a[1, 0] = -2;
            a[0, 1] = -1; a[1, 1] =  4;
            a[0, 2] =  6; a[1, 2] =  1;
            a[0, 3] =  3; a[1, 3] = 10;
            a[0, 4] = -4; a[1, 4] =  9;
            var res2 = Class1.all(a);
            Assert.AreEqual(60, Math.Round(res2, 0));
        }

        [Test]// треугольник
        public void Test3()
        {
            double a = 2;
            double b = 2;
            double c = 3;
            var res = Class1.tre(a,b,c);
            Assert.AreEqual(1.984, Math.Round(res, 3));
        }

        [Test]//прямой
        public void Test4()
        {
            double a = 3;
            double b = 4;
            double c = 5;
            if (a < b)
            {
                a = a + b;
                b = a - b;
                a = a - b;
            }
            if (a < c)
            {
                a = a + c;
                c = a - c;
                a = a - c;
            }
            //var res = ClassLibrary1.Class1.tre(a, b, c);
            Assert.AreEqual((a * a), b * b + c * c);
        }
    }
	}
	
--код sql запроса
--запрос пишу без проверки, уже поздно а завтра на работу, как я понял есть таблицы статей, тегов и таблица связей

	Select
  		art.[title]
  		,teg.[name]
 	from
  		[bd].[dbo].[dic_articles] as art
  		left join [bd].[dbo].[ass_articles_and_tegs] as aat
		    on aat.[id_article] = art.[id_article]
  		left join [bd].[dbo].[dic_tegs] as teg
    			on teg.[id_teg] = aat.[id_teg]

-- из последних рабочих кодов, могу что то прислать в личной переписке, в общей доступ выкладывать не могу.
 
