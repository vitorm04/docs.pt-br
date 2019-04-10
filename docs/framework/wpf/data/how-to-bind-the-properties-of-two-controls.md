---
title: 'Como: Associar as propriedades de dois controles'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 0dd7b817b632758cfca8b5c45d88e333510485f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222050"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>Como: Associar as propriedades de dois controles
Este exemplo mostra como associar a propriedade de um controle instanciado a de outro usando o <xref:System.Windows.Data.Binding.ElementName%2A> propriedade.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como associar o <xref:System.Windows.Controls.Panel.Background%2A> propriedade de um <xref:System.Windows.Controls.Canvas> para o <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> propriedade de um <xref:System.Windows.Controls.ComboBox>:  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 Quando este exemplo é renderizado, ele é semelhante ao seguinte:  
  
 ![Uma tela com um plano de fundo verde](./media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")  
  
 **Observação** a propriedade de destino de associação (neste exemplo, o <xref:System.Windows.Controls.Panel.Background%2A> propriedade) deve ser uma propriedade de dependência. Para obter mais informações, consulte [Visão geral de vinculação de dados](data-binding-overview.md).  
  
## <a name="see-also"></a>Consulte também

- [Especificar a origem da associação](how-to-specify-the-binding-source.md)
- [Tópicos explicativos ](data-binding-how-to-topics.md)
