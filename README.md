# Test-repository-automation-38

import org.junit.Test;

public class MainClass
{
    @Test
    public void getLocalNumber()
    {
    int number = 14;
        System.out.println(number);
}
}



import org.junit.Assert;
import org.junit.Test;

public class MainClassTest
{
  @Test
      public void testGetLocalNumber ()
      {
          int expected = 14;
          int actual = 14;

          Assert.assertTrue("if less or more = fail", actual == expected);
      }
  }
