---
title: Coletar tinta em aplicativos WPF
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
ms.openlocfilehash: 25f9c0141a97d8e52e0883b14fd3e1f4574a05ea
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46004267"
---
# <a name="collect-ink"></a><span data-ttu-id="99f9b-102">Coletar tinta</span><span class="sxs-lookup"><span data-stu-id="99f9b-102">Collect Ink</span></span>

<span data-ttu-id="99f9b-103">A plataforma [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) coleta tinta digital como uma parte importante da sua funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="99f9b-103">The [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) platform collects digital ink as a core part of its functionality.</span></span> <span data-ttu-id="99f9b-104">Este tópico discute métodos para coleta de tinta no Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="99f9b-104">This topic discusses methods for collection of ink in Windows Presentation Foundation (WPF).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="99f9b-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="99f9b-105">Prerequisites</span></span>

<span data-ttu-id="99f9b-106">Para usar os exemplos a seguir, você deve primeiro instalar o Visual Studio e o [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99f9b-106">To use the following examples, you must first install Visual Studio and the [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span></span> <span data-ttu-id="99f9b-107">Você também deve compreender como escrever aplicativos para o WPF.</span><span class="sxs-lookup"><span data-stu-id="99f9b-107">You should also understand how to write applications for the WPF.</span></span> <span data-ttu-id="99f9b-108">Para obter mais informações sobre a introdução ao WPF, consulte [instruções passo a passo: meu primeiro aplicativo da área de trabalho do WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="99f9b-108">For more information about getting started with WPF, see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="use-the-inkcanvas-element"></a><span data-ttu-id="99f9b-109">Use o elemento InkCanvas</span><span class="sxs-lookup"><span data-stu-id="99f9b-109">Use the InkCanvas Element</span></span>

<span data-ttu-id="99f9b-110">O <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> elemento fornece a maneira mais fácil para coletar tinta no WPF.</span><span class="sxs-lookup"><span data-stu-id="99f9b-110">The <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> element provides the easiest way to collect ink in WPF.</span></span> <span data-ttu-id="99f9b-111">Use um <xref:System.Windows.Controls.InkCanvas> elemento para receber e exibir a entrada de tinta.</span><span class="sxs-lookup"><span data-stu-id="99f9b-111">Use an <xref:System.Windows.Controls.InkCanvas> element to receive and display ink input.</span></span> <span data-ttu-id="99f9b-112">Você normalmente insere tinta usando uma caneta, que interage com um digitalizador para produzir traços de tinta.</span><span class="sxs-lookup"><span data-stu-id="99f9b-112">You commonly input ink through the use of a stylus, which interacts with a digitizer to produce ink strokes.</span></span> <span data-ttu-id="99f9b-113">Além disso, um mouse pode ser usado no lugar de uma caneta.</span><span class="sxs-lookup"><span data-stu-id="99f9b-113">In addition, a mouse can be used in place of a stylus.</span></span> <span data-ttu-id="99f9b-114">Os traços criados são representados como <xref:System.Windows.Ink.Stroke> objetos e eles podem ser manipulados tanto programaticamente quanto por usuário de entrada.</span><span class="sxs-lookup"><span data-stu-id="99f9b-114">The created strokes are represented as <xref:System.Windows.Ink.Stroke> objects, and they can be manipulated both programmatically and by user input.</span></span> <span data-ttu-id="99f9b-115">O <xref:System.Windows.Controls.InkCanvas> permite aos usuários selecionar, modificar ou excluir um existente <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="99f9b-115">The <xref:System.Windows.Controls.InkCanvas> enables users to select, modify, or delete an existing <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="99f9b-116">Usando XAML, você pode configurar a coleta de tinta tão facilmente quanto adicionar um **InkCanvas** elemento à sua árvore.</span><span class="sxs-lookup"><span data-stu-id="99f9b-116">By using XAML, you can set up ink collection as easily as adding an **InkCanvas** element to your tree.</span></span> <span data-ttu-id="99f9b-117">O exemplo a seguir adiciona um <xref:System.Windows.Controls.InkCanvas> a um projeto do WPF padrão criado no Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="99f9b-117">The following example adds an <xref:System.Windows.Controls.InkCanvas> to a default WPF project created in Visual Studio:</span></span>

[!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

<span data-ttu-id="99f9b-118">O **InkCanvas** elemento também pode conter elementos filho, tornando possível adicionar recursos de anotação a tinta a quase qualquer tipo de elemento XAML.</span><span class="sxs-lookup"><span data-stu-id="99f9b-118">The **InkCanvas** element can also contain child elements, making it possible to add ink annotation capabilities to almost any type of XAML element.</span></span> <span data-ttu-id="99f9b-119">Por exemplo, para adicionar recursos de tinta a um elemento de texto, basta torná-lo um filho de um <xref:System.Windows.Controls.InkCanvas>:</span><span class="sxs-lookup"><span data-stu-id="99f9b-119">For example, to add inking capabilities to a text element, simply make it a child of an <xref:System.Windows.Controls.InkCanvas>:</span></span>

[!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

<span data-ttu-id="99f9b-120">Adicionando suporte para marcação de uma imagem com tinta é tão fácil:</span><span class="sxs-lookup"><span data-stu-id="99f9b-120">Adding support for marking up an image with ink is just as easy:</span></span>

[!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a><span data-ttu-id="99f9b-121">Modos de InkCollection</span><span class="sxs-lookup"><span data-stu-id="99f9b-121">InkCollection Modes</span></span>

<span data-ttu-id="99f9b-122">O <xref:System.Windows.Controls.InkCanvas> oferece suporte para vários modos de entrada pela sua <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="99f9b-122">The <xref:System.Windows.Controls.InkCanvas> provides support for various input modes through its <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> property.</span></span>

### <a name="manipulate-ink"></a><span data-ttu-id="99f9b-123">Manipular tinta</span><span class="sxs-lookup"><span data-stu-id="99f9b-123">Manipulate Ink</span></span>

<span data-ttu-id="99f9b-124">O <xref:System.Windows.Controls.InkCanvas> fornece suporte para muitas operações de edição de tinta.</span><span class="sxs-lookup"><span data-stu-id="99f9b-124">The <xref:System.Windows.Controls.InkCanvas> provides support for many ink editing operations.</span></span> <span data-ttu-id="99f9b-125">Por exemplo, <xref:System.Windows.Controls.InkCanvas> apagar dá suporte a traseira da caneta e nenhum código adicional é necessária para adicionar a funcionalidade para o elemento.</span><span class="sxs-lookup"><span data-stu-id="99f9b-125">For example, <xref:System.Windows.Controls.InkCanvas> supports back-of-pen erase, and no additional code is needed to add the functionality to the element.</span></span>

#### <a name="selection"></a><span data-ttu-id="99f9b-126">Seleção</span><span class="sxs-lookup"><span data-stu-id="99f9b-126">Selection</span></span>

<span data-ttu-id="99f9b-127">Configurar modo de seleção é tão simple quanto a configuração do <xref:System.Windows.Controls.InkCanvasEditingMode> propriedade para **selecione**.</span><span class="sxs-lookup"><span data-stu-id="99f9b-127">Setting selection mode is as simple as setting the <xref:System.Windows.Controls.InkCanvasEditingMode> property to **Select**.</span></span>

<span data-ttu-id="99f9b-128">O código a seguir define o modo de edição com base no valor de um <xref:System.Windows.Forms.CheckBox>:</span><span class="sxs-lookup"><span data-stu-id="99f9b-128">The following code sets the editing mode based on the value of a <xref:System.Windows.Forms.CheckBox>:</span></span>

[!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a><span data-ttu-id="99f9b-129">DrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="99f9b-129">DrawingAttributes</span></span>

<span data-ttu-id="99f9b-130">Use o <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> propriedade para alterar a aparência dos traços de tinta.</span><span class="sxs-lookup"><span data-stu-id="99f9b-130">Use the <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> property to change the appearance of ink strokes.</span></span> <span data-ttu-id="99f9b-131">Por exemplo, o <xref:System.Windows.Ink.DrawingAttributes.Color%2A> membro <xref:System.Windows.Ink.DrawingAttributes> define a cor do renderizado <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="99f9b-131">For instance, the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> member of <xref:System.Windows.Ink.DrawingAttributes> sets the color of the rendered <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="99f9b-132">O exemplo a seguir altera a cor dos traços selecionados para vermelho:</span><span class="sxs-lookup"><span data-stu-id="99f9b-132">The following example changes the color of the selected strokes to red:</span></span>

[!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a><span data-ttu-id="99f9b-133">DefaultDrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="99f9b-133">DefaultDrawingAttributes</span></span>

<span data-ttu-id="99f9b-134">O <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> propriedade fornece acesso a propriedades como altura, largura e cor dos traços a serem criados em um <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="99f9b-134">The <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property provides access to properties such as the height, width, and color of the strokes to be created in an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="99f9b-135">Depois que você alterar o <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, todos os traços futuros inseridos no <xref:System.Windows.Controls.InkCanvas> são renderizados com os novos valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="99f9b-135">Once you change the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, all future strokes entered into the <xref:System.Windows.Controls.InkCanvas> are rendered with the new property values.</span></span>

<span data-ttu-id="99f9b-136">Além de modificar as <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> no arquivo code-behind, você pode usar a sintaxe XAML para especificar <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="99f9b-136">In addition to modifying the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> in the code-behind file, you can use XAML syntax for specifying <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties.</span></span>

<span data-ttu-id="99f9b-137">O exemplo a seguir demonstra como definir o <xref:System.Windows.Ink.DrawingAttributes.Color%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="99f9b-137">The next example demonstrates how to set the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> property.</span></span> <span data-ttu-id="99f9b-138">Para usar esse código, crie um novo projeto WPF chamado "HelloInkCanvas" no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="99f9b-138">To use this code, create a new WPF project called "HelloInkCanvas" in Visual Studio.</span></span> <span data-ttu-id="99f9b-139">Substitua o código na *MainWindow. XAML* arquivo pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="99f9b-139">Replace the code in the *MainWindow.xaml* file with the following code:</span></span>

[!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

<span data-ttu-id="99f9b-140">Em seguida, adicione os seguintes manipuladores de eventos do botão para o arquivo code-behind, dentro da classe MainWindow:</span><span class="sxs-lookup"><span data-stu-id="99f9b-140">Next, add the following button event handlers to the code behind file, inside the MainWindow class:</span></span>

[!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

<span data-ttu-id="99f9b-141">Após copiar esse código, pressione **F5** no Visual Studio para executar o programa no depurador.</span><span class="sxs-lookup"><span data-stu-id="99f9b-141">After copying this code, press **F5** in Visual Studio to run the program in the debugger.</span></span>

<span data-ttu-id="99f9b-142">Observe como o <xref:System.Windows.Controls.StackPanel> coloca os botões na parte superior do <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="99f9b-142">Notice how the <xref:System.Windows.Controls.StackPanel> places the buttons on top of the <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="99f9b-143">Se você tentar escrever à tinta na parte superior dos botões, o <xref:System.Windows.Controls.InkCanvas> coleta e renderiza a tinta atrás dos botões.</span><span class="sxs-lookup"><span data-stu-id="99f9b-143">If you try to ink over the top of the buttons, the <xref:System.Windows.Controls.InkCanvas> collects and renders the ink behind the buttons.</span></span> <span data-ttu-id="99f9b-144">Isso ocorre porque os botões são irmãos do <xref:System.Windows.Controls.InkCanvas> em vez de filhos.</span><span class="sxs-lookup"><span data-stu-id="99f9b-144">This is because the buttons are siblings of the <xref:System.Windows.Controls.InkCanvas> as opposed to children.</span></span> <span data-ttu-id="99f9b-145">Além disso, os botões estão mais altos na ordem z, de modo que a tinta é renderizada atrás deles.</span><span class="sxs-lookup"><span data-stu-id="99f9b-145">Also, the buttons are higher in the z-order, so the ink is rendered behind them.</span></span>

## <a name="see-also"></a><span data-ttu-id="99f9b-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99f9b-146">See Also</span></span>

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>