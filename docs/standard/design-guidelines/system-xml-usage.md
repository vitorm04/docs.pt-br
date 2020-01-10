---
title: Uso de System.XML
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: c57f5451526094d58066d7d391f41795f17732de
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709030"
---
# <a name="systemxml-usage"></a><span data-ttu-id="d5a82-102">Uso de System.XML</span><span class="sxs-lookup"><span data-stu-id="d5a82-102">System.Xml Usage</span></span>
<span data-ttu-id="d5a82-103">Esta seção fala sobre o uso de vários tipos que residem em namespaces <xref:System.Xml?displayProperty=nameWithType> que podem ser usados para representar dados XML.</span><span class="sxs-lookup"><span data-stu-id="d5a82-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>  
  
 <span data-ttu-id="d5a82-104">**X DO NOT** usar <xref:System.Xml.XmlNode> ou <xref:System.Xml.XmlDocument> para representar dados XML.</span><span class="sxs-lookup"><span data-stu-id="d5a82-104">**X DO NOT** use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="d5a82-105">Favor usar instâncias de <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>ou subtipos de <xref:System.Xml.Linq.XNode> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="d5a82-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="d5a82-106">`XmlNode` e `XmlDocument` não são projetados para exposição em APIs públicas.</span><span class="sxs-lookup"><span data-stu-id="d5a82-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>  
  
 <span data-ttu-id="d5a82-107">**✓ DO** usar `XmlReader`, `IXPathNavigable`, ou subtipos `XNode` como entrada ou saída de membros que aceitam ou retornam XML.</span><span class="sxs-lookup"><span data-stu-id="d5a82-107">**✓ DO** use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>  
  
 <span data-ttu-id="d5a82-108">Use essas abstrações em vez de `XmlDocument`, `XmlNode`ou <xref:System.Xml.XPath.XPathDocument>, porque isso dissocia os métodos de implementações específicas de um documento XML na memória e permite que eles trabalhem com fontes de dados XML virtuais que expõem `XNode`, `XmlReader`ou <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="d5a82-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="d5a82-109">**X DO NOT** subclasse `XmlDocument` se você deseja criar um tipo que representa uma exibição XML de uma fonte de dados ou modelo de objeto subjacente.</span><span class="sxs-lookup"><span data-stu-id="d5a82-109">**X DO NOT** subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>  
  
 <span data-ttu-id="d5a82-110">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="d5a82-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d5a82-111">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="d5a82-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5a82-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="d5a82-112">See also</span></span>

- [<span data-ttu-id="d5a82-113">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="d5a82-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="d5a82-114">Diretrizes de uso</span><span class="sxs-lookup"><span data-stu-id="d5a82-114">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
