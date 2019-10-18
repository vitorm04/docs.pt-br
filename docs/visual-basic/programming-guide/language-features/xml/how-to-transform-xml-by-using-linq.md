---
title: Como transformar XML usando LINQ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: 347ca45c2417c1ffb9a86f3bcb51c75f3382bfad
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524813"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a>Como transformar XML usando LINQ (Visual Basic)

Os [literais XML](../../../../visual-basic/language-reference/xml-literals/index.md) facilitam a leitura de XML de uma fonte e a transformação para um novo formato XML. Você pode aproveitar as consultas LINQ para recuperar o conteúdo para transformar ou alterar o conteúdo de um documento existente para um novo formato XML.

O exemplo neste tópico transforma o conteúdo de um documento de origem XML em HTML a ser exibido em um navegador.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-transform-an-xml-document"></a>Para transformar um documento XML

1. No Visual Studio, crie um novo projeto de Visual Basic no modelo de projeto de **aplicativo de console** .

2. Clique duas vezes no arquivo Module1. vb criado no projeto para modificar o código de Visual Basic. Adicione o código a seguir ao `Sub Main` do módulo `Module1`. Esse código cria o documento XML de origem como um objeto <xref:System.Xml.Linq.XDocument>.

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

     [Como carregar XML de um arquivo, uma cadeia de caracteres ou um fluxo](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).

3. Depois do código para criar o documento XML de origem, adicione o código a seguir para recuperar todos os elementos de > de \<Book do objeto e transformá-los em um documento HTML. A lista de elementos de > de \<Book é criada usando uma consulta LINQ que retorna uma coleção de objetos <xref:System.Xml.Linq.XElement> que contêm o HTML transformado. Você pode usar expressões inseridas para colocar os valores do documento de origem no novo formato XML.

     O documento HTML resultante é gravado em um arquivo usando o método <xref:System.Xml.Linq.XElement.Save%2A>.

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

4. Depois de `Sub Main` de `Module1`, adicione um novo método (`Sub`) para transformar um nó de \<Description > no formato HTML especificado. Esse método é chamado pelo código na etapa anterior e é usado para preservar o formato dos elementos de > de \<Description.

     Esse método substitui os subelementos do elemento \<Description > por HTML. O método `ReplaceWith` é usado para preservar o local dos subelementos. O conteúdo transformado do elemento \<Description > é incluído em um elemento de parágrafo HTML (\<p >). A propriedade <xref:System.Xml.Linq.XContainer.Nodes%2A> é usada para recuperar o conteúdo transformado do elemento \<Description >. Isso garante que os subelementos sejam incluídos no conteúdo transformado.

     Adicione o código a seguir após `Sub Main` de `Module1`.

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

## <a name="see-also"></a>Consulte também

- [Literais XML](../../../../visual-basic/language-reference/xml-literals/index.md)
- [Manipulando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Como carregar XML de um arquivo, cadeia de caracteres ou fluxo](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
