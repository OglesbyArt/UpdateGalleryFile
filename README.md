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
	int	      choice;	                        // user's choice
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
                    System.out.println ("\t        3. Update Title of Work\n");
                    System.out.println ("\t        4. Update Date of Work\n");
                    System.out.println ("\t        5. Update Classification\n");
                    System.out.println ("\t        6. Update Height\n");
                    System.out.println ("\t        7. Update Width\n");
                    System.out.println ("\t        8. Update Medium\n");
                    System.out.println ("\t        9. Update Subject\n");
                    System.out.println ("\t        10. Update Date of Purchase\n");
                    System.out.println ("\t        11. Update Name of Seller\n");
                    System.out.println ("\t        12. Update Address of Seller\n");
                    System.out.println ("\t        13. Update Actual Purchase Price\n");
                    System.out.println ("\t        14. Update Date of Sale\n");
                    System.out.println ("\t        15. Update Name of Buyer\n");
                    System.out.println ("\t        16. Update Address of Buyer\n");
                    System.out.println ("\t        17. Update Actual Selling Price\n");
                    System.out.println ("\t        18. Exit to menu\n\n");
                    System.out.println ("Enter your choice and press <ENTER>: ");
                    try
                    {
			choice = UserInterface.getInt();

			switch (choice)
			{
                            case 1:
                                sold.updateArtistsFirstName();
                                break;

                            case 2:
                                sold.updateArtistsLastName();
                                break;
                            
                            case 3:
                              sold.updateTitleOfWork();
                              break;
                                
                            case 4:
                              sold.updateDateOfWork();
                              break;
                                
                            case 5:
                              sold.updateClassification();
                              break;
                            
                            case 6:
                              sold.updateHeight();
                              break;
                                
                            case 7:
                              sold.updateWidth();
                              break;
                                
                            case 8:
                              sold.updateMedium();
                              break;
                                
                            case 9:
                              sold.updateSubject();
                              break;
                                
                            case 10:
                              sold.updateDateOfPurchase();
                              break;
                                
                            case 11:
                              sold.updateNameOfSeller();
                              break;
                                
                            case 12:
                              sold.updateAddressOfSeller();
                              break;
                                
                            case 13:
                              sold.updateActualPurchasePrice();
                              break;
                                
                            case 14:
                              sold.updateDateOfSale();
                              break;
                                
                            case 15:
                              sold.updateNameOfBuyer();
                              break;
                                
                            case 16:
                              sold.updateAddressOfBuyer();
                              break;
                                
                            case 17:
                              sold.updateActualSellingPrice();
                              break;

                            case 18:
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
	int	      choice;	                        // user's choice
        BoughtPainting    b = new BoughtPainting();    // painting to be modified

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

                    System.out.println ("\t           UPDATE SOLD PAINTING\n\n"); //this needs to change based on what updates we allow
                    System.out.println ("\t Oglesby Art Pricing System\n\n");
                    System.out.println ("\t        1. Update Artist first name\n");
                    System.out.println ("\t        2. Update Artist last name\n");
                    System.out.println ("\t        3. Update Title of Work\n");
                    System.out.println ("\t        4. Update Date of Work\n");
                    System.out.println ("\t        5. Update Classification\n");
                    System.out.println ("\t        6. Update Height\n");
                    System.out.println ("\t        7. Update Width\n");
                    System.out.println ("\t        8. Update Medium\n");
                    System.out.println ("\t        9. Update Subject\n");
                    System.out.println ("\t        10. Update Date of Purchase\n");
                    System.out.println ("\t        11. Update Name of Seller\n");
                    System.out.println ("\t        12. Update Address of Seller\n");
                    System.out.println ("\t        13. Update Actual Purchase Price\n");
                    System.out.println ("\t        14. Exit to menu\n\n");
                    System.out.println ("Enter your choice and press <ENTER>: ");
                    try
                    {
			choice = UserInterface.getInt();

			switch (choice)
			{
                            case 1:
                                b.updateArtistsFirstName();
                                break;

                            case 2:
                                b.updateArtistsLastName();
                                break;
                            
                            case 3:
                              b.updateTitleOfWork();
                              break;
                                
                            case 4:
                              b.updateDateOfWork();
                              break;
                                
                            case 5:
                              b.updateClassification();
                              break;
                            
                            case 6:
                              b.updateHeight();
                              break;
                                
                            case 7:
                              b.updateWidth();
                              break;
                                
                            case 8:
                              b.updateMedium();
                              break;
                                
                            case 9:
                              b.updateSubject();
                              break;
                                
                            case 10:
                              b.updateDateOfPurchase();
                              break;
                                
                            case 11:
                              b.updateNameOfSeller();
                              break;
                                
                            case 12:
                              b.updateAddressOfSeller();
                              break;
                                
                            case 13:
                              b.updateActualPurchasePrice();
                              break;

                            case 14:
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
