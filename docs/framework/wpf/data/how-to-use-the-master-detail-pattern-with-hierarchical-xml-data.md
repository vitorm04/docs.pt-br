---
title: 'Como: Usar o padrão de detalhes mestre com os dados XML hierárquicos'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: ba6c932f519ffa5c3c70ecb21eb9b5d08c40fb28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086254"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a><span data-ttu-id="0e6ad-102">Como: Usar o padrão de detalhes mestre com os dados XML hierárquicos</span><span class="sxs-lookup"><span data-stu-id="0e6ad-102">How to: Use the Master-Detail Pattern with Hierarchical XML Data</span></span>
<span data-ttu-id="0e6ad-103">Este exemplo mostra como implementar o cenário mestre / detalhes com [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados.</span><span class="sxs-lookup"><span data-stu-id="0e6ad-103">This example shows how to implement the master-detail scenario with [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e6ad-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0e6ad-104">Example</span></span>  
 <span data-ttu-id="0e6ad-105">Este exemplo é o [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] versão de dados de exemplo discutido no [usar o padrão de detalhes mestre com dados hierárquicos](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).</span><span class="sxs-lookup"><span data-stu-id="0e6ad-105">This example is the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data version of the example discussed in [Use the Master-Detail Pattern with Hierarchical Data](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).</span></span> <span data-ttu-id="0e6ad-106">Neste exemplo, os dados são do arquivo `League.xml`.</span><span class="sxs-lookup"><span data-stu-id="0e6ad-106">In this example, the data is from the file `League.xml`.</span></span> <span data-ttu-id="0e6ad-107">Observe como o terceiro <xref:System.Windows.Controls.ListBox> controle rastreia as alterações de seleção na segunda <xref:System.Windows.Controls.ListBox> fazendo a ligação com seu <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="0e6ad-107">Note how the third <xref:System.Windows.Controls.ListBox> control tracks selection changes in the second <xref:System.Windows.Controls.ListBox> by binding to its <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property.</span></span>  
  
 [!code-xaml[MasterDetailXml#HowTo1](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a><span data-ttu-id="0e6ad-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e6ad-108">See also</span></span>

- <xref:System.Windows.HierarchicalDataTemplate>
- [<span data-ttu-id="0e6ad-109">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="0e6ad-109">How-to Topics</span></span>](data-binding-how-to-topics.md)
