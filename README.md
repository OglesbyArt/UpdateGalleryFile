
import java.util.Date;
import java.util.Scanner;

public class UpdateSoldPaintingsFile 
{
    
    //Desc: Adds a painting to the sold painting file
    //Pre: SoldPainting.txt must exsist
    //Post: The changes are made to the painting in the text file
    public static void addSoldPaintingFile() 
    {

        try
        {
            boolean	      done = false;		        // terminates while-loop
            boolean	      found = false;		        // tells if investment is found
            char	      c;			        // character entered by user
            String        title;                            // buffer for line of characters
            String        lName;
            char	      choice;	                        // user's choice
            SoldPainting sold = new SoldPainting();    

            while (!found && !done)
            {
                System.out.println ("Please enter last name of Artist and the" +
                                " painting title you have sold : ");

            lName = UserInterface.getString();
            title = UserInterface.getString();

	    found = sold.find (lName, title);

	    if (!found)
	    {
		System.out.println ("Painting by " + lName +" Titled "+ title + " was not found.");
		System.out.println ("Would you like to enter another Painting Name? enter 'y' or 'n'");

		choice = UserInterface.getChar();

		if (choice == 'n')
		{
		  done = true;
		}
            }
	}

	if (!found)
	{
	    return;
	}

	while (!done)
	{
		while (!done)
		{
                    UserInterface.clearScreen ();

                    System.out.println ("\t           ADD SOLD PAINTING\n\n");
                    System.out.println ("\t Oglesby Art Pricing System\n\n");
                    System.out.println ("\t        Please enter the Date of sale: ");
                    String temp = UserInterface.getString();
                    Date date = new Date(temp);
                    sold.setDateOfSale(date);
                    System.out.println ("\t        Please enter the Name of the Buyer (No longer than 30 characters): ");
                    String name = UserInterface.getString();
                    sold.setNameOfBuyer(name);
                    System.out.println ("\t        Please enter the Address of buyer (No longer than 40 characters): ");
                    String address = UserInterface.getString();
                    sold.setAddressOfBuyer(address);

                }

		if (!done)
		{
	            sold.print ();
	            UserInterface.pressEnter();
		}
        }

	sold.save ();
    }
    catch (Exception e)
    {
	    System.out.println ("***** Error: UpdateSoldPaintingsFile() () *****");
	    System.out.println ("\t" + e);
    }

  } 
	
    //Desc: Removes a painting from the text file
    //Pre: SoldPainting.txt must exsist
    //Post: The painting is removed from the text file
    public static void deletePaintingFile()
    {
        Scanner s = new Scanner(System.in);
	System.out.println ("Enter Name of Artist and title of work of File "
                + "you want to delete: ");
	String name = s.nextLine();
        String title = s.nextLine();
		
        //call delete method
    }
}
