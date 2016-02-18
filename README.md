# SeleniumWebdriverAutomationDemo
Basic demonstration of use of automation framework testing 

package com.Testing.Pages;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;

public class LoginSegment {
	
	WebDriver driver;
	
	By UserEmail = By.id("login_field");
	By Password = By.id("password");
	By loginButton = By.xpath("//input[@class= 'btn btn-primary btn-block']");
	
	public LoginSegment(WebDriver driver){
		
		this.driver = driver;
	}
	
	public void UserloginEmail(){
		
		driver.findElement(UserEmail).sendKeys("batmanblue79@gmail.com");
	}
	
	public void UserloginPassword(){
		
		driver.findElement(Password).sendKeys("quicksilver427");
	}
	
	public void LoginButton(){
		
		driver.findElement(loginButton).click();
	}

}


#Second part of the SeleniumWebdriverAutomationDemo code

package com.Testing.Pages2;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.testng.annotations.Test;

import com.Testing.Pages.LoginSegment;

public class GithubVerification {

	
	WebDriver driver = new FirefoxDriver();
	
	
	@Test
	public void TestVerification(){
		
		driver.manage().window().maximize();
		driver.get("https://github.com/");
		driver.findElement(By.xpath("//a[@class= 'btn' and @href= '/login' ]")).click();
		
		
		LoginSegment login = new LoginSegment(driver);
		login.UserloginEmail();
		login.UserloginPassword();
		login.LoginButton();
		
		
		//Link to pricing information
		driver.findElement(By.linkText("Pricing")).click();
		
		//Link to GutHub Enterprise
		driver.findElement(By.xpath("//a[contains(@href, 'https://enterprise.github.com') ]")).click();
		
		//Link to about GitHub
		driver.findElement(By.linkText("About us")).click();
		
		//Navigation menu
		driver.findElement(By.xpath("//a[contains(@href, '/about/team')]")).click();
		driver.findElement(By.xpath("//a[contains(@href, '/about/press')]")).click();
		driver.findElement(By.xpath("//a[contains(@href, '/about/jobs')]")).click();
		
		
	}
	
	
	
}
