---
title: Visão geral do uso de layout automático
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: af564c4ca865c47c7efdda6ed86732581f677218
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353589"
---
# <a name="use-automatic-layout-overview"></a><span data-ttu-id="a2065-102">Visão geral do uso de layout automático</span><span class="sxs-lookup"><span data-stu-id="a2065-102">Use Automatic Layout Overview</span></span>
<span data-ttu-id="a2065-103">Este tópico apresenta diretrizes para desenvolvedores sobre como escrever [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplicativos com localizáveis [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a2065-103">This topic introduces guidelines for developers on how to write [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications with localizable [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)].</span></span> <span data-ttu-id="a2065-104">No passado, a localização de uma interface do usuário era um processo demorado.</span><span class="sxs-lookup"><span data-stu-id="a2065-104">In the past, localization of a UI was a time consuming process.</span></span> <span data-ttu-id="a2065-105">A interface do usuário foi adaptado para cada idioma necessário um ajuste pixel por pixel.</span><span class="sxs-lookup"><span data-stu-id="a2065-105">Each language that the UI was adapted for required a pixel by pixel adjustment.</span></span> <span data-ttu-id="a2065-106">Hoje, com o design e o direito de padrões de codificação, [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] pode ser criado para que os localizadores tenham menos redimensionamento e reposicionamento.</span><span class="sxs-lookup"><span data-stu-id="a2065-106">Today with the right design and right coding standards, [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] can be constructed so that localizers have less resizing and repositioning to do.</span></span> <span data-ttu-id="a2065-107">A abordagem para escrever aplicativos que podem ser mais facilmente redimensionados e reposicionados é chamada de layout automático e pode ser obtida usando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] design do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a2065-107">The approach to writing applications that can be more easily resized and repositioned is called automatic layout, and can be achieved by using [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application design.</span></span>  

<a name="advantages_of_autolayout"></a>   
## <a name="advantages-of-using-automatic-layout"></a><span data-ttu-id="a2065-108">Vantagens de usar o layout automático</span><span class="sxs-lookup"><span data-stu-id="a2065-108">Advantages of Using Automatic Layout</span></span>  
 <span data-ttu-id="a2065-109">Porque o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistema de apresentação é poderoso e flexível, ele fornece a capacidade de dispor os elementos em um aplicativo que pode ser ajustada para atender às necessidades de diferentes idiomas.</span><span class="sxs-lookup"><span data-stu-id="a2065-109">Because the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] presentation system is powerful and flexible, it provides the ability to layout elements in an application that can be adjusted to fit the requirements of different languages.</span></span> <span data-ttu-id="a2065-110">A lista a seguir destaca algumas das vantagens do layout automático.</span><span class="sxs-lookup"><span data-stu-id="a2065-110">The following list points out some of the advantages of automatic layout.</span></span>  

-   <span data-ttu-id="a2065-111">Interface do usuário exibe bem em qualquer idioma.</span><span class="sxs-lookup"><span data-stu-id="a2065-111">UI displays well  in any language.</span></span>  

-   <span data-ttu-id="a2065-112">Reduz a necessidade de reajustar a posição e o tamanho dos controles após o texto ser traduzido.</span><span class="sxs-lookup"><span data-stu-id="a2065-112">Reduces the need to readjust position and size of controls after text is translated.</span></span>  
  
-   <span data-ttu-id="a2065-113">Reduz a necessidade de reajustar o tamanho da janela.</span><span class="sxs-lookup"><span data-stu-id="a2065-113">Reduces the need to readjust window size.</span></span>  

-   <span data-ttu-id="a2065-114">Layout da interface do usuário é renderizada corretamente em qualquer idioma.</span><span class="sxs-lookup"><span data-stu-id="a2065-114">UI layout renders properly in any language.</span></span>  

-   <span data-ttu-id="a2065-115">A localização pode ser reduzida a tal ponto que é pouco mais do que uma tradução de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a2065-115">Localization can be reduced to the point that it is little more than string translation.</span></span>  
  
<a name="autolayout_controls"></a>   
## <a name="automatic-layout-and-controls"></a><span data-ttu-id="a2065-116">Layout automático e controles</span><span class="sxs-lookup"><span data-stu-id="a2065-116">Automatic Layout and Controls</span></span>  
 <span data-ttu-id="a2065-117">O layout automático permite que um aplicativo ajuste o tamanho de um controle automaticamente.</span><span class="sxs-lookup"><span data-stu-id="a2065-117">Automatic layout enables an application to adjust the size of a control automatically.</span></span> <span data-ttu-id="a2065-118">Por exemplo, um controle pode ser alterado para acomodar o tamanho de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a2065-118">For example, a control can change to accommodate the length of a string.</span></span> <span data-ttu-id="a2065-119">Essa funcionalidade permite que os localizadores traduzam a cadeia de caracteres; eles não precisam redimensionar o controle para ajustar o texto traduzido.</span><span class="sxs-lookup"><span data-stu-id="a2065-119">This capability enables  localizers to translate the string; they no longer need to resize the control to fit the translated text.</span></span> <span data-ttu-id="a2065-120">O exemplo a seguir cria um botão com conteúdo em inglês.</span><span class="sxs-lookup"><span data-stu-id="a2065-120">The following example creates a button with English content.</span></span>  
  
 [!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="a2065-121">No exemplo, tudo que você tem que fazer para criar um botão em espanhol é mudar o texto.</span><span class="sxs-lookup"><span data-stu-id="a2065-121">In the example, all you have to do to make a Spanish button is change the text.</span></span> <span data-ttu-id="a2065-122">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="a2065-122">For example,</span></span>  
  
 [!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="a2065-123">O gráfico a seguir mostra a saída dos exemplos de código.</span><span class="sxs-lookup"><span data-stu-id="a2065-123">The following graphic shows the output of the code samples.</span></span>  
  
 <span data-ttu-id="a2065-124">![O mesmo botão com texto em diferentes idiomas](./media/globalizationbutton.png "GlobalizationButton")</span><span class="sxs-lookup"><span data-stu-id="a2065-124">![The same button with text in different languages](./media/globalizationbutton.png "GlobalizationButton")</span></span>  
<span data-ttu-id="a2065-125">Botão redimensionável automaticamente</span><span class="sxs-lookup"><span data-stu-id="a2065-125">Auto Resizable Button</span></span>  
  
<a name="autolayout_coding"></a>   
## <a name="automatic-layout-and-coding-standards"></a><span data-ttu-id="a2065-126">Layout automático e padrões de codificação</span><span class="sxs-lookup"><span data-stu-id="a2065-126">Automatic Layout and Coding Standards</span></span>  
 <span data-ttu-id="a2065-127">Usando a abordagem de layout automático requer um conjunto de padrões de design e codificação e as regras para produzir uma interface do usuário completamente localizável.</span><span class="sxs-lookup"><span data-stu-id="a2065-127">Using the automatic layout approach requires a set of coding and design standards and rules to produce a fully localizable UI.</span></span> <span data-ttu-id="a2065-128">As diretrizes a seguir ajudarão na sua codificação de layout automático.</span><span class="sxs-lookup"><span data-stu-id="a2065-128">The following guidelines will aid your automatic layout coding.</span></span>  

<span data-ttu-id="a2065-129">**Não use posições absolutas**</span><span class="sxs-lookup"><span data-stu-id="a2065-129">**Do not use absolute positions**</span></span>

- <span data-ttu-id="a2065-130">Não use <xref:System.Windows.Controls.Canvas> porque ele posiciona elementos absolutamente.</span><span class="sxs-lookup"><span data-stu-id="a2065-130">Do not use <xref:System.Windows.Controls.Canvas> because it positions elements absolutely.</span></span>

- <span data-ttu-id="a2065-131">Use <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, e <xref:System.Windows.Controls.Grid> para posicionar controles.</span><span class="sxs-lookup"><span data-stu-id="a2065-131">Use <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, and <xref:System.Windows.Controls.Grid> to position controls.</span></span>

<span data-ttu-id="a2065-132">Para uma discussão sobre diversos tipos de painéis, consulte [visão geral de painéis](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a2065-132">For a discussion about various types of panels, see [Panels Overview](../controls/panels-overview.md).</span></span>

<span data-ttu-id="a2065-133">**Não defina um tamanho fixo para uma janela**</span><span class="sxs-lookup"><span data-stu-id="a2065-133">**Do not set a fixed size for a window**</span></span>

- <span data-ttu-id="a2065-134">Use <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a2065-134">Use <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a2065-135">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a2065-135">For example:</span></span>

   [!code-xaml[LocalizationGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

<span data-ttu-id="a2065-136">**Adicionar um <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span><span class="sxs-lookup"><span data-stu-id="a2065-136">**Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span></span>

- <span data-ttu-id="a2065-137">Adicionar um <xref:System.Windows.FrameworkElement.FlowDirection%2A> ao elemento raiz do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a2065-137">Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A> to the root element of your application.</span></span>

   <span data-ttu-id="a2065-138">O WPF fornece uma maneira conveniente de dar suporte a horizontais, bidirecionais e layouts verticais.</span><span class="sxs-lookup"><span data-stu-id="a2065-138">WPF provides a convenient way to support horizontal, bidirectional, and vertical layouts.</span></span> <span data-ttu-id="a2065-139">No framework de apresentação, o <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade pode ser usada para definir o layout.</span><span class="sxs-lookup"><span data-stu-id="a2065-139">In presentation framework, the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property can be used to define layout.</span></span> <span data-ttu-id="a2065-140">Os padrões de direção de fluxo são:</span><span class="sxs-lookup"><span data-stu-id="a2065-140">The flow-direction patterns are:</span></span>
   
     - <span data-ttu-id="a2065-141"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — layout horizontal para latim, Leste Asiático e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="a2065-141"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — horizontal layout for Latin, East Asian, and so forth.</span></span>
     
     - <span data-ttu-id="a2065-142"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — bidirecional para árabe, hebraico e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="a2065-142"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — bidirectional for Arabic, Hebrew, and so forth.</span></span>

<span data-ttu-id="a2065-143">**Use fontes de composição em vez de fontes físicas**</span><span class="sxs-lookup"><span data-stu-id="a2065-143">**Use composite fonts instead of physical fonts**</span></span>

- <span data-ttu-id="a2065-144">Com fontes compostas, o <xref:System.Windows.Controls.Control.FontFamily%2A> propriedade não precisa ser localizada.</span><span class="sxs-lookup"><span data-stu-id="a2065-144">With composite fonts, the <xref:System.Windows.Controls.Control.FontFamily%2A> property does not need to be localized.</span></span>

- <span data-ttu-id="a2065-145">Os desenvolvedores podem usar uma das seguintes fontes ou criar suas próprias.</span><span class="sxs-lookup"><span data-stu-id="a2065-145">Developers can use one of the following fonts or create their own.</span></span>

   - <span data-ttu-id="a2065-146">Interface de Usuário Global</span><span class="sxs-lookup"><span data-stu-id="a2065-146">Global User Interface</span></span>
   - <span data-ttu-id="a2065-147">Global San Serif</span><span class="sxs-lookup"><span data-stu-id="a2065-147">Global San Serif</span></span>
   - <span data-ttu-id="a2065-148">Global Serif</span><span class="sxs-lookup"><span data-stu-id="a2065-148">Global Serif</span></span>

<span data-ttu-id="a2065-149">**Adicionar XML: lang**</span><span class="sxs-lookup"><span data-stu-id="a2065-149">**Add xml:lang**</span></span>

- <span data-ttu-id="a2065-150">Adicione a `xml:lang` atributo no elemento raiz da sua interface do usuário, como `xml:lang="en-US"` para um aplicativo em inglês.</span><span class="sxs-lookup"><span data-stu-id="a2065-150">Add the `xml:lang` attribute in the root element of your UI, such as `xml:lang="en-US"` for an English application.</span></span>

- <span data-ttu-id="a2065-151">Como usam fontes de composição `xml:lang` para determinar qual fonte utilizar, defina essa propriedade para dar suporte a cenários multilíngues.</span><span class="sxs-lookup"><span data-stu-id="a2065-151">Because composite fonts use `xml:lang` to determine what font to use, set this property to support multilingual scenarios.</span></span>

<a name="autolay_grids"></a>   
## <a name="automatic-layout-and-grids"></a><span data-ttu-id="a2065-152">Layout automático e grades</span><span class="sxs-lookup"><span data-stu-id="a2065-152">Automatic Layout and Grids</span></span>  
 <span data-ttu-id="a2065-153">O <xref:System.Windows.Controls.Grid> elemento, é útil para layout automático porque ele permite que um desenvolvedor posicione elementos.</span><span class="sxs-lookup"><span data-stu-id="a2065-153">The <xref:System.Windows.Controls.Grid> element, is useful for automatic layout because it enables a developer to position elements.</span></span> <span data-ttu-id="a2065-154">Um <xref:System.Windows.Controls.Grid> controle é capaz de distribuir o espaço disponível entre seus elementos filhos, usando uma disposição de linha e coluna.</span><span class="sxs-lookup"><span data-stu-id="a2065-154">A <xref:System.Windows.Controls.Grid> control is capable of distributing the available space among its child elements, using a column and row arrangement.</span></span> <span data-ttu-id="a2065-155">Os elementos de interface do usuário podem abranger várias células, e é possível que haja grades dentro de grades.</span><span class="sxs-lookup"><span data-stu-id="a2065-155">The UI elements can span multiple cells, and it is possible to have grids within grids.</span></span> <span data-ttu-id="a2065-156">As grades são úteis porque permitem que você crie e posicione a interface do usuário complexa.</span><span class="sxs-lookup"><span data-stu-id="a2065-156">Grids are useful because they enable you to create and position complex UI.</span></span> <span data-ttu-id="a2065-157">O exemplo a seguir demonstra o uso de uma grade para posicionar alguns botões e o texto.</span><span class="sxs-lookup"><span data-stu-id="a2065-157">The following example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="a2065-158">Observe que a altura e largura das células são definidas como <xref:System.Windows.GridUnitType.Auto>; portanto, a célula que contém o botão com uma imagem é ajustada para ajustar a imagem.</span><span class="sxs-lookup"><span data-stu-id="a2065-158">Notice that the height and width of the cells are set to <xref:System.Windows.GridUnitType.Auto>; therefore, the cell that contains the button with an image adjusts to fit the image.</span></span>  

 [!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="a2065-159">O gráfico a seguir mostra a grade produzida pelo código anterior.</span><span class="sxs-lookup"><span data-stu-id="a2065-159">The following graphic shows the grid produced by the previous code.</span></span>  
  
 <span data-ttu-id="a2065-160">![Exemplo de grade](./media/glob-grid.png "glob_grid")</span><span class="sxs-lookup"><span data-stu-id="a2065-160">![Grid example](./media/glob-grid.png "glob_grid")</span></span>  
<span data-ttu-id="a2065-161">Grade</span><span class="sxs-lookup"><span data-stu-id="a2065-161">Grid</span></span>  
  
<a name="autolay_grids_issharedsizescope"></a>   
## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a><span data-ttu-id="a2065-162">Layout automático e grades que utilizam a propriedade IsSharedSizeScope</span><span class="sxs-lookup"><span data-stu-id="a2065-162">Automatic Layout and Grids Using the IsSharedSizeScope Property</span></span>  
 <span data-ttu-id="a2065-163">Um <xref:System.Windows.Controls.Grid> elemento é útil em aplicativos localizáveis para criar controles que são ajustadas para que o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="a2065-163">A <xref:System.Windows.Controls.Grid> element is useful in localizable applications to create controls that adjust to fit content.</span></span> <span data-ttu-id="a2065-164">No entanto, às vezes, você deseja que os controles mantenham um tamanho específico, independentemente do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="a2065-164">However, at times you want controls to maintain a particular size regardless of content.</span></span> <span data-ttu-id="a2065-165">Por exemplo, se tiver os botões "OK", "Cancelar" e "Procurar", provavelmente você não desejará que os botões sejam redimensionados para se ajustarem ao conteúdo.</span><span class="sxs-lookup"><span data-stu-id="a2065-165">For example, if you have "OK", "Cancel" and "Browse" buttons you probably do not want the buttons sized to fit the content.</span></span> <span data-ttu-id="a2065-166">Nesse caso, o <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> propriedade anexada é útil para compartilhar o mesmo tamanho entre vários elementos da grade.</span><span class="sxs-lookup"><span data-stu-id="a2065-166">In this case the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> attached property is useful for sharing the same sizing among multiple grid elements.</span></span> <span data-ttu-id="a2065-167">O exemplo a seguir demonstra como compartilhar dados entre vários de tamanho de linha e coluna <xref:System.Windows.Controls.Grid> elementos.</span><span class="sxs-lookup"><span data-stu-id="a2065-167">The following example demonstrates how to share column and row sizing data between multiple <xref:System.Windows.Controls.Grid> elements.</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="a2065-168">**Observação** para o exemplo de código completo, consulte [compartilhar propriedades de dimensionamento entre grades](../controls/how-to-share-sizing-properties-between-grids.md)</span><span class="sxs-lookup"><span data-stu-id="a2065-168">**Note** For the complete code sample, see [Share Sizing Properties Between Grids](../controls/how-to-share-sizing-properties-between-grids.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2065-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2065-169">See also</span></span>
- [<span data-ttu-id="a2065-170">Globalização para WPF</span><span class="sxs-lookup"><span data-stu-id="a2065-170">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="a2065-171">Usar layout automático para criar um botão</span><span class="sxs-lookup"><span data-stu-id="a2065-171">Use Automatic Layout to Create a Button</span></span>](how-to-use-automatic-layout-to-create-a-button.md)
- [<span data-ttu-id="a2065-172">Usar uma grade para layout automático</span><span class="sxs-lookup"><span data-stu-id="a2065-172">Use a Grid for Automatic Layout</span></span>](how-to-use-a-grid-for-automatic-layout.md)
