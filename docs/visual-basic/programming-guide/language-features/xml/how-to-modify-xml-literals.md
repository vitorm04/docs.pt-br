---
title: "Como modificar literais XML (Visual Basic) | Microsoft Docs"
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
  - "eixo XML [Visual Basic], Valor"
  - "literais XML [Visual Basic]"
  - "literais XML [Visual Basic], modificando"
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como modificar literais XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tem meios convenientes de modificar XML literais.  Você pode adicionar ou deletar elementos, e você pode também substituir um elemento existente por um novo elemento XML.  Este tópico fornece vários exemplos de como modificar um XML literal existente.  
  
### Modificar o valor de um XML literal.  
  
1.  Para modificar o valor de um XML literal, obtenha uma referência para o XML literal e defina a propriedade `Value` com o valor desejado.  
  
     O seguinte exemplo de código atualiza o valor de todos os elementos \<Price\> num documento XML.  
  
     [!code-vb[VbXmlSamples2#4](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]  
  
     A seguir temos um trecho de códigos XML e de XML modificado deste exemplo de código.  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
    >  A propriedade `Value` se refere ao primeiro elemento XML numa coleção.  Se há mais de um elemento que tenha o mesmo nome numa coleção, definir a propriedade `Value` afeta apenas o primeiro elemento na coleção.  
  
### Adicionar um atributo a um XML literal.  
  
1.  Para adicionar um atributo a um XML literal, primeiro obtenha uma referência ao XML literal.  Você pode então adicionar um atributo adicionando uma nova propriedade eixo de atributo XML.  Você pode também adicionar um novo objeto <xref:System.Xml.Linq.XAttribute> ao XML literal usando o método <xref:System.Xml.Linq.XContainer.Add%2A>.  O exemplo a seguir mostra ambas opções.  
  
     [!code-vb[VbXmlSamples2#5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]  
  
     A seguir temos um trecho de códigos XML e de XML modificado deste exemplo de código.  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
  
     Para mais informações sobre propriedades de eixos de atributos XML, consulte: [Propriedade de eixo do atributo XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).  
  
### Adicionar um elemento a um XML literal.  
  
1.  Para adicionar um elemento a um XML literal, primeiro obtenha uma referência ao XML literal.  Você pode então adicionar um novo objeto <xref:System.Xml.Linq.XElement> como o último subelemento usando o método <xref:System.Xml.Linq.XContainer.Add%2A>.  Você pode adicionar um novo objeto <xref:System.Xml.Linq.XElement> como o primeiro subelemento usando o método <xref:System.Xml.Linq.XContainer.AddFirst%2A>.  
  
     Para adicionar um novo elemento num localização específica relativa a outros subelementos, primeiro obtenha uma referência a um subelemento adjacente.  Você pode adicionar o novo objeto <xref:System.Xml.Linq.XElement> antes do subelemento adjacente usando o método <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>.  ADICVocê pode também adicionar o novo objeto <xref:System.Xml.Linq.XElement> depois do subelemento adjacente usando o método <xref:System.Xml.Linq.XNode.AddAfterSelf%2A>.  
  
     O seguinte trecho mostra exemplos de cada uma dessas técnicas.  
  
     [!code-vb[VbXmlSamples2#6](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]  
  
     A seguir temos um trecho de códigos XML e de XML modificado deste exemplo de código.  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
  
### Remover um elemento ou atributo de um XML literal.  
  
1.  Para remover um elemento ou atributo de um XML literal, obtenha uma referência ao elemento ou atributo e chame o método `Remove`, como mostrado no exemplo seguinte.  
  
     [!code-vb[VbXmlSamples2#7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]  
  
     A seguir temos um trecho de códigos XML e de XML modificado deste exemplo de código.  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
      </Book> </Catalog>  
    ```  
  
     Para remover todos os elementos ou atributos de um XML literal, obtenha uma referência ao XML literal e chame o método <xref:System.Xml.Linq.XElement.RemoveAll%2A>.  
  
### Modificar um XML literal.  
  
1.  Para mudar o nome de um elemento XML, primeiro obtenha uma referência ao elemento.  Você pode então criar um novo objeto <xref:System.Xml.Linq.XElement> que tenha um novo nome e passe o objeto <xref:System.Xml.Linq.XElement> para o método <xref:System.Xml.Linq.XNode.ReplaceWith%2A> do objeto <xref:System.Xml.Linq.XElement> existente.  
  
     Se o elemento que você está substituindo tem subelementos que devem ser mantidos, defina o valor do novo objeto <xref:System.Xml.Linq.XElement> para a propriedade <xref:System.Xml.Linq.XContainer.Nodes%2A> do elemento existente.  Isto vai definir o valor do novo elemento para o XML interno do elemento existente.  De qualquer maneira, você pode definir o valor do novo elemento para a propriedade `Value` do elemento existente.  
  
     O seguinte exemplo de código substiui todos os elementos \<Description\> com um elemento \<Abstract\>.  O conteúdo do elemento \<Description\> é mantido no novo elemento \<Abstract\> usando a propriedade <xref:System.Xml.Linq.XContainer.Nodes%2A> do objeto \<Description\> <xref:System.Xml.Linq.XElement>.  
  
     [!code-vb[VbXmlSamples2#8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]  
  
     A seguir temos um trecho de códigos XML e de XML modificado deste exemplo de código.  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <MSRP>44.95</MSRP>     <Abstract>  
          An in-depth look at creating applications  
          with <technology>XML</technology>. For   
          <audience>beginners</audience> or   
          <audience>advanced</audience> developers.  
        </Abstract>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <MSRP>45.95</MSRP>     <Abstract>  
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
  
## Consulte também  
 [Manipulando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [Como carregar XML a partir de um arquivo, cadeia de caracteres ou fluxo](../Topic/How%20to:%20Load%20XML%20from%20a%20File,%20String,%20or%20Stream%20\(Visual%20Basic\).md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)