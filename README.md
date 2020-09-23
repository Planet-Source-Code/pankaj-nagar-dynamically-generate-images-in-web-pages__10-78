<div align="center">

## Dynamically Generate Images in Web Pages


</div>

### Description

The .NET Framework includes a rich set of classes for generating images. You can use these classes to generate images in a variety of different formats, such as GIF, JPEG, TIFF, PNG, and BMP. You can also use these classes to draw complex shapes, including arcs, polygons, and Bezier curves.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Pankaj Nagar](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/pankaj-nagar.md)
**Level**          |Beginner
**User Rating**    |4.6 (37 globes from 8 users)
**Compatibility**  |ASP\.NET
**Category**       |[Internet/ Browsers/ HTML](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/internet-browsers-html__10-9.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/pankaj-nagar-dynamically-generate-images-in-web-pages__10-78/archive/master.zip)





### Source Code

<html>
<head>
<meta name="GENERATOR" content="Microsoft FrontPage 5.0">
<meta name="ProgId" content="FrontPage.Editor.Document">
<meta http-equiv="Content-Type" content="text/html; charset=windows-1252">
<title>New Page 1</title>
</head>
<body>
<p>If you want to dynamically generate an image and display the image in a Web
Page, then you actually need to create two ASP.NET pages. You create one page
that generates the byte data for the actual image. This page is then displayed
in a second page, the display page, with an HTML &lt;img&gt;&nbsp; tag.<br>
This example creates a pair of pages that displays a red circle. We'll generate
a GIF image for the circle in an ASP.NET page named Circle.aspx. </p>
<p>1. Circle.aspx<br>
-----------<br>
<br>
&lt;%@ Page ContentType=&quot;image/gif&quot; %&gt;<br>
&lt;%@ Import namespace=&quot;System.Drawing&quot; %&gt;<br>
&lt;%@ Import namespace=&quot;System.Drawing.Imaging&quot; %&gt;<br>
&lt;Script Runat=&quot;Server&quot;&gt;<br>
Sub Page_Load<br>
Dim objBitmap As Bitmap<br>
Dim objGraphics As Graphics<br>
' Create Bitmap<br>
objBitmap = New Bitmap( 200, 200 )<br>
' Initialize Graphics Class<br>
objGraphics = Graphics.FromImage( objBitmap )<br>
objGraphics.FillEllipse( Brushes.Red, 0, 0, 200, 200 )<br>
' Display Bitmap<br>
objBitmap.Save( Response.OutputStream, ImageFormat.Gif )<br>
End Sub<br>
&lt;/Script&gt;<br>
<br>
<br>
The purpose of the ContentType directive that appears at the very top of the
page is to actually pretend that ASP .NET page to be a GIF image. When the page
is requested, the ContentType directive tells the Web browser that it should
expect a GIF image instead of a normal HTML page.<br>
Normally you will need to open the page in a second page to use it effectively
in a web page.<br>
The second page contains an HTML &lt;img&gt; tag that loads the above page. This page
contains normal HTML content that appears around the image.<br>
<br>
2. <u>DisplayCircle.aspx</u><br>
<br>
<br>
&lt;html&gt;<br>
&lt;head&gt;&lt;title&gt;DisplayCircle.aspx&lt;/title&gt;&lt;/head&gt;<br>
&lt;body&gt;<br>
&lt;h1&gt;Here is an image:&lt;/h1&gt;<br>
&lt;img src=&quot;Circle.aspx&quot;&gt;<br>
&lt;h1&gt;The image appears above!&lt;h1&gt;<br>
&lt;/body&gt;<br>
&lt;/html&gt;<br>
<br>
<br>
The Web browser treats the Circle.aspx page as a normal GIF image. It has no
idea that the image was dynamically generated in an ASP.NET page.</p>
</body>
</html>

