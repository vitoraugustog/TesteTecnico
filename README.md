Olá seja bem vindo (a) apresento aqui um teste técnico que realizei para uma entrevista, onde fica mais claro meu conhecimento em BDD, espero que aproveite!

<strong>BDD</strong>
<br>Given store is open
<br>And POS is up and running
<br>And crew is logged in 
<br>When customer orders a meal
<br>Then crew register the order in the POS
<br>And order is sent to the kitchen
<br>And order is displayed in the kitchen monitors
<br>When order is in the kitchen
<br>Then order is prepared
<br>And delivered to the customer</br>

<strong>BDD VALIDATION</strong>
<br>Given store is open // Validate if store is open -- Check the store status
<br>And POS is up and running // Validate if POS up and running -- We can use some command which will be called by the automation in order to check the POS status
<br>And crew is logged in // Validate if the login was success -- We can check the login response after the login API is called
<br>When customer orders a meal
<br>Then crew register the order in the POS // Validate if the order is register properly -- The automation can check if the order registration result is success
<br>And order is sent to the kitchen
<br>And order is displayed in the kitchen monitors // Validate if the order is displayed in the monitor -- The automation can use some screen validator tool in order to check what is displayed in the monitor
<br>When order is in the kitchen
<br>Then order is prepared 
<br>And delivered to the customer // Validate if the order is finalized in the POS System -- The automation can use a command to check the order status</br>

<strong>PSEUDO LANGUAGE</strong>
  <br>using library commands; // For this automation i'am considering to use a pseudo library called commands</br>

commands.OpenStore ();
commands.RunPos ();

variable storeStatus=commands.GetStoreStatus ();

 if (storeStatus==open) { 
   continue;
 }

  else { 
    Write testfailed - Failed the storeStatus;
    Endtest;
  }

variable posStatus=commands.GetPosStatus ();

 if (posStatus==isRunning) { 
   Continue;
 }
  
  else { 
    Write testfailed - Failed the posStatus;
    Endtest;
  }

variable loginResponse=commands.CrewLogin ();

 if (loginResponse==success) { 
   Continue;
 }
  
  else { 
    Write testfailed - Failed the loginResponse;
    Endtest;
  }

variable registerOrderResponse=commands.RegisterOrder();

 if (registerOrderResponse==success) { 
   Continue;
 }
  
  else { 
    Write testfailed - Failed the registerOrderResponse;
    Endtest;
  }

variable isOrderDisplayed=commands.CheckOrderIsDisplayedInTheMonitor();

if (isOrderDisplayed==true) { 
   Continue;
 }
  
  else { 
    Write testfailed - Failed the isOrderDisplayed;
    Endtest;
  }

variable orderStatus=commands.GetOrderStatus();

if (orderStatus==finalized) { 
    Write testpassed;
    Endtest;
}

else {
    Write testfailed - Failed the orderStatus;
    Endtest;
}
