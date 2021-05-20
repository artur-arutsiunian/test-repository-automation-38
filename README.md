# Test-repository-automation-38

package tests;

import lib.CoreTestCase;
import lib.ui.*;
import org.junit.Test;
import org.openqa.selenium.By;

public class MyListsTests extends CoreTestCase
{
    private lib.ui.MainPageObject MainPageObject;

    protected void setUp() throws Exception
    {
        super.setUp();

        MainPageObject = new MainPageObject(driver);
    }

    @Test
    public void testSaveFirstArticleToMyList() {
        SearchPageObject SearchPageObject = new SearchPageObject(driver);

        SearchPageObject.initSearchInput();
        SearchPageObject.typeSearchLine("Java");
        SearchPageObject.clickByArticleWithSubstring("bject-oriented programming language");


        ArticlePageObject ArticlePageObject = new ArticlePageObject(driver);

        ArticlePageObject.waitForTitleElement();
        ArticlePageObject.addArticleToMyListForMW();
        SearchPageObject.initSearchInput();
        SearchPageObject.typeSearchLine("Macbook");
        SearchPageObject.clickByArticleWithSubstring("ntel-based line of Macintosh notebook computers");
        ArticlePageObject.waitForTitleElement();
        ArticlePageObject.addArticleToMyListForMW();
        SearchPageObject.moveToMainMenu();
        SearchPageObject.clickWatchlist();
        SearchPageObject.deleteOneArticle();
        SearchPageObject.sureThatArticleExist();
    }
}