---
title: Como modificar literais XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: a2ac2e9802d4c8ab522bb430d15cce5616430437
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374869"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="818ff-102">Como modificar literais XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="818ff-102">How to: Modify XML Literals (Visual Basic)</span></span>

<span data-ttu-id="818ff-103">Visual Basic fornece maneiras convenientes de modificar literais XML.</span><span class="sxs-lookup"><span data-stu-id="818ff-103">Visual Basic provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="818ff-104">Você pode adicionar ou excluir elementos e atributos, e também pode substituir um elemento existente por um novo elemento XML.</span><span class="sxs-lookup"><span data-stu-id="818ff-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="818ff-105">Este tópico fornece vários exemplos de como modificar um literal XML existente.</span><span class="sxs-lookup"><span data-stu-id="818ff-105">This topic provides several examples of how to modify an existing XML literal.</span></span>

### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="818ff-106">Para modificar o valor de um literal XML</span><span class="sxs-lookup"><span data-stu-id="818ff-106">To modify the value of an XML literal</span></span>

1. <span data-ttu-id="818ff-107">Para modificar o valor de um literal XML, obtenha uma referência para o literal XML e defina a `Value` propriedade para o valor desejado.</span><span class="sxs-lookup"><span data-stu-id="818ff-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>

    <span data-ttu-id="818ff-108">O exemplo de código a seguir atualiza o valor de todos os \<Price> elementos em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="818ff-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    <span data-ttu-id="818ff-109">O exemplo a seguir mostra o XML de origem de exemplo e o XML modificado deste código.</span><span class="sxs-lookup"><span data-stu-id="818ff-109">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="818ff-110">XML de origem:</span><span class="sxs-lookup"><span data-stu-id="818ff-110">Source XML:</span></span>

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

    <span data-ttu-id="818ff-111">XML modificado:</span><span class="sxs-lookup"><span data-stu-id="818ff-111">Modified XML:</span></span>

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
    > <span data-ttu-id="818ff-112">A `Value` Propriedade refere-se ao primeiro elemento XML em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="818ff-112">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="818ff-113">Se houver mais de um elemento que tenha o mesmo nome em uma coleção, a definição da `Value` propriedade afetará apenas o primeiro elemento da coleção.</span><span class="sxs-lookup"><span data-stu-id="818ff-113">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>

### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="818ff-114">Para adicionar um atributo a um literal XML</span><span class="sxs-lookup"><span data-stu-id="818ff-114">To add an attribute to an XML literal</span></span>

1. <span data-ttu-id="818ff-115">Para adicionar um atributo a um literal XML, primeiro obtenha uma referência para o literal XML.</span><span class="sxs-lookup"><span data-stu-id="818ff-115">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="818ff-116">Em seguida, você pode adicionar um atributo adicionando uma nova propriedade de eixo de atributo XML.</span><span class="sxs-lookup"><span data-stu-id="818ff-116">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="818ff-117">Você também pode adicionar um novo <xref:System.Xml.Linq.XAttribute> objeto ao literal XML usando o <xref:System.Xml.Linq.XContainer.Add%2A> método.</span><span class="sxs-lookup"><span data-stu-id="818ff-117">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="818ff-118">O exemplo a seguir mostra as duas opções.</span><span class="sxs-lookup"><span data-stu-id="818ff-118">The following example shows both options.</span></span>

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    <span data-ttu-id="818ff-119">O exemplo a seguir mostra o XML de origem de exemplo e o XML modificado deste código.</span><span class="sxs-lookup"><span data-stu-id="818ff-119">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="818ff-120">XML de origem:</span><span class="sxs-lookup"><span data-stu-id="818ff-120">Source XML:</span></span>

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

    <span data-ttu-id="818ff-121">XML modificado:</span><span class="sxs-lookup"><span data-stu-id="818ff-121">Modified XML:</span></span>

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

    <span data-ttu-id="818ff-122">Para obter mais informações sobre propriedades do eixo de atributo XML, consulte [Propriedade do eixo de atributo XML](../../../language-reference/xml-axis/xml-attribute-axis-property.md).</span><span class="sxs-lookup"><span data-stu-id="818ff-122">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>

### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="818ff-123">Para adicionar um elemento a um literal XML</span><span class="sxs-lookup"><span data-stu-id="818ff-123">To add an element to an XML literal</span></span>

