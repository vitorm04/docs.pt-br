---
title: Como associar um ListBox a dados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4701fe99231e115eb8cb14f7c1e5e003928bc5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-a-listbox-to-data"></a><span data-ttu-id="b68e8-102">Como associar um ListBox a dados</span><span class="sxs-lookup"><span data-stu-id="b68e8-102">How to: Bind a ListBox to Data</span></span>
<span data-ttu-id="b68e8-103">Um desenvolvedor de aplicativos pode criar <xref:System.Windows.Controls.ListBox> controles sem especificar o conteúdo de cada <xref:System.Windows.Controls.ListBoxItem> separadamente.</span><span class="sxs-lookup"><span data-stu-id="b68e8-103">An application developer can create <xref:System.Windows.Controls.ListBox> controls without specifying the contents of each <xref:System.Windows.Controls.ListBoxItem> separately.</span></span> <span data-ttu-id="b68e8-104">Você pode usar a associação de dados para associar dados aos itens individuais.</span><span class="sxs-lookup"><span data-stu-id="b68e8-104">You can use data binding to bind data to the individual items.</span></span>  
  
 <span data-ttu-id="b68e8-105">O exemplo a seguir mostra como criar um <xref:System.Windows.Controls.ListBox> que preenche a <xref:System.Windows.Controls.ListBoxItem> elementos de associação de dados a uma fonte de dados chamada *cores*.</span><span class="sxs-lookup"><span data-stu-id="b68e8-105">The following example shows how to create a <xref:System.Windows.Controls.ListBox> that populates the <xref:System.Windows.Controls.ListBoxItem> elements by data binding to a data source called *Colors*.</span></span> <span data-ttu-id="b68e8-106">Nesse caso não é necessário usar <xref:System.Windows.Controls.ListBoxItem> marcas para especificar o conteúdo de cada item.</span><span class="sxs-lookup"><span data-stu-id="b68e8-106">In this case it is not necessary to use <xref:System.Windows.Controls.ListBoxItem> tags to specify the content of each item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b68e8-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b68e8-107">Example</span></span>  
 [!code-xaml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b68e8-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b68e8-108">See Also</span></span>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.Controls.ListBoxItem>  
 [<span data-ttu-id="b68e8-109">Controles</span><span class="sxs-lookup"><span data-stu-id="b68e8-109">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
