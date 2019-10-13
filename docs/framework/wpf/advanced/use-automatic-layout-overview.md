---
title: Visão geral do uso de layout automático
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: 2fe473da3eeabef3852e3003e61b3b9604332855
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291264"
---
# <a name="use-automatic-layout-overview"></a><span data-ttu-id="72c6f-102">Visão geral do uso de layout automático</span><span class="sxs-lookup"><span data-stu-id="72c6f-102">Use Automatic Layout Overview</span></span>

<span data-ttu-id="72c6f-103">Este tópico apresenta diretrizes para desenvolvedores sobre como escrever aplicativos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] com interfaces do usuário localizáveis (UIs).</span><span class="sxs-lookup"><span data-stu-id="72c6f-103">This topic introduces guidelines for developers on how to write [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications with localizable user interfaces (UIs).</span></span> <span data-ttu-id="72c6f-104">No passado, a localização de uma interface do usuário era um processo demorado.</span><span class="sxs-lookup"><span data-stu-id="72c6f-104">In the past, localization of a UI was a time consuming process.</span></span> <span data-ttu-id="72c6f-105">Cada idioma para o qual a interface do usuário foi adaptada exigia um ajuste de pixel por pixel.</span><span class="sxs-lookup"><span data-stu-id="72c6f-105">Each language that the UI was adapted for required a pixel by pixel adjustment.</span></span> <span data-ttu-id="72c6f-106">Hoje, com o design certo e com os padrões de codificação corretos, as interfaces do projeto podem ser construídas para que os localizadores tenham menos redimensionamento e reposicionamento para fazer.</span><span class="sxs-lookup"><span data-stu-id="72c6f-106">Today with the right design and right coding standards, UIs can be constructed so that localizers have less resizing and repositioning to do.</span></span> <span data-ttu-id="72c6f-107">A abordagem para escrever aplicativos que podem ser mais facilmente redimensionados e reposicionados é chamada de layout automático e pode ser obtida usando o design de aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="72c6f-107">The approach to writing applications that can be more easily resized and repositioned is called automatic layout, and can be achieved by using [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application design.</span></span>

<a name="advantages_of_autolayout"></a>

## <a name="advantages-of-using-automatic-layout"></a><span data-ttu-id="72c6f-108">Vantagens de usar o layout automático</span><span class="sxs-lookup"><span data-stu-id="72c6f-108">Advantages of Using Automatic Layout</span></span>

<span data-ttu-id="72c6f-109">Como o sistema de apresentação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é poderoso e flexível, ele fornece a capacidade de layout de elementos em um aplicativo que pode ser ajustado para atender aos requisitos de diferentes idiomas.</span><span class="sxs-lookup"><span data-stu-id="72c6f-109">Because the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] presentation system is powerful and flexible, it provides the ability to layout elements in an application that can be adjusted to fit the requirements of different languages.</span></span> <span data-ttu-id="72c6f-110">A lista a seguir destaca algumas das vantagens do layout automático.</span><span class="sxs-lookup"><span data-stu-id="72c6f-110">The following list points out some of the advantages of automatic layout.</span></span>

- <span data-ttu-id="72c6f-111">A interface do usuário é bem exibida em qualquer idioma.</span><span class="sxs-lookup"><span data-stu-id="72c6f-111">UI displays well  in any language.</span></span>

- <span data-ttu-id="72c6f-112">Reduz a necessidade de reajustar a posição e o tamanho dos controles após o texto ser traduzido.</span><span class="sxs-lookup"><span data-stu-id="72c6f-112">Reduces the need to readjust position and size of controls after text is translated.</span></span>

- <span data-ttu-id="72c6f-113">Reduz a necessidade de reajustar o tamanho da janela.</span><span class="sxs-lookup"><span data-stu-id="72c6f-113">Reduces the need to readjust window size.</span></span>

- <span data-ttu-id="72c6f-114">O layout da interface do usuário é renderizado corretamente em qualquer idioma.</span><span class="sxs-lookup"><span data-stu-id="72c6f-114">UI layout renders properly in any language.</span></span>

- <span data-ttu-id="72c6f-115">A localização pode ser reduzida a tal ponto que é pouco mais do que uma tradução de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="72c6f-115">Localization can be reduced to the point that it is little more than string translation.</span></span>

<a name="autolayout_controls"></a>

## <a name="automatic-layout-and-controls"></a><span data-ttu-id="72c6f-116">Layout automático e controles</span><span class="sxs-lookup"><span data-stu-id="72c6f-116">Automatic Layout and Controls</span></span>

<span data-ttu-id="72c6f-117">O layout automático permite que um aplicativo ajuste o tamanho de um controle automaticamente.</span><span class="sxs-lookup"><span data-stu-id="72c6f-117">Automatic layout enables an application to adjust the size of a control automatically.</span></span> <span data-ttu-id="72c6f-118">Por exemplo, um controle pode ser alterado para acomodar o tamanho de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="72c6f-118">For example, a control can change to accommodate the length of a string.</span></span> <span data-ttu-id="72c6f-119">Essa funcionalidade permite que os localizadores traduzam a cadeia de caracteres; eles não precisam redimensionar o controle para ajustar o texto traduzido.</span><span class="sxs-lookup"><span data-stu-id="72c6f-119">This capability enables  localizers to translate the string; they no longer need to resize the control to fit the translated text.</span></span> <span data-ttu-id="72c6f-120">O exemplo a seguir cria um botão com conteúdo em inglês.</span><span class="sxs-lookup"><span data-stu-id="72c6f-120">The following example creates a button with English content.</span></span>

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]

