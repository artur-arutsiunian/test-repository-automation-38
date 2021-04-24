# Test-repository-automation-38

@Test
    public void testCancelSearch()
    {
        SearchPageObject SearchPageObject = new SearchPageObject(driver);

        SearchPageObject.initSearchInput();
        SearchPageObject.typeSearchLine("Java");
        SearchPageObject.waitSearchResult();
        SearchPageObject.waitForClear();
        SearchPageObject.waitForCancelButtonToAppear();
        SearchPageObject.clickCancelSearch();
        SearchPageObject.waitForCancelButtonToDisappear();
    }

    @Test
    public void testAssertTitle() {
        SearchPageObject SearchPageObject = new SearchPageObject(driver);

        SearchPageObject.initSearchInput();
        SearchPageObject.typeSearchLine("Iphone");
        MyListsPageObject MyListPageObject = new MyListsPageObject(driver);
        MyListPageObject.click_in_assert_title();
        ArticlePageObject ArticlePageObject = new ArticlePageObject(driver);
        ArticlePageObject.waitForTitleElement();
        MyListPageObject.immediately_assert_element();
    }
    
    @Test
       public void testSaveFirstArticleToMyList()
       {
       SearchPageObject SearchPageObject = new SearchPageObject(driver);

       SearchPageObject.initSearchInput();
       SearchPageObject.typeSearchLine("Java");
       SearchPageObject.clickByArticleWithSubstring("Object-oriented programming language");


       ArticlePageObject ArticlePageObject = new ArticlePageObject(driver);
       ArticlePageObject.waitForTitleElement();
       String article_title = ArticlePageObject.getArticleTitle();
       String name_of_folder = "My folder";
       ArticlePageObject.addArticleToMyList(name_of_folder);
       ArticlePageObject.closeArticle();

       SearchPageObject.initSearchInput();
       SearchPageObject.typeSearchLine("Macbook");
       SearchPageObject.clickByArticleWithSubstring("Intel-based line of Macintosh notebook computers");


       ArticlePageObject.waitForTitleElement();
       String article_title1 = ArticlePageObject.getArticleTitle();
       ArticlePageObject.addArticleToMyList1(name_of_folder);
       ArticlePageObject.closeArticle();

           NavigationUI NavigationUI = new NavigationUI(driver);
         NavigationUI.ClickMyList();

           MyListsPageObject MyListPageObject = new MyListsPageObject(driver);
           MyListPageObject.openFolderByName(name_of_folder);
           MyListPageObject.swipeByArticleToDelete(article_title);
           MyListPageObject.waitForSecondElement();
           MyListPageObject.clickOnSecondElement();
           int amount_of_search_results = MainPageObject.getAmountOfElements(
                   By.id("org.wikipedia:id/view_page_title_text")
           );
