# Get-Infirmation-From-Table-Data

In this file I will show you
How to get some or entire information from table data

Task 1 : Print the entire table
Task 2 : Print All Rows
Task 3 : Print Last row data only
Task 4 : Print column 5 data in the table body
Task 5 : Write a method that accepts 2 parameters (I did not show task 5. if you have any question ask me)



import deneme.utilities.TestBase;
import org.apache.logging.log4j.LogManager;
import org.apache.logging.log4j.Logger;
import org.junit.Test;
import org.openqa.selenium.By;
import org.openqa.selenium.WebElement;
import tests.D12_Log4JTest;

import java.util.List;

public class WebTables extends TestBase {
    private static Logger logger = LogManager.getLogger(D09_WebTables.class.getName());
    @Test
    public void printTable() {

//    https://the-internet.herokuapp.com/tables
        logger.info("Going to the main page");
        driver.get("https://the-internet.herokuapp.com/tables");

//    Task 1 : Print the entire table


//        System.out.println("***Print Entire table***");
        logger.info("***Print Entire table***");
        String table = driver.findElement(By.xpath("//table[@id='table1']")).getText();
        System.out.println(table);
        logger.info("***Print All table Data***");

//        System.out.println("***Print All Table Data***");

List<WebElement> allData = driver.findElements(By.xpath("//table[@id='table1']//td"));
        for (WebElement eachData : allData){

            System.out.println(eachData.getText());
        }
        System.out.println("10th data in the table :"+allData.get(10).getText());

        logger.info("TESTING COMPLETE. YAAAAAAY");
    }
    
    
//    Task 2 : Print All Rows

    @Test
    public void printAll() {
        driver.get("https://the-internet.herokuapp.com/tables");
        System.out.println("***Prints All Rows***");

        List<WebElement> allRows = driver.findElements(By.xpath("//table[@id='table1']//tr"));

        int count = 1;
        for (WebElement eachRow : allRows) {
            System.out.println("Row Num " + count + " =>" + eachRow.getText());
            count++;
        }
        System.out.println("Row 4 data ===>>>" + allRows.get(3).getText());
    

//    Task 3 : Print Last row data only


        System.out.println("Last Row===>>> "+allRows.get(allRows.size()-1).getText());
    }
    
    
//    Task 4 : Print column 5 data in the table body
    
    
    @Test
    public void printColumns(){
        driver.get("https://the-internet.herokuapp.com/tables");
        List<WebElement> column5 = driver.findElements(By.xpath("//table[@id='table1']//tbody//tr//td[5]"));
        for (WebElement each : column5){
            System.out.println(each.getText());
        }

    }
//    Think about Task 5....
//    Task 5 : Write a method that accepts 2 parameters
//    Parameter 1 = row number
//    Parameter 2 = column number
//    printData(2,3);  => prints data in 2nd row 3rd column

}