<span data-ttu-id="72c6f-121">No exemplo, tudo que você tem que fazer para criar um botão em espanhol é mudar o texto.</span><span class="sxs-lookup"><span data-stu-id="72c6f-121">In the example, all you have to do to make a Spanish button is change the text.</span></span> <span data-ttu-id="72c6f-122">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="72c6f-122">For example,</span></span>

[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]

<span data-ttu-id="72c6f-123">O gráfico a seguir mostra a saída dos exemplos de código:</span><span class="sxs-lookup"><span data-stu-id="72c6f-123">The following graphic shows the output of the code samples:</span></span>

![O mesmo botão com texto em idiomas diferentes](./media/use-automatic-layout-overview/auto-resizable-button.png)

<a name="autolayout_coding"></a>

## <a name="automatic-layout-and-coding-standards"></a><span data-ttu-id="72c6f-125">Layout automático e padrões de codificação</span><span class="sxs-lookup"><span data-stu-id="72c6f-125">Automatic Layout and Coding Standards</span></span>

<span data-ttu-id="72c6f-126">O uso da abordagem de layout automático requer um conjunto de padrões de codificação e design e regras para produzir uma interface do usuário totalmente localizável.</span><span class="sxs-lookup"><span data-stu-id="72c6f-126">Using the automatic layout approach requires a set of coding and design standards and rules to produce a fully localizable UI.</span></span> <span data-ttu-id="72c6f-127">As diretrizes a seguir ajudarão na sua codificação de layout automático.</span><span class="sxs-lookup"><span data-stu-id="72c6f-127">The following guidelines will aid your automatic layout coding.</span></span>

<span data-ttu-id="72c6f-128">**Não usar posições absolutas**</span><span class="sxs-lookup"><span data-stu-id="72c6f-128">**Do not use absolute positions**</span></span>

- <span data-ttu-id="72c6f-129">Não use <xref:System.Windows.Controls.Canvas> porque ele posiciona elementos absolutamente.</span><span class="sxs-lookup"><span data-stu-id="72c6f-129">Do not use <xref:System.Windows.Controls.Canvas> because it positions elements absolutely.</span></span>

- <span data-ttu-id="72c6f-130">Use <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel> e <xref:System.Windows.Controls.Grid> para posicionar controles.</span><span class="sxs-lookup"><span data-stu-id="72c6f-130">Use <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, and <xref:System.Windows.Controls.Grid> to position controls.</span></span>

