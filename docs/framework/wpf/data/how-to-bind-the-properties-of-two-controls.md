---
title: Como associar as propriedades de dois controles
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: d38c473b8c4d3f71f1e3decd4f66be248665c57b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974810"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="b704c-102">Como associar as propriedades de dois controles</span><span class="sxs-lookup"><span data-stu-id="b704c-102">How to: Bind the Properties of Two Controls</span></span>

<span data-ttu-id="b704c-103">Este exemplo mostra como associar a propriedade de um controle instanciado a outro usando a propriedade <xref:System.Windows.Data.Binding.ElementName%2A>.</span><span class="sxs-lookup"><span data-stu-id="b704c-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>

## <a name="example"></a><span data-ttu-id="b704c-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b704c-104">Example</span></span>

<span data-ttu-id="b704c-105">O exemplo a seguir mostra como associar a propriedade <xref:System.Windows.Controls.Panel.Background%2A> de um <xref:System.Windows.Controls.Canvas> à propriedade [SelectedItem. Content](xref:System.Windows.Controls.ContentControl.Content%2A) de um <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="b704c-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the [SelectedItem.Content](xref:System.Windows.Controls.ContentControl.Content%2A) property of a <xref:System.Windows.Controls.ComboBox>:</span></span>

[!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]

<span data-ttu-id="b704c-106">Quando este exemplo é renderizado, ele é semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="b704c-106">When this example is rendered it looks like the following:</span></span>

![Captura de tela mostrando uma caixa de combinação com o valor verde selecionado e um quadrado verde.](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> <span data-ttu-id="b704c-108">A propriedade de destino de associação (neste exemplo, a propriedade <xref:System.Windows.Controls.Panel.Background%2A>) deve ser uma propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="b704c-108">The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="b704c-109">Para obter mais informações, consulte [Visão geral de vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b704c-109">For more information, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b704c-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b704c-110">See also</span></span>

- [<span data-ttu-id="b704c-111">Especificar a origem da associação</span><span class="sxs-lookup"><span data-stu-id="b704c-111">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="b704c-112">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="b704c-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
