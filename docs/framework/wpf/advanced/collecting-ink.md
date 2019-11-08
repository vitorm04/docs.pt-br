---
title: Coletar tinta em aplicativos do WPF
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], collecting
- InkCanvas element [WPF]
- properties [WPF], DrawingAttributes
- collecting digital ink [WPF]
- digital ink [WPF], collecting
- properties [WPF], DefaultDrawingAttributes
- DefaultDrawingAttributes property [WPF]
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
ms.openlocfilehash: 8109e0d6a746d6ca23c25643c510014c1a1e656c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740880"
---
# <a name="collect-ink"></a><span data-ttu-id="f5493-102">Coletar tinta</span><span class="sxs-lookup"><span data-stu-id="f5493-102">Collect Ink</span></span>

<span data-ttu-id="f5493-103">A plataforma [Windows Presentation Foundation](../index.md) coleta tinta digital como uma parte importante da sua funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="f5493-103">The [Windows Presentation Foundation](../index.md) platform collects digital ink as a core part of its functionality.</span></span> <span data-ttu-id="f5493-104">Este tópico discute métodos para a coleta de tinta no Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="f5493-104">This topic discusses methods for collection of ink in Windows Presentation Foundation (WPF).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f5493-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f5493-105">Prerequisites</span></span>

<span data-ttu-id="f5493-106">Para usar os exemplos a seguir, você deve primeiro instalar o Visual Studio e o SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="f5493-106">To use the following examples, you must first install Visual Studio and the Windows SDK.</span></span> <span data-ttu-id="f5493-107">Você também deve entender como escrever aplicativos para o WPF.</span><span class="sxs-lookup"><span data-stu-id="f5493-107">You should also understand how to write applications for the WPF.</span></span> <span data-ttu-id="f5493-108">Para obter mais informações sobre como começar a usar o WPF, consulte [Walkthrough: meu primeiro aplicativo de área de trabalho do WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="f5493-108">For more information about getting started with WPF, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="use-the-inkcanvas-element"></a><span data-ttu-id="f5493-109">Usar o elemento InkCanvas</span><span class="sxs-lookup"><span data-stu-id="f5493-109">Use the InkCanvas Element</span></span>

<span data-ttu-id="f5493-110">O elemento <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> fornece a maneira mais fácil de coletar tinta no WPF.</span><span class="sxs-lookup"><span data-stu-id="f5493-110">The <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> element provides the easiest way to collect ink in WPF.</span></span> <span data-ttu-id="f5493-111">Use um elemento <xref:System.Windows.Controls.InkCanvas> para receber e exibir a entrada à tinta.</span><span class="sxs-lookup"><span data-stu-id="f5493-111">Use an <xref:System.Windows.Controls.InkCanvas> element to receive and display ink input.</span></span> <span data-ttu-id="f5493-112">Você normalmente insere tinta usando uma caneta, que interage com um digitalizador para produzir traços de tinta.</span><span class="sxs-lookup"><span data-stu-id="f5493-112">You commonly input ink through the use of a stylus, which interacts with a digitizer to produce ink strokes.</span></span> <span data-ttu-id="f5493-113">Além disso, um mouse pode ser usado no lugar de uma caneta.</span><span class="sxs-lookup"><span data-stu-id="f5493-113">In addition, a mouse can be used in place of a stylus.</span></span> <span data-ttu-id="f5493-114">Os traços criados são representados como objetos <xref:System.Windows.Ink.Stroke> e podem ser manipulados de forma programática e por entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="f5493-114">The created strokes are represented as <xref:System.Windows.Ink.Stroke> objects, and they can be manipulated both programmatically and by user input.</span></span> <span data-ttu-id="f5493-115">O <xref:System.Windows.Controls.InkCanvas> permite que os usuários selecionem, modifiquem ou excluam um <xref:System.Windows.Ink.Stroke>existente.</span><span class="sxs-lookup"><span data-stu-id="f5493-115">The <xref:System.Windows.Controls.InkCanvas> enables users to select, modify, or delete an existing <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="f5493-116">Usando o XAML, você pode configurar a coleta de tinta tão facilmente quanto adicionar um elemento **InkCanvas** à sua árvore.</span><span class="sxs-lookup"><span data-stu-id="f5493-116">By using XAML, you can set up ink collection as easily as adding an **InkCanvas** element to your tree.</span></span> <span data-ttu-id="f5493-117">O exemplo a seguir adiciona um <xref:System.Windows.Controls.InkCanvas> a um projeto padrão do WPF criado no Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="f5493-117">The following example adds an <xref:System.Windows.Controls.InkCanvas> to a default WPF project created in Visual Studio:</span></span>

[!code-xaml[DigitalInkTopics#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

<span data-ttu-id="f5493-118">O elemento **InkCanvas** também pode conter elementos filho, possibilitando a adição de recursos de anotação à tinta a praticamente qualquer tipo de elemento XAML.</span><span class="sxs-lookup"><span data-stu-id="f5493-118">The **InkCanvas** element can also contain child elements, making it possible to add ink annotation capabilities to almost any type of XAML element.</span></span> <span data-ttu-id="f5493-119">Por exemplo, para adicionar recursos de tinta a um elemento de texto, basta torná-lo um filho de um <xref:System.Windows.Controls.InkCanvas>:</span><span class="sxs-lookup"><span data-stu-id="f5493-119">For example, to add inking capabilities to a text element, simply make it a child of an <xref:System.Windows.Controls.InkCanvas>:</span></span>

[!code-xaml[DigitalInkTopics#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

<span data-ttu-id="f5493-120">Adicionar suporte para marcar uma imagem com tinta é tão fácil quanto:</span><span class="sxs-lookup"><span data-stu-id="f5493-120">Adding support for marking up an image with ink is just as easy:</span></span>

[!code-xaml[DigitalInkTopics#7](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a><span data-ttu-id="f5493-121">Modos de InkCollection</span><span class="sxs-lookup"><span data-stu-id="f5493-121">InkCollection Modes</span></span>

<span data-ttu-id="f5493-122">O <xref:System.Windows.Controls.InkCanvas> fornece suporte para vários modos de entrada por meio de sua propriedade <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="f5493-122">The <xref:System.Windows.Controls.InkCanvas> provides support for various input modes through its <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> property.</span></span>

### <a name="manipulate-ink"></a><span data-ttu-id="f5493-123">Manipular tinta</span><span class="sxs-lookup"><span data-stu-id="f5493-123">Manipulate Ink</span></span>

<span data-ttu-id="f5493-124">O <xref:System.Windows.Controls.InkCanvas> fornece suporte para muitas operações de edição de tinta.</span><span class="sxs-lookup"><span data-stu-id="f5493-124">The <xref:System.Windows.Controls.InkCanvas> provides support for many ink editing operations.</span></span> <span data-ttu-id="f5493-125">Por exemplo, <xref:System.Windows.Controls.InkCanvas> dá suporte a apagamento de verso da caneta e nenhum código adicional é necessário para adicionar a funcionalidade ao elemento.</span><span class="sxs-lookup"><span data-stu-id="f5493-125">For example, <xref:System.Windows.Controls.InkCanvas> supports back-of-pen erase, and no additional code is needed to add the functionality to the element.</span></span>

#### <a name="selection"></a><span data-ttu-id="f5493-126">Seleção</span><span class="sxs-lookup"><span data-stu-id="f5493-126">Selection</span></span>

<span data-ttu-id="f5493-127">Definir o modo de seleção é tão simples quanto definir a propriedade <xref:System.Windows.Controls.InkCanvasEditingMode> para **selecionar**.</span><span class="sxs-lookup"><span data-stu-id="f5493-127">Setting selection mode is as simple as setting the <xref:System.Windows.Controls.InkCanvasEditingMode> property to **Select**.</span></span>

<span data-ttu-id="f5493-128">O código a seguir define o modo de edição com base no valor de um <xref:System.Windows.Forms.CheckBox>:</span><span class="sxs-lookup"><span data-stu-id="f5493-128">The following code sets the editing mode based on the value of a <xref:System.Windows.Forms.CheckBox>:</span></span>

[!code-csharp[DigitalInkTopics#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a><span data-ttu-id="f5493-129">DrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="f5493-129">DrawingAttributes</span></span>

<span data-ttu-id="f5493-130">Use a propriedade <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> para alterar a aparência dos traços de tinta.</span><span class="sxs-lookup"><span data-stu-id="f5493-130">Use the <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> property to change the appearance of ink strokes.</span></span> <span data-ttu-id="f5493-131">Por exemplo, o membro <xref:System.Windows.Ink.DrawingAttributes.Color%2A> de <xref:System.Windows.Ink.DrawingAttributes> define a cor da <xref:System.Windows.Ink.Stroke>renderizada.</span><span class="sxs-lookup"><span data-stu-id="f5493-131">For instance, the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> member of <xref:System.Windows.Ink.DrawingAttributes> sets the color of the rendered <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="f5493-132">O exemplo a seguir altera a cor dos traços selecionados para vermelho:</span><span class="sxs-lookup"><span data-stu-id="f5493-132">The following example changes the color of the selected strokes to red:</span></span>

[!code-csharp[DigitalInkTopics#9](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a><span data-ttu-id="f5493-133">DefaultDrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="f5493-133">DefaultDrawingAttributes</span></span>

<span data-ttu-id="f5493-134">A propriedade <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> fornece acesso a propriedades como a altura, a largura e a cor dos traços a serem criados em uma <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="f5493-134">The <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property provides access to properties such as the height, width, and color of the strokes to be created in an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="f5493-135">Depois de alterar o <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, todos os traços futuros inseridos na <xref:System.Windows.Controls.InkCanvas> serão renderizados com os novos valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="f5493-135">Once you change the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, all future strokes entered into the <xref:System.Windows.Controls.InkCanvas> are rendered with the new property values.</span></span>

<span data-ttu-id="f5493-136">Além de modificar o <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> no arquivo code-behind, você pode usar a sintaxe XAML para especificar <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> Propriedades.</span><span class="sxs-lookup"><span data-stu-id="f5493-136">In addition to modifying the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> in the code-behind file, you can use XAML syntax for specifying <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties.</span></span>

<span data-ttu-id="f5493-137">O exemplo a seguir demonstra como definir a propriedade <xref:System.Windows.Ink.DrawingAttributes.Color%2A>.</span><span class="sxs-lookup"><span data-stu-id="f5493-137">The next example demonstrates how to set the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> property.</span></span> <span data-ttu-id="f5493-138">Para usar esse código, crie um novo projeto do WPF chamado "HelloInkCanvas" no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f5493-138">To use this code, create a new WPF project called "HelloInkCanvas" in Visual Studio.</span></span> <span data-ttu-id="f5493-139">Substitua o código no arquivo *MainWindow. XAML* pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="f5493-139">Replace the code in the *MainWindow.xaml* file with the following code:</span></span>

[!code-xaml[HelloInkCanvas#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

<span data-ttu-id="f5493-140">Em seguida, adicione os seguintes manipuladores de eventos de botão ao arquivo code-behind, dentro da classe MainWindow:</span><span class="sxs-lookup"><span data-stu-id="f5493-140">Next, add the following button event handlers to the code behind file, inside the MainWindow class:</span></span>

[!code-csharp[HelloInkCanvas#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

<span data-ttu-id="f5493-141">Depois de copiar esse código, pressione **F5** no Visual Studio para executar o programa no depurador.</span><span class="sxs-lookup"><span data-stu-id="f5493-141">After copying this code, press **F5** in Visual Studio to run the program in the debugger.</span></span>

<span data-ttu-id="f5493-142">Observe como o <xref:System.Windows.Controls.StackPanel> coloca os botões na parte superior do <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="f5493-142">Notice how the <xref:System.Windows.Controls.StackPanel> places the buttons on top of the <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="f5493-143">Se você tentar passar a tinta sobre a parte superior dos botões, a <xref:System.Windows.Controls.InkCanvas> coleta e renderiza a tinta por trás dos botões.</span><span class="sxs-lookup"><span data-stu-id="f5493-143">If you try to ink over the top of the buttons, the <xref:System.Windows.Controls.InkCanvas> collects and renders the ink behind the buttons.</span></span> <span data-ttu-id="f5493-144">Isso ocorre porque os botões são irmãos da <xref:System.Windows.Controls.InkCanvas> em vez de filhos.</span><span class="sxs-lookup"><span data-stu-id="f5493-144">This is because the buttons are siblings of the <xref:System.Windows.Controls.InkCanvas> as opposed to children.</span></span> <span data-ttu-id="f5493-145">Além disso, os botões estão mais altos na ordem z, de modo que a tinta é renderizada atrás deles.</span><span class="sxs-lookup"><span data-stu-id="f5493-145">Also, the buttons are higher in the z-order, so the ink is rendered behind them.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5493-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5493-146">See also</span></span>

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>
