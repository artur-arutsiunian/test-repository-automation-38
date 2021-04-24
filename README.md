# Test-repository-automation-38

package lib.ui;

import io.appium.java_client.AppiumDriver;
import org.openqa.selenium.By;

public class SearchPageObject extends MainPageObject{

    private static final String
    SEARCH_INIT_ELEMENT = "org.wikipedia:id/search_container",
    SEARCH_INPUT = "org.wikipedia:id/search_src_text",
    SEARCH_RESULT = "//*[@resource-id='org.wikipedia:id/page_list_item_container']//*[@text='Object-oriented programming language']",
    SEARCH_CLEAR = "org.wikipedia:id/search_src_text",
    SEARCH_CANCEL_BUTTON = "org.wikipedia:id/search_close_btn",
    SEARCH_RESULT_BY_SUBSTRING_TPL= "//*[@resource-id='org.wikipedia:id/page_list_item_container']//*[@text='{SUBSTRING}']",
    SEARCH_RESULT_ELEMENT = "//*[@resource-id='org.wikipedia:id/search_results_list']/*[@resource-id='org.wikipedia:id/page_list_item_container']",
    SEARCH_EMPTY_RESULT_ELEMENT = "//*[@text='No results found]";


    public SearchPageObject(AppiumDriver driver)
    {
        super(driver);
    }

    /* TEMPLATE METHODS */
    private static String getResultSearchElement(String substring)
    {
        return SEARCH_RESULT_BY_SUBSTRING_TPL.replace("{SUBSTRING}", substring);
    }
    /* TEMPLATE METHODS */

    public void initSearchInput()
    {
        this.waitForElementAndClick(By.id(SEARCH_INIT_ELEMENT),"Cannot find and click search init element", 5);
        this.waitForElementPresent(By.id(SEARCH_INIT_ELEMENT), "Cannot find search input after clicking search init element");
    }

    public void waitSearchResult()
    {
        this.waitForElementPresent(By.xpath(SEARCH_RESULT), "cannot find search result", 5);
    }

    public void waitForClear()
    {
        this.waitForElementAndClear(By.id(SEARCH_CLEAR), "cannot clear", 5);
    }

    public void waitForCancelButtonToAppear()
    {
        this.waitForElementPresent(By.id(SEARCH_CANCEL_BUTTON), "cannot find search cancel button", 5);
    }

    public void waitForCancelButtonToDisappear()
    {
        this.waitForElementNotPresent(By.id(SEARCH_CANCEL_BUTTON), "search cancel button is still present", 5);
    }

    public void clickCancelSearch()
    {
        this.waitForElementAndClick(By.id(SEARCH_CANCEL_BUTTON), "Cannot find click search cancel button",5);
    }

    public void typeSearchLine(String search_line)
    {
        this.waitForElementAndSendKeys(By.id(SEARCH_INPUT), search_line, "Cannot find and type into search input", 5);
    }

    public void clickByArticleWithSubstring(String substring)
    {
        String search_result_id = getResultSearchElement(substring);
        this.waitForElementAndClick(By.xpath(search_result_id), "Cannot find and click search result with substring " + substring, 10);
    }

    public void waitForSearchResult(String substring)
    {
        String search_result_id = getResultSearchElement(substring);
        this.waitForElementPresent(By.xpath(search_result_id), "Cannot find search result with substring " + substring);
    }

    public int getAmountOfFoundArticles()
    {
        this.waitForElementPresent(
                By.xpath(SEARCH_RESULT_ELEMENT),
                "Cannot find anything by the request",
                15
        );
            return this.getAmountOfElements(By.xpath(SEARCH_RESULT_ELEMENT));
    }

    public void waitForEmptyResultsLabel()
    {
        this.waitForElementPresent(By.xpath(SEARCH_EMPTY_RESULT_ELEMENT),"Cannot find empty result element,", 15);

    }

    public void assertThereIsResultsOfSearch()
    {
        this.assertElementNotPresent(By.xpath(SEARCH_RESULT_ELEMENT),"We supposed not find any results");
    }
}
