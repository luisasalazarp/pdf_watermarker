# PDF Watermarker

PDFWatermarker .NET enables you to add an image as a watermark to existing PDF files. It uses PdfSharpCore that allows you to write PDF files.

### Using it, you can:

* Use jpg and png (with alpha channels or transparency) files.

* Easily position the watermark on the pages of the PDF file

## Run tests

We have 3 kinds of test:

### 1. Application Test:

#### To run Application Test you have to execute the following command:
```
dotnet test pdf-watermarker-net/test/pdf-watermarker-test/Application/Watermarker.Application.Test/Watermarker.Application.Test.csproj
```
#### Or move to:
```
pdf-watermarker-net/test/pdf-watermarker-test/Application/Watermarker.Application.Test
```
#### Then run :
```
dotnet test Watermarker.Application.Test.csproj
```

### 2. Domain Test:

#### To run Application Test you have to execute the following command:
```
dotnet test pdf-watermarker-net/test/pdf-watermarker-test/Domain/Watermarker.Domain.Test/Watermarker.Domain.Test.csproj
```
#### Or move to:
```
pdf-watermarker-net/test/pdf-watermarker-test/Domain/Watermarker.Domain.Test
```
#### Then run:
```
dotnet test Watermarker.Domain.Test.csproj
```

### 3. Infrastructure Test:

#### To run Application Test you have to execute the following command:
```
dotnet test pdf-watermarker-net/test/pdf-watermarker-test/Infrastructure/Watermarker.Infrastructure.Test/Watermarker.Infrastructure.Test.csproj
```
#### Or move to:
```
pdf-watermarker-net/test/pdf-watermarker-test/Infrastructure/Watermarker.Infrastructure.Test
```
#### Then run:
```
dotnet test Watermarker.Infrastructure.Test.csproj
```
## Run tests (Example)

Passed test:

![ScreenShot](https://github.com/Lumbar/pdf-watermarker-net/blob/master/Images/test-ok.png)

Non Passed test:

![ScreenShot](https://github.com/Lumbar/pdf-watermarker-net/blob/master/Images/test-ko.png)

## Test API with Swagger 

To Launch the app the app you have 2 options:

#### Option A

1. Go to the clonned or downloaded project and move to:
     ```  
    pdf-watermarker-net/src/pdf-watermarker/Infrastructure/Watermarker.API folder.
    ```
2. Then run:
   ````
   dotnet run Watermarker.API.csproj
   ````

#### Option B

1. Launch the app with the folling command:
    ```
    dotnet run pdf-watermarker-net/src/pdf-watermarker/Infrastructure/Watermarker.API/Watermarker.API.csproj
    ```
#### Then you have to:

1. Go to:
   ```
   https://localhost:{PORT}/swagger/index.html
   ```
   **NOTE: {PORT} may change so you will see when run the app in CLI Output, Example below.**


2. For each use case click on "Try it out" and add the necessary parameters you will see an example. Then click on "Execute"

## Test API with Swagger (Example)

Run API:
![ScreenShot](https://github.com/Lumbar/pdf-watermarker-net/blob/master/Images/dotnet-run.png)

Swagger UI:
![ScreenShot](https://github.com/Lumbar/pdf-watermarker-net/blob/master/Images/swagger.png)

### Results:

You will see the results in the same folder of the input file, so, depending if you tested the app in swagger or by the test you will have:

#### Test: Results in the Assets folder contained in the project.
#### Swagger: Same folder as the input file.


## How we work:

Specify path to image:
```
PDFWatermark watermark = new PDFWatermark("C:\myimage.png");
```

Set the position:
```
watermark.SetPosition(Position.TopLeft);
```

Place watermark behind original PDF content. Default behavior places it over the content:
```
watermark.SetAsBackground();
```

Specify the path to the existing pdf, the path to the new pdf file, and the watermark object, we decided to use the same path:
```
PDFWatermarker watermarker = new PDFWatermarker("C:\test.pdf", "C:\output.pdf", watermark);
```

Set page range. Use 1-based index:
```
watermarker.SetPageRange(1, 5);
```

Save the new PDF to its specified location:
```
watermarker.SavePdf();
```

Five positions can be used. 'center' is the default:

* center = 0
* topleft = 1
* topright = 2
* bottomright = 3
* bottomleft = 4
