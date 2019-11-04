---
title: Como limpar associações
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
ms.openlocfilehash: 66f7eb0209d23660b9c7351ca793f509b2f4bb8d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458870"
---
# <a name="how-to-clear-bindings"></a>Como limpar associações
Este exemplo mostra como limpar associações de um objeto.  
  
## <a name="example"></a>Exemplo  
 Para limpar uma associação de uma propriedade individual em um objeto, chame <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> conforme mostrado no exemplo a seguir. O exemplo a seguir remove a associação da <xref:System.Windows.Controls.TextBlock.TextProperty> de *MyText*, um objeto <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 Limpar a associação remove a associação de forma que o valor da propriedade de dependência seja alterado para o que fosse feito sem a associação. Esse valor pode ser um valor padrão, um valor herdado ou um valor de uma associação de modelo de dados.  
  
 Para limpar associações de todas as propriedades possíveis em um objeto, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Data.BindingOperations>
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)
