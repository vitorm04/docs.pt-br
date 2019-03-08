---
title: 'Como: Modificar literais XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 003715b04f3a5c0fb41e846beb189f117378ea58
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675323"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a>Como: Modificar literais XML (Visual Basic)

Visual Basic fornece maneiras convenientes para modificar literais XML. Você pode adicionar ou excluir elementos e atributos, e você também pode substituir um elemento existente com um novo elemento XML. Este tópico fornece vários exemplos de como modificar um literal do XML existente.

### <a name="to-modify-the-value-of-an-xml-literal"></a>Para modificar o valor de um literal XML

1. Para modificar o valor de um literal XML, obtenha uma referência para o XML literal e defina o `Value` propriedade para o valor desejado.

    O exemplo de código a seguir atualiza o valor de todos os \<preço > elementos em um documento XML.

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    A seguir mostra o XML de origem de exemplo e de que este exemplo de código XML modificado.

    XML de origem:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    XML modificado:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>47.20</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>48.25</Price>
      </Book>
    </Catalog>
    ```

    > [!NOTE]
    > O `Value` propriedade se refere ao primeiro elemento XML em uma coleção. Se houver mais de um elemento que tem o mesmo nome em uma coleção, definindo o `Value` propriedade afeta apenas o primeiro elemento na coleção.

### <a name="to-add-an-attribute-to-an-xml-literal"></a>Para adicionar um atributo a um literal XML

1. Para adicionar um atributo a um literal XML, primeiro obtenha uma referência ao XML literal. Em seguida, você pode adicionar um atributo, adicionando uma nova propriedade de eixo de atributo XML. Você também pode adicionar um novo <xref:System.Xml.Linq.XAttribute> objeto para o XML literal usando o <xref:System.Xml.Linq.XContainer.Add%2A> método. O exemplo a seguir mostra as duas opções.

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    A seguir mostra o XML de origem de exemplo e de que este exemplo de código XML modificado.

    XML de origem:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    XML modificado:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    Para obter mais informações sobre as propriedades de eixo de atributo XML, consulte [propriedade de eixo de atributo XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).

### <a name="to-add-an-element-to-an-xml-literal"></a>Para adicionar um elemento a um literal XML

1. Para adicionar um elemento a um literal XML, primeiro obtenha uma referência ao XML literal. Você pode adicionar um novo <xref:System.Xml.Linq.XElement> objeto como o último subelemento do elemento usando o <xref:System.Xml.Linq.XContainer.Add%2A> método. Você pode adicionar um novo <xref:System.Xml.Linq.XElement> objeto como o primeiro sub-elemento usando o <xref:System.Xml.Linq.XContainer.AddFirst%2A> método.

    Para adicionar um novo elemento em um local específico em relação a outros subelementos, primeiro obtenha uma referência a um subelemento adjacente. Você pode adicionar a nova <xref:System.Xml.Linq.XElement> objeto antes do sub-elemento adjacente usando o <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> método. Você também pode adicionar o novo <xref:System.Xml.Linq.XElement> objeto após o subelemento adjacente, usando o <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> método.

    O exemplo a seguir mostra exemplos de cada uma dessas técnicas.

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    A seguir mostra o XML de origem de exemplo e de que este exemplo de código XML modificado.

    XML de origem:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    XML modificado:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331">
        <Publisher>Microsoft Press</Publisher>
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
        <PublishDate>2005-2-14</PublishDate>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a>Para remover um elemento ou atributo de um literal XML

1. Para remover um elemento ou atributo de um literal XML, obtenha uma referência ao elemento ou atributo e chame o `Remove` método, conforme mostrado no exemplo a seguir.

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    A seguir mostra o XML de origem de exemplo e de que este exemplo de código XML modificado.

    XML de origem:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

    XML modificado:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book></Catalog>
    ```

    Para remover todos os elementos ou atributos de um literal XML, obtenha uma referência ao XML literal e chame o <xref:System.Xml.Linq.XElement.RemoveAll%2A> método.

### <a name="to-modify-an-xml-literal"></a>Para modificar um literal XML

1. Para alterar o nome de um elemento XML, primeiro obtenha uma referência ao elemento. Você pode criar um novo <xref:System.Xml.Linq.XElement> objeto que tem um novo nome e passe o novo <xref:System.Xml.Linq.XElement> do objeto para o <xref:System.Xml.Linq.XNode.ReplaceWith%2A> método existente <xref:System.Xml.Linq.XElement> objeto.

    Se o elemento que você está substituindo tem subelementos que devem ser preservados, defina o valor da nova <xref:System.Xml.Linq.XElement> do objeto para o <xref:System.Xml.Linq.XContainer.Nodes%2A> propriedade do elemento existente. Isso definirá o valor do novo elemento para o XML interno do elemento existente. Caso contrário, você pode definir o valor do novo elemento para o `Value` propriedade do elemento existente.

    O exemplo de código a seguir substitui todos os \<descrição > elementos com um \<abstrata > elemento. O conteúdo do \<descrição > elemento é preservado na nova \<abstrata > elemento usando o <xref:System.Xml.Linq.XContainer.Nodes%2A> propriedade do \<descrição > <xref:System.Xml.Linq.XElement> objeto.

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    A seguir mostra o XML de origem de exemplo e de que este exemplo de código XML modificado.

    XML de origem:

    ```xml
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
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Description>
      </Book>
    </Catalog>
    ```

    XML modificado:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <MSRP>44.95</MSRP>    <Abstract>
          An in-depth look at creating applications
          with <technology>XML</technology>. For
          <audience>beginners</audience> or
          <audience>advanced</audience> developers.
        </Abstract>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <MSRP>45.95</MSRP>    <Abstract>
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Abstract>
      </Book>
    </Catalog>
    ```

## <a name="see-also"></a>Consulte também

- [Manipulando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Como: Carregar XML de um arquivo, cadeia de caracteres ou Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
