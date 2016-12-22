---
title: "Como transformar XML usando LINQ (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "LINQ to XML [Visual Basic], transformando XML"
  - "XML [Visual Basic], transformando"
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como transformar XML usando LINQ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[Literais XML](../../../../visual-basic/language-reference/xml-literals/index.md) torna fácil ler XML de uma fonte e transfomá\-lo num novo formato de XML.  Você pode aproveitar consultas LINQ para recuperar o conteúdo a transformar, ou alterar contexto num documento existente para um novo formato XML.  
  
 O exemplo neste tópico transforma conteúdo de um documento\-fonte XML num HTML a ser visto num navegador.  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### Para transformar um documento XML  
  
1.  No Visual Studio, crie um novo projeto Visual Basic no modelo de projeto **Aplicativo Console**.  
  
2.  Dê um clique duplo no arquivo Module1.vb criado no projeto para modificar o código Visual Basic.  Adicione o seguinte código ao `Sub Main` do módulo `Module1`.  Este código cria o documento XML fonte como um objeto <xref:System.Xml.Linq.XDocument>.  
  
    ```vb#  
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
  
     [Como carregar XML a partir de um arquivo, cadeia de caracteres ou fluxo](../Topic/How%20to:%20Load%20XML%20from%20a%20File,%20String,%20or%20Stream%20\(Visual%20Basic\).md).  
  
3.  Após o código criar o documento XML fonte, adicione o código a seguir para recuperar todos os elementos \<Book\> do objeto e transforme\-os num documento HTML.  A lista de elementos \<Book\> é criada usando uma consulta LINQ que retorna uma coleção de objetos <xref:System.Xml.Linq.XElement> que contém o HTML transformado.  Você pode usar expressões embutidas para pôr valores do documento fonte no novo formato XML.  
  
     O documento HTML resultante é gravado num arquivo usando o método <xref:System.Xml.Linq.XElement.Save%2A>.  
  
    ```vb#  
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
  
4.  Após `Sub Main` de `Module1`, adicione um novo método \(`Sub`\) para transformar um nó \<Description\> no formato HTML especificado.  Este método é chamado pelo código no passo anterior e é usado para preservar o formato de elementos \<Description\>.  
  
     Este método substitui subelementos do elemento \<Description\> com HTML.  O método `ReplaceWith` é usado para preservar a localização de subelementos.  O conteúdo transformado do elemento \<Description\> está incluído num elemento de parágrafo \(\<p\>\) HTML.  A propriedade <xref:System.Xml.Linq.XContainer.Nodes%2A> é usada para recuperar o conteúdo transformado do elemento \<Description\>.  Isto assegura que subelementos são incluídos no conteúdo transformado.  
  
     Adicione o seguinte código após `Sub Main` de `Module1`.  
  
    ```vb#  
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
  
5.  Salve suas alterações.  
  
6.  Pressione F5 para executar o código.  O documento salvo resultante vai parece\-se com o seguinte:  
  
    ```  
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
  
## Consulte também  
 [Literais XML](../../../../visual-basic/language-reference/xml-literals/index.md)   
 [Manipulando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [Como carregar XML a partir de um arquivo, cadeia de caracteres ou fluxo](../Topic/How%20to:%20Load%20XML%20from%20a%20File,%20String,%20or%20Stream%20\(Visual%20Basic\).md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)