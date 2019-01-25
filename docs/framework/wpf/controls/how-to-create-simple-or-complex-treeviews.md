---
title: 'Como: Criar TreeViews simples ou complexos'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], creating
- Control class [WPF], TreeView [WPF], creating
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
ms.openlocfilehash: d6f9653304b67948d8a8995d1582cb10b012ee06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609129"
---
# <a name="how-to-create-simple-or-complex-treeviews"></a><span data-ttu-id="e1705-102">Como: Criar TreeViews simples ou complexos</span><span class="sxs-lookup"><span data-stu-id="e1705-102">How to: Create Simple or Complex TreeViews</span></span>
<span data-ttu-id="e1705-103">Este exemplo mostra como criar simples ou complexos <xref:System.Windows.Controls.TreeView> controles.</span><span class="sxs-lookup"><span data-stu-id="e1705-103">This example shows how to create simple or complex <xref:System.Windows.Controls.TreeView> controls.</span></span>  
  
 <span data-ttu-id="e1705-104">Um <xref:System.Windows.Controls.TreeView> consiste em uma hierarquia do <xref:System.Windows.Controls.TreeViewItem> controles, que podem conter cadeias de caracteres de texto simples e também conteúdo mais complexo, como <xref:System.Windows.Controls.Button> controles ou um <xref:System.Windows.Controls.StackPanel> com conteúdo inserido.</span><span class="sxs-lookup"><span data-stu-id="e1705-104">A <xref:System.Windows.Controls.TreeView> consists of a hierarchy of <xref:System.Windows.Controls.TreeViewItem> controls, which can contain simple text strings and also more complex content, such as <xref:System.Windows.Controls.Button> controls or a <xref:System.Windows.Controls.StackPanel> with embedded content.</span></span> <span data-ttu-id="e1705-105">Você pode definir explicitamente o <xref:System.Windows.Controls.TreeView> conteúdo ou uma fonte de dados pode fornecer o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="e1705-105">You can explicitly define the <xref:System.Windows.Controls.TreeView> content or a data source can provide the content.</span></span> <span data-ttu-id="e1705-106">Este tópico fornece exemplos desses conceitos.</span><span class="sxs-lookup"><span data-stu-id="e1705-106">This topic provides examples of these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1705-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1705-107">Example</span></span>  
 <span data-ttu-id="e1705-108">O <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> propriedade do <xref:System.Windows.Controls.TreeViewItem> contém o conteúdo que o <xref:System.Windows.Controls.TreeView> exibe para aquele item.</span><span class="sxs-lookup"><span data-stu-id="e1705-108">The <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property of the <xref:System.Windows.Controls.TreeViewItem> contains the content that the <xref:System.Windows.Controls.TreeView> displays for that item.</span></span> <span data-ttu-id="e1705-109">Um <xref:System.Windows.Controls.TreeViewItem> também pode ter <xref:System.Windows.Controls.TreeViewItem> controles como seus elementos filho e você podem definir esses elementos filho usando o <xref:System.Windows.Controls.ItemsControl.Items%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="e1705-109">A <xref:System.Windows.Controls.TreeViewItem> can also have <xref:System.Windows.Controls.TreeViewItem> controls as its child elements and you can define these child elements by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="e1705-110">O exemplo a seguir mostra como definir explicitamente <xref:System.Windows.Controls.TreeViewItem> conteúdo, definindo o <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> propriedade como uma cadeia de caracteres de texto.</span><span class="sxs-lookup"><span data-stu-id="e1705-110">The following example shows how to explicitly define <xref:System.Windows.Controls.TreeViewItem> content by setting the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property to a text string.</span></span>  
  
 [!code-xaml[TreeViewSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="e1705-111">O exemplo a seguir mostram como definir os elementos filho de um <xref:System.Windows.Controls.TreeViewItem> definindo <xref:System.Windows.Controls.ItemsControl.Items%2A> que são <xref:System.Windows.Controls.Button> controles.</span><span class="sxs-lookup"><span data-stu-id="e1705-111">The following example show how to define child elements of a <xref:System.Windows.Controls.TreeViewItem> by defining <xref:System.Windows.Controls.ItemsControl.Items%2A> that are <xref:System.Windows.Controls.Button> controls.</span></span>  
  
 [!code-xaml[TreeViewSimple#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 <span data-ttu-id="e1705-112">O exemplo a seguir mostra como criar uma <xref:System.Windows.Controls.TreeView> em que um <xref:System.Windows.Data.XmlDataProvider> fornece <xref:System.Windows.Controls.TreeViewItem> conteúdo e um <xref:System.Windows.HierarchicalDataTemplate> define a aparência do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="e1705-112">The following example shows how to create a <xref:System.Windows.Controls.TreeView> where an <xref:System.Windows.Data.XmlDataProvider> provides <xref:System.Windows.Controls.TreeViewItem> content and a <xref:System.Windows.HierarchicalDataTemplate> defines the appearance of the content.</span></span>  
  
 [!code-xaml[TreeViewSimple#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xaml[TreeViewSimple#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xaml[TreeViewSimple#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 <span data-ttu-id="e1705-113">O exemplo a seguir mostra como criar uma <xref:System.Windows.Controls.TreeView> onde o <xref:System.Windows.Controls.TreeViewItem> contém conteúdo <xref:System.Windows.Controls.DockPanel> controles que têm um conteúdo embutido.</span><span class="sxs-lookup"><span data-stu-id="e1705-113">The following example shows how to create a <xref:System.Windows.Controls.TreeView> where the <xref:System.Windows.Controls.TreeViewItem> content contains <xref:System.Windows.Controls.DockPanel> controls that have embedded content.</span></span>  
  
 [!code-xaml[TreeViewSimple#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## <a name="see-also"></a><span data-ttu-id="e1705-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1705-114">See also</span></span>
- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [<span data-ttu-id="e1705-115">Visão geral de TreeView</span><span class="sxs-lookup"><span data-stu-id="e1705-115">TreeView Overview</span></span>](../../../../docs/framework/wpf/controls/treeview-overview.md)
- [<span data-ttu-id="e1705-116">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="e1705-116">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
