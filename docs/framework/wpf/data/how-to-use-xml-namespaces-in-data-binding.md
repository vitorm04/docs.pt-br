---
title: Como usar namespaces XML na vinculação de dados
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: 9d8ddc5445bac28c68cd6cc99acf3313613a8c7f
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919661"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a><span data-ttu-id="773f9-102">Como usar namespaces XML na vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="773f9-102">How to: Use XML Namespaces in Data Binding</span></span>
## <a name="example"></a><span data-ttu-id="773f9-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="773f9-103">Example</span></span>
 <span data-ttu-id="773f9-104">Este exemplo mostra como tratar namespaces especificados em sua fonte de associação de [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="773f9-104">This example shows how to handle namespaces specified in your [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] binding source.</span></span>

 <span data-ttu-id="773f9-105">Se seus dados de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] tiverem a seguinte definição de namespace [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="773f9-105">If your [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data has the following [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace definition:</span></span>

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 <span data-ttu-id="773f9-106">Você pode usar o elemento <xref:System.Windows.Data.XmlNamespaceMapping> para mapear o namespace para um <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="773f9-106">You can use the <xref:System.Windows.Data.XmlNamespaceMapping> element to map the namespace to a <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, as in the following example.</span></span> <span data-ttu-id="773f9-107">Em seguida, você pode usar o <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> para fazer referência ao namespace [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="773f9-107">You can then use the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> to refer to the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace.</span></span> <span data-ttu-id="773f9-108">O <xref:System.Windows.Controls.ListBox> neste exemplo exibe o *título* e o *DC: data* de cada *Item*.</span><span class="sxs-lookup"><span data-stu-id="773f9-108">The <xref:System.Windows.Controls.ListBox> in this example displays the *title* and *dc:date* of each *item*.</span></span>

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 <span data-ttu-id="773f9-109">Observe que o <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> especificado não precisa corresponder ao usado na fonte de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]; Se o prefixo for alterado na fonte de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], seu mapeamento ainda funcionará.</span><span class="sxs-lookup"><span data-stu-id="773f9-109">Note that the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> you specify does not have to match the one used in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source; if the prefix changes in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source your mapping still works.</span></span>

 <span data-ttu-id="773f9-110">Neste exemplo específico, os dados de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] vêm de um serviço Web, mas o elemento <xref:System.Windows.Data.XmlNamespaceMapping> também funciona com dados embutidos [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ou [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] em um arquivo inserido.</span><span class="sxs-lookup"><span data-stu-id="773f9-110">In this particular example, the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data comes from a web service, but the <xref:System.Windows.Data.XmlNamespaceMapping> element also works with inline [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] or [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data in an embedded file.</span></span>

## <a name="see-also"></a><span data-ttu-id="773f9-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="773f9-111">See also</span></span>

- [<span data-ttu-id="773f9-112">Associar dados XML usando um XMLDataProvider e consultas XPath</span><span class="sxs-lookup"><span data-stu-id="773f9-112">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="773f9-113">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="773f9-113">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="773f9-114">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="773f9-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
