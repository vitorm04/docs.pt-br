---
title: 'Como: Transformar XML usando LINQ (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9f97466727064ea275c051b5916b0fb297e9e23a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a>Como transformar XML usando LINQ (Visual Basic)
[Literais XML](../../../../visual-basic/language-reference/xml-literals/index.md) mais fácil ler XML de uma fonte e transformá-lo em um novo formato XML. Você pode aproveitar consultas LINQ para recuperar o conteúdo para transformar ou alterar o conteúdo em um documento existente para um novo formato XML.  
  
 O exemplo neste tópico transforma conteúdo de um documento de origem XML para HTML para ser exibido em um navegador.  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-transform-an-xml-document"></a>Para transformar um documento XML  
  
1.  No Visual Studio, crie um novo projeto do Visual Basic no **aplicativo de Console** modelo de projeto.  
  
2.  Clique duas vezes no arquivo Module1. vb criado no projeto para modificar o código do Visual Basic. Adicione o seguinte código para o `Sub Main` do `Module1` módulo. Esse código cria o documento XML de origem como uma <xref:System.Xml.Linq.XDocument>objeto.</xref:System.Xml.Linq.XDocument>  
  
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
  
     [Como: carregar XML de um arquivo, cadeia de caracteres ou fluxo](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).  
  
3.  Após o código para criar o documento XML de origem, adicione o seguinte código para recuperar todos os \<livro > elementos do objeto e transformá-los em um documento HTML. A lista de \<livro > elementos é criada usando uma consulta LINQ que retorna uma coleção de <xref:System.Xml.Linq.XElement>objetos que contêm o HTML transformado.</xref:System.Xml.Linq.XElement> Você pode usar expressões inseridas para colocar os valores do documento de origem no novo formato XML.  
  
     O documento HTML resultante é gravado em um arquivo usando o <xref:System.Xml.Linq.XElement.Save%2A>método.</xref:System.Xml.Linq.XElement.Save%2A>  
  
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
  
4.  Depois de `Sub Main` de `Module1`, adicione um novo método (`Sub`) para transformar um \<descrição > nó no formato HTML especificado. Esse método é chamado pelo código na etapa anterior e é usado para preservar o formato do \<descrição > elementos.  
  
     Este método substitui subelementos do \<descrição > elemento HTML. O `ReplaceWith` método é usado para preservar a localização de subelementos. O conteúdo transformado do \<descrição > elemento é incluído em um parágrafo HTML (\<p >) elemento. O <xref:System.Xml.Linq.XContainer.Nodes%2A>propriedade é usada para recuperar o conteúdo transformado do \<descrição > elemento.</xref:System.Xml.Linq.XContainer.Nodes%2A> Isto assegura que subelementos são incluídos no conteúdo transformado.  
  
     Adicione o seguinte código após `Sub Main` de `Module1`.  
  
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
  
5.  Salve as alterações.  
  
6.  Pressione F5 para executar o código. O documento salvo resultante será semelhante ao seguinte:  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Literais XML](../../../../visual-basic/language-reference/xml-literals/index.md)   
 [Manipulando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [Como: carregar XML de um arquivo, cadeia de caracteres ou fluxo](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)

