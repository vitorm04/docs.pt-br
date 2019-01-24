---
title: 'Como: Limpar associações'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
ms.openlocfilehash: bd0f42b868c316cb9a6344134d4aaf01930519ac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508425"
---
# <a name="how-to-clear-bindings"></a>Como: Limpar associações
Este exemplo mostra como limpar as associações de um objeto.  
  
## <a name="example"></a>Exemplo  
 Para limpar uma associação de uma propriedade individual em um objeto, chame <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> conforme mostrado no exemplo a seguir. O exemplo a seguir remove a associação a <xref:System.Windows.Controls.TextBlock.TextProperty> dos *mytext*, um <xref:System.Windows.Controls.TextBlock> objeto.  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 Limpar a associação remove a associação para que o valor da propriedade de dependência é alterado para tudo o que teria sido sem a associação. Esse valor pode ser um valor padrão, um valor herdado ou um valor de uma associação de modelo de dados.  
  
 Para limpar as associações de todas as propriedades possíveis em um objeto, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Data.BindingOperations>
- [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