1. <span data-ttu-id="818ff-124">Para adicionar um elemento a um literal XML, primeiro obtenha uma referência para o literal XML.</span><span class="sxs-lookup"><span data-stu-id="818ff-124">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="818ff-125">Em seguida, você pode adicionar um novo <xref:System.Xml.Linq.XElement> objeto como o último subelemento do elemento usando o <xref:System.Xml.Linq.XContainer.Add%2A> método.</span><span class="sxs-lookup"><span data-stu-id="818ff-125">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="818ff-126">Você pode adicionar um novo <xref:System.Xml.Linq.XElement> objeto como o primeiro subelemento usando o <xref:System.Xml.Linq.XContainer.AddFirst%2A> método.</span><span class="sxs-lookup"><span data-stu-id="818ff-126">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>

    <span data-ttu-id="818ff-127">Para adicionar um novo elemento em um local específico em relação a outros subelementos, primeiro obtenha uma referência a um sub-elemento adjacente.</span><span class="sxs-lookup"><span data-stu-id="818ff-127">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="818ff-128">Em seguida, você pode adicionar o novo <xref:System.Xml.Linq.XElement> objeto antes do subelemento adjacente usando o <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> método.</span><span class="sxs-lookup"><span data-stu-id="818ff-128">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="818ff-129">Você também pode adicionar o novo <xref:System.Xml.Linq.XElement> objeto após o subelemento adjacente usando o <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> método.</span><span class="sxs-lookup"><span data-stu-id="818ff-129">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>

    <span data-ttu-id="818ff-130">O exemplo a seguir mostra exemplos de cada uma dessas técnicas.</span><span class="sxs-lookup"><span data-stu-id="818ff-130">The following example shows examples of each of these techniques.</span></span>

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    <span data-ttu-id="818ff-131">O exemplo a seguir mostra o XML de origem de exemplo e o XML modificado deste código.</span><span class="sxs-lookup"><span data-stu-id="818ff-131">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="818ff-132">XML de origem:</span><span class="sxs-lookup"><span data-stu-id="818ff-132">Source XML:</span></span>

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

    <span data-ttu-id="818ff-133">XML modificado:</span><span class="sxs-lookup"><span data-stu-id="818ff-133">Modified XML:</span></span>

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

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="818ff-134">Para remover um elemento ou atributo de um literal XML</span><span class="sxs-lookup"><span data-stu-id="818ff-134">To remove an element or attribute from an XML literal</span></span>

1. <span data-ttu-id="818ff-135">Para remover um elemento ou um atributo de um literal XML, obtenha uma referência para o elemento ou atributo e chame o `Remove` método, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="818ff-135">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    <span data-ttu-id="818ff-136">O exemplo a seguir mostra o XML de origem de exemplo e o XML modificado deste código.</span><span class="sxs-lookup"><span data-stu-id="818ff-136">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="818ff-137">XML de origem:</span><span class="sxs-lookup"><span data-stu-id="818ff-137">Source XML:</span></span>

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

    <span data-ttu-id="818ff-138">XML modificado:</span><span class="sxs-lookup"><span data-stu-id="818ff-138">Modified XML:</span></span>

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

    <span data-ttu-id="818ff-139">Para remover todos os elementos ou atributos de um literal XML, obtenha uma referência para o literal XML e chame o <xref:System.Xml.Linq.XElement.RemoveAll%2A> método.</span><span class="sxs-lookup"><span data-stu-id="818ff-139">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>

### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="818ff-140">Para modificar um literal XML</span><span class="sxs-lookup"><span data-stu-id="818ff-140">To modify an XML literal</span></span>

1. <span data-ttu-id="818ff-141">Para alterar o nome de um elemento XML, primeiro obtenha uma referência para o elemento.</span><span class="sxs-lookup"><span data-stu-id="818ff-141">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="818ff-142">Você pode criar um novo <xref:System.Xml.Linq.XElement> objeto que tem um novo nome e passar o novo <xref:System.Xml.Linq.XElement> objeto para o <xref:System.Xml.Linq.XNode.ReplaceWith%2A> método do objeto existente <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="818ff-142">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>

    <span data-ttu-id="818ff-143">Se o elemento que você está substituindo tiver subelementos que devam ser preservados, defina o valor do novo <xref:System.Xml.Linq.XElement> objeto como a <xref:System.Xml.Linq.XContainer.Nodes%2A> Propriedade do elemento existente.</span><span class="sxs-lookup"><span data-stu-id="818ff-143">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="818ff-144">Isso definirá o valor do novo elemento como o XML interno do elemento existente.</span><span class="sxs-lookup"><span data-stu-id="818ff-144">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="818ff-145">Caso contrário, você pode definir o valor do novo elemento como a `Value` Propriedade do elemento existente.</span><span class="sxs-lookup"><span data-stu-id="818ff-145">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>

    <span data-ttu-id="818ff-146">O exemplo de código a seguir substitui todos os \<Description> elementos por um \<Abstract> elemento.</span><span class="sxs-lookup"><span data-stu-id="818ff-146">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="818ff-147">O conteúdo do \<Description> elemento é preservado no novo \<Abstract> elemento usando a <xref:System.Xml.Linq.XContainer.Nodes%2A> Propriedade do \<Description> <xref:System.Xml.Linq.XElement> objeto.</span><span class="sxs-lookup"><span data-stu-id="818ff-147">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    <span data-ttu-id="818ff-148">O exemplo a seguir mostra o XML de origem de exemplo e o XML modificado deste código.</span><span class="sxs-lookup"><span data-stu-id="818ff-148">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="818ff-149">XML de origem:</span><span class="sxs-lookup"><span data-stu-id="818ff-149">Source XML:</span></span>

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

    <span data-ttu-id="818ff-150">XML modificado:</span><span class="sxs-lookup"><span data-stu-id="818ff-150">Modified XML:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="818ff-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="818ff-151">See also</span></span>

- [<span data-ttu-id="818ff-152">Manipulando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="818ff-152">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
- [<span data-ttu-id="818ff-153">XML</span><span class="sxs-lookup"><span data-stu-id="818ff-153">XML</span></span>](index.md)
- [<span data-ttu-id="818ff-154">Como carregar XML a partir de um arquivo, cadeia de caracteres ou fluxo</span><span class="sxs-lookup"><span data-stu-id="818ff-154">How to: Load XML from a File, String, or Stream</span></span>](how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="818ff-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="818ff-155">LINQ</span></span>](../linq/index.md)
- [<span data-ttu-id="818ff-156">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="818ff-156">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
