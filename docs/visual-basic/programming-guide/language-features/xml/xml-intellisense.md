---
title: XML IntelliSense no Visual Basic | Documentos do Microsoft
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
- Visual Basic code, XML
- XML IntelliSense [Visual Basic]
- XML [Visual Basic], IntelliSense
- IntelliSense [Visual Basic], XML
ms.assetid: 59506ce9-d64e-417e-90fc-e9fe19f0a8fa
caps.latest.revision: 27
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
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: 9a3c6f923bc9458997c388d4cf74ca113265a8cc
ms.contentlocale: pt-br
ms.lasthandoff: 06/01/2017

---
# <a name="xml-intellisense-in-visual-basic"></a><span data-ttu-id="c30fb-102">XML IntelliSense no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c30fb-102">XML IntelliSense in Visual Basic</span></span>
<span data-ttu-id="c30fb-103">Editor de código do Visual Basic inclui recursos do IntelliSense para XML que fornecem conclusão de palavras para os elementos definidos em um esquema XML.</span><span class="sxs-lookup"><span data-stu-id="c30fb-103">The Visual Basic Code Editor includes IntelliSense features for XML that provide word completion for elements defined in an XML schema.</span></span> <span data-ttu-id="c30fb-104">Se você incluir um arquivo de definição de esquema XML (XSD) no seu projeto e importar o namespace de destino do esquema usando o `Imports` instrução, o Editor de códigos irá incluir elementos do esquema XSD na lista do IntelliSense das variáveis de membro válido para <xref:System.Xml.Linq.XElement>e <xref:System.Xml.Linq.XDocument>objetos.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="c30fb-104">If you include an XML Schema Definition (XSD) file in your project and import the target namespace of the schema by using the `Imports` statement, the Code Editor will include elements from the XSD schema in the IntelliSense list of valid member variables for <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="c30fb-105">A ilustração a seguir mostra a lista de membros do IntelliSense para um <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="c30fb-105">The following illustration shows the IntelliSense members list for an <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="c30fb-106">![XML IntelliSense no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/media/xml_intellisense.png "XML_Intellisense")</span><span class="sxs-lookup"><span data-stu-id="c30fb-106">![XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/media/xml_intellisense.png "XML_Intellisense")</span></span>  
<span data-ttu-id="c30fb-107">XML IntelliSense</span><span class="sxs-lookup"><span data-stu-id="c30fb-107">XML IntelliSense</span></span>  
  
