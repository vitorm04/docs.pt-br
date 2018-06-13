---
title: Como usar SelectedValue, SelectedValuePath e SelectedItem
ms.date: 03/30/2017
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
ms.openlocfilehash: 93720c0e1ac96a55fafa36479968cc3492cb0d84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554781"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a>Como usar SelectedValue, SelectedValuePath e SelectedItem
Este exemplo mostra como usar o <xref:System.Windows.Controls.TreeView.SelectedValue%2A> e <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriedades para especificar um valor para o <xref:System.Windows.Controls.TreeView.SelectedItem%2A> de um <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriedade fornece uma maneira de especificar um <xref:System.Windows.Controls.TreeView.SelectedValue%2A> para o <xref:System.Windows.Controls.TreeView.SelectedItem%2A> em um <xref:System.Windows.Controls.TreeView>. O <xref:System.Windows.Controls.TreeView.SelectedItem%2A> representa um objeto de <xref:System.Windows.Controls.ItemsControl.Items%2A> coleção e o <xref:System.Windows.Controls.TreeView> exibe o valor de uma única propriedade do item selecionado. O <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriedade especifica o caminho para a propriedade que é usado para determinar o valor de <xref:System.Windows.Controls.TreeView.SelectedValue%2A> propriedade. Os exemplos neste tópico ilustram esse conceito.  
  
 A exemplo a seguir mostra um <xref:System.Windows.Data.XmlDataProvider> que contém informações de funcionários.  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 O exemplo a seguir define uma <xref:System.Windows.HierarchicalDataTemplate> que exibe o `EmployeeName` e `EmployeeWorkDay` do `Employee`. Observe que o <xref:System.Windows.HierarchicalDataTemplate> não especificar o `EmployeeNumber` como parte do modelo.  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 A exemplo a seguir mostra um <xref:System.Windows.Controls.TreeView> que usa o previamente definido <xref:System.Windows.HierarchicalDataTemplate> e que define o <xref:System.Windows.Controls.TreeView.SelectedValue%2A> propriedade para o `EmployeeNumber`. Quando você seleciona um `EmployeeName` no <xref:System.Windows.Controls.TreeView>, o <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriedade retorna o `EmployeeInfo` item de dados que corresponde ao selecionado `EmployeeName`. No entanto, porque o <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> deste <xref:System.Windows.Controls.TreeView> é definido como `EmployeeNumber`, o <xref:System.Windows.Controls.TreeView.SelectedValue%2A> é definido como o `EmployeeNumber`.  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [Visão geral de TreeView](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
