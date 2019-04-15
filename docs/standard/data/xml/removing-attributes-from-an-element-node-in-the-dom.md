---
title: Removendo os atributos de um nó no elemento DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e38ad777112e5e88fe40c530da6107d0de0e3ac
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336129"
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a><span data-ttu-id="a6766-102">Removendo os atributos de um nó no elemento DOM</span><span class="sxs-lookup"><span data-stu-id="a6766-102">Removing Attributes from an Element Node in the DOM</span></span>
<span data-ttu-id="a6766-103">Há várias maneiras para remover os atributos.</span><span class="sxs-lookup"><span data-stu-id="a6766-103">There are many ways to remove attributes.</span></span> <span data-ttu-id="a6766-104">Uma técnica é removê-los de coleção de atributo.</span><span class="sxs-lookup"><span data-stu-id="a6766-104">One technique is to remove them from the attribute collection.</span></span> <span data-ttu-id="a6766-105">Para fazer isso, as seguintes etapas são executadas:</span><span class="sxs-lookup"><span data-stu-id="a6766-105">To do this, the following steps are performed:</span></span>  
  
1. <span data-ttu-id="a6766-106">Obter a coleção de atributo do elemento usando `XmlAttributeCollection attrs = elem.Attributes;`.</span><span class="sxs-lookup"><span data-stu-id="a6766-106">Get the attribute collection from the element using `XmlAttributeCollection attrs = elem.Attributes;`.</span></span>  
  
2. <span data-ttu-id="a6766-107">Remova o atributo da coleção de atributo usando um dos três métodos:</span><span class="sxs-lookup"><span data-stu-id="a6766-107">Remove the attribute from the attribute collection using one of three methods:</span></span>  
  
    -   <span data-ttu-id="a6766-108">Use <xref:System.Xml.XmlAttributeCollection.Remove%2A> para remover um atributo específico.</span><span class="sxs-lookup"><span data-stu-id="a6766-108">Use <xref:System.Xml.XmlAttributeCollection.Remove%2A> to remove a specific attribute.</span></span>  
  
    -   <span data-ttu-id="a6766-109">Use <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> para remover todos os atributos de coleção e para permitir que o elemento sem atributos.</span><span class="sxs-lookup"><span data-stu-id="a6766-109">Use <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> to remove all attributes from the collection and leave the element with no attributes.</span></span>  
  
    -   <span data-ttu-id="a6766-110">Use <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> para remover um atributo da coleção de atributo usando o número de índice.</span><span class="sxs-lookup"><span data-stu-id="a6766-110">Use <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> to remove an attribute from the attribute collection by using its index number.</span></span>  
  
 <span data-ttu-id="a6766-111">Os seguintes métodos remove os atributos do nó do elemento.</span><span class="sxs-lookup"><span data-stu-id="a6766-111">The following methods remove attributes from the element node.</span></span>  
  
-   <span data-ttu-id="a6766-112">Use <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> para remover a coleção de atributo.</span><span class="sxs-lookup"><span data-stu-id="a6766-112">Use <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> to remove the attribute collection.</span></span>  
  
-   <span data-ttu-id="a6766-113">Use <xref:System.Xml.XmlElement.RemoveAttribute%2A> para remover por nome um único atributo de coleção.</span><span class="sxs-lookup"><span data-stu-id="a6766-113">Use <xref:System.Xml.XmlElement.RemoveAttribute%2A> to remove a single attribute by name from the collection.</span></span>  
  
-   <span data-ttu-id="a6766-114">Use <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> para remover um único atributo pelo número de índice da coleção.</span><span class="sxs-lookup"><span data-stu-id="a6766-114">Use <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> to remove a single attribute by index number from the collection.</span></span>  
  
 <span data-ttu-id="a6766-115">Uma alternativa é mais obter o elemento, obter o atributo de coleção de atributo, e remova diretamente o nó de atributo.</span><span class="sxs-lookup"><span data-stu-id="a6766-115">One more alternative is to get the element, get the attribute from the attribute collection, and remove the attribute node directly.</span></span> <span data-ttu-id="a6766-116">Para obter o atributo de coleção de atributo, você pode usar um nome, `XmlAttribute attr = attrs["attr_name"];`, um índice `XmlAttribute attr = attrs[0];`, ou qualificando totalmente o nome com o namespace `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.</span><span class="sxs-lookup"><span data-stu-id="a6766-116">To get the attribute from the attribute collection, you can use a name, `XmlAttribute attr = attrs["attr_name"];`, an index `XmlAttribute attr = attrs[0];`, or by fully qualifying the name with the namespace `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.</span></span>  
  
 <span data-ttu-id="a6766-117">Independentemente do método usado para remover os atributos, há limitações especiais em remover os atributos que são definidos como atributos padrão em Document type definition (DTD).</span><span class="sxs-lookup"><span data-stu-id="a6766-117">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the document type definition (DTD).</span></span> <span data-ttu-id="a6766-118">Os atributos padrão não podem ser removidos a menos que o elemento que pertencem a for removido.</span><span class="sxs-lookup"><span data-stu-id="a6766-118">Default attributes cannot be removed unless the element they belong to is removed.</span></span> <span data-ttu-id="a6766-119">Os atributos padrão são sempre atual para elementos que têm atributos padrões declarados.</span><span class="sxs-lookup"><span data-stu-id="a6766-119">Default attributes are always present for elements that have default attributes declared.</span></span> <span data-ttu-id="a6766-120">Removendo um padrão do atributo <xref:System.Xml.XmlAttributeCollection> ou de resultados de <xref:System.Xml.XmlElement> em um atributo de substituição inserido em <xref:System.Xml.XmlAttributeCollection> do elemento inicializado, o valor padrão que foi declarado.</span><span class="sxs-lookup"><span data-stu-id="a6766-120">Removing a default attribute from an <xref:System.Xml.XmlAttributeCollection> or from the <xref:System.Xml.XmlElement> results in a replacement attribute inserted into the <xref:System.Xml.XmlAttributeCollection> of the element, initialized to the default value that was declared.</span></span> <span data-ttu-id="a6766-121">Se você tiver um elemento definido como `<book att1="1" att2="2" att3="3"></book>`, então você tiver um elemento de `book` com os três atributos padrões declarados.</span><span class="sxs-lookup"><span data-stu-id="a6766-121">If you have an element defined as `<book att1="1" att2="2" att3="3"></book>`, then you have a `book` element with three default attributes declared.</span></span> <span data-ttu-id="a6766-122">A implementação DOM (Modelo de Objeto de Documento) de XML garante que, contanto que esse elemento `book` exista, ele tenha esses três atributos padrões de `att1`, `att2` e `att3`.</span><span class="sxs-lookup"><span data-stu-id="a6766-122">The XML Document Object Model (DOM) implementation guarantees that as long as this `book` element exists, it has these three default attributes of `att1`, `att2`, and `att3`.</span></span>  
  
 <span data-ttu-id="a6766-123">Quando chamado com <xref:System.Xml.XmlAttribute>, o método de <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> define o valor do atributo para String.Empty, como um atributo não pode existir sem um valor.</span><span class="sxs-lookup"><span data-stu-id="a6766-123">When called with an <xref:System.Xml.XmlAttribute>, the <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> method sets the value of the attribute to String.Empty, as an attribute cannot exist without a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6766-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6766-124">See also</span></span>

- [<span data-ttu-id="a6766-125">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="a6766-125">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
