---
title: "Como usar o padrão de detalhes mestre com dados XML hierárquicos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0ef460664b3701f4942b8c28b8e39f891d7c871
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a><span data-ttu-id="0a83d-102">Como usar o padrão de detalhes mestre com dados XML hierárquicos</span><span class="sxs-lookup"><span data-stu-id="0a83d-102">How to: Use the Master-Detail Pattern with Hierarchical XML Data</span></span>
<span data-ttu-id="0a83d-103">Este exemplo mostra como implementar o cenário mestre-detalhes com [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados.</span><span class="sxs-lookup"><span data-stu-id="0a83d-103">This example shows how to implement the master-detail scenario with [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a83d-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0a83d-104">Example</span></span>  
 <span data-ttu-id="0a83d-105">Este exemplo é o [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] versão de dados de exemplo discutido no [usam o padrão de detalhes mestre com dados hierárquicos](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).</span><span class="sxs-lookup"><span data-stu-id="0a83d-105">This example is the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data version of the example discussed in [Use the Master-Detail Pattern with Hierarchical Data](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).</span></span> <span data-ttu-id="0a83d-106">Neste exemplo, os dados são do arquivo `League.xml`.</span><span class="sxs-lookup"><span data-stu-id="0a83d-106">In this example, the data is from the file `League.xml`.</span></span> <span data-ttu-id="0a83d-107">Observe como o terceiro <xref:System.Windows.Controls.ListBox> controle rastreia as alterações de seleção no segundo <xref:System.Windows.Controls.ListBox> associando seu <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="0a83d-107">Note how the third <xref:System.Windows.Controls.ListBox> control tracks selection changes in the second <xref:System.Windows.Controls.ListBox> by binding to its <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property.</span></span>  
  
 [!code-xaml[MasterDetailXml#HowTo1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a><span data-ttu-id="0a83d-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a83d-108">See Also</span></span>  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [<span data-ttu-id="0a83d-109">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="0a83d-109">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