## <a name="enabling-xml-intellisense-in-visual-basic"></a><span data-ttu-id="c30fb-108">Habilitar o IntelliSense XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c30fb-108">Enabling XML IntelliSense in Visual Basic</span></span>  
 <span data-ttu-id="c30fb-109">Para habilitar o XML IntelliSense no Visual Basic, você deve incluir um arquivo de esquema XSD em seu projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c30fb-109">To enable XML IntelliSense in Visual Basic, you must include an XSD schema file in your Visual Basic project.</span></span> <span data-ttu-id="c30fb-110">Você também deve importar o namespace de destino para o esquema XSD para seu arquivo de código usando o `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="c30fb-110">You must also import the target namespace for the XSD schema into your code file by using the `Imports` statement.</span></span> <span data-ttu-id="c30fb-111">Como alternativa, você pode adicionar o namespace de destino à lista de namespace de nível de projeto usando o **referências** página do Designer de projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c30fb-111">Alternatively, you can add the target namespace to the project-level namespace list by using the **References** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="c30fb-112">Para obter exemplos, consulte [como: habilitar o XML IntelliSense no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md).</span><span class="sxs-lookup"><span data-stu-id="c30fb-112">For examples, see [How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md).</span></span> <span data-ttu-id="c30fb-113">Para obter mais informações, consulte [instrução Imports (Namespace XML)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) e [referências de página, Designer de projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c30fb-113">For more information, see [Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) and [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="c30fb-114">Observe que por padrão você não pode ver os arquivos de esquema XSD em projetos do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c30fb-114">Note that by default you cannot see XSD schema files in Visual Basic projects.</span></span> <span data-ttu-id="c30fb-115">Você talvez tenha que clicar o **Show All Files** para selecionar um arquivo XSD para incluir em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c30fb-115">You may have to click the **Show All Files** button to select an XSD file to include in your project.</span></span>  
  
### <a name="generating-a-schema-file-schema-inference"></a><span data-ttu-id="c30fb-116">Gerar um arquivo de esquema (inferência de esquema)</span><span class="sxs-lookup"><span data-stu-id="c30fb-116">Generating a Schema File (Schema Inference)</span></span>  
 <span data-ttu-id="c30fb-117">Você pode criar um esquema XSD para um arquivo XML existente inferindo o esquema XSD usando as ferramentas de XML do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c30fb-117">You can create an XSD schema for an existing XML file by inferring the XSD schema by using Visual Studio XML tools.</span></span>  
  
-   <span data-ttu-id="c30fb-118">A partir do SP1, você pode usar o Assistente de XML para esquema para criar um conjunto de esquema XML é inferido de um ou mais documentos XML e incluí-lo em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c30fb-118">Starting in SP1, you can use the XML to Schema Wizard to create an XML Schema set that is inferred from one or more XML documents and include it your project.</span></span> <span data-ttu-id="c30fb-119">Você pode usar qualquer combinação de documentos XML na forma de arquivos de texto, XML de endereços de HTTP Internet ou XML que é digitado ou colado em XML para Assistente de esquema.</span><span class="sxs-lookup"><span data-stu-id="c30fb-119">You can use any combination of XML documents in the form of text files, XML from HTTP Internet addresses, or XML that is typed or pasted into the XML to Schema Wizard.</span></span> <span data-ttu-id="c30fb-120">Para acessar o Assistente de XML para esquema, clique em **Adicionar Novo Item** no **projeto** menu e adicione um **XML para esquema** modelo do **dados** ou **itens comuns** grupo de modelos.</span><span class="sxs-lookup"><span data-stu-id="c30fb-120">To access the XML to Schema Wizard, click **Add New Item** on the **Project** menu and add an **XML to Schema** template from either the **Data** or **Common Items** template group.</span></span> <span data-ttu-id="c30fb-121">Depois de incluir todas as fontes de documento XML para inferir o conjunto de esquema XML do, clique em **Okey** criar o esquema inferido definido.</span><span class="sxs-lookup"><span data-stu-id="c30fb-121">After you have included all the XML document sources to infer the XML Schema set from, click **OK** to create the inferred schema set.</span></span> <span data-ttu-id="c30fb-122">Para obter mais informações, consulte [XML para Assistente de esquema](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md).</span><span class="sxs-lookup"><span data-stu-id="c30fb-122">For more information, see [XML to Schema Wizard](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md).</span></span>  
  
-   <span data-ttu-id="c30fb-123">Você também pode usar o Editor de XML do Visual Studio para inferir um esquema XSD definido de um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="c30fb-123">You can also use the Visual Studio XML Editor to infer an XSD schema set from an XML file.</span></span> <span data-ttu-id="c30fb-124">Para criar um esquema XML definido usando o Editor XML, abra um arquivo XML no Designer do Visual Studio XML e, em seguida, clique em **Create Schema** sobre o **XML** menu.</span><span class="sxs-lookup"><span data-stu-id="c30fb-124">To create an XML schema set by using the XML Editor, open an XML file in the Visual Studio XML Designer and then click **Create Schema** on the **XML** menu.</span></span> <span data-ttu-id="c30fb-125">Depois de criar o conjunto de esquema XSD, você pode salvar o conjunto de esquema criado para um ou mais arquivos XSD e incluí-los em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c30fb-125">After you create the XSD schema set, you can save the created schema set to one or more XSD files and include them in your project.</span></span> <span data-ttu-id="c30fb-126">Para obter mais informações, consulte[como: habilitar o XML IntelliSense no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md).</span><span class="sxs-lookup"><span data-stu-id="c30fb-126">For more information, see[How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md).</span></span>  
  
 <span data-ttu-id="c30fb-127">Observe que diferentes conjuntos de esquema XSD podem ser inferidos de vários documentos XML que devem ter o mesmo esquema.</span><span class="sxs-lookup"><span data-stu-id="c30fb-127">Note that different XSD schema sets might be inferred from multiple XML documents that are intended to have the same schema.</span></span> <span data-ttu-id="c30fb-128">Isso pode ocorrer quando determinados elementos e atributos são encontrados em um arquivo XML e não no outro, ou quando estiver incluído em uma ordem diferente, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="c30fb-128">This can occur when particular elements and attributes are found in one XML file and not in another, or when elements are included in different order, for example.</span></span> <span data-ttu-id="c30fb-129">Você deve examinar conjuntos de esquema XSD inferidos para a integridade e a precisão quando você usa a inferência de esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="c30fb-129">You should review inferred XSD schema sets for completeness and accuracy when you use XSD schema inference.</span></span>  
  
## <a name="member-list"></a><span data-ttu-id="c30fb-130">Lista de membros</span><span class="sxs-lookup"><span data-stu-id="c30fb-130">Member List</span></span>  
 <span data-ttu-id="c30fb-131">Depois de digitar um ponto (.) para delimitar uma instância de um <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>objeto (ou uma instância de `IEnumerable(Of XElement)` ou `IEnumerable(Of XDocument)`), Visual Basic IntelliSense exibe uma lista de possíveis membros do objeto.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="c30fb-131">After you type a period (.) to delimit an instance of an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object (or an instance of `IEnumerable(Of XElement)` or `IEnumerable(Of XDocument)`), Visual Basic IntelliSense displays a list of possible object members.</span></span> <span data-ttu-id="c30fb-132">A lista inicial inclui três opções que representam propriedades do eixo XML, conforme descrito na lista a seguir.</span><span class="sxs-lookup"><span data-stu-id="c30fb-132">The initial list includes three options that represent XML axis properties, as described in the following list.</span></span>  
  
|<span data-ttu-id="c30fb-133">Opção</span><span class="sxs-lookup"><span data-stu-id="c30fb-133">Option</span></span>|<span data-ttu-id="c30fb-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="c30fb-134">Description</span></span>|  
|---|---|  
|**\< >**|<span data-ttu-id="c30fb-135">Selecione esta opção para mostrar uma lista de possíveis filho elementos.</span><span class="sxs-lookup"><span data-stu-id="c30fb-135">Select this option to show a list of possible child elements.</span></span> <span data-ttu-id="c30fb-136">Para obter mais informações, consulte [o Literal de elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) e o <xref:System.Xml.Linq.XContainer.Elements%2A>método.</xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="c30fb-136">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>|  
|**@**|<span data-ttu-id="c30fb-137">Selecione esta opção para mostrar uma lista de possíveis atributos.</span><span class="sxs-lookup"><span data-stu-id="c30fb-137">Select this option to show a list of possible attributes.</span></span> <span data-ttu-id="c30fb-138">Para obter mais informações, consulte [propriedades do eixo XML](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md). Essa opção está disponível somente para objetos do tipo <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="c30fb-138">For more information, see [XML Axis Properties](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).This option is available only for objects of type <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="c30fb-139">**…\< >**</span><span class="sxs-lookup"><span data-stu-id="c30fb-139">**…\< >**</span></span>|<span data-ttu-id="c30fb-140">Selecione esta opção para mostrar uma lista de possíveis elementos descendentes.</span><span class="sxs-lookup"><span data-stu-id="c30fb-140">Select this option to show a list of possible descendant elements.</span></span> <span data-ttu-id="c30fb-141">Para obter mais informações, consulte [como: acessar XML descendente elementos](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md) e o <xref:System.Xml.Linq.XContainer.Elements%2A>método.</xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="c30fb-141">For more information, see [How to: Access XML Descendant Elements](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md) and the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>|  
  
 <span data-ttu-id="c30fb-142">Selecione ou começar a digitar qualquer uma das opções da lista XML.</span><span class="sxs-lookup"><span data-stu-id="c30fb-142">Select or begin typing any of the XML options from the list.</span></span> <span data-ttu-id="c30fb-143">A lista de membros, em seguida, exibirá possíveis membros do esquema XML que são específicos para a opção selecionada.</span><span class="sxs-lookup"><span data-stu-id="c30fb-143">The member list will then display potential members from the XML schema that are specific to the selected option.</span></span> <span data-ttu-id="c30fb-144">Se você tiver namespace XML importados que está associado com um prefixo de namespace XML específico, uma lista de possíveis prefixos de namespace XML está incluída na lista de membros.</span><span class="sxs-lookup"><span data-stu-id="c30fb-144">If you have XML namespaces imported that are associated with a specific XML namespace prefix, a list of potential XML namespace prefixes is included in the member list.</span></span>  
  
 <span data-ttu-id="c30fb-145">Por exemplo, considere o seguinte esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="c30fb-145">For example, consider the following XSD schema.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema attributeFormDefault="unqualified"   
           elementFormDefault="qualified"   
           targetNamespace="http://SamplePurchaseOrder"   
           xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="PurchaseOrders">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="PurchaseOrder">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="Address" />  
              <xs:element name="Items" />  
              <xs:element name="Comment" />  
            </xs:sequence>  
            <xs:attribute name="PurchaseOrderNumber" type="xs:unsignedShort" use="required" />  
            <xs:attribute name="OrderDate" type="xs:string" use="required" />  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="c30fb-146">XML válido para o esquema XSD seria semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="c30fb-146">Valid XML for the XSD schema would resemble the following.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<PurchaseOrders xmlns="http://SamplePurchaseOrder">  
  <PurchaseOrder PurchaseOrderNumber="12345" OrderDate="2000-1-1">  
    <Address />  
    <Items />  
    <Comment />  
  </PurchaseOrder>  
</PurchaseOrders>  
```  
  
 <span data-ttu-id="c30fb-147">Se você incluir esse arquivo de esquema XSD em um projeto e importa o namespace de destino do esquema XSD para seu arquivo de código ou projeto, o Visual Basic IntelliSense exibe membros do esquema conforme você digita seu código Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c30fb-147">If you include this XSD schema file in a project and import the target namespace from the XSD schema into your code file or project, Visual Basic IntelliSense displays members from the schema as you type your Visual Basic code.</span></span> <span data-ttu-id="c30fb-148">Se o namespace de destino para o esquema XSD é importado como o namespace padrão e digite o seguinte, o IntelliSense exibe uma lista dos elementos filho possíveis para o `PurchaseOrder` elemento XML.</span><span class="sxs-lookup"><span data-stu-id="c30fb-148">If the target namespace for the XSD schema is imported as the default namespace and you type the following, IntelliSense displays a list of possible child elements for the `PurchaseOrder` XML element.</span></span>  
  
```  
Dim po = <PurchaseOrder />  
po.<  
```  
  
 <span data-ttu-id="c30fb-149">A lista consiste nos elementos de endereço, comentário e itens.</span><span class="sxs-lookup"><span data-stu-id="c30fb-149">The list consists of the Address, Comment, and Items elements.</span></span>  
  
### <a name="certainty-levels-for-intellisense-list-items"></a><span data-ttu-id="c30fb-150">Níveis de certeza para itens de lista do IntelliSense</span><span class="sxs-lookup"><span data-stu-id="c30fb-150">Certainty Levels for IntelliSense List Items</span></span>  
 <span data-ttu-id="c30fb-151">Determinar o tipo XSD para usar no IntelliSense não é exato.</span><span class="sxs-lookup"><span data-stu-id="c30fb-151">Determining the XSD type to use for IntelliSense is not exact.</span></span> <span data-ttu-id="c30fb-152">Como resultado, o XML IntelliSense geralmente mostrará uma lista expandida de membros possíveis.</span><span class="sxs-lookup"><span data-stu-id="c30fb-152">As a result, XML IntelliSense will often show an expanded list of possible members.</span></span> <span data-ttu-id="c30fb-153">Para ajudar você a selecionar um item da lista de membros do IntelliSense, os itens são exibidos com uma indicação do nível de certeza que o XML IntelliSense tem para um determinado membro.</span><span class="sxs-lookup"><span data-stu-id="c30fb-153">To aid you in selecting an item from the IntelliSense member list, items are displayed with an indication of the level of certainty that XML IntelliSense has for a particular member.</span></span>  
  
 <span data-ttu-id="c30fb-154">Às vezes, XML IntelliSense pode identificar um tipo específico do esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="c30fb-154">Sometimes XML IntelliSense can identify a specific type from the XSD schema.</span></span> <span data-ttu-id="c30fb-155">Nesses casos, ele exibirá possíveis elementos filho, atributos ou elementos descendentes para aquele tipo XSD com um alto grau de certeza.</span><span class="sxs-lookup"><span data-stu-id="c30fb-155">In these cases, it will display possible child elements, attributes, or descendant elements for that XSD type with a high degree of certainty.</span></span> <span data-ttu-id="c30fb-156">Esses itens são identificados com uma marca de seleção.</span><span class="sxs-lookup"><span data-stu-id="c30fb-156">These items are identified with a check mark.</span></span>  
  
 <span data-ttu-id="c30fb-157">No entanto, às vezes, XML IntelliSense não é capaz de identificar um tipo específico do esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="c30fb-157">However, sometimes XML IntelliSense is not able to identify a specific type from the XSD schema.</span></span> <span data-ttu-id="c30fb-158">Nesses casos, ele exibirá uma lista expandida de possíveis elementos filho, atributos ou elementos descendentes do esquema XSD para o projeto com um baixo grau de certeza.</span><span class="sxs-lookup"><span data-stu-id="c30fb-158">In these cases, it will display an expanded list of possible child elements, attributes, or descendant elements from the XSD schema for the project with a low degree of certainty.</span></span> <span data-ttu-id="c30fb-159">Esses itens são identificados com um ponto de interrogação.</span><span class="sxs-lookup"><span data-stu-id="c30fb-159">These items are identified with a question mark.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c30fb-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c30fb-160">See Also</span></span>  
 <span data-ttu-id="c30fb-161">[Como: habilitar o XML IntelliSense no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md) </span><span class="sxs-lookup"><span data-stu-id="c30fb-161">[How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md) </span></span>  
<span data-ttu-id="c30fb-162"> [Assistente de esquema XML](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="c30fb-162"> [XML to Schema Wizard](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md) </span></span>  
<span data-ttu-id="c30fb-163"> [Instrução Imports (Namespace XML)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span><span class="sxs-lookup"><span data-stu-id="c30fb-163"> [Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span></span>  
<span data-ttu-id="c30fb-164"> [Literal do elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="c30fb-164"> [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="c30fb-165"> [Propriedade de eixo de atributo XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md) </span><span class="sxs-lookup"><span data-stu-id="c30fb-165"> [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md) </span></span>  
<span data-ttu-id="c30fb-166"> [Propriedade de eixo descendente XML](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md) </span><span class="sxs-lookup"><span data-stu-id="c30fb-166"> [XML Descendant Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md) </span></span>  
<span data-ttu-id="c30fb-167"> [Página Referências, Designer de Projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="c30fb-167"> [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span></span>
