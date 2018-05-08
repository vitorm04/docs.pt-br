---
title: Como criar uma grade complexa
ms.date: 03/30/2017
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
ms.openlocfilehash: 49bf9781d56b93fd4529f3c9b62deb171e69155f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-complex-grid"></a>Como criar uma grade complexa
Este exemplo mostra como usar um <xref:System.Windows.Controls.Grid> para criar um layout que pareça um calendário mensal.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define oito linhas e oito colunas usando o <xref:System.Windows.Controls.RowDefinition> e <xref:System.Windows.Controls.ColumnDefinition> classes. Ele usa o <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> e <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> anexado propriedades, junto com <xref:System.Windows.Shapes.Rectangle> elementos, que preenchem os planos de fundo das várias colunas e linhas. Esse design é possível porque mais de um elemento pode existir em cada célula em uma <xref:System.Windows.Controls.Grid>, uma diferença de princípio entre <xref:System.Windows.Controls.Grid> e <xref:System.Windows.Documents.Table>.  
  
 O exemplo usa gradientes verticais para <xref:System.Windows.Shapes.Shape.Fill%2A> as colunas e linhas para melhorar a legibilidade do calendário e a apresentação visual. O estilo <xref:System.Windows.Controls.TextBlock> elementos representam as datas e os dias da semana. <xref:System.Windows.Controls.TextBlock> elementos são posicionados absolutamente em suas células usando o <xref:System.Windows.FrameworkElement.Margin%2A> propriedade e propriedades de alinhamento que são definidas no estilo para o aplicativo.  
  
 [!code-xaml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Documents.TableCell>  
 [Visão geral da pintura com cores sólidas e gradientes](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Visão geral da tabela](../../../../docs/framework/wpf/advanced/table-overview.md)
