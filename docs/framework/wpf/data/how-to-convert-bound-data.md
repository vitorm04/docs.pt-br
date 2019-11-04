---
title: Como converter dados associados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: f9ad390626092d481bf47f017f643a29302c1b29
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458864"
---
# <a name="how-to-convert-bound-data"></a>Como converter dados associados
Este exemplo mostra como aplicar a conversão a dados que são usados em associações.  
  
 Para converter dados durante a associação, você deve criar uma classe que implemente a interface <xref:System.Windows.Data.IValueConverter>, que inclui os métodos <xref:System.Windows.Data.IValueConverter.Convert%2A> e <xref:System.Windows.Data.IValueConverter.ConvertBack%2A>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra a implementação de um conversor de data que converte o valor passado de modo que mostre apenas o ano, mês e dia. Ao implementar a interface <xref:System.Windows.Data.IValueConverter>, é uma boa prática decorar a implementação com um atributo <xref:System.Windows.Data.ValueConversionAttribute> para indicar às ferramentas de desenvolvimento os tipos de dados envolvidos na conversão, como no exemplo a seguir:  
  
 [!code-csharp[DataBindingLab#18](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 Depois de criar um conversor, você pode adicioná-lo como um recurso em seu arquivo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. No exemplo a seguir, o *src* mapeia para o namespace no qual *DateConverter* está definido.  
  
 [!code-xaml[DataBindingLab#15](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 Finalmente, você pode usar o conversor em sua associação usando a sintaxe a seguir. No exemplo a seguir, o conteúdo de texto do <xref:System.Windows.Controls.TextBlock> está associado a *StartDate*, que é uma propriedade de uma fonte de dados externa.  
  
 [!code-xaml[DataBindingLab#17](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 Os recursos de estilo referenciados no exemplo acima são definidos em uma seção de recursos não mostrada neste tópico.  
  
## <a name="see-also"></a>Consulte também

- [Implementar a validação de associação](how-to-implement-binding-validation.md)
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)
