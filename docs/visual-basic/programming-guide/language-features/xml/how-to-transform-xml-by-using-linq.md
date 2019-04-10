---
title: 'Como: Transformar XML usando LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: c34d3988c89e0ce07676e9181200fc039010b50a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324975"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a>Como: Transformar XML usando LINQ (Visual Basic)
[Literais XML](../../../../visual-basic/language-reference/xml-literals/index.md) torná-lo mais fácil de ler o XML de uma fonte e transformá-lo em um novo formato XML. Você pode tirar proveito das consultas LINQ para recuperar o conteúdo para transformar ou alterar o conteúdo em um documento existente em um novo formato XML.  
  
 O exemplo neste tópico transforma o conteúdo de um documento de origem XML HTML a ser exibida em um navegador.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-transform-an-xml-document"></a>Para transformar um documento XML  
  
1. No Visual Studio, crie um novo projeto do Visual Basic na **aplicativo de Console** modelo de projeto.  
  
2. Clique duas vezes no arquivo Module1.vb criado no projeto para modificar o código do Visual Basic. Adicione o seguinte código para o `Sub Main` do `Module1` módulo. Esse código cria o documento XML de origem como um <xref:System.Xml.Linq.XDocument> objeto.  
  
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
  
     [Como: Carregar XML de um arquivo, cadeia de caracteres ou Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).  
  
3. Após o código para criar o documento XML de origem, adicione o seguinte código para recuperar todos os \<livro > elementos do objeto e transformá-los em um documento HTML. A lista de \<livro > elementos é criado usando uma consulta LINQ que retorna uma coleção de <xref:System.Xml.Linq.XElement> objetos que contém o HTML transformado. Você pode usar expressões inseridas para colocar os valores do documento de origem no novo formato XML.  
  
     O documento HTML resultante é gravado em um arquivo usando o <xref:System.Xml.Linq.XElement.Save%2A> método.  
  
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
  
4. Após `Sub Main` dos `Module1`, adicione um novo método (`Sub`) para transformar um \<descrição > nó em formato HTML especificado. Esse método é chamado pelo código na etapa anterior e é usado para preservar o formato do \<descrição > elementos.  
  
     Esse método substitui subelementos do \<descrição > elemento com HTML. O `ReplaceWith` método é usado para preservar a localização de subelementos. O conteúdo transformado do \<descrição > elemento é incluído em um parágrafo HTML (\<p >) elemento. O <xref:System.Xml.Linq.XContainer.Nodes%2A> propriedade é usada para recuperar o conteúdo transformado do \<descrição > elemento. Isso garante que os subelementos são incluídos no conteúdo transformado.  
  
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
  
5. Salve as alterações.  
  
6. Pressione F5 para executar o código. O documento salvo resultante será semelhante ao seguinte:  
  
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

- [Literais XML](../../../../visual-basic/language-reference/xml-literals/index.md)
- [Manipulando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Como: carregar XML de um arquivo, cadeia de caracteres ou fluxo](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
