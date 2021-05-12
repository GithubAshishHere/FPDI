# FPDI
How to Configure and use FPDI using Laravel


1. Go to the link : https://packagist.org/packages/setasign/fpdf For More Information

You can install FPDF using below directly run composer:
 composer require setasign/fpdi


You can also install by copy and paste below code in composer.json
Or

1. Include below code in composer.json file:

{
    "require": {
       "setasign/fpdi": "^2.0"

    }
}


2. Make Controller using below line:

php artisan make:controller DemoController


3. Add below function inside created controller


Now go to created controller and add below function
You will get this project file. I will upload to GitHub. :)

So, I already have copy of below code.

public function Addtopdf()
    {

         $pdf = new Fpdi();


        // add a page
        $pdf->AddPage();
        $pdf->SetFont('Arial','B',14);

        // set the source file
        $path = public_path("white.pdf");

        $pdf->setSourceFile($path);

        // import page 1
        $tplId = $pdf->importPage(1);


        // use the imported page and place it at point 10,10 with a width of 100 mm
        $pdf->useTemplate($tplId, null, null, null, 210, true);

        $pdf->SetXY(90, 110);
        $pdf->Write(0.1,"Demo Test");

	// Preview PDF
        $pdf->Output('I',"Demotest.pdf");

		// Download PDF
//Download use D
	  $pdf->Output(‘D’,”Demotest.pdf");

	// Save PDF to Particular path or project path

	  $pdf->Output(‘F’,”/new/yourfoldername/Demotest.pdf");

    }


4. Add Route to web.php 
Route::get('/generatePDF',[DemoController::class,'Addtopdf']);

5. Add white.pdf from below link.
You can get blank pdf from below link
http://www.smartcaptech.com/wp-content/uploads/sample.pdf
You have to add this pdf inside public folder.

After adding white.pdf let run the project.


Run Below Commands
php artisan serve

Copy link to browser.
http://127.0.0.1:8000/generatePDF



FPDI Output
	•	I: send the file inline to the browser. The PDF viewer is used if available.
	•	D: send to the browser and force a file download with the name given by name.
	•	F: save to a local file with the name given by name (may include a path).
	•	S: return the document as a string.

Above are the output.
