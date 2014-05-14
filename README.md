import java.util.Date;
import java.util.Scanner;

public class UpdateGalleryFile 
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
                System.out.println ("Please enter the following for the sold painting you want to sell: \n"
                    + "\t   Last name of Artist then press <ENTER> and Painting Title then press <ENTER>"); 

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
            System.out.println("The Actual Purchase Price is: " +sold.getActualPurchasePrice());
            System.out.println("The Target Selling Price is: " +sold.getTargetSellingPrice());
	}

	if (!found)
	{
	    return;
	}
        System.out.println("\n\nDo you want to buy this painting? y/n");
        char response = UserInterface.getChar();
        if(response == 'y')
        {                
            

            while (!done)
            {
                    while (!done)
                    {
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
                        done=true;

                    }

                    if (!done)
                    {
                        sold.print ();
                        UserInterface.pressEnter();
                    }


                sold.save ();
            }
        }
    }
    catch (Exception e)
    {
	    System.out.println ("***** Error: UpdateSoldPaintingsFile() () *****");
	    System.out.println ("\t" + e);
    }

  }
    //Desc: updates the GalleryPainting file by searching for the last name of the artist
    //      and painting title
    //Pre: the GalleryPaintings.dat file must exist
    //Post: The GalleryPaintings file is updated
    public static void updateSoldPainting()
    {

    try
    {
	boolean	      done = false;		        // terminates while-loop
	boolean	      found = false;		        // tells if investment is found
	char	      c;			        // character entered by user
	String        title;                            // buffer for line of characters
        String        lName;
	char	      choice;	                        // user's choice
        SoldPainting    sold = new SoldPainting();    // investment to be modified

	while (!found && !done)
	{
            System.out.println ("Please enter the following for the sold painting you want to update "
                    + "\t   Last name of Artist then press <ENTER> "
                    + "and Painting Title then press <ENTER>"); 

            lName = UserInterface.getString();
            title = UserInterface.getString();

	    found = sold.find (lName,title);

	    if (!found)
	    {
		System.out.println ("Painting by " + lName +" Titled "+ title + " was not found.");
		System.out.println ("Would you like to enter another Artist Name and Title?");

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

                    System.out.println ("\t           UPDATE SOLD PAINTING\n\n"); //this needs to change based on what updates we allow
                    System.out.println ("\t Oglesby Art Pricing System\n\n");
                    System.out.println ("\t        1. Update Artist first name\n");
                    System.out.println ("\t        2. Update Artist last name\n");
                    System.out.println ("\t        3. Update Artist fashionability value\n");
                    System.out.println ("\t        4. Exit to menu\n\n");
                    System.out.println ("Enter your choice and press <ENTER>: ");

                    try
                    {
			choice = UserInterface.getChar();

			switch (choice)
			{
                            case '1':
                                sold.updateArtistsFirstName();
                                break;

                            case '2':
                                sold.updateArtistsLastName();
                                break;
                            
                            case '3':
                              //sold.updateFashionabilityValue();
                              break;

                            case '4':
                            case '\n':
                              done = true;
				  break;

                            default:
                              System.out.println ("\n\nNot a valid choice\n");
                              UserInterface.pressEnter();
                              break;
			}
                     }
			catch (Exception e)
			{
			    System.out.println ("***** Error: UpdateGalleryFile.updateSoldPainting() *****");
			    System.out.println ("\t" + e);
			}

			if (!done)
			{
		            sold.print ();
		            UserInterface.pressEnter();
			}
                }
        }

	sold.save ();
    }
    catch (Exception e)
    {
	    System.out.println ("***** Error: UpdateGalleryFile.updateSoldPainting() () *****");
	    System.out.println ("\t" + e);
    }

  }
    
        //Desc: updates the GalleryPainting file by searching for the last name of the artist
    //      and painting title
    //Pre: the GalleryPaintings.dat file must exist
    //Post: The GalleryPaintings file is updated
    public static void updateBoughtPainting()
    {

    try
    {
	boolean	      done = false;		        // terminates while-loop
	boolean	      found = false;		        // tells if investment is found
	char	      c;			        // character entered by user
	String        title;                            // buffer for line of characters
        String        lName;
	char	      choice;	                        // user's choice
        BoughtPainting    b = new BoughtPainting();    // investment to be modified

	while (!found && !done)
	{
            System.out.println ("Please enter the following for the Bought painting you want to update "
                    + "\t   Last name of Artist then press <ENTER> "
                    + "and Painting Title then press <ENTER>"); 

            lName = UserInterface.getString();
            title = UserInterface.getString();

	    found = b.find (lName,title);

	    if (!found)
	    {
		System.out.println ("Painting by " + lName +" Titled "+ title + " was not found.");
		System.out.println ("Would you like to enter another Artist Name and Title?");

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

                    System.out.println ("\t           UPDATE BOUGHT PAINTING\n\n"); //this needs to change based on what updates we allow
                    System.out.println ("\t Oglesby Art Pricing System\n\n");
                    System.out.println ("\t        1. Update Artist first name\n");
                    System.out.println ("\t        2. Update Artist last name\n");
                    System.out.println ("\t        3. Update Artist fashionability value\n");
                    System.out.println ("\t        4. Exit to menu\n\n");
                    System.out.println ("Enter your choice and press <ENTER>: ");

                    try
                    {
			choice = UserInterface.getChar();

			switch (choice)
			{
                            case '1':
                                b.updateArtistsFirstName();
                                break;

                            case '2':
                                b.updateArtistsLastName();
                                break;
                            
                            case '3':
                              //b.updateFashionabilityValue();
                              break;

                            case '4':
                            case '\n':
                              done = true;
				  break;

                            default:
                              System.out.println ("\n\nNot a valid choice\n");
                              UserInterface.pressEnter();
                              break;
			}
                     }
			catch (Exception e)
			{
			    System.out.println ("***** Error: UpdateGalleryFile.updateBoughtPainting() *****");
			    System.out.println ("\t" + e);
			}

			if (!done)
			{
		            b.print ();
		            UserInterface.pressEnter();
			}
                }
        }

	b.save ();
    }
    catch (Exception e)
    {
	    System.out.println ("***** Error: UpdateGalleryFile.updateBoughtPainting() () *****");
	    System.out.println ("\t" + e);
    }
  }
}
