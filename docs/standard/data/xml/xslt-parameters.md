---
title: Parâmetros XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef57d16c52100398919563205a97205be3c5dd7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570592"
---
# <a name="xslt-parameters"></a><span data-ttu-id="b75db-102">Parâmetros XSLT</span><span class="sxs-lookup"><span data-stu-id="b75db-102">XSLT Parameters</span></span>
<span data-ttu-id="b75db-103">Os parâmetros XSLT são adicionados a <xref:System.Xml.Xsl.XsltArgumentList> usando o método <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> .</span><span class="sxs-lookup"><span data-stu-id="b75db-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="b75db-104">Um nome qualificado e URI de namespace são associados com o objeto de parâmetro no momento.</span><span class="sxs-lookup"><span data-stu-id="b75db-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="b75db-105">Para usar um parâmetro XSLT</span><span class="sxs-lookup"><span data-stu-id="b75db-105">To use an XSLT parameter</span></span>  
  
1.  <span data-ttu-id="b75db-106">Crie um objeto de <xref:System.Xml.Xsl.XsltArgumentList> e adicione o parâmetro usando o método <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> .</span><span class="sxs-lookup"><span data-stu-id="b75db-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2.  <span data-ttu-id="b75db-107">Chame o parâmetro folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="b75db-107">Call the parameter from the style sheet.</span></span>  
  
3.  <span data-ttu-id="b75db-108">Passe o objeto de <xref:System.Xml.Xsl.XsltArgumentList> para o método de <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> .</span><span class="sxs-lookup"><span data-stu-id="b75db-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="b75db-109">Tipos de parâmetro</span><span class="sxs-lookup"><span data-stu-id="b75db-109">Parameter Types</span></span>  
 <span data-ttu-id="b75db-110">O objeto de parâmetro deve corresponder a um tipo W3C.</span><span class="sxs-lookup"><span data-stu-id="b75db-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="b75db-111">A tabela seguinte mostra tipos correspondentes W3C, as classes equivalentes do Microsoft.NET (tipo), e se o tipo W3C é um tipo XPath ou tipo de fonte.</span><span class="sxs-lookup"><span data-stu-id="b75db-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="b75db-112">Tipo W3C</span><span class="sxs-lookup"><span data-stu-id="b75db-112">W3C type</span></span>|<span data-ttu-id="b75db-113">Classe. NET equivalente (tipo)</span><span class="sxs-lookup"><span data-stu-id="b75db-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="b75db-114">XPath ou tipo XSLT</span><span class="sxs-lookup"><span data-stu-id="b75db-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="b75db-115">XPath</span><span class="sxs-lookup"><span data-stu-id="b75db-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="b75db-116">XPath</span><span class="sxs-lookup"><span data-stu-id="b75db-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="b75db-117">XPath</span><span class="sxs-lookup"><span data-stu-id="b75db-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="b75db-118">XSLT</span><span class="sxs-lookup"><span data-stu-id="b75db-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="b75db-119">XPath</span><span class="sxs-lookup"><span data-stu-id="b75db-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="b75db-120">**XPathNavigator[]**</span><span class="sxs-lookup"><span data-stu-id="b75db-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="b75db-121">XPath</span><span class="sxs-lookup"><span data-stu-id="b75db-121">XPath</span></span>|  
  
 <span data-ttu-id="b75db-122">os \*This são equivalentes a um nó definida que contém um único nó.</span><span class="sxs-lookup"><span data-stu-id="b75db-122">\*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="b75db-123">Se o objeto de parâmetro não é uma das classes anterior, ele é convertido de acordo com as regras a seguir.</span><span class="sxs-lookup"><span data-stu-id="b75db-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="b75db-124">Os tipos numéricos do Common Language Runtime (CLR) são convertidos a <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="b75db-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="b75db-125">O tipo <xref:System.DateTime> é convertido em <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b75db-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="b75db-126">Os tipos <xref:System.Xml.XPath.IXPathNavigable> são convertidos em <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="b75db-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="b75db-127">**XPathNavigator[]** é convertido em <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="b75db-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="b75db-128">Todos os outros tipos lançam um erro.</span><span class="sxs-lookup"><span data-stu-id="b75db-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b75db-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b75db-129">Example</span></span>  
 <span data-ttu-id="b75db-130">O exemplo a seguir usa o método de <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> para criar um parâmetro para armazenar calculou a data de desconto.</span><span class="sxs-lookup"><span data-stu-id="b75db-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="b75db-131">A data de desconto é calculada para ser a 20 dias de data pedido.</span><span class="sxs-lookup"><span data-stu-id="b75db-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="b75db-132">Entrada</span><span class="sxs-lookup"><span data-stu-id="b75db-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="b75db-133">order.xml</span><span class="sxs-lookup"><span data-stu-id="b75db-133">order.xml</span></span>  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="b75db-134">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="b75db-134">discount.xsl</span></span>  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="b75db-135">Saída</span><span class="sxs-lookup"><span data-stu-id="b75db-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b75db-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b75db-136">See Also</span></span>  
 [<span data-ttu-id="b75db-137">Transformações XSLT</span><span class="sxs-lookup"><span data-stu-id="b75db-137">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
