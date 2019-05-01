---
title: 'Como: Associar as propriedades de dois controles'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 332e8e0dfa30ff7aff27c95652f07446baf6511a
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63809532"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>Como: Associar as propriedades de dois controles
Este exemplo mostra como associar a propriedade de um controle instanciado a de outro usando o <xref:System.Windows.Data.Binding.ElementName%2A> propriedade.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como associar o <xref:System.Windows.Controls.Panel.Background%2A> propriedade de um <xref:System.Windows.Controls.Canvas> para o <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> propriedade de um <xref:System.Windows.Controls.ComboBox>:  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 Quando este exemplo é renderizado, ele é semelhante ao seguinte:  
  
![Captura de tela mostrando uma caixa de combinação, caixa com o valor de verde e um quadrado verde.](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> A propriedade de destino de associação (neste exemplo, o <xref:System.Windows.Controls.Panel.Background%2A> propriedade) deve ser uma propriedade de dependência. Para obter mais informações, consulte [Visão geral de vinculação de dados](data-binding-overview.md).  
  
## <a name="see-also"></a>Consulte também

- [Especificar a origem da associação](how-to-specify-the-binding-source.md)
- [Tópicos de instruções](data-binding-how-to-topics.md)
