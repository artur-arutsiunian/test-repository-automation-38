# Test-repository-automation-38

Test 2

import org.junit.Test;

public class MainClass {
    private void class_number() {
        int number = 20;
        System.out.println(number);
    }

    @Test
    public void getClassNumber() {
        this.class_number();
    }
}



import org.junit.Assert;
import org.junit.Test;

public class MainClassTest

{
    @Test
    public void testGetClassNumber ()
    {
        int expected = 46;
        int actual = 45;
        Assert.assertTrue("Warning! Your expected result equal actual", expected > actual);
        if (expected <= actual) {
            System.out.println("Must be more or equal 45");
        } else {
            System.out.println("This is correct result");
        }
    }
}