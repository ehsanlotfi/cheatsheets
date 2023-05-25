# xUnit
###### menu/test/testExplore
```
using ConsoleApp.TestData;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Xunit;
using Xunit.Abstractions;

namespace ConsoleApp.Test
{
    public class MathHelperTest
    {

        private readonly ITestOutputHelper _outputHelper;

        public MathHelperTest(ITestOutputHelper outputHelper)
        {
            _outputHelper= outputHelper;
        }

        //[Fact(Skip ="برای بحث آموزش این رو غیرفعال کردم")]
        [Theory(Skip = "برای بحث آموزش این رو غیرفعال کردم")]
        [Trait("Service","Cart")]
        [InlineData(5,5,10)]
        [InlineData(-5,-5,-10)]
        [InlineData(1000,5000,6000)]
        public void JamTest(int x , int y,int expected)
        {
            MathHelper mathHelper = new MathHelper();
   
            var result= mathHelper.Jam(x, y);

            Assert.Equal(expected,result);
            Assert.IsType<int>(result);
           
        }  
        
        
        [Theory]
        [Trait("Service", "Order")]
        [MemberData(nameof(DataForTest.GetData) , MemberType = typeof(DataForTest) )]
        public void Jam_MemderData_Test(int x , int y,int expected)
        {
            MathHelper mathHelper = new MathHelper();
   
            var result= mathHelper.Jam(x, y);

            Assert.Equal(expected,result);
            Assert.IsType<int>(result);
           
        }   
        
        
        [Theory]
        [Trait("Endpoint","Order")]
        [ClassData(typeof(MemberCalssData))]
        public void Jam_ClassData_Test(int x , int y,int expected)
        {
            MathHelper mathHelper = new MathHelper();
   
            var result= mathHelper.Jam(x, y);
            _outputHelper.WriteLine("thisis a test");
            _outputHelper.WriteLine( x.ToString());
            Assert.Equal(expected,result);
            Assert.IsType<int>(result);
           
        }


    }
}

```
