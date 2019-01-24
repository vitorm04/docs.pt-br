---
title: 'Como: Modificar literais XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 7a01fdc9d0541b5d277c2f283e25e9a1cef3b862
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636333"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="dff61-102">Como: Modificar literais XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dff61-102">How to: Modify XML Literals (Visual Basic)</span></span>
<span data-ttu-id="dff61-103">Visual Basic fornece maneiras convenientes para modificar literais XML.</span><span class="sxs-lookup"><span data-stu-id="dff61-103">Visual Basic provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="dff61-104">Você pode adicionar ou excluir elementos e atributos, e você também pode substituir um elemento existente com um novo elemento XML.</span><span class="sxs-lookup"><span data-stu-id="dff61-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="dff61-105">Este tópico fornece vários exemplos de como modificar um literal do XML existente.</span><span class="sxs-lookup"><span data-stu-id="dff61-105">This topic provides several examples of how to modify an existing XML literal.</span></span>  
  
### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="dff61-106">Para modificar o valor de um literal XML</span><span class="sxs-lookup"><span data-stu-id="dff61-106">To modify the value of an XML literal</span></span>  
  
1.  <span data-ttu-id="dff61-107">Para modificar o valor de um literal XML, obtenha uma referência para o XML literal e defina o `Value` propriedade para o valor desejado.</span><span class="sxs-lookup"><span data-stu-id="dff61-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>  
  
     <span data-ttu-id="dff61-108">O exemplo de código a seguir atualiza o valor de todos os \<preço > elementos em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="dff61-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>  
  
     [!code-vb[VbXmlSamples2#4](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]  
  
     <span data-ttu-id="dff61-109">A seguir mostra o XML de origem de exemplo e de que este exemplo de código XML modificado.</span><span class="sxs-lookup"><span data-stu-id="dff61-109">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
    >  <span data-ttu-id="dff61-110">O `Value` propriedade se refere ao primeiro elemento XML em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="dff61-110">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="dff61-111">Se houver mais de um elemento que tem o mesmo nome em uma coleção, definindo o `Value` propriedade afeta apenas o primeiro elemento na coleção.</span><span class="sxs-lookup"><span data-stu-id="dff61-111">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>  
  
### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="dff61-112">Para adicionar um atributo a um literal XML</span><span class="sxs-lookup"><span data-stu-id="dff61-112">To add an attribute to an XML literal</span></span>  
  
1.  <span data-ttu-id="dff61-113">Para adicionar um atributo a um literal XML, primeiro obtenha uma referência ao XML literal.</span><span class="sxs-lookup"><span data-stu-id="dff61-113">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="dff61-114">Em seguida, você pode adicionar um atributo, adicionando uma nova propriedade de eixo de atributo XML.</span><span class="sxs-lookup"><span data-stu-id="dff61-114">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="dff61-115">Você também pode adicionar um novo <xref:System.Xml.Linq.XAttribute> objeto para o XML literal usando o <xref:System.Xml.Linq.XContainer.Add%2A> método.</span><span class="sxs-lookup"><span data-stu-id="dff61-115">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="dff61-116">O exemplo a seguir mostra as duas opções.</span><span class="sxs-lookup"><span data-stu-id="dff61-116">The following example shows both options.</span></span>  
  
     [!code-vb[VbXmlSamples2#5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]  
  
     <span data-ttu-id="dff61-117">A seguir mostra o XML de origem de exemplo e de que este exemplo de código XML modificado.</span><span class="sxs-lookup"><span data-stu-id="dff61-117">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
     <span data-ttu-id="dff61-118">Para obter mais informações sobre as propriedades de eixo de atributo XML, consulte [propriedade de eixo de atributo XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span><span class="sxs-lookup"><span data-stu-id="dff61-118">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>  
  
### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="dff61-119">Para adicionar um elemento a um literal XML</span><span class="sxs-lookup"><span data-stu-id="dff61-119">To add an element to an XML literal</span></span>  
  
1.  <span data-ttu-id="dff61-120">Para adicionar um elemento a um literal XML, primeiro obtenha uma referência ao XML literal.</span><span class="sxs-lookup"><span data-stu-id="dff61-120">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="dff61-121">Você pode adicionar um novo <xref:System.Xml.Linq.XElement> objeto como o último subelemento do elemento usando o <xref:System.Xml.Linq.XContainer.Add%2A> método.</span><span class="sxs-lookup"><span data-stu-id="dff61-121">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="dff61-122">Você pode adicionar um novo <xref:System.Xml.Linq.XElement> objeto como o primeiro sub-elemento usando o <xref:System.Xml.Linq.XContainer.AddFirst%2A> método.</span><span class="sxs-lookup"><span data-stu-id="dff61-122">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>  
  
     <span data-ttu-id="dff61-123">Para adicionar um novo elemento em um local específico em relação a outros subelementos, primeiro obtenha uma referência a um subelemento adjacente.</span><span class="sxs-lookup"><span data-stu-id="dff61-123">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="dff61-124">Você pode adicionar a nova <xref:System.Xml.Linq.XElement> objeto antes do sub-elemento adjacente usando o <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> método.</span><span class="sxs-lookup"><span data-stu-id="dff61-124">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="dff61-125">Você também pode adicionar o novo <xref:System.Xml.Linq.XElement> objeto após o subelemento adjacente, usando o <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> método.</span><span class="sxs-lookup"><span data-stu-id="dff61-125">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>  
  
     <span data-ttu-id="dff61-126">O exemplo a seguir mostra exemplos de cada uma dessas técnicas.</span><span class="sxs-lookup"><span data-stu-id="dff61-126">The following example shows examples of each of these techniques.</span></span>  
  
     [!code-vb[VbXmlSamples2#6](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]  
  
     <span data-ttu-id="dff61-127">A seguir mostra o XML de origem de exemplo e de que este exemplo de código XML modificado.</span><span class="sxs-lookup"><span data-stu-id="dff61-127">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="dff61-128">Para remover um elemento ou atributo de um literal XML</span><span class="sxs-lookup"><span data-stu-id="dff61-128">To remove an element or attribute from an XML literal</span></span>  
  
1.  <span data-ttu-id="dff61-129">Para remover um elemento ou atributo de um literal XML, obtenha uma referência ao elemento ou atributo e chame o `Remove` método, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="dff61-129">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>  
  
     [!code-vb[VbXmlSamples2#7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]  
  
     <span data-ttu-id="dff61-130">A seguir mostra o XML de origem de exemplo e de que este exemplo de código XML modificado.</span><span class="sxs-lookup"><span data-stu-id="dff61-130">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
     <span data-ttu-id="dff61-131">Para remover todos os elementos ou atributos de um literal XML, obtenha uma referência ao XML literal e chame o <xref:System.Xml.Linq.XElement.RemoveAll%2A> método.</span><span class="sxs-lookup"><span data-stu-id="dff61-131">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>  
  
### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="dff61-132">Para modificar um literal XML</span><span class="sxs-lookup"><span data-stu-id="dff61-132">To modify an XML literal</span></span>  
  
1.  <span data-ttu-id="dff61-133">Para alterar o nome de um elemento XML, primeiro obtenha uma referência ao elemento.</span><span class="sxs-lookup"><span data-stu-id="dff61-133">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="dff61-134">Você pode criar um novo <xref:System.Xml.Linq.XElement> objeto que tem um novo nome e passe o novo <xref:System.Xml.Linq.XElement> do objeto para o <xref:System.Xml.Linq.XNode.ReplaceWith%2A> método existente <xref:System.Xml.Linq.XElement> objeto.</span><span class="sxs-lookup"><span data-stu-id="dff61-134">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     <span data-ttu-id="dff61-135">Se o elemento que você está substituindo tem subelementos que devem ser preservados, defina o valor da nova <xref:System.Xml.Linq.XElement> do objeto para o <xref:System.Xml.Linq.XContainer.Nodes%2A> propriedade do elemento existente.</span><span class="sxs-lookup"><span data-stu-id="dff61-135">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="dff61-136">Isso definirá o valor do novo elemento para o XML interno do elemento existente.</span><span class="sxs-lookup"><span data-stu-id="dff61-136">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="dff61-137">Caso contrário, você pode definir o valor do novo elemento para o `Value` propriedade do elemento existente.</span><span class="sxs-lookup"><span data-stu-id="dff61-137">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>  
  
     <span data-ttu-id="dff61-138">O exemplo de código a seguir substitui todos os \<descrição > elementos com um \<abstrata > elemento.</span><span class="sxs-lookup"><span data-stu-id="dff61-138">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="dff61-139">O conteúdo do \<descrição > elemento é preservado na nova \<abstrata > elemento usando o <xref:System.Xml.Linq.XContainer.Nodes%2A> propriedade do \<descrição > <xref:System.Xml.Linq.XElement> objeto.</span><span class="sxs-lookup"><span data-stu-id="dff61-139">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     [!code-vb[VbXmlSamples2#8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]  
  
     <span data-ttu-id="dff61-140">A seguir mostra o XML de origem de exemplo e de que este exemplo de código XML modificado.</span><span class="sxs-lookup"><span data-stu-id="dff61-140">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dff61-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dff61-141">See also</span></span>
- [<span data-ttu-id="dff61-142">Manipulando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dff61-142">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [<span data-ttu-id="dff61-143">XML</span><span class="sxs-lookup"><span data-stu-id="dff61-143">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="dff61-144">Como: Carregar XML de um arquivo, cadeia de caracteres ou Stream</span><span class="sxs-lookup"><span data-stu-id="dff61-144">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="dff61-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="dff61-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="dff61-146">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dff61-146">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
