---
title: Como criar uma grade complexa
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9dfb913407622f3cbd9a067a94cc6400b501e2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-complex-grid"></a><span data-ttu-id="10fff-102">Como criar uma grade complexa</span><span class="sxs-lookup"><span data-stu-id="10fff-102">How to: Create a Complex Grid</span></span>
<span data-ttu-id="10fff-103">Este exemplo mostra como usar um <xref:System.Windows.Controls.Grid> para criar um layout que pareça um calendário mensal.</span><span class="sxs-lookup"><span data-stu-id="10fff-103">This example shows how to use a <xref:System.Windows.Controls.Grid> to create layout that looks like a monthly calendar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10fff-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="10fff-104">Example</span></span>  
 <span data-ttu-id="10fff-105">O exemplo a seguir define oito linhas e oito colunas usando o <xref:System.Windows.Controls.RowDefinition> e <xref:System.Windows.Controls.ColumnDefinition> classes.</span><span class="sxs-lookup"><span data-stu-id="10fff-105">The following example defines eight rows and eight columns by using the <xref:System.Windows.Controls.RowDefinition> and <xref:System.Windows.Controls.ColumnDefinition> classes.</span></span> <span data-ttu-id="10fff-106">Ele usa o <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> e <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> anexado propriedades, junto com <xref:System.Windows.Shapes.Rectangle> elementos, que preenchem os planos de fundo das várias colunas e linhas.</span><span class="sxs-lookup"><span data-stu-id="10fff-106">It uses the <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> and <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> attached properties, together with <xref:System.Windows.Shapes.Rectangle> elements, which fill the backgrounds of various columns and rows.</span></span> <span data-ttu-id="10fff-107">Esse design é possível porque mais de um elemento pode existir em cada célula em uma <xref:System.Windows.Controls.Grid>, uma diferença de princípio entre <xref:System.Windows.Controls.Grid> e <xref:System.Windows.Documents.Table>.</span><span class="sxs-lookup"><span data-stu-id="10fff-107">This design is possible because more than one element can exist in each cell in a <xref:System.Windows.Controls.Grid>, a principle difference between <xref:System.Windows.Controls.Grid> and <xref:System.Windows.Documents.Table>.</span></span>  
  
 <span data-ttu-id="10fff-108">O exemplo usa gradientes verticais para <xref:System.Windows.Shapes.Shape.Fill%2A> as colunas e linhas para melhorar a legibilidade do calendário e a apresentação visual.</span><span class="sxs-lookup"><span data-stu-id="10fff-108">The example uses vertical gradients to <xref:System.Windows.Shapes.Shape.Fill%2A> the columns and rows in order to improve the visual presentation and readability of the calendar.</span></span> <span data-ttu-id="10fff-109">O estilo <xref:System.Windows.Controls.TextBlock> elementos representam as datas e os dias da semana.</span><span class="sxs-lookup"><span data-stu-id="10fff-109">Styled <xref:System.Windows.Controls.TextBlock> elements represent the dates and days of the week.</span></span> <span data-ttu-id="10fff-110"><xref:System.Windows.Controls.TextBlock>elementos são posicionados absolutamente em suas células usando o <xref:System.Windows.FrameworkElement.Margin%2A> propriedade e propriedades de alinhamento que são definidas no estilo para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="10fff-110"><xref:System.Windows.Controls.TextBlock> elements are absolutely positioned within their cells by using the <xref:System.Windows.FrameworkElement.Margin%2A> property and alignment properties that are defined within the style for the application.</span></span>  
  
 [!code-xaml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="10fff-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10fff-111">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Documents.TableCell>  
 [<span data-ttu-id="10fff-112">Visão geral da pintura com cores sólidas e gradientes</span><span class="sxs-lookup"><span data-stu-id="10fff-112">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="10fff-113">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="10fff-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="10fff-114">Visão geral da tabela</span><span class="sxs-lookup"><span data-stu-id="10fff-114">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
