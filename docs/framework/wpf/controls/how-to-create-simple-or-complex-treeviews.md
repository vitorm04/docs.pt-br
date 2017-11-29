---
title: Como criar TreeViews simples ou complexos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TreeView control [WPF], creating
- Control class [WPF], TreeView [WPF], creating
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5e09f0f39d0c9a40a0e91299d308921917067166
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-simple-or-complex-treeviews"></a><span data-ttu-id="57ad4-102">Como criar TreeViews simples ou complexos</span><span class="sxs-lookup"><span data-stu-id="57ad4-102">How to: Create Simple or Complex TreeViews</span></span>
<span data-ttu-id="57ad4-103">Este exemplo mostra como criar simples ou complexa <xref:System.Windows.Controls.TreeView> controles.</span><span class="sxs-lookup"><span data-stu-id="57ad4-103">This example shows how to create simple or complex <xref:System.Windows.Controls.TreeView> controls.</span></span>  
  
 <span data-ttu-id="57ad4-104">Um <xref:System.Windows.Controls.TreeView> consiste em uma hierarquia de <xref:System.Windows.Controls.TreeViewItem> controles, que podem conter cadeias de caracteres de texto simples e também conteúdo mais complexo, como <xref:System.Windows.Controls.Button> controles ou <xref:System.Windows.Controls.StackPanel> com conteúdo incorporado.</span><span class="sxs-lookup"><span data-stu-id="57ad4-104">A <xref:System.Windows.Controls.TreeView> consists of a hierarchy of <xref:System.Windows.Controls.TreeViewItem> controls, which can contain simple text strings and also more complex content, such as <xref:System.Windows.Controls.Button> controls or a <xref:System.Windows.Controls.StackPanel> with embedded content.</span></span> <span data-ttu-id="57ad4-105">Você pode definir explicitamente o <xref:System.Windows.Controls.TreeView> conteúdo ou uma fonte de dados pode fornecer o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="57ad4-105">You can explicitly define the <xref:System.Windows.Controls.TreeView> content or a data source can provide the content.</span></span> <span data-ttu-id="57ad4-106">Este tópico fornece exemplos desses conceitos.</span><span class="sxs-lookup"><span data-stu-id="57ad4-106">This topic provides examples of these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57ad4-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="57ad4-107">Example</span></span>  
 <span data-ttu-id="57ad4-108">O <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> propriedade o <xref:System.Windows.Controls.TreeViewItem> contém o conteúdo que o <xref:System.Windows.Controls.TreeView> exibe para aquele item.</span><span class="sxs-lookup"><span data-stu-id="57ad4-108">The <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property of the <xref:System.Windows.Controls.TreeViewItem> contains the content that the <xref:System.Windows.Controls.TreeView> displays for that item.</span></span> <span data-ttu-id="57ad4-109">Um <xref:System.Windows.Controls.TreeViewItem> também pode ter <xref:System.Windows.Controls.TreeViewItem> controles como seus elementos filho e você podem definir esses elementos filho usando o <xref:System.Windows.Controls.ItemsControl.Items%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="57ad4-109">A <xref:System.Windows.Controls.TreeViewItem> can also have <xref:System.Windows.Controls.TreeViewItem> controls as its child elements and you can define these child elements by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="57ad4-110">O exemplo a seguir mostra como definir explicitamente <xref:System.Windows.Controls.TreeViewItem> conteúdo definindo o <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> propriedade como uma cadeia de caracteres de texto.</span><span class="sxs-lookup"><span data-stu-id="57ad4-110">The following example shows how to explicitly define <xref:System.Windows.Controls.TreeViewItem> content by setting the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property to a text string.</span></span>  
  
 [!code-xaml[TreeViewSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="57ad4-111">O exemplo a seguir mostram como definir os elementos filho de um <xref:System.Windows.Controls.TreeViewItem> definindo <xref:System.Windows.Controls.ItemsControl.Items%2A> que são <xref:System.Windows.Controls.Button> controles.</span><span class="sxs-lookup"><span data-stu-id="57ad4-111">The following example show how to define child elements of a <xref:System.Windows.Controls.TreeViewItem> by defining <xref:System.Windows.Controls.ItemsControl.Items%2A> that are <xref:System.Windows.Controls.Button> controls.</span></span>  
  
 [!code-xaml[TreeViewSimple#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 <span data-ttu-id="57ad4-112">O exemplo a seguir mostra como criar um <xref:System.Windows.Controls.TreeView> onde um <xref:System.Windows.Data.XmlDataProvider> fornece <xref:System.Windows.Controls.TreeViewItem> conteúdo e um <xref:System.Windows.HierarchicalDataTemplate> define a aparência do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="57ad4-112">The following example shows how to create a <xref:System.Windows.Controls.TreeView> where an <xref:System.Windows.Data.XmlDataProvider> provides <xref:System.Windows.Controls.TreeViewItem> content and a <xref:System.Windows.HierarchicalDataTemplate> defines the appearance of the content.</span></span>  
  
 [!code-xaml[TreeViewSimple#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xaml[TreeViewSimple#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xaml[TreeViewSimple#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 <span data-ttu-id="57ad4-113">O exemplo a seguir mostra como criar um <xref:System.Windows.Controls.TreeView> onde o <xref:System.Windows.Controls.TreeViewItem> contém conteúdo <xref:System.Windows.Controls.DockPanel> controles que têm conteúdo embutido.</span><span class="sxs-lookup"><span data-stu-id="57ad4-113">The following example shows how to create a <xref:System.Windows.Controls.TreeView> where the <xref:System.Windows.Controls.TreeViewItem> content contains <xref:System.Windows.Controls.DockPanel> controls that have embedded content.</span></span>  
  
 [!code-xaml[TreeViewSimple#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## <a name="see-also"></a><span data-ttu-id="57ad4-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57ad4-114">See Also</span></span>  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [<span data-ttu-id="57ad4-115">Visão geral de TreeView</span><span class="sxs-lookup"><span data-stu-id="57ad4-115">TreeView Overview</span></span>](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [<span data-ttu-id="57ad4-116">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="57ad4-116">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
