---
title: Como criar uma associação simples
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 8910dd3ec6c9f72f9d8fb64cd33912f0d4318e5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555004"
---
# <a name="how-to-create-a-simple-binding"></a>Como criar uma associação simples
Este exemplo mostra como criar um simples <xref:System.Windows.Data.Binding>.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, você tem uma `Person` objeto com uma propriedade de cadeia de caracteres denominada `PersonName`. O objeto `Person` é definido no namespace chamado `SDKSample`.  
  
 A linha realçada que contém o `<src>` elemento no exemplo a seguir cria uma instância de `Person` do objeto com um `PersonName` valor da propriedade `Joe`. Isso é feito o `Resources` seção e atribuído um `x:Key`.  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 A linha realçada que contém o `<TextBlock>` elemento, em seguida, associa a <xref:System.Windows.Controls.TextBlock> o controle para o `PersonName` propriedade. Como resultado, o <xref:System.Windows.Controls.TextBlock> é exibida com o valor "Joe".  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
