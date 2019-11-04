---
title: Como criar uma associação simples
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: faef59ed426059eb2d488d0584d3325c8d46d415
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453503"
---
# <a name="how-to-create-a-simple-binding"></a>Como criar uma associação simples
Este exemplo mostra como criar um <xref:System.Windows.Data.Binding>simples.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, você tem um objeto `Person` com uma propriedade de cadeia de caracteres chamada `PersonName`. O objeto `Person` é definido no namespace chamado `SDKSample`.  
  
 A linha realçada que contém o elemento `<src>` no exemplo a seguir instancia o objeto `Person` com um valor de propriedade `PersonName` de `Joe`. Isso é feito na seção `Resources` e recebe um `x:Key`.  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 A linha realçada que contém o elemento `<TextBlock>` associa o controle <xref:System.Windows.Controls.TextBlock> à propriedade `PersonName`. Como resultado, o <xref:System.Windows.Controls.TextBlock> aparece com o valor "Joe".  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)
