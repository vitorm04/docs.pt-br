---
title: Como criar uma grade complexa
description: Um exemplo de como usar um controle de grade para criar um layout que pareça um calendário mensal.
ms.date: 03/30/2017
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
ms.openlocfilehash: dd17dfeea85e2b404f7a284f93faceec63145b1f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910983"
---
# <a name="how-to-create-a-complex-grid"></a>Como criar uma grade complexa

Este exemplo mostra como usar um <xref:System.Windows.Controls.Grid> controle para criar um layout que pareça um calendário mensal.

## <a name="example"></a>Exemplo

O exemplo a seguir define oito linhas e oito colunas usando o <xref:System.Windows.Controls.RowDefinition> e <xref:System.Windows.Controls.ColumnDefinition> classes. Ele usa o <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> e <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> anexado propriedades, junto com <xref:System.Windows.Shapes.Rectangle> elementos, que preenchem as telas de fundo das várias colunas e linhas. Esse design é possível porque mais de um elemento pode existir em cada célula em uma <xref:System.Windows.Controls.Grid>, uma diferença de princípio entre <xref:System.Windows.Controls.Grid> e <xref:System.Windows.Documents.Table>.

O exemplo usa gradientes verticais para <xref:System.Windows.Shapes.Shape.Fill%2A> as colunas e linhas para melhorar a legibilidade do calendário e a apresentação visual. Com o estilo <xref:System.Windows.Controls.TextBlock> elementos representam as datas e os dias da semana. <xref:System.Windows.Controls.TextBlock> elementos são posicionados absolutamente em suas células usando a <xref:System.Windows.FrameworkElement.Margin%2A> propriedade e propriedades de alinhamento que são definidas no estilo para o aplicativo.

[!code-xaml[GridComplex#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]

A imagem a seguir mostra o controle resultante, um calendário personalizável:

![Captura de tela do controle resultante](././media/how-to-create-a-complex-grid/wpf-manual-calendar.png)

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.Grid?displayProperty=nameWithType>
- <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>
- [Visão geral da pintura com cores sólidas e gradientes](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Visão geral de painéis](panels-overview.md)
- [Visão geral da tabela](../advanced/table-overview.md)