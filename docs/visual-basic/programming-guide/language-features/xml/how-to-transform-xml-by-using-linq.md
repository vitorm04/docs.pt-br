---
title: 'Como: Transformar XML usando LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: 08378775f2c30d8ebfcc4f7ceea6fc3ecb2066e5
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003256"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a><span data-ttu-id="574de-102">Como: Transformar XML usando LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="574de-102">How to: Transform XML by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="574de-103">Os [literais XML](../../../../visual-basic/language-reference/xml-literals/index.md) facilitam a leitura de XML de uma fonte e a transformação para um novo formato XML.</span><span class="sxs-lookup"><span data-stu-id="574de-103">[XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) make it easy to read XML from one source and transform it to a new XML format.</span></span> <span data-ttu-id="574de-104">Você pode aproveitar as consultas LINQ para recuperar o conteúdo para transformar ou alterar o conteúdo de um documento existente para um novo formato XML.</span><span class="sxs-lookup"><span data-stu-id="574de-104">You can take advantage of LINQ queries to retrieve the content to transform, or change content in an existing document to a new XML format.</span></span>  
  
 <span data-ttu-id="574de-105">O exemplo neste tópico transforma o conteúdo de um documento de origem XML em HTML a ser exibido em um navegador.</span><span class="sxs-lookup"><span data-stu-id="574de-105">The example in this topic transforms content from an XML source document to HTML to be viewed in a browser.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-transform-an-xml-document"></a><span data-ttu-id="574de-106">Para transformar um documento XML</span><span class="sxs-lookup"><span data-stu-id="574de-106">To transform an XML document</span></span>  
  
1. <span data-ttu-id="574de-107">No Visual Studio, crie um novo projeto de Visual Basic no modelo de projeto de **aplicativo de console** .</span><span class="sxs-lookup"><span data-stu-id="574de-107">In Visual Studio, create a new Visual Basic project in the **Console Application** project template.</span></span>  
  
