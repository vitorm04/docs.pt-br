---
title: 'Como: modificar literais XML (Visual Basic) | Documentos do Microsoft'
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
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
caps.latest.revision: 11
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9c21ded9fdd8f49b469b9a712be304c0d4cabb8c
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="cd336-102">Como modificar literais XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd336-102">How to: Modify XML Literals (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="cd336-103">fornece maneiras convenientes para modificar literais XML.</span><span class="sxs-lookup"><span data-stu-id="cd336-103"> provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="cd336-104">Você pode adicionar ou excluir elementos e atributos, e você também pode substituir um elemento existente com um novo elemento XML.</span><span class="sxs-lookup"><span data-stu-id="cd336-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="cd336-105">Este tópico fornece vários exemplos de como modificar um XML literal existente.</span><span class="sxs-lookup"><span data-stu-id="cd336-105">This topic provides several examples of how to modify an existing XML literal.</span></span>  
  
### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="cd336-106">Para modificar o valor de um literal XML</span><span class="sxs-lookup"><span data-stu-id="cd336-106">To modify the value of an XML literal</span></span>  
  
1.  <span data-ttu-id="cd336-107">Para modificar o valor de um XML literal, obtenha uma referência ao XML literal e defina a `Value` propriedade para o valor desejado.</span><span class="sxs-lookup"><span data-stu-id="cd336-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>  
  
     <span data-ttu-id="cd336-108">O exemplo de código a seguir atualiza o valor de todos os \<preço > elementos em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="cd336-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>  
  
     <span data-ttu-id="cd336-109">[!code-vb[VbXmlSamples2 n º&4;](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="cd336-109">[!code-vb[VbXmlSamples2#4](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]</span></span>  
  
     <span data-ttu-id="cd336-110">A seguir mostra o XML de origem de exemplo e XML modificado deste exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="cd336-110">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
    >  <span data-ttu-id="cd336-111">O `Value` propriedade se refere ao primeiro elemento XML em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="cd336-111">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="cd336-112">Se houver mais de um elemento que tem o mesmo nome em uma coleção, configurando o `Value` propriedade afeta apenas o primeiro elemento na coleção.</span><span class="sxs-lookup"><span data-stu-id="cd336-112">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>  
  
### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="cd336-113">Para adicionar um atributo a um literal XML</span><span class="sxs-lookup"><span data-stu-id="cd336-113">To add an attribute to an XML literal</span></span>  
  
1.  <span data-ttu-id="cd336-114">Para adicionar um atributo a um XML literal, primeiro obtenha uma referência ao XML literal.</span><span class="sxs-lookup"><span data-stu-id="cd336-114">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="cd336-115">Em seguida, você pode adicionar um atributo adicionando uma nova propriedade de eixo de atributo XML.</span><span class="sxs-lookup"><span data-stu-id="cd336-115">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="cd336-116">Você também pode adicionar um novo <xref:System.Xml.Linq.XAttribute>objeto ao XML literal usando o <xref:System.Xml.Linq.XContainer.Add%2A>método.</xref:System.Xml.Linq.XContainer.Add%2A> </xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="cd336-116">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="cd336-117">O exemplo a seguir mostra as duas opções.</span><span class="sxs-lookup"><span data-stu-id="cd336-117">The following example shows both options.</span></span>  
  
     <span data-ttu-id="cd336-118">[!code-vb[VbXmlSamples2 n º&5;](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="cd336-118">[!code-vb[VbXmlSamples2#5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]</span></span>  
  
     <span data-ttu-id="cd336-119">A seguir mostra o XML de origem de exemplo e XML modificado deste exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="cd336-119">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
     <span data-ttu-id="cd336-120">Para obter mais informações sobre as propriedades de eixo de atributo XML, consulte [propriedade de eixo de atributo XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span><span class="sxs-lookup"><span data-stu-id="cd336-120">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>  
  
### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="cd336-121">Para adicionar um elemento a um literal XML</span><span class="sxs-lookup"><span data-stu-id="cd336-121">To add an element to an XML literal</span></span>  
  
1.  <span data-ttu-id="cd336-122">Para adicionar um elemento a um XML literal, primeiro obtenha uma referência ao XML literal.</span><span class="sxs-lookup"><span data-stu-id="cd336-122">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="cd336-123">Você pode adicionar um novo <xref:System.Xml.Linq.XElement>objeto como o último sub-elemento do elemento usando o <xref:System.Xml.Linq.XContainer.Add%2A>método.</xref:System.Xml.Linq.XContainer.Add%2A> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="cd336-123">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="cd336-124">Você pode adicionar um novo <xref:System.Xml.Linq.XElement>objeto como o primeiro sub-elemento usando o <xref:System.Xml.Linq.XContainer.AddFirst%2A>método.</xref:System.Xml.Linq.XContainer.AddFirst%2A> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="cd336-124">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>  
  
     <span data-ttu-id="cd336-125">Para adicionar um novo elemento em um local específico em relação a outros sub-elementos, primeiro obtenha uma referência a um sub-elemento adjacente.</span><span class="sxs-lookup"><span data-stu-id="cd336-125">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="cd336-126">Você pode adicionar o novo <xref:System.Xml.Linq.XElement>objeto antes do sub-elemento adjacente usando o <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>método.</xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="cd336-126">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="cd336-127">Você também pode adicionar o novo <xref:System.Xml.Linq.XElement>objeto depois do sub-elemento adjacente usando o <xref:System.Xml.Linq.XNode.AddAfterSelf%2A>método.</xref:System.Xml.Linq.XNode.AddAfterSelf%2A> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="cd336-127">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>  
  
     <span data-ttu-id="cd336-128">O exemplo a seguir mostra exemplos de cada uma dessas técnicas.</span><span class="sxs-lookup"><span data-stu-id="cd336-128">The following example shows examples of each of these techniques.</span></span>  
  
     <span data-ttu-id="cd336-129">[!code-vb[VbXmlSamples2 n º&6;](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="cd336-129">[!code-vb[VbXmlSamples2#6](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]</span></span>  
  
     <span data-ttu-id="cd336-130">A seguir mostra o XML de origem de exemplo e XML modificado deste exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="cd336-130">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="cd336-131">Para remover um elemento ou atributo de um literal XML</span><span class="sxs-lookup"><span data-stu-id="cd336-131">To remove an element or attribute from an XML literal</span></span>  
  
1.  <span data-ttu-id="cd336-132">Para remover um elemento ou atributo de um XML literal, obtenha uma referência para o elemento ou atributo e chamar o `Remove` método, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="cd336-132">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>  
  
     <span data-ttu-id="cd336-133">[!code-vb[VbXmlSamples&#2;7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="cd336-133">[!code-vb[VbXmlSamples2#7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]</span></span>  
  
     <span data-ttu-id="cd336-134">A seguir mostra o XML de origem de exemplo e XML modificado deste exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="cd336-134">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
      </Book></Catalog>  
    ```  
  
     <span data-ttu-id="cd336-135">Para remover todos os elementos ou atributos de um XML literal, obtenha uma referência ao XML literal e chame o <xref:System.Xml.Linq.XElement.RemoveAll%2A>método.</xref:System.Xml.Linq.XElement.RemoveAll%2A></span><span class="sxs-lookup"><span data-stu-id="cd336-135">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>  
  
### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="cd336-136">Para modificar um literal XML</span><span class="sxs-lookup"><span data-stu-id="cd336-136">To modify an XML literal</span></span>  
  
1.  <span data-ttu-id="cd336-137">Para alterar o nome de um elemento XML, primeiro obtenha uma referência ao elemento.</span><span class="sxs-lookup"><span data-stu-id="cd336-137">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="cd336-138">Você pode criar um novo <xref:System.Xml.Linq.XElement>que tem um novo nome e passe o objeto <xref:System.Xml.Linq.XElement>de objeto para o <xref:System.Xml.Linq.XNode.ReplaceWith%2A>método existente <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XNode.ReplaceWith%2A> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="cd336-138">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     <span data-ttu-id="cd336-139">Se o elemento que você está substituindo tem sub-elementos que devem ser mantidos, defina o valor do novo <xref:System.Xml.Linq.XElement>o objeto para o <xref:System.Xml.Linq.XContainer.Nodes%2A>propriedade do elemento existente.</xref:System.Xml.Linq.XContainer.Nodes%2A> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="cd336-139">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="cd336-140">Isso definirá o valor do novo elemento para o XML interno do elemento existente.</span><span class="sxs-lookup"><span data-stu-id="cd336-140">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="cd336-141">Caso contrário, você pode definir o valor do novo elemento para o `Value` propriedade do elemento existente.</span><span class="sxs-lookup"><span data-stu-id="cd336-141">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>  
  
     <span data-ttu-id="cd336-142">O exemplo de código a seguir substitui todos \<descrição > elementos com um \<abstrato > elemento.</span><span class="sxs-lookup"><span data-stu-id="cd336-142">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="cd336-143">O conteúdo da \<descrição > elemento é mantido no novo \<abstrato > elemento usando o <xref:System.Xml.Linq.XContainer.Nodes%2A>propriedade o \<descrição > <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XContainer.Nodes%2A></span><span class="sxs-lookup"><span data-stu-id="cd336-143">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     <span data-ttu-id="cd336-144">[!code-vb[VbXmlSamples2 n º&8;](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="cd336-144">[!code-vb[VbXmlSamples2#8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]</span></span>  
  
     <span data-ttu-id="cd336-145">A seguir mostra o XML de origem de exemplo e XML modificado deste exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="cd336-145">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cd336-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd336-146">See Also</span></span>  
 <span data-ttu-id="cd336-147">[Manipulando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="cd336-147">[Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md) </span></span>  
<span data-ttu-id="cd336-148"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="cd336-148"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="cd336-149"> [Como: carregar XML de um arquivo, cadeia de caracteres ou fluxo](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md) </span><span class="sxs-lookup"><span data-stu-id="cd336-149"> [How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md) </span></span>  
<span data-ttu-id="cd336-150"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="cd336-150"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="cd336-151"> [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="cd336-151"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
