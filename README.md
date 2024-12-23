# FrontAccounting
package testpackage;

import org.testng.annotations.Test;
import org.testng.annotations.BeforeTest;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.testng.annotations.AfterTest;

public class DependsonMethod {
	WebDriver d;
  @Test
  public void b() {
	//login
	  d.findElement(By.id("user-name")).sendKeys("standard_user");
		d.findElement(By.id("password")).sendKeys("secret_sauce");
		d.findElement(By.id("login-button")).click();	  
	  
  }
  @Test(dependsOnMethods="b")
  public void a() {
	  //logout
  d.findElement(By.xpath("//button[@id='react-burger-menu-btn']")).click();
  d.findElement(By.xpath("//a[@id='logout_sidebar_link']")).click();
	    
	  
  }
  @BeforeTest
  public void beforeTest() {
	  System.setProperty("Webdriver.gecko.driver", "/home/student/Documents/Selenium/Selenium Jars");
		d = new FirefoxDriver();
		d.get("https://www.saucedemo.com/");
  }

  @AfterTest
  public void afterTest() {
	  d.quit();

  }

}

