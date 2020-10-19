```c#
using System;
using System.Collections;

public interface IPayment{
	void Pay();
}

public class CreditCard : IPayment{
	public void Pay(){
		Console.WriteLine("Paid from Credit Card");
	}
}

public class PayTm : IPayment{
	public void Pay(){
		Console.WriteLine("Paid from PayTm");
	}
}

public class UPI : IPayment{
	public void Pay(){
		Console.WriteLine("Paid from UPI");
	}
}

public class PaymentType{
	
	public IPayment GetPaymentObject(string paymentMethod){
		Hashtable ht = new Hashtable();
		ht.Add("upi", new UPI());
		ht.Add("creditcard", new CreditCard());
		ht.Add("paytm", new PayTm());
		
		return (IPayment)ht[paymentMethod];
	}	
}
					
public class Program
{
	public static void Main()
	{			
		PaymentType pt = new PaymentType();		
		IPayment pay = pt.GetPaymentObject("upi");
		pay.Pay();
	}
}
```

