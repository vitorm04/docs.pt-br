---
title: Como associar as propriedades de dois controles
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 66c759c28747de5b0288c906f5d51e4253fb7d52
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459173"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>Como associar as propriedades de dois controles
Este exemplo mostra como associar a propriedade de um controle instanciado a outro usando a propriedade <xref:System.Windows.Data.Binding.ElementName%2A>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como associar a propriedade <xref:System.Windows.Controls.Panel.Background%2A> de um <xref:System.Windows.Controls.Canvas> ao <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> Propriedade de uma <xref:System.Windows.Controls.ComboBox>:  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 Quando este exemplo é renderizado, ele é semelhante ao seguinte:  
  
![Captura de tela mostrando uma caixa de combinação com o valor verde selecionado e um quadrado verde.](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> A propriedade de destino de associação (neste exemplo, a propriedade <xref:System.Windows.Controls.Panel.Background%2A>) deve ser uma propriedade de dependência. Para obter mais informações, consulte [Visão geral de vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md).  
  
## <a name="see-also"></a>Consulte também

- [Especificar a origem da associação](how-to-specify-the-binding-source.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)
