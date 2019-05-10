---
title: 'Como: Associar as propriedades de dois controles'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 332e8e0dfa30ff7aff27c95652f07446baf6511a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754051"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="660f7-102">Como: Associar as propriedades de dois controles</span><span class="sxs-lookup"><span data-stu-id="660f7-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="660f7-103">Este exemplo mostra como associar a propriedade de um controle instanciado a de outro usando o <xref:System.Windows.Data.Binding.ElementName%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="660f7-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="660f7-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="660f7-104">Example</span></span>  
 <span data-ttu-id="660f7-105">O exemplo a seguir mostra como associar o <xref:System.Windows.Controls.Panel.Background%2A> propriedade de um <xref:System.Windows.Controls.Canvas> para o <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span><span class="sxs-lookup"><span data-stu-id="660f7-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span></span> <span data-ttu-id="660f7-106">propriedade de um <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="660f7-106">property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="660f7-107">Quando este exemplo é renderizado, ele é semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="660f7-107">When this example is rendered it looks like the following:</span></span>  
  
![Captura de tela mostrando uma caixa de combinação, caixa com o valor de verde e um quadrado verde.](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> <span data-ttu-id="660f7-109">A propriedade de destino de associação (neste exemplo, o <xref:System.Windows.Controls.Panel.Background%2A> propriedade) deve ser uma propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="660f7-109">The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="660f7-110">Para obter mais informações, consulte [Visão geral de vinculação de dados](data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="660f7-110">For more information, see [Data Binding Overview](data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="660f7-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="660f7-111">See also</span></span>

- [<span data-ttu-id="660f7-112">Especificar a origem da associação</span><span class="sxs-lookup"><span data-stu-id="660f7-112">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="660f7-113">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="660f7-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
