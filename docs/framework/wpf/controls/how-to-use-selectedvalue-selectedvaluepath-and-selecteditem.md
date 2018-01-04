---
title: Como usar SelectedValue, SelectedValuePath e SelectedItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TreeView control [WPF], SelectedValue properties
- Control class [WPF], SelectedItem properties
- Control class [WPF], TreeView properties
- Control class [WPF], SelectedValue properties
- TreeView control [WPF], SelectedItem properties
- SelectedValue [WPF], SelectedValuePath properties
- TreeView control [WPF], SelectedValuePath properties
- Control class [WPF], SelectedValuePath properties
- SelectedValue [WPF], SelectedItem properties
ms.assetid: 2fc92ad4-f02c-4f89-bbe9-d4978a7af0db
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6355ed45d7422735d1dac1e1419990e1c5bd120
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a><span data-ttu-id="bd75d-102">Como usar SelectedValue, SelectedValuePath e SelectedItem</span><span class="sxs-lookup"><span data-stu-id="bd75d-102">How to: Use SelectedValue, SelectedValuePath, and SelectedItem</span></span>
<span data-ttu-id="bd75d-103">Este exemplo mostra como usar o <xref:System.Windows.Controls.TreeView.SelectedValue%2A> e <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriedades para especificar um valor para o <xref:System.Windows.Controls.TreeView.SelectedItem%2A> de um <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="bd75d-103">This example shows how to use the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> and <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> properties to specify a value for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> of a <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd75d-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bd75d-104">Example</span></span>  
 <span data-ttu-id="bd75d-105">O <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriedade fornece uma maneira de especificar um <xref:System.Windows.Controls.TreeView.SelectedValue%2A> para o <xref:System.Windows.Controls.TreeView.SelectedItem%2A> em um <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="bd75d-105">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property provides a way to specify a <xref:System.Windows.Controls.TreeView.SelectedValue%2A> for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> in a <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="bd75d-106">O <xref:System.Windows.Controls.TreeView.SelectedItem%2A> representa um objeto de <xref:System.Windows.Controls.ItemsControl.Items%2A> coleção e o <xref:System.Windows.Controls.TreeView> exibe o valor de uma única propriedade do item selecionado.</span><span class="sxs-lookup"><span data-stu-id="bd75d-106">The <xref:System.Windows.Controls.TreeView.SelectedItem%2A> represents an object in the <xref:System.Windows.Controls.ItemsControl.Items%2A> collection and the <xref:System.Windows.Controls.TreeView> displays the value of a single property of the selected item.</span></span> <span data-ttu-id="bd75d-107">O <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriedade especifica o caminho para a propriedade que é usado para determinar o valor de <xref:System.Windows.Controls.TreeView.SelectedValue%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="bd75d-107">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property specifies the path to the property that is used to determine the value of the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property.</span></span> <span data-ttu-id="bd75d-108">Os exemplos neste tópico ilustram esse conceito.</span><span class="sxs-lookup"><span data-stu-id="bd75d-108">The examples in this topic illustrate this concept.</span></span>  
  
 <span data-ttu-id="bd75d-109">A exemplo a seguir mostra um <xref:System.Windows.Data.XmlDataProvider> que contém informações de funcionários.</span><span class="sxs-lookup"><span data-stu-id="bd75d-109">The following example shows an <xref:System.Windows.Data.XmlDataProvider> that contains employee information.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 <span data-ttu-id="bd75d-110">O exemplo a seguir define uma <xref:System.Windows.HierarchicalDataTemplate> que exibe o `EmployeeName` e `EmployeeWorkDay` do `Employee`.</span><span class="sxs-lookup"><span data-stu-id="bd75d-110">The following example defines a <xref:System.Windows.HierarchicalDataTemplate> that displays the `EmployeeName` and `EmployeeWorkDay` of the `Employee`.</span></span> <span data-ttu-id="bd75d-111">Observe que o <xref:System.Windows.HierarchicalDataTemplate> não especificar o `EmployeeNumber` como parte do modelo.</span><span class="sxs-lookup"><span data-stu-id="bd75d-111">Note that the <xref:System.Windows.HierarchicalDataTemplate> does not specify the `EmployeeNumber` as part of the template.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 <span data-ttu-id="bd75d-112">A exemplo a seguir mostra um <xref:System.Windows.Controls.TreeView> que usa o previamente definido <xref:System.Windows.HierarchicalDataTemplate> e que define o <xref:System.Windows.Controls.TreeView.SelectedValue%2A> propriedade para o `EmployeeNumber`.</span><span class="sxs-lookup"><span data-stu-id="bd75d-112">The following example shows a <xref:System.Windows.Controls.TreeView> that uses the previously defined <xref:System.Windows.HierarchicalDataTemplate> and that sets the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property to the `EmployeeNumber`.</span></span> <span data-ttu-id="bd75d-113">Quando você seleciona um `EmployeeName` no <xref:System.Windows.Controls.TreeView>, o <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriedade retorna o `EmployeeInfo` item de dados que corresponde ao selecionado `EmployeeName`.</span><span class="sxs-lookup"><span data-stu-id="bd75d-113">When you select an `EmployeeName` in the <xref:System.Windows.Controls.TreeView>, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property returns the `EmployeeInfo` data item that corresponds to the selected `EmployeeName`.</span></span> <span data-ttu-id="bd75d-114">No entanto, porque o <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> deste <xref:System.Windows.Controls.TreeView> é definido como `EmployeeNumber`, o <xref:System.Windows.Controls.TreeView.SelectedValue%2A> é definido como o `EmployeeNumber`.</span><span class="sxs-lookup"><span data-stu-id="bd75d-114">However, because the <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> of this <xref:System.Windows.Controls.TreeView> is set to `EmployeeNumber`, the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> is set to the `EmployeeNumber`.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a><span data-ttu-id="bd75d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd75d-115">See Also</span></span>  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [<span data-ttu-id="bd75d-116">Visão geral de TreeView</span><span class="sxs-lookup"><span data-stu-id="bd75d-116">TreeView Overview</span></span>](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [<span data-ttu-id="bd75d-117">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="bd75d-117">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
