---
title: 'Como: Obter ou definir propriedades de posicionamento da tela'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Canvas control [WPF], setting positioning properties
ms.assetid: 1636b950-2b5a-4507-8a10-c5034cc58b1c
ms.openlocfilehash: 06508e1198736ccb1cbda41641dff4bc634ef82b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59194403"
---
# <a name="how-to-get-or-set-canvas-positioning-properties"></a><span data-ttu-id="ecf29-102">Como: Obter ou definir propriedades de posicionamento da tela</span><span class="sxs-lookup"><span data-stu-id="ecf29-102">How to: Get or Set Canvas Positioning Properties</span></span>
<span data-ttu-id="ecf29-103">Este exemplo mostra como usar os métodos de posicionamento a <xref:System.Windows.Controls.Canvas> elemento para posicionar conteúdo filho.</span><span class="sxs-lookup"><span data-stu-id="ecf29-103">This example shows how to use the positioning methods of the <xref:System.Windows.Controls.Canvas> element to position child content.</span></span> <span data-ttu-id="ecf29-104">Este exemplo usa conteúdo em um <xref:System.Windows.Controls.ListBoxItem> para representar valores de posicionamento e converte os valores em instâncias de <xref:System.Double>, que é um argumento requerido para posicionamento.</span><span class="sxs-lookup"><span data-stu-id="ecf29-104">This example uses content in a <xref:System.Windows.Controls.ListBoxItem> to represent positioning values and converts the values into instances of <xref:System.Double>, which is a required argument for positioning.</span></span> <span data-ttu-id="ecf29-105">Os valores são, em seguida, convertidos de volta em cadeias de caracteres e exibidos como texto em uma <xref:System.Windows.Controls.TextBlock> elemento usando o <xref:System.Windows.Controls.Canvas.GetLeft%2A> método.</span><span class="sxs-lookup"><span data-stu-id="ecf29-105">The values are then converted back into strings and displayed as text in a <xref:System.Windows.Controls.TextBlock> element by using the <xref:System.Windows.Controls.Canvas.GetLeft%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecf29-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ecf29-106">Example</span></span>  
 <span data-ttu-id="ecf29-107">O exemplo a seguir cria uma <xref:System.Windows.Controls.ListBox> elemento que tem onze selecionável <xref:System.Windows.Controls.ListBoxItem> elementos.</span><span class="sxs-lookup"><span data-stu-id="ecf29-107">The following example creates a <xref:System.Windows.Controls.ListBox> element that has eleven selectable <xref:System.Windows.Controls.ListBoxItem> elements.</span></span> <span data-ttu-id="ecf29-108">O <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> gatilhos de evento o `ChangeLeft` método personalizado, que o bloco de código subsequente define.</span><span class="sxs-lookup"><span data-stu-id="ecf29-108">The <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event triggers the `ChangeLeft` custom method, which the subsequent code block defines.</span></span>  
  
 <span data-ttu-id="ecf29-109">Cada <xref:System.Windows.Controls.ListBoxItem> representa uma <xref:System.Double> valor, que é um dos argumentos que o <xref:System.Windows.Controls.Canvas.SetLeft%2A> método <xref:System.Windows.Controls.Canvas> aceita.</span><span class="sxs-lookup"><span data-stu-id="ecf29-109">Each <xref:System.Windows.Controls.ListBoxItem> represents a <xref:System.Double> value, which is one of the arguments that the <xref:System.Windows.Controls.Canvas.SetLeft%2A> method of <xref:System.Windows.Controls.Canvas> accepts.</span></span> <span data-ttu-id="ecf29-110">Para usar um <xref:System.Windows.Controls.ListBoxItem> para representar uma instância do <xref:System.Double>, você deve primeiro converter o <xref:System.Windows.Controls.ListBoxItem> para o tipo de dados correto.</span><span class="sxs-lookup"><span data-stu-id="ecf29-110">In order to use a <xref:System.Windows.Controls.ListBoxItem> to represent an instance of <xref:System.Double>, you must first convert the <xref:System.Windows.Controls.ListBoxItem> to the correct data type.</span></span>  
  
 [!code-xaml[CanvasPositioningProperties#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="ecf29-111">Quando um usuário altera a <xref:System.Windows.Controls.ListBox> seleção, ele invoca o `ChangeLeft` método personalizado.</span><span class="sxs-lookup"><span data-stu-id="ecf29-111">When a user changes the <xref:System.Windows.Controls.ListBox> selection, it invokes the `ChangeLeft` custom method.</span></span> <span data-ttu-id="ecf29-112">Esse método passa o <xref:System.Windows.Controls.ListBoxItem> para um <xref:System.Windows.LengthConverter> objeto, que converte o <xref:System.Windows.Controls.ContentControl.Content%2A> de uma <xref:System.Windows.Controls.ListBoxItem> a uma instância do <xref:System.Double> (Observe que esse valor já foi convertido em um <xref:System.String> usando o <xref:System.Windows.Controls.Control.ToString%2A> método).</span><span class="sxs-lookup"><span data-stu-id="ecf29-112">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.LengthConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Double> (notice that this value has already been converted to a <xref:System.String> by using the <xref:System.Windows.Controls.Control.ToString%2A> method).</span></span> <span data-ttu-id="ecf29-113">Esse valor é passado, em seguida, volta para o <xref:System.Windows.Controls.Canvas.SetLeft%2A> e <xref:System.Windows.Controls.Canvas.GetLeft%2A> métodos da <xref:System.Windows.Controls.Canvas> para alterar a posição do `text1` objeto.</span><span class="sxs-lookup"><span data-stu-id="ecf29-113">This value is then passed back to the <xref:System.Windows.Controls.Canvas.SetLeft%2A> and <xref:System.Windows.Controls.Canvas.GetLeft%2A> methods of <xref:System.Windows.Controls.Canvas> in order to change the position of the `text1` object.</span></span>  
  
 [!code-csharp[CanvasPositioningProperties#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml.cs#2)]
 [!code-vb[CanvasPositioningProperties#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasPositioningProperties/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ecf29-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ecf29-114">See also</span></span>

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.ListBoxItem>
- <xref:System.Windows.LengthConverter>
- [<span data-ttu-id="ecf29-115">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="ecf29-115">Panels Overview</span></span>](panels-overview.md)
