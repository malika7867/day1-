# Guru99 E-commerce Live Project - Automation Testing with Selenium

This repository contains Selenium WebDriver scripts that automate the testing of a demo e-commerce website (`http://live.techpanda.org/`). The scripts are written in Java and use Microsoft Edge as the browser for execution. The project aims to verify various functionalities of the e-commerce site, including price verification and sorting options.

## Features

- **Browser Automation**: Opens the Microsoft Edge browser and navigates to the e-commerce website.
- **Price Verification**: Checks the price of the Sony Xperia mobile on the list and details page to ensure they match.
- **Page Title Verification**: Verifies the title of the Home page and the Mobile page to ensure they match the expected values.
- **Menu Navigation**: Navigates to the "Mobile" section of the website.
- **Product Sorting**: Selects the "Price" option from the dropdown to sort mobile products and verifies if the correct option is selected.

## Prerequisites

Before running the scripts, ensure you have the following installed:

- [Java Development Kit (JDK) 8+](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html)
- [Selenium WebDriver](https://www.selenium.dev/downloads/)
- [Microsoft Edge Driver](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/)

## How to Run the Scripts

1. **Clone this repository to your local machine**:
    ```bash
    git clone https://github.com/your-username/your-repo-name.git
    ```

2. **Open the project in your preferred IDE** (e.g., Eclipse, IntelliJ IDEA).

3. **Ensure that the Microsoft Edge WebDriver path is correctly set** in your environment variables or specify the path in the code.

4. **Run the scripts** by executing the `main` method in each class (`day1` and `verfi`).

## Code Overview

### Test Case 1: E-commerce Website Automation

#### File: `day1.java`

This script automates the verification of page titles and sorting options on the e-commerce site.

```java
package ecom;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.edge.EdgeDriver;
import org.openqa.selenium.support.ui.Select;

public class day1 {

    public static void main(String[] args) {
        WebDriver driver;
        driver = new EdgeDriver();
        driver.manage().window().maximize();
        driver.get("http://live.techpanda.org/index.php/");
        
        // Verify Home Page Title
        String expectedTitle = "Home page";
        String actualTitle = driver.getTitle();
        System.out.println(actualTitle);
        if (expectedTitle.equals(actualTitle)) {
            System.out.println("Title verification passed");
        } else {
            System.out.println("Title verification failed");
        }
        
        // Navigate to Mobile section
        WebElement mobileMenu = driver.findElement(By.xpath("//*[@id=\"nav\"]/ol/li[1]/a"));
        mobileMenu.click();
        
        // Verify Mobile Page Title
        String expectedMobileTitle = "Mobile";
        String actualMobileTitle = driver.getTitle();
        System.out.println(actualMobileTitle);
        if (expectedMobileTitle.equals(actualMobileTitle)) {
            System.out.println("Mobile page title verification passed");
        } else {
            System.out.println("Mobile page title verification failed");
        }
        
        // Sort products by Price
        Select dropdown = new Select(driver.findElement(By.xpath("/html/body/div/div/div[2]/div/div[2]/div[1]/div[3]/div[1]/div[1]/div/select")));
        dropdown.selectByVisibleText("Price");
        
        // Verify the selected sorting option
        String selectedOptionText = dropdown.getFirstSelectedOption().getText();
        if (selectedOptionText.equals("Name")) {
            System.out.println("The correct option is selected: " + selectedOptionText);
        } else {
            System.out.println("Incorrect option selected. Expected 'Name', but found: " + selectedOptionText);
        }

        driver.quit();  // Close the browser
    }
}
Project Structure
package ecom: Contains the main classes day1 and verfi.
day1: Automates the verification of page titles and sorting options.
verfi: Automates the verification of the Sony Xperia mobile price.
Contributing
If you find any issues or have suggestions for improvements, feel free to fork the repository and submit a pull request. Contributions are always welcome!

License
This project is licensed under the MIT License - see the LICENSE file for details.

Contact
For any questions or suggestions, please reach out to Malika Zeshan via email or open an issue on this repository.
