---
title: Como criar uma associação em código
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: 2d13650cb3e9a4e97a6642992b7211f323b9ea96
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502252"
---
# <a name="how-to-create-a-binding-in-code"></a>Como criar uma associação em código
Este exemplo mostra como criar e definir um <xref:System.Windows.Data.Binding> no código.  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.FrameworkElement> classe e o <xref:System.Windows.FrameworkContentElement> expõem um `SetBinding` método. Se você estiver associando um elemento que herda de qualquer uma dessas classes, você pode chamar o <xref:System.Windows.FrameworkElement.SetBinding%2A> método diretamente.  
  
 O exemplo a seguir cria uma classe chamada `MyData`, que contém uma propriedade chamada `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 O exemplo a seguir mostra como criar um objeto de associação para definir a origem da associação.  O exemplo usa <xref:System.Windows.FrameworkElement.SetBinding%2A> para associar o <xref:System.Windows.Controls.TextBlock.Text%2A> propriedade de `myText`, que é uma <xref:System.Windows.Controls.TextBlock> controlam a, `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Para ver o exemplo de código completo, confira [Exemplo de associação somente de código](https://msdn.microsoft.com/library/764aaf0b-2216-4941-9548-9c98da18d1a6).  
  
 Em vez de chamar <xref:System.Windows.FrameworkElement.SetBinding%2A>, você pode usar o <xref:System.Windows.Data.BindingOperations.SetBinding%2A> método estático do <xref:System.Windows.Data.BindingOperations> classe. O exemplo a seguir, chamadas <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> em vez de <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> para associar `myText` para `myDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
