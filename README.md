# layouts
#### Scenario

You have been asked to add a slideshow to the homepage of a zoo web application that will show some of the animals’ photos. The slideshow will display each photo in a large size. However, the slideshow will display only one photo at a time, and cycle through all the photos in order.



#### Objectives

After completing this lab, you will be able to:

- Apply a consistent look and feel to the web application.
- Use layouts to ensure that common interface features, such as the headers, are consistent across the entire web application.
- Render and execute JavaScript code in the browser.
- Use the jQuery script library to update and animate page elements.

### Lab Setup

Estimated Time: **60 minutes**

### Preparation Steps
Ensure that you have cloned the 20486D directory from GitHub. It contains the code segments for the labs and demos in this course. (https://github.com/MicrosoftLearning/20486D-DevelopingASPNETMVCWebApplications/tree/master/Allfiles)

### Exercise 1: Applying a Layout and Link Views to it

#### Scenario

To construct a web application with a consistent look and feel, a layout should be added to the web application. In this exercise, you will create a layout and link views to it.

The main tasks for this exercise are as follows:

1. Create a layout

2. Add a view and link it to the layout

3. Add _ViewStart.cshtml

4. Add existing views to the web application

5. Add a section to the layout

6. Run the application


#### Task 1: Create a layout
1. 
    >**Note**: If a **Security Warning for ZooSite** dialog box appears, verify that the **Ask me for every project in this solution** check box is cleared, and then click OK.

2. Create a new folder with the following information:

   - Parent folder: **Views**
   - Folder name: **Shared**

3. Add a new **Razor Layout** with the following information:

	- Folder: **Views/Shared**
	- Name: **_Layout**	

4. In the **_Layout.cshtml** file, in the **BODY** element, add a **UL** element with the following information:

	- Class: **nav**

5. In the **UL** element, add a **LI** element.

6. In the **LI** element, add an **A** element with the following information:

	- Href: **@Url.Action("Index", "Zoo")**
	- Content: **Attractions**

7. After the **LI** element, add a second **LI** element.

8. In the second **LI** element, add an **A** element with the following information:

	- Href: **@Url.Action("VisitorDetails", "Zoo")**
	- Content: **Visitor Info**

9. After the second **LI** element, add a third **LI** element.

10. In the third **LI** element, add an **A** element with the following information:

	- Href: **@Url.Action("BuyTickets", "Zoo")**
	- Content: **Tickets**

11. After the **UL** element, add a **DIV** element with the following information:

	- Class: **header-container**

12. In the **DIV** element, add an **H1** element with the following information:

	- Class: **content**
	- Content: **Welcome to Zoo Center**

13. After the **H1** element, add a **DIV** element with the following information:

	- Class: **slider-buttons**

14. In the **DIV** element, add an **IMG** element with the following information:

    - Src: **~/images/prevArrow.png**
	- Class: **prev**
    - Onclick: **prevImage()**

15. After the **IMG** element, add an **IMG** element with the following information:

	- Class: **next**
    - Src: **~/images/nextArrow.png**
    - Onclick: **nextImage()**


#### Task 2: Add a view and link it to a layout

1. In the **ZooController** class, right-click the **Index** action name, and then click **Add View**. 

2. Create a new view by using the **Add MVC View** dialog box, with the following information:

    - View Name: **Index**
    - Template: **Empty (without model)**
    - Create as Partial View: **False**
    - Use a layout page: **True**
    - Layout Page: **_Layout.cshtml**

3. Add a **@model** directive with the following information:

   - Type: **IEnumerable&lt;ZooSite.Models.Photo&gt;**


4.  Replace **_&lt;h2&gt;_Index_&lt;/h2&gt;_** with an **H1** element by using the following information:

	- Class: **main-title**
    - Content: **Zoo Attractions**

5.  Add a **DIV** element with the following information:

	- Class: **container**

6. In the **DIV** element, create a **FOREACH** statement, with the following information:

	- Variable Type: **var**
	- Variable Name: **item**
	- Collection: **Model**

7. In the **FOREACH** statement block, add a **DIV** element with the following information:

	- Class: **photo-index-card**

8. Create an **IF** statement that checks that the value of the **item.PhotoFileName** property is not **NULL**.

9. In the **IF** statement, add a **DIV** element with the following information:

	- Class: **image-wrapper**

10. In the **DIV** element, add an **IMG** element with the following information:

	- Class: **photo-display-img**
    - Src: **@Url.Action("GetImage", "Zoo", new { PhotoId = item.PhotoID })**

11. After the **IF** statement, add an **H3** element with the following information:

	- Class: **display-picture-title**
    - Content: **@Html.DisplayFor(modelItem  => item.Title)**

12. Add a **DIV** element.

13. In the **DIV** element, add a **SPAN** element with the following information:

	- Class: **display**
    - Content: **@Html.DisplayFor(model => item.Description)**

#### Task 3: Add _ViewStart.cshtml

1. Create a new **Razor View Start** file, with the following information:

    - Name: **_ViewStart**
    - Folder: **Views**

2. At the beginning of the **Index.cshtml** view, remove the **Layout** property with its value.

#### Task 4: Add existing views to the web application

1. Add the existing **.cshtml** files to the **ZooSite** project, with the following information:

    - Source location: **[Repository Root]\Sources**
	- Target location: **[Repository Root]\ZooSite\Views**


#### Task 5: Add a section to the layout

1. In the **_Layout.cshtml** file, after the **DIV** element with **@RenderBody()** content, call the **RenderSection** method. 

2. Pass **"Scripts"** and **false** as parameters to the **RenderSection** method.

#### Task 6: Run the application

1. Save all the changes.

2. Start the application without debugging.

    >**Note**: The browser displays the **Index.cshtml** file content, but the HTML content is not designed by a CSS file yet.

3. In the menu bar, click **Visitor Info**.

    >**Note**: Examine the browser content.

4. In the menu bar, click **Tickets**.

    >**Note**: Examine the browser content.

5. Close Microsoft Edge.

>**Results**: After completing this exercise, you will be able to add a layout and link views to it. You will also be able to use the **_ViewStart** file in the web application.  

### Exercise 2: Using CSS 

#### Scenario

To improve the appearance of the web application, a CSS should be used. In this exercise, you will add a CSS file to the web application, and add a link from the layout to the CSS file.

The main tasks for this exercise are as follows:

1. Add an existing CSS file to the project

2. Link the layout to the CSS file

3. Style the menu

4. Style the photos section in Index.cshtml

5. Style a form in BuyTickets.cshtml

6. Run the application

#### Task 1: Add an existing CSS file to the project

1. Create a new folder with the following information:

	- Folder name: **css**
	- Parent folder: **wwwroot**

2. To the **ZooSite** project, add the **zoo-style.css** file, with the following information:

	- Source location: **[Repository Root]\Sources**
	- Target location: **[Repository Root]\wwwroot\css**

3. In the **Startup** class, in the **Configure** method, after the call to the **zooContext.Database.EnsureCreated** method, call the **UseStaticFiles** method of the **app** parameter.

#### Task 2: Link the layout to the CSS file

1. In the **_Layout.cshtml** file, in the **HEAD** element, add a **LINK** element with the following information:

	- Type: **text/css**
	- Rel: **stylesheet**
	- Href: **~/css/zoo-style.css**

#### Task 3: Style the menu

1. At the bottom of the **zoo-style.css** file, add a **.nav** selector with the following properties:

	- list-style-type: **none**
	- margin: **0**
	- padding: **0**
	- overflow: **hidden**
	- background-color: **#85754e**
	- Position: **fixed**
	- top: **0**
	- left: **0**
	- width: **100%**

2. Add a **.nav li** selector with the following property:

	- float: **left**

3. Add a **.nav li a** selector with the following properties:

	- display: **block**
	- color: **white**
	- text-align: **center**
	- padding: **14px 16px**
	- text-decoration: **none**

4. Add a **.nav li a:hover:not(.active)** selector with the following property:

	- background-color: **#016b6b**

5. Add a **.active** selector with the following properties:

	- background-color: **#008484**		
	- color: **#fff**


#### Task 4: Style the photos section in Index.cshtml

1. Add a **.photo-index-card** selector with the following properties:

	- background-color: **#ffffff**
	- padding: **0**
	- margin: **10px 5px 15px 18px**
	- padding-bottom: **25px**
	- width: **355px**
	- border: **1px solid #d6d4d4**
	- border-radius: **10px**
	- overflow: **hidden**

#### Task 5: Style a form in BuyTickets.cshtml

1. Add a **.info .form-field** selector with the following property:

	- text-align: **left**

2. Add a **.info .form-field div** selector with the following properties:

	- width: **172px**
	- text-align: **right**
	- float: **right**

3. Add a **.info label** selector with the following properties:

	- width: **118px**
	- display: **inline-block**
	- margin-bottom: **10px**

4. Add a **.info input** selector with the following properties:

	- border-radius: **2px**
	- line-height: **20px**
	- border: **1px solid #ccc6c6**
	- background-color: **#f9f6f6**
	- width: **100%**

5. Add a **input.submit-btn** selector with the following properties:

	- width: **100px**
	- margin-top: **12px**
	- height: **29px**
	- background-color: **orange**
	- font-weight: **bold**
	- box-shadow: **inset 0px 0px 4px #b77006**
	- border: **1px solid #a59797**

6. Add a **input.submit-btn[disabled]** selector with the following properties:

	- opacity: **0.8**
	- background-color: **whitesmoke**
	- box-shadow: **none**

#### Task 6: Run the application

1. Save all the changes.

2. Start the application without debugging.

    >**Note**: The browser displays the content of the **Index.cshtml** file, with HTML content that is designed by a CSS file.

3. In the **Zoo Attractions** page, in the **Welcome to Zoo Center** header, click the **right arrow**.

    >**Note:** Currently, clicking the button has no effect since no JavaScript code has been added to the web application yet.

4. In the menu bar, click **Visitor Info**.

    >**Note**: Examine the browser content.

5. Click **Tickets**.

6. On **Step 1 - Choose Tickets**, select the following:

	- Adult: _&lt;As many tickets as you like&gt;_
	- Child: _&lt;As many tickets as you like&gt;_
	- Senior: _&lt;As many tickets as you like&gt;_
   
	>**Note:** Currently the total cost of the tickets is not shown on the page since no JavaScript code has been added to the web application yet.

7.  On **Step 2 - Buy Tickets**, type the following:

	- First Name: _&lt;A first name of your choice&gt;_
	- Last Name: _&lt;A last name of your choice&gt;_
	- Address: _&lt;An address of your choice&gt;_
	- Email: **abcd**
	- Phone Number _&lt;A phone number of your choice&gt;_

8. Click **Buy**.

    >**Note:** Currently you can't buy the tickets and there is no validation since the functionality has not been applied yet.

9. Close Microsoft Edge.

>**Results**: After completing this exercise, you will be able to add an existing CSS file to a web application, and add a link from a layout to the CSS file. You will also be able to add new CSS selectors to a CSS file. 
