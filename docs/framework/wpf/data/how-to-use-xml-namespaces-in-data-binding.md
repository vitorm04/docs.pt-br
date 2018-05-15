---
title: Como usar namespaces XML na vinculação de dados
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: 483b59bb7cea25617c832b96690f742b8b64b3e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a><span data-ttu-id="5c56b-102">Como usar namespaces XML na vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="5c56b-102">How to: Use XML Namespaces in Data Binding</span></span>
## <a name="example"></a><span data-ttu-id="5c56b-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5c56b-103">Example</span></span>  
 <span data-ttu-id="5c56b-104">Este exemplo mostra como lidar com namespaces especificados em seu [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] fonte da associação.</span><span class="sxs-lookup"><span data-stu-id="5c56b-104">This example shows how to handle namespaces specified in your [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] binding source.</span></span>  
  
 <span data-ttu-id="5c56b-105">Se seu [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados tem as seguintes [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] definição de namespace:</span><span class="sxs-lookup"><span data-stu-id="5c56b-105">If your [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data has the following [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace definition:</span></span>  
  
 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`  
  
 <span data-ttu-id="5c56b-106">Você pode usar o <xref:System.Windows.Data.XmlNamespaceMapping> elemento para mapear o namespace para um <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5c56b-106">You can use the <xref:System.Windows.Data.XmlNamespaceMapping> element to map the namespace to a <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, as in the following example.</span></span> <span data-ttu-id="5c56b-107">Você pode usar o <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> para referir-se a [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace.</span><span class="sxs-lookup"><span data-stu-id="5c56b-107">You can then use the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> to refer to the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace.</span></span> <span data-ttu-id="5c56b-108">O <xref:System.Windows.Controls.ListBox> neste exemplo exibe o *título* e *DC: Date* de cada *item*.</span><span class="sxs-lookup"><span data-stu-id="5c56b-108">The <xref:System.Windows.Controls.ListBox> in this example displays the *title* and *dc:date* of each *item*.</span></span>  
  
 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]  
  
 <span data-ttu-id="5c56b-109">Observe que o <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> você especificar não precisa corresponder à usada no [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] fonte; se o prefixo for alterado no [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] fonte seu mapeamento ainda funciona.</span><span class="sxs-lookup"><span data-stu-id="5c56b-109">Note that the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> you specify does not have to match the one used in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source; if the prefix changes in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source your mapping still works.</span></span>  
  
 <span data-ttu-id="5c56b-110">Nesse exemplo específico, o [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] os dados vêm de um serviço web, mas o <xref:System.Windows.Data.XmlNamespaceMapping> elemento também funciona com embutido [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ou [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados em um arquivo incorporado.</span><span class="sxs-lookup"><span data-stu-id="5c56b-110">In this particular example, the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data comes from a web service, but the <xref:System.Windows.Data.XmlNamespaceMapping> element also works with inline [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] or [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data in an embedded file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c56b-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c56b-111">See Also</span></span>  
 [<span data-ttu-id="5c56b-112">Associar dados XML usando um XMLDataProvider e consultas XPath</span><span class="sxs-lookup"><span data-stu-id="5c56b-112">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [<span data-ttu-id="5c56b-113">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="5c56b-113">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="5c56b-114">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="5c56b-114">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
