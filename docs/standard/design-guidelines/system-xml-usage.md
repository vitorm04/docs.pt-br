---
title: Uso de System. XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce9869d538b69af9beaa74be3300175f279b8f53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="systemxml-usage"></a><span data-ttu-id="62c10-102">Uso de System. XML</span><span class="sxs-lookup"><span data-stu-id="62c10-102">System.Xml Usage</span></span>
<span data-ttu-id="62c10-103">Esta seção fala sobre o uso de vários tipos que residem em <xref:System.Xml?displayProperty=nameWithType> namespaces que podem ser usados para representar dados XML.</span><span class="sxs-lookup"><span data-stu-id="62c10-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>  
  
 <span data-ttu-id="62c10-104">**X não** usar <xref:System.Xml.XmlNode> ou <xref:System.Xml.XmlDocument> para representar dados XML.</span><span class="sxs-lookup"><span data-stu-id="62c10-104">**X DO NOT** use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="62c10-105">Favorecer usando as instâncias de <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, ou subtipos <xref:System.Xml.Linq.XNode> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="62c10-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="62c10-106">`XmlNode` e `XmlDocument` não são projetados para expor em APIs públicas.</span><span class="sxs-lookup"><span data-stu-id="62c10-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>  
  
 <span data-ttu-id="62c10-107">**FAZER ✓** usar `XmlReader`, `IXPathNavigable`, ou subtipos `XNode` como entrada ou saída de membros que aceitam ou retornam XML.</span><span class="sxs-lookup"><span data-stu-id="62c10-107">**✓ DO** use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>  
  
 <span data-ttu-id="62c10-108">Use essas abstrações em vez de `XmlDocument`, `XmlNode`, ou <xref:System.Xml.XPath.XPathDocument>, pois isso separa os métodos de implementações específicas de um documento XML na memória e permite trabalhar com fontes de dados XML virtuais que expõem `XNode` , `XmlReader`, ou <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="62c10-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="62c10-109">**X não** subclasse `XmlDocument` se você deseja criar um tipo que representa uma exibição XML de uma fonte de dados ou modelo de objeto subjacente.</span><span class="sxs-lookup"><span data-stu-id="62c10-109">**X DO NOT** subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>  
  
 <span data-ttu-id="62c10-110">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="62c10-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="62c10-111">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="62c10-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62c10-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62c10-112">See Also</span></span>  
 [<span data-ttu-id="62c10-113">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="62c10-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="62c10-114">Diretrizes de uso</span><span class="sxs-lookup"><span data-stu-id="62c10-114">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
