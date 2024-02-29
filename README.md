# Reactfolio compatible version with Git Pages

## 📚 Getting started

Clone down this repository. You will need `NodeJS` and `git` installed globally on your machine.

## 🛠 Installation and Setup Instructions

1. Go to the repo root directory `cd reactfolio`

2. Installation: `npm install`

3. Deploy the project: `npm run deploy`
    - might need to run the following command for the first time and run again, if an error occurs.
      ```
      rm -rf node_modules/.cache/gh-pages
      npm run deploy
      ```
      
4. Configure Git Pages
    - Select `gh-pages` as branch and Save
      
      ![image](https://github.com/shanefujs/reactfolio/assets/75388289/3f928df6-5bdd-4a7e-80d0-41a0b967fd5c)

  
5.  Set up git hook

    - Edit hooks/pre-push with vim: `vim .git/hooks/pre-push`
    - Add cmmand: press `i` to enter edit mode, add the following line.
        ```
        npm run deploy
        ```
    - Save (`esc` > `:wq` > `enter`)
    - make pre-push executable: `chmod +x .git/hooks/pre-push`
  
  
5.  Done 🚀. Every time you push a change to master, a workflow will be triggered to deploy your page to https://<user_name>.github.io/reactfolio/


## 📁 Folder structure

-   `/public`: publicly accessible contents (ex: images, media).
-   `/src`: all the components used in this project.
    -   `/src/components/`: each reusable components of each pages.
    -   `/src/data`: configurations of the web app.
    -   `/src/pages`: pages that include in the web app.

## ⚙️ Configurations

Since this is a public and open source project, you can make any changes to it. If you are a ReactJS developer you can do it easily. But if you are a beginner, I have extracted the configurable data into a single directory, so you can edit the files in that directory to configure the entire web application.

Directory: `/src/data/`

-   `user.js`

    From this you can change the content of each page of the web application.

-   `articles.js`

    From this you can add your articles to the web application.

    Instructions:

    -   Add new article

        1. Create a new function starts with `article_`. For example you can add new function named `article_3`.

        2. Then add the data accordingly.

            - Add `<React.Fragment>` tag and it's closing tags in body.
            - In React there has no keyword `class`, so you should use `className` to define html classes.

            ```js
            function article_3() {
            	return {
            		date: "7 May 2023",
            		title: "The Benefits of Cloud Computing",
            		description: "Why businesses are turning to the cloud.",
            		style: `
            				.random-image {
            					align-self: center;
            					outline: 2px solid red;
            				}
            				`,
            		body: (
            			<React.Fragment>
            				<div className="article-content">
            					<div className="paragraph">
            						Content of article 1
            					</div>
            					<img
            						src="https://picsum.photos/200/300"
            						alt="random"
            						className="random-image"
            					/>
            				</div>
            			</React.Fragment>
            		),
            	};
            }
            ```

        3. In the last lines you will see an array to which you need to add your new `articles` function.

            ```js
            const myArticles = [article_1, article_2, article_3];
            ```

-   `seo.js`

    The SEO.js file is a module that contains an array of objects, with each object representing metadata for a specific page of a React website. The purpose of this file is to centralize and manage the SEO (Search Engine Optimization) information for different pages.

    Each object in the SEO array has the following properties:

    `page`: Represents the page name or identifier. It helps in mapping the SEO data to the appropriate page.

    `title`: Specifies the title of the page. This title is typically displayed in the browser's title bar and is an important element for search engines.

    `description`: Provides a concise and informative description of the page content. This description is often displayed in search engine results and can greatly influence click-through rates.
    keywords: Contains an array of keywords relevant to the page's content. Keywords can help search engines understand the topics covered on the page and can impact its visibility in search results.
    By storing the SEO information in the SEO.js file, you can easily manage and update the metadata for different pages of your React website. This approach allows you to keep the SEO data separate from the components and reuse it across the application, ensuring consistent and optimized metadata for each page.

    Example:

    ```js
    const SEO = [
    	{
    		page: "home",
    		description:
    			"I am a backend developer with expertise in Node.js. I have experience in building scalable, secure and reliable web applications using various frameworks and technologies.",
    		keywords: ["Bonnie", "Bonnie L", "Bonnie Lee"],
    	},
    ];
    ```

-   `styles.css`

    From this you can change the font colors and font families of the web application.

    ```css
    :root {
    	/* ------- colors ------- */
    	--primary-color: #27272a;
    	--secondary-color: #65656d;
    	--tertiary-color: #acacb4;
    	--quaternary-color: #e4e4e7;
    	--link-color: #14b8a6;
    	/* ---------------------- */

    	/* ------- fonts ------- */
    	--primary-font: "Heebo", sans-serif;
    	--secondary-font: "Roboto", sans-serif;
    	/* --------------------- */
    }
    ```

## 📈 Google Analytics

Add your Google Analytics 4 MEASUREMENT ID to `/src/data/tracking.js`.

How to find the Google Analytics 4 MEASUREMENT ID ?

[https://support.google.com/analytics/answer/9539598?hl=en](https://support.google.com/analytics/answer/9539598?hl=en)


## 🤔 FAQ

**Q1. Subpages can only be accessed through links on the homepage or navigation bar, but those pages are not accessible through direct links.**

If you are using Apache as your web server, you can insert this into your .htaccess file:

```c
<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteBase /
  RewriteRule ^index\.html$ - [L]
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteCond %{REQUEST_FILENAME} !-l
  RewriteRule . /index.html [L]
</IfModule>
```

## 🌱 Contribution

If you have any suggestions on what to improve in Reactfolio and would like to share them, feel free to leave an issue or fork project to implement your own ideas
