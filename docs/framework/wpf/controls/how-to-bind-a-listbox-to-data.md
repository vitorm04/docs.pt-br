---
title: 'Como: Associar um ListBox a dados'
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
ms.openlocfilehash: 6d37cda057ea1e7ca6761363857a2647da37afee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650646"
---
# <a name="how-to-bind-a-listbox-to-data"></a><span data-ttu-id="0c95b-102">Como: Associar um ListBox a dados</span><span class="sxs-lookup"><span data-stu-id="0c95b-102">How to: Bind a ListBox to Data</span></span>
<span data-ttu-id="0c95b-103">Um desenvolvedor de aplicativos pode criar <xref:System.Windows.Controls.ListBox> controles sem especificar o conteúdo de cada <xref:System.Windows.Controls.ListBoxItem> separadamente.</span><span class="sxs-lookup"><span data-stu-id="0c95b-103">An application developer can create <xref:System.Windows.Controls.ListBox> controls without specifying the contents of each <xref:System.Windows.Controls.ListBoxItem> separately.</span></span> <span data-ttu-id="0c95b-104">Você pode usar a vinculação de dados para associar dados aos itens individuais.</span><span class="sxs-lookup"><span data-stu-id="0c95b-104">You can use data binding to bind data to the individual items.</span></span>  
  
 <span data-ttu-id="0c95b-105">O exemplo a seguir mostra como criar uma <xref:System.Windows.Controls.ListBox> que preenche a <xref:System.Windows.Controls.ListBoxItem> elementos pela vinculação de dados a uma fonte de dados chamada *cores*.</span><span class="sxs-lookup"><span data-stu-id="0c95b-105">The following example shows how to create a <xref:System.Windows.Controls.ListBox> that populates the <xref:System.Windows.Controls.ListBoxItem> elements by data binding to a data source called *Colors*.</span></span> <span data-ttu-id="0c95b-106">Nesse caso, não é necessário usar <xref:System.Windows.Controls.ListBoxItem> marcas para especificar o conteúdo de cada item.</span><span class="sxs-lookup"><span data-stu-id="0c95b-106">In this case it is not necessary to use <xref:System.Windows.Controls.ListBoxItem> tags to specify the content of each item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c95b-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c95b-107">Example</span></span>  
 [!code-xaml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="0c95b-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c95b-108">See also</span></span>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.Controls.ListBoxItem>
- [<span data-ttu-id="0c95b-109">Controles</span><span class="sxs-lookup"><span data-stu-id="0c95b-109">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
