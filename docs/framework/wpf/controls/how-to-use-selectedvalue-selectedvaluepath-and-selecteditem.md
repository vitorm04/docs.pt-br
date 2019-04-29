---
title: 'Como: Usar SelectedValue, SelectedValuePath e SelectedItem'
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
ms.openlocfilehash: d9f7a8f04f53b7d38a49dfef2c947dfa1c2d263d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699130"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a>Como: Usar SelectedValue, SelectedValuePath e SelectedItem
Este exemplo mostra como usar o <xref:System.Windows.Controls.TreeView.SelectedValue%2A> e <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriedades para especificar um valor para o <xref:System.Windows.Controls.TreeView.SelectedItem%2A> de um <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriedade fornece uma maneira de especificar um <xref:System.Windows.Controls.TreeView.SelectedValue%2A> para o <xref:System.Windows.Controls.TreeView.SelectedItem%2A> em um <xref:System.Windows.Controls.TreeView>. O <xref:System.Windows.Controls.TreeView.SelectedItem%2A> representa um objeto na <xref:System.Windows.Controls.ItemsControl.Items%2A> coleção e o <xref:System.Windows.Controls.TreeView> exibe o valor de uma única propriedade do item selecionado. O <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriedade especifica o caminho para a propriedade que é usado para determinar o valor da <xref:System.Windows.Controls.TreeView.SelectedValue%2A> propriedade. Os exemplos neste tópico ilustram esse conceito.  
  
 A exemplo a seguir mostra um <xref:System.Windows.Data.XmlDataProvider> que contém informações de funcionários.  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 O exemplo a seguir define uma <xref:System.Windows.HierarchicalDataTemplate> que exibe as `EmployeeName` e `EmployeeWorkDay` da `Employee`. Observe que o <xref:System.Windows.HierarchicalDataTemplate> não especificar o `EmployeeNumber` como parte do modelo.  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 A exemplo a seguir mostra uma <xref:System.Windows.Controls.TreeView> que usa o previamente definido <xref:System.Windows.HierarchicalDataTemplate> e que define o <xref:System.Windows.Controls.TreeView.SelectedValue%2A> propriedade para o `EmployeeNumber`. Quando você seleciona uma `EmployeeName` no <xref:System.Windows.Controls.TreeView>, o <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriedade retorna o `EmployeeInfo` item de dados que corresponde ao selecionado `EmployeeName`. No entanto, porque o <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> isso <xref:System.Windows.Controls.TreeView> é definido como `EmployeeNumber`, o <xref:System.Windows.Controls.TreeView.SelectedValue%2A> é definido como o `EmployeeNumber`.  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [Visão geral de TreeView](treeview-overview.md)
- [Tópicos de instruções](treeview-how-to-topics.md)