2. <span data-ttu-id="574de-108">Clique duas vezes no arquivo Module1. vb criado no projeto para modificar o código de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="574de-108">Double-click the Module1.vb file created in the project to modify the Visual Basic code.</span></span> <span data-ttu-id="574de-109">Adicione o código a seguir ao `Sub Main` do módulo `Module1`.</span><span class="sxs-lookup"><span data-stu-id="574de-109">Add the following code to the `Sub Main` of the `Module1` module.</span></span> <span data-ttu-id="574de-110">Esse código cria o documento XML de origem como um objeto <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="574de-110">This code creates the source XML document as an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
    ```vb  
    Dim catalog =   
      <?xml version="1.0"?>  
        <Catalog>  
          <Book id="bk101">  
            <Author>Garghentini, Davide</Author>  
            <Title>XML Developer's Guide</Title>  
            <Price>44.95</Price>  
            <Description>  
              An in-depth look at creating applications  
              with <technology>XML</technology>. For   
              <audience>beginners</audience> or   
              <audience>advanced</audience> developers.  
            </Description>  
          </Book>  
          <Book id="bk331">  
            <Author>Spencer, Phil</Author>  
            <Title>Developing Applications with Visual Basic .NET</Title>  
            <Price>45.95</Price>  
            <Description>  
              Get the expert insights, practical code samples,   
              and best practices you need   
              to advance your expertise with <technology>Visual   
              Basic .NET</technology>.   
              Learn how to create faster, more reliable applications  
              based on professional,   
              pragmatic guidance by today's top <audience>developers</audience>.  
            </Description>  
          </Book>  
        </Catalog>  
    ```  
  
     <span data-ttu-id="574de-111">[Como: Carregar XML de um arquivo, Cadeia de caracteres ou fluxo @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="574de-111">[How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).</span></span>  
  
3. <span data-ttu-id="574de-112">Depois do código para criar o documento XML de origem, adicione o código a seguir para recuperar todos os elementos de > de @no__t 0Book do objeto e transformá-los em um documento HTML.</span><span class="sxs-lookup"><span data-stu-id="574de-112">After the code to create the source XML document, add the following code to retrieve all the \<Book> elements from the object and transform them into an HTML document.</span></span> <span data-ttu-id="574de-113">A lista de elementos de > de @no__t 0Book é criada usando uma consulta LINQ que retorna uma coleção de objetos <xref:System.Xml.Linq.XElement> que contêm o HTML transformado.</span><span class="sxs-lookup"><span data-stu-id="574de-113">The list of \<Book> elements is created by using a LINQ query that returns a collection of <xref:System.Xml.Linq.XElement> objects that contain the transformed HTML.</span></span> <span data-ttu-id="574de-114">Você pode usar expressões inseridas para colocar os valores do documento de origem no novo formato XML.</span><span class="sxs-lookup"><span data-stu-id="574de-114">You can use embedded expressions to put the values from the source document in the new XML format.</span></span>  
  
     <span data-ttu-id="574de-115">O documento HTML resultante é gravado em um arquivo usando o método <xref:System.Xml.Linq.XElement.Save%2A>.</span><span class="sxs-lookup"><span data-stu-id="574de-115">The resulting HTML document is written to a file by using the <xref:System.Xml.Linq.XElement.Save%2A> method.</span></span>  
  
    ```vb  
    Dim htmlOutput =   
      <html>  
        <body>  
          <%= From book In catalog.<Catalog>.<Book>   
              Select <div>  
                       <h1><%= book.<Title>.Value %></h1>  
                       <h3><%= "By " & book.<Author>.Value %></h3>  
                        <h3><%= "Price = " & book.<Price>.Value %></h3>  
                        <h2>Description</h2>  
                        <%= TransformDescription(book.<Description>(0)) %>  
                        <hr/>  
                      </div> %>  
        </body>  
      </html>  
  
    htmlOutput.Save("BookDescription.html")  
    ```  
  
4. <span data-ttu-id="574de-116">Após `Sub Main` de `Module1`, adicione um novo método (`Sub`) para transformar um nó \<Description > no formato HTML especificado.</span><span class="sxs-lookup"><span data-stu-id="574de-116">After `Sub Main` of `Module1`, add a new method (`Sub`) to transform a \<Description> node into the specified HTML format.</span></span> <span data-ttu-id="574de-117">Esse método é chamado pelo código na etapa anterior e é usado para preservar o formato dos elementos de > de @no__t 0Description.</span><span class="sxs-lookup"><span data-stu-id="574de-117">This method is called by the code in the previous step and is used to preserve the format of the \<Description> elements.</span></span>  
  
     <span data-ttu-id="574de-118">Esse método substitui os subelementos do elemento \<Description > com HTML.</span><span class="sxs-lookup"><span data-stu-id="574de-118">This method replaces sub-elements of the \<Description> element with HTML.</span></span> <span data-ttu-id="574de-119">O método `ReplaceWith` é usado para preservar o local dos subelementos.</span><span class="sxs-lookup"><span data-stu-id="574de-119">The `ReplaceWith` method is used to preserve the location of the sub-elements.</span></span> <span data-ttu-id="574de-120">O conteúdo transformado do elemento \<Description > está incluído em um elemento de parágrafo HTML (\<p >).</span><span class="sxs-lookup"><span data-stu-id="574de-120">The transformed content of the \<Description> element is included in an HTML paragraph (\<p>) element.</span></span> <span data-ttu-id="574de-121">A propriedade <xref:System.Xml.Linq.XContainer.Nodes%2A> é usada para recuperar o conteúdo transformado do elemento de > \<Description.</span><span class="sxs-lookup"><span data-stu-id="574de-121">The <xref:System.Xml.Linq.XContainer.Nodes%2A> property is used to retrieve the transformed content of the \<Description> element.</span></span> <span data-ttu-id="574de-122">Isso garante que os subelementos sejam incluídos no conteúdo transformado.</span><span class="sxs-lookup"><span data-stu-id="574de-122">This ensures that sub-elements are included in the transformed content.</span></span>  
  
     <span data-ttu-id="574de-123">Adicione o código a seguir após `Sub Main` de `Module1`.</span><span class="sxs-lookup"><span data-stu-id="574de-123">Add the following code after `Sub Main` of `Module1`.</span></span>  
  
    ```vb  
    Public Function TransformDescription(ByVal desc As XElement) As XElement  
  
      ' Replace <technology> elements with <b>.  
      Dim content = (From element In desc...<technology>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<b><%= content(i).Value %></b>)  
        Next  
      End If  
  
      ' Replace <audience> elements with <i>.  
      content = (From element In desc...<audience>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<i><%= content(i).Value %></i>)  
        Next  
      End If  
  
      ' Return the updated contents of the <Description> element.  
      Return <p><%= desc.Nodes %></p>  
    End Function  
    ```  
  
5. <span data-ttu-id="574de-124">Salve as alterações.</span><span class="sxs-lookup"><span data-stu-id="574de-124">Save your changes.</span></span>  
  
6. <span data-ttu-id="574de-125">Pressione F5 para executar o código.</span><span class="sxs-lookup"><span data-stu-id="574de-125">Press F5 to run the code.</span></span> <span data-ttu-id="574de-126">O documento salvo resultante será semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="574de-126">The resulting saved document will resemble the following:</span></span>  
  
    ```html  
    <?xml version="1.0"?>  
    <html>  
      <body>  
        <div>  
          <h1>XML Developer's Guide</h1>  
          <h3>By Garghentini, Davide</h3>  
          <h3>Price = 44.95</h3>  
          <h2>Description</h2>  
          <p>  
            An in-depth look at creating applications  
            with <b>XML</b>. For   
            <i>beginners</i> or   
            <i>advanced</i> developers.  
          </p>  
          <hr />  
        </div>  
        <div>  
          <h1>Developing Applications with Visual Basic .NET</h1>  
          <h3>By Spencer, Phil</h3>  
          <h3>Price = 45.95</h3>  
          <h2>Description</h2>  
          <p>  
            Get the expert insights, practical code   
            samples, and best practices you need   
            to advance your expertise with <b>Visual   
            Basic .NET</b>. Learn how to create faster,  
            more reliable applications based on  
            professional, pragmatic guidance by today's   
            top <i>developers</i>.  
          </p>  
          <hr />  
        </div>  
      </body>  
    </html>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="574de-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="574de-127">See also</span></span>

- [<span data-ttu-id="574de-128">Literais XML</span><span class="sxs-lookup"><span data-stu-id="574de-128">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="574de-129">Manipulando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="574de-129">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [<span data-ttu-id="574de-130">XML</span><span class="sxs-lookup"><span data-stu-id="574de-130">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- <span data-ttu-id="574de-131">[Como: Carregar XML de um arquivo, Cadeia de caracteres ou fluxo @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="574de-131">[How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)</span></span>
- [<span data-ttu-id="574de-132">LINQ</span><span class="sxs-lookup"><span data-stu-id="574de-132">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="574de-133">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="574de-133">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
