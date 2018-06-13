---
title: Como associar as propriedades de dois controles
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 02e71bfcc41fc3d256ea95381ed27d36b289b8f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555575"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>Como associar as propriedades de dois controles
Este exemplo mostra como associar a propriedade de um controle instanciado a de outro usando o <xref:System.Windows.Data.Binding.ElementName%2A> propriedade.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como associar o <xref:System.Windows.Controls.Panel.Background%2A> propriedade de um <xref:System.Windows.Controls.Canvas> para o <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> propriedade de um <xref:System.Windows.Controls.ComboBox>:  
  
 [!code-xaml[BindDptoDp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 Quando este exemplo é processado, ele é semelhante ao seguinte:  
  
 ![Uma tela com um plano de fundo verde](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")  
  
 **Observação** a propriedade de destino de vinculação (neste exemplo, o <xref:System.Windows.Controls.Panel.Background%2A> propriedade) deve ser uma propriedade de dependência. Para obter mais informações, consulte [Visão geral de vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 [Especificar a origem da associação](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
