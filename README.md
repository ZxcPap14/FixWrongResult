# FixWrongResult

-lib

      using System;
      using System.Collections.Generic;
      using System.Linq;
      using System.Text;
      using System.Text.RegularExpressions;
      using System.Threading.Tasks;
    
    namespace fractionLib
    {
        public class Fraction
        {
            public static string FixWrongResult(string text)
            {

            string[] words = text.Split(new char[]{'/'});
            string first = words[0];
            string second = words[1];
            bool z = Int32.TryParse(first, out int result);
            bool y = Int32.TryParse(second, out int result1);
            string regex1 = "/";
            bool zxc = string.Equals(regex1,text);
            if (result > result1)   
            {
                text= second + "/" + second;
            }
            if (string.IsNullOrEmpty(text))
            {
                throw new ArgumentException("Exception");
            }
            

            return (text);
        }
    }
    }

-test

    using Microsoft.VisualStudio.TestTools.UnitTesting;
    using System;
    using FixWrongResultTests;
    using fractionLib;
    
    namespace FixWrongResultTests
    {
        [TestClass]
        public class UnitTest1
        {
            /// <summary>
            /// 
            /// </summary>
            [TestMethod]
            public void FixResult_RightAnswer()
            {
                //Arrange
                string text = "2/3";
                string res = "2/3";
                //Act
                string actual = Fraction.FixWrongResult(text);
                //Assert
                Assert.AreEqual(actual, res);
            }
            [TestMethod]
            public void FixResult_WrongAnswer()
            {
                //Arrange
                string text = "10/3";
                string res = "3/3";
                //Act
                string actual = Fraction.FixWrongResult(text);
                //Assert
                Assert.AreEqual(actual, res);
            }
            [TestMethod]
            public void FixResult_Empty()
            {
                //Arrange
                string text = " ";
                //Act
                Action action = () => Fraction.FixWrongResult(text);
                //Assert
                Assert.ThrowsException<ArgumentException>(action);

        }
    }
    }

