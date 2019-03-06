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
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355006"
---
# <a name="how-to-create-a-complex-grid"></a><span data-ttu-id="429ef-103">Como criar uma grade complexa</span><span class="sxs-lookup"><span data-stu-id="429ef-103">How to create a complex Grid</span></span>

<span data-ttu-id="429ef-104">Este exemplo mostra como usar um <xref:System.Windows.Controls.Grid> controle para criar um layout que pareça um calendário mensal.</span><span class="sxs-lookup"><span data-stu-id="429ef-104">This example shows how to use a <xref:System.Windows.Controls.Grid> control to create a layout that looks like a monthly calendar.</span></span>

## <a name="example"></a><span data-ttu-id="429ef-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="429ef-105">Example</span></span>

<span data-ttu-id="429ef-106">O exemplo a seguir define oito linhas e oito colunas usando o <xref:System.Windows.Controls.RowDefinition> e <xref:System.Windows.Controls.ColumnDefinition> classes.</span><span class="sxs-lookup"><span data-stu-id="429ef-106">The following example defines eight rows and eight columns by using the <xref:System.Windows.Controls.RowDefinition> and <xref:System.Windows.Controls.ColumnDefinition> classes.</span></span> <span data-ttu-id="429ef-107">Ele usa o <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> e <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> anexado propriedades, junto com <xref:System.Windows.Shapes.Rectangle> elementos, que preenchem as telas de fundo das várias colunas e linhas.</span><span class="sxs-lookup"><span data-stu-id="429ef-107">It uses the <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> and <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> attached properties, together with <xref:System.Windows.Shapes.Rectangle> elements, which fill the backgrounds of various columns and rows.</span></span> <span data-ttu-id="429ef-108">Esse design é possível porque mais de um elemento pode existir em cada célula em uma <xref:System.Windows.Controls.Grid>, uma diferença de princípio entre <xref:System.Windows.Controls.Grid> e <xref:System.Windows.Documents.Table>.</span><span class="sxs-lookup"><span data-stu-id="429ef-108">This design is possible because more than one element can exist in each cell in a <xref:System.Windows.Controls.Grid>, a principle difference between <xref:System.Windows.Controls.Grid> and <xref:System.Windows.Documents.Table>.</span></span>

<span data-ttu-id="429ef-109">O exemplo usa gradientes verticais para <xref:System.Windows.Shapes.Shape.Fill%2A> as colunas e linhas para melhorar a legibilidade do calendário e a apresentação visual.</span><span class="sxs-lookup"><span data-stu-id="429ef-109">The example uses vertical gradients to <xref:System.Windows.Shapes.Shape.Fill%2A> the columns and rows to improve the visual presentation and readability of the calendar.</span></span> <span data-ttu-id="429ef-110">Com o estilo <xref:System.Windows.Controls.TextBlock> elementos representam as datas e os dias da semana.</span><span class="sxs-lookup"><span data-stu-id="429ef-110">Styled <xref:System.Windows.Controls.TextBlock> elements represent the dates and days of the week.</span></span> <span data-ttu-id="429ef-111"><xref:System.Windows.Controls.TextBlock> elementos são posicionados absolutamente em suas células usando a <xref:System.Windows.FrameworkElement.Margin%2A> propriedade e propriedades de alinhamento que são definidas no estilo para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="429ef-111"><xref:System.Windows.Controls.TextBlock> elements are absolutely positioned within their cells by using the <xref:System.Windows.FrameworkElement.Margin%2A> property and alignment properties that are defined within the style for the application.</span></span>

[!code-xaml[GridComplex#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]

<span data-ttu-id="429ef-112">A imagem a seguir mostra o controle resultante, um calendário personalizável:</span><span class="sxs-lookup"><span data-stu-id="429ef-112">The following image shows the resulting control, a customizable calendar:</span></span>

![Captura de tela do controle resultante](././media/how-to-create-a-complex-grid/wpf-manual-calendar.png)

## <a name="see-also"></a><span data-ttu-id="429ef-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="429ef-114">See also</span></span>

- <xref:System.Windows.Controls.Grid?displayProperty=nameWithType>
- <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>
- [<span data-ttu-id="429ef-115">Visão geral da pintura com cores sólidas e gradientes</span><span class="sxs-lookup"><span data-stu-id="429ef-115">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="429ef-116">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="429ef-116">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="429ef-117">Visão geral da tabela</span><span class="sxs-lookup"><span data-stu-id="429ef-117">Table Overview</span></span>](../advanced/table-overview.md)