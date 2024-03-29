**Assignment - 1**

Typical product database consists of two types of product components — product categories and product items. A product category is generally contain product items and also other product categories as its subcategories. Example Product Categories:

Computers

Desktops

Laptops

Peripherals

Printers

Cables

The Computers product category contains both the Desktops and the Laptops product categories as its subcategories. The Desktop category can contain a product item such as Compaq Presario 5050. Product items are usually individual, in the sense that they do not contain any product component within. Design and implement an PricingCalculator to list the dollar value of a product component or Product Category.

Composite Pattern

![image](https://user-images.githubusercontent.com/53172079/181826869-f10b53fe-cfab-49ed-9958-929ea938da87.png)


**Assignment - 2**

public class OnlineCart

{
    
    public void CheckOut(PaymentType paymentType)
	  
    {
        
        switch(paymentType)
        
        {
            
            case PaymentType.CreditCard:
                    
                    ProcessCreditCardPayment();
                    
                    break;
            
            case PaymentType.Paypal:
                    
                    ProcessPaypalPayment();
                    
                    break;
            
            case PaymentType.GoogleCheckout:
                    
                    ProcessGooglePayment();
                    
                    break;
            
            case PaymentType.AmazonPayments:P
                    
                    ProcessAmazonPayment();
                    
                    break;
        
        }
    
    }
    
    private void ProcessCreditCardPayment()
    
    {
        
        Print("Credit card payment chosen");
    
    }
    
    private void ProcessPaypalPayment()
    
    {
        
        Print("Paypal payment chosen");
    
    }
    
    private void ProcessGooglePayment()
    
    {
        
        Print("Google payment chosen");
    
    }
    
    private void ProcessAmazonPayment()
    
    {
        
        Print("Amazon payment chosen");
    
    }

}

•	Violation of open close principle because if a new payment type is added switch case needs to be modified.
•	Violation of single responsibility principle because one method has multiple responsibility

![image](https://user-images.githubusercontent.com/53172079/181827144-6e5f3c3b-9a11-4e32-9372-7682a3733487.png)


**Assignment - 3**

CNC Monitoring and Alerting

We need a solution to interpret data coming out of a CNC-machine monitor. Our purpose is to alert when something needs attention. The alert needs to include information on the area that needs attention - the machine or the environment. The personnel that need to be alerted are different in each case.

A basic idea of CNC machines can be seen here. Keeping these machines safe and reliable is vital in any manufacturing unit.

Monitored data

The CNC-machine monitor gives the following data:

Operating temperature: Temperature around the CNC machine in Celsius. Reported every half-hour. Need to alert if it goes beyond 35 degrees.
Part-dimension variation: In mm. A variation of more than 0.05 mm needs attention (example: a drill-bit in the machine may need replacement)
Duration of continuous operation: Reported in minutes. Updated once every 15 minutes. More than 6 hours of continuous operation requires attention.
Self-test status-code, reported at startup

Code	Meaning

0xFF	All ok

0x00	No data (examples: no power, no connection to the data-collector)

0x01	Controller board in the machine is not ok

0x02	Configuration data in the machine is corrupted

Assume that the above data is monitored and passed-on to your program. You can choose to take the inputs as function calls to your program, or as events.

Expected outputs

The program needs to indicate if there is a need for attention.
When there is a need to attend, it needs to offer an initial diagnosis, to help in alerting the appropriate personnel: It needs to convey whether the machine needs attention, or if its environment needs attention.
Design-it

![image](https://user-images.githubusercontent.com/53172079/182923161-1c411c64-669e-41a7-8695-198d0945ae01.png)

**Assignment -4**

https://github.com/venu-shastri/design-patterns-summary/blob/main/DEBT_CODE.docx

1. Violation of SRP

public class Icon

{

    float speed, glow, energy;
    
    int x, y;

    public void move(IAction action)
    {
        action.Act();
    }
}

public interface IAction

{

    void Act();

}

public class Hopper : IAction

{
    
    bool visible; // need for hopper
    
    int xcoord, ycoord; // need for hopper

    public void Act() 
    { 
    
    }

}

public class Spinner : IAction

{
    
    bool clockwise; // need for spinner
    
    bool expand; // need for spinner

    public void Act() 
    { 
    }
    
}

public class Slider : IAction

{
    
    bool vertical; // need for slider
 
    int distance; // need for slider

    public void Act() 
    { 
    }
    
}

<img width="503" alt="image" src="https://user-images.githubusercontent.com/53172079/181908214-13aa777e-2c7a-42d1-a759-cf428d2c3660.png">


**Assignment 5**

Let us build a sales reporting application for the management of a store with multiple departments. The features of the application include:
Users should be able to select a specific department they are interested in.

Upon selecting a department, two types of reports are to be displayed:

Monthly report — A list of all transactions for the current month for the selected department.

YTD sales chart — A chart showing the year-to-date sales for the selected department by month. Whenever a different department is selected, both reports should be refreshed with the data for the currently selected department

Mediator Pattern

<img width="434" alt="image" src="https://user-images.githubusercontent.com/53172079/182024090-cc066340-89c9-451f-81f3-c7f8914a764b.png">

Visitor Pattern

<img width="550" alt="image" src="https://user-images.githubusercontent.com/53172079/182922131-61104506-ffa2-4e5d-ac7e-0b1991f675ca.png">

**Assignment 6**
Refactor Below Code and remove code pollution

public class ConcreteCalculator : ICalculator

{

    public int Add(int x, int y)

    {
        
	Print("Add(x={0}, y={1})", x, y);
        
	var addition = x + y;
        
	Print("result={0}", addition);
        
	return addition;
    }
}

**Refactored**

Decorator Pattern

public interface ICalculator

{

   int Add(int x, int y)

}

public class LoggingCalculator : ICalculator

{

   private readonly ICalculator calculator;
 
   public LoggingCalculator(ICalculator calculator)
 
   {
 
      this.calculator = calculator;
 
   }
 
   public int Add(int x, int y)
 
   {
    
      Console.WriteLine("Add(x={0}, y={1})", x, y);
    
      var result = calculator.Add(x, y);
    
      Console.WriteLine("result={0}", result);
    
      return result;
 
   }

}

public class ConcreteCalculator : ICalculator

{
 
   public int Add(int x, int y)
 
   {
    
      return x + y;
 
   }

}

**Assignment - 7**
Let us consider an online job site that receives XML data files from different employers with current openings in their organizations. When the number of vacancies is small, employers can enter details online. When the number of vacancies is large, employers upload details in the form of an XML file. Once the XML file is received, it needs to be parsed and processed. Let us assume the XML file to have the following details:

a.Job title

b.Minimum qualifications

c.Medical insurance

d.Dental insurance

e.Vision care

f.Minimum number of hours of work

g.Paid vacation

h.Employer name

i.Employer address 

In general, Details from (c) through (i) are all considered being the same for all jobs posted by a given employer. Apply the required pattern to design the process of parsing the input XML file and creating different JOB objects

Flyweight Pattern

<img width="340" alt="image" src="https://user-images.githubusercontent.com/53172079/182039609-03765cae-b304-4a61-a656-7f74f4ed0a87.png">
 
<img width="427" alt="Assignment7" src="https://user-images.githubusercontent.com/53172079/182904015-7f7bc32c-f11f-4af7-9c5d-c7aa1fc5c21c.PNG">
