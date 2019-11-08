---
title: Como usar namespaces XML na vinculação de dados
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: f6e6e042fa5583fcf91bd15c524537490fb6670c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740580"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a><span data-ttu-id="4d1ad-102">Como usar namespaces XML na vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="4d1ad-102">How to: Use XML Namespaces in Data Binding</span></span>
## <a name="example"></a><span data-ttu-id="4d1ad-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d1ad-103">Example</span></span>
 <span data-ttu-id="4d1ad-104">Este exemplo mostra como tratar namespaces especificados em sua origem de associação XML.</span><span class="sxs-lookup"><span data-stu-id="4d1ad-104">This example shows how to handle namespaces specified in your XML binding source.</span></span>

 <span data-ttu-id="4d1ad-105">Se os dados XML tiverem a seguinte definição de namespace XML:</span><span class="sxs-lookup"><span data-stu-id="4d1ad-105">If your XML data has the following XML namespace definition:</span></span>

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 <span data-ttu-id="4d1ad-106">Você pode usar o elemento <xref:System.Windows.Data.XmlNamespaceMapping> para mapear o namespace para um <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4d1ad-106">You can use the <xref:System.Windows.Data.XmlNamespaceMapping> element to map the namespace to a <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, as in the following example.</span></span> <span data-ttu-id="4d1ad-107">Você pode usar o <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> para se referir ao namespace XML.</span><span class="sxs-lookup"><span data-stu-id="4d1ad-107">You can then use the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> to refer to the XML namespace.</span></span> <span data-ttu-id="4d1ad-108">O <xref:System.Windows.Controls.ListBox> neste exemplo exibe o *título* e o *DC: data* de cada *Item*.</span><span class="sxs-lookup"><span data-stu-id="4d1ad-108">The <xref:System.Windows.Controls.ListBox> in this example displays the *title* and *dc:date* of each *item*.</span></span>

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 <span data-ttu-id="4d1ad-109">Observe que o <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> especificado não precisa corresponder ao usado na origem XML; Se o prefixo for alterado na origem XML, seu mapeamento ainda funcionará.</span><span class="sxs-lookup"><span data-stu-id="4d1ad-109">Note that the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> you specify does not have to match the one used in the XML source; if the prefix changes in the XML source your mapping still works.</span></span>

 <span data-ttu-id="4d1ad-110">Neste exemplo específico, os dados XML vêm de um serviço Web, mas o elemento <xref:System.Windows.Data.XmlNamespaceMapping> também funciona com dados XML ou XML embutidos em um arquivo inserido.</span><span class="sxs-lookup"><span data-stu-id="4d1ad-110">In this particular example, the XML data comes from a web service, but the <xref:System.Windows.Data.XmlNamespaceMapping> element also works with inline XML or XML data in an embedded file.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d1ad-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d1ad-111">See also</span></span>

- [<span data-ttu-id="4d1ad-112">Associar dados XML usando um XMLDataProvider e consultas XPath</span><span class="sxs-lookup"><span data-stu-id="4d1ad-112">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="4d1ad-113">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="4d1ad-113">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="4d1ad-114">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="4d1ad-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
