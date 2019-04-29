---
title: Uso de System.XML
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
author: KrzysztofCwalina
ms.openlocfilehash: fc94ac62d1f2413c5f51446a8f6d0a52d9151557
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650122"
---
# <a name="systemxml-usage"></a><span data-ttu-id="cf0e0-102">Uso de System.XML</span><span class="sxs-lookup"><span data-stu-id="cf0e0-102">System.Xml Usage</span></span>
<span data-ttu-id="cf0e0-103">Esta seção fala sobre o uso de vários tipos que residem em <xref:System.Xml?displayProperty=nameWithType> namespaces que pode ser usado para representar dados XML.</span><span class="sxs-lookup"><span data-stu-id="cf0e0-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>  
  
 <span data-ttu-id="cf0e0-104">**X DO NOT** usar <xref:System.Xml.XmlNode> ou <xref:System.Xml.XmlDocument> para representar dados XML.</span><span class="sxs-lookup"><span data-stu-id="cf0e0-104">**X DO NOT** use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="cf0e0-105">Favorecer usando as instâncias de <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, ou subtipos <xref:System.Xml.Linq.XNode> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="cf0e0-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="cf0e0-106">`XmlNode` e `XmlDocument` não foi projetado para expor em APIs públicas.</span><span class="sxs-lookup"><span data-stu-id="cf0e0-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>  
  
 <span data-ttu-id="cf0e0-107">**✓ DO** usar `XmlReader`, `IXPathNavigable`, ou subtipos `XNode` como entrada ou saída de membros que aceitam ou retornam XML.</span><span class="sxs-lookup"><span data-stu-id="cf0e0-107">**✓ DO** use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>  
  
 <span data-ttu-id="cf0e0-108">Use essas abstrações em vez de `XmlDocument`, `XmlNode`, ou <xref:System.Xml.XPath.XPathDocument>, pois isso separa os métodos de implementações específicas de um documento XML na memória e lhes permite trabalhar com fontes de dados XML virtuais que expõem `XNode` , `XmlReader`, ou <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="cf0e0-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="cf0e0-109">**X DO NOT** subclasse `XmlDocument` se você deseja criar um tipo que representa uma exibição XML de uma fonte de dados ou modelo de objeto subjacente.</span><span class="sxs-lookup"><span data-stu-id="cf0e0-109">**X DO NOT** subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>  
  
 <span data-ttu-id="cf0e0-110">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="cf0e0-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="cf0e0-111">*Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="cf0e0-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf0e0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf0e0-112">See also</span></span>

- [<span data-ttu-id="cf0e0-113">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="cf0e0-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="cf0e0-114">Diretrizes de uso</span><span class="sxs-lookup"><span data-stu-id="cf0e0-114">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
