# Test-repository-automation-38

import org.junit.Test;


public class MainClass {

    private static int class_number = 45;

    public static int getClassNumber() {
        return class_number;
    }
}


import org.junit.Assert;
import org.junit.Test;

public class MainClassTest {

    @Test
    public void testGetLocalNumber() {
        int actual  = MainClass.getClassNumber();
        Assert.assertTrue( "if less = fail",actual >= 45);
    }


}