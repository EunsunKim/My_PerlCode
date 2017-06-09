## Dynamic Image Presentation, Login, and Purchase System

  * This program was school project, 2016
  

## Sample  http://zenit.senecac.on.ca/~int322_163sa07/


## Job ordered discription

  * Design and code with Perl CGI web page as an interactive order and purchase interface for your virtual client

## History

   1. Created New Perl CGI Web Login CGI/Web Page   
   
     [1] Two labels
     [2] two textboxes : username value, user’s password
     [3] one button    : submit the entered values back to the Login Perl CGI on Apache server for validation
     
     - This validation process must be conducted by verifying entered credentials against the content of user.txt file
     
     
   2. Modifed Existing Dynamic Image Presentation CGI/Web Page
   
     [1] When clicked login button, the link is to invoke the download and display process of the new Login web page
     [2] After successful login, the Dynamic Image Presentation web page is to be redisplayed with user name
   
   
   3. Created New MySQL Table
   
    * created a Gallery table which is consist of columns FILENAME, DESCRIPTION, PRICE and STATUS
   
   
   4. Created New Perl CGI Order and Purchase Web Page
   
    [1] One button with the caption BUY and the other with the caption CANCEL
    [2] When clicking the CANCEL button, a message box showing MAYBE NEXT TIME is to be displayed
    [3] After clicking the OK button on either message box, the control is to return to the Dynamic Image Presentation web page
    [4] clicking the BUY button, the status of that image must be changed from “A” (Available) to “S” (Sold)
   
   
   5. Modifying Existing Dynamic Image Presentation Web Page
   
    * Purchase works only after logging on successfully
   
   
    ## Sample code
    
    if(!$value)
    {	
	    my $dbh = DBI->connect("DBI:mysql:database=$serverDb;host=$serverName;port=$serverPort", $serverUser, $serverPass);
	    my $sql = "UPDATE MYNAME SET STATUS = 'A' WHERE STATUS = 'S'";
    	my $sth = $dbh->prepare($sql);
	    $sth -> execute() or die $DBI::errstr;
	    $sth->finish();
	    $dbh->disconnect();
    }
    my $dbh = DBI->connect("DBI:mysql:database=$serverDb;host=$serverName;port=$serverPort", $serverUser, $serverPass);
    my $sth = $dbh->prepare( "SELECT FILENAME, DESCRIPTION FROM INT322SA07 WHERE STATUS = 'A'" );
    $sth -> execute();

    while ( my @row = $sth->fetchrow_array())
    {
	    push @filename, $row[0];
	    push @descriptions, $row[1];
    }
    $dbh->disconnect();
   
   
