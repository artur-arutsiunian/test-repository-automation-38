# Test-repository-automation-38

import org.junit.Test;

public class MainClass {

    private static String class_string = "Hello world";

    public static String getClassString() {
        return class_string;
    }
}



import org.junit.Assert;
import org.junit.Test;

public class MainClassTest {

    @Test
    public void testGetClassString() {
        String actual  = MainClass.getClassString();
        Assert.assertTrue( "if not Hello",actual.contains("Hello") || actual.contains("hello1"));
    }

}