<span data-ttu-id="72c6f-131">Para obter uma discussão sobre vários tipos de painéis, consulte [visão geral dos painéis](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="72c6f-131">For a discussion about various types of panels, see [Panels Overview](../controls/panels-overview.md).</span></span>

<span data-ttu-id="72c6f-132">**Não definir um tamanho fixo para uma janela**</span><span class="sxs-lookup"><span data-stu-id="72c6f-132">**Do not set a fixed size for a window**</span></span>

- <span data-ttu-id="72c6f-133">Use <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="72c6f-133">Use <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="72c6f-134">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="72c6f-134">For example:</span></span>

  [!code-xaml[LocalizationGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

<span data-ttu-id="72c6f-135">**Adicionar um <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span><span class="sxs-lookup"><span data-stu-id="72c6f-135">**Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span></span>

- <span data-ttu-id="72c6f-136">Adicione um <xref:System.Windows.FrameworkElement.FlowDirection%2A> ao elemento raiz do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="72c6f-136">Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A> to the root element of your application.</span></span>

  <span data-ttu-id="72c6f-137">O WPF fornece uma maneira conveniente para dar suporte a layouts horizontais, bidirecionais e verticais.</span><span class="sxs-lookup"><span data-stu-id="72c6f-137">WPF provides a convenient way to support horizontal, bidirectional, and vertical layouts.</span></span> <span data-ttu-id="72c6f-138">Na estrutura de apresentação, a propriedade <xref:System.Windows.FrameworkElement.FlowDirection%2A> pode ser usada para definir o layout.</span><span class="sxs-lookup"><span data-stu-id="72c6f-138">In presentation framework, the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property can be used to define layout.</span></span> <span data-ttu-id="72c6f-139">Os padrões de direção de fluxo são:</span><span class="sxs-lookup"><span data-stu-id="72c6f-139">The flow-direction patterns are:</span></span>

  - <span data-ttu-id="72c6f-140"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) – layout horizontal para latim, leste asiático e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="72c6f-140"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — horizontal layout for Latin, East Asian, and so forth.</span></span>

  - <span data-ttu-id="72c6f-141"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) – bidirecional para árabe, Hebraico e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="72c6f-141"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — bidirectional for Arabic, Hebrew, and so forth.</span></span>

<span data-ttu-id="72c6f-142">**Usar fontes compostas em vez de fontes físicas**</span><span class="sxs-lookup"><span data-stu-id="72c6f-142">**Use composite fonts instead of physical fonts**</span></span>

- <span data-ttu-id="72c6f-143">Com fontes compostas, a propriedade <xref:System.Windows.Controls.Control.FontFamily%2A> não precisa ser localizada.</span><span class="sxs-lookup"><span data-stu-id="72c6f-143">With composite fonts, the <xref:System.Windows.Controls.Control.FontFamily%2A> property does not need to be localized.</span></span>

- <span data-ttu-id="72c6f-144">Os desenvolvedores podem usar uma das seguintes fontes ou criar suas próprias.</span><span class="sxs-lookup"><span data-stu-id="72c6f-144">Developers can use one of the following fonts or create their own.</span></span>

  - <span data-ttu-id="72c6f-145">Interface de Usuário Global</span><span class="sxs-lookup"><span data-stu-id="72c6f-145">Global User Interface</span></span>
  - <span data-ttu-id="72c6f-146">Global San Serif</span><span class="sxs-lookup"><span data-stu-id="72c6f-146">Global San Serif</span></span>
  - <span data-ttu-id="72c6f-147">Global Serif</span><span class="sxs-lookup"><span data-stu-id="72c6f-147">Global Serif</span></span>

<span data-ttu-id="72c6f-148">**Adicionar XML: lang**</span><span class="sxs-lookup"><span data-stu-id="72c6f-148">**Add xml:lang**</span></span>

- <span data-ttu-id="72c6f-149">Adicione o atributo `xml:lang` no elemento raiz da interface do usuário, como `xml:lang="en-US"` para um aplicativo em inglês.</span><span class="sxs-lookup"><span data-stu-id="72c6f-149">Add the `xml:lang` attribute in the root element of your UI, such as `xml:lang="en-US"` for an English application.</span></span>

- <span data-ttu-id="72c6f-150">Como as fontes compostas usam `xml:lang` para determinar qual fonte usar, defina essa propriedade para dar suporte a cenários multilíngues.</span><span class="sxs-lookup"><span data-stu-id="72c6f-150">Because composite fonts use `xml:lang` to determine what font to use, set this property to support multilingual scenarios.</span></span>

<a name="autolay_grids"></a>

## <a name="automatic-layout-and-grids"></a><span data-ttu-id="72c6f-151">Layout automático e grades</span><span class="sxs-lookup"><span data-stu-id="72c6f-151">Automatic Layout and Grids</span></span>

<span data-ttu-id="72c6f-152">O elemento <xref:System.Windows.Controls.Grid>, é útil para layout automático porque permite que um desenvolvedor Posicione elementos.</span><span class="sxs-lookup"><span data-stu-id="72c6f-152">The <xref:System.Windows.Controls.Grid> element, is useful for automatic layout because it enables a developer to position elements.</span></span> <span data-ttu-id="72c6f-153">Um controle <xref:System.Windows.Controls.Grid> é capaz de distribuir o espaço disponível entre seus elementos filho, usando uma organização de coluna e linha.</span><span class="sxs-lookup"><span data-stu-id="72c6f-153">A <xref:System.Windows.Controls.Grid> control is capable of distributing the available space among its child elements, using a column and row arrangement.</span></span> <span data-ttu-id="72c6f-154">Os elementos da interface do usuário podem abranger várias células e é possível ter grades dentro de grades.</span><span class="sxs-lookup"><span data-stu-id="72c6f-154">The UI elements can span multiple cells, and it is possible to have grids within grids.</span></span> <span data-ttu-id="72c6f-155">As grades são úteis porque permitem que você crie e posicione uma interface do usuário complexa.</span><span class="sxs-lookup"><span data-stu-id="72c6f-155">Grids are useful because they enable you to create and position complex UI.</span></span> <span data-ttu-id="72c6f-156">O exemplo a seguir demonstra o uso de uma grade para posicionar alguns botões e o texto.</span><span class="sxs-lookup"><span data-stu-id="72c6f-156">The following example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="72c6f-157">Observe que a altura e a largura das células são definidas como <xref:System.Windows.GridUnitType.Auto>; Portanto, a célula que contém o botão com uma imagem é ajustada para se ajustar à imagem.</span><span class="sxs-lookup"><span data-stu-id="72c6f-157">Notice that the height and width of the cells are set to <xref:System.Windows.GridUnitType.Auto>; therefore, the cell that contains the button with an image adjusts to fit the image.</span></span>

[!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]

<span data-ttu-id="72c6f-158">O gráfico a seguir mostra a grade produzida pelo código anterior.</span><span class="sxs-lookup"><span data-stu-id="72c6f-158">The following graphic shows the grid produced by the previous code.</span></span>

<span data-ttu-id="72c6f-159">Grade de ![exemplo]de grade(./media/glob-grid.png "glob_grid")</span><span class="sxs-lookup"><span data-stu-id="72c6f-159">![Grid example](./media/glob-grid.png "glob_grid") Grid</span></span>

<a name="autolay_grids_issharedsizescope"></a>

## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a><span data-ttu-id="72c6f-160">Layout automático e grades que utilizam a propriedade IsSharedSizeScope</span><span class="sxs-lookup"><span data-stu-id="72c6f-160">Automatic Layout and Grids Using the IsSharedSizeScope Property</span></span>

<span data-ttu-id="72c6f-161">Um elemento <xref:System.Windows.Controls.Grid> é útil em aplicativos localizáveis para criar controles que se ajustam para ajustar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="72c6f-161">A <xref:System.Windows.Controls.Grid> element is useful in localizable applications to create controls that adjust to fit content.</span></span> <span data-ttu-id="72c6f-162">No entanto, às vezes, você deseja que os controles mantenham um tamanho específico, independentemente do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="72c6f-162">However, at times you want controls to maintain a particular size regardless of content.</span></span> <span data-ttu-id="72c6f-163">Por exemplo, se tiver os botões "OK", "Cancelar" e "Procurar", provavelmente você não desejará que os botões sejam redimensionados para se ajustarem ao conteúdo.</span><span class="sxs-lookup"><span data-stu-id="72c6f-163">For example, if you have "OK", "Cancel" and "Browse" buttons you probably do not want the buttons sized to fit the content.</span></span> <span data-ttu-id="72c6f-164">Nesse caso, a propriedade anexada <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> é útil para compartilhar o mesmo dimensionamento entre vários elementos de grade.</span><span class="sxs-lookup"><span data-stu-id="72c6f-164">In this case the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> attached property is useful for sharing the same sizing among multiple grid elements.</span></span> <span data-ttu-id="72c6f-165">O exemplo a seguir demonstra como compartilhar dados de dimensionamento de coluna e linha entre vários elementos <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="72c6f-165">The following example demonstrates how to share column and row sizing data between multiple <xref:System.Windows.Controls.Grid> elements.</span></span>

[!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]

> [!NOTE]
> <span data-ttu-id="72c6f-166">Para obter o exemplo de código completo, consulte [compartilhar Propriedades de dimensionamento entre grades](../controls/how-to-share-sizing-properties-between-grids.md).</span><span class="sxs-lookup"><span data-stu-id="72c6f-166">For the complete code sample, see [Share Sizing Properties Between Grids](../controls/how-to-share-sizing-properties-between-grids.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="72c6f-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72c6f-167">See also</span></span>

- [<span data-ttu-id="72c6f-168">Globalização para WPF</span><span class="sxs-lookup"><span data-stu-id="72c6f-168">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="72c6f-169">Usar layout automático para criar um botão</span><span class="sxs-lookup"><span data-stu-id="72c6f-169">Use Automatic Layout to Create a Button</span></span>](how-to-use-automatic-layout-to-create-a-button.md)
- [<span data-ttu-id="72c6f-170">Usar uma grade para layout automático</span><span class="sxs-lookup"><span data-stu-id="72c6f-170">Use a Grid for Automatic Layout</span></span>](how-to-use-a-grid-for-automatic-layout.md)
