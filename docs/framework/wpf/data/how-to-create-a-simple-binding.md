---
title: 'Como: Criar uma associação simples'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 3e38fa5fd1c7d0a635efd93de6ebe551f1eb1b82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594831"
---
# <a name="how-to-create-a-simple-binding"></a>Como: Criar uma associação simples
Este exemplo mostra como criar um simples <xref:System.Windows.Data.Binding>.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, você tem um `Person` objeto com uma propriedade de cadeia de caracteres denominada `PersonName`. O objeto `Person` é definido no namespace chamado `SDKSample`.  
  
 A linha realçada que contém o `<src>` elemento no exemplo a seguir cria uma instância de `Person` do objeto com um `PersonName` valor da propriedade `Joe`. Isso é feito na `Resources` seção e atribuído um `x:Key`.  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 A linha realçada que contém o `<TextBlock>` , em seguida, associa um elemento de <xref:System.Windows.Controls.TextBlock> o controle para o `PersonName` propriedade. Como resultado, o <xref:System.Windows.Controls.TextBlock> aparece com o valor "Joe".  
  
## <a name="see-also"></a>Consulte também
- [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
