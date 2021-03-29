# Test-repository-automation-38


import org.junit.Test;

public class MainClass {

    public static int getLocalNumber() {
        int number = 14;
        System.out.println(number);
        return number;
    }
}



import org.junit.Assert;
import org.junit.Test;

public class MainClassTest {


    @Test

        public void testGetLocalNumber2() {
            int expected = 14;
            int actual  = MainClass.getLocalNumber();
            Assert.assertTrue( "if less or more = fail",actual == expected);
    }

}


