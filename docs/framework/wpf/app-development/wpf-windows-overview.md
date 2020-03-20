---
title: Visão geral do Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], displaying content via
- XAML pages [WPF], displaying
- content [WPF], displaying via XAML
- window objects [WPF]
- hosting [WPF], applications
- managing windows [WPF]
- dialog boxes [WPF]
- Page object [WPF]
- NavigationWindow objects [WPF]
- applications [WPF], hosting
- content [WPF], displaying
- events [WPF]
- content [WPF], displaying via procedural code
- modal windows [WPF]
- procedural code [WPF], displaying content via
- displaying content via procedural code [WPF]
- window management [WPF]
- displaying content [WPF]
- window events [WPF]
- windows [WPF]
- modal dialog boxes [WPF]
- displaying XAML pages [WPF]
ms.assetid: 737d04ec-8861-46c3-8d44-fa11d3528d23
ms.openlocfilehash: b06afb56f43a874815cf9f679f1f7fefbdfd4565
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145534"
---
# <a name="wpf-windows-overview"></a><span data-ttu-id="ee49f-102">Visão geral do WPF do Windows</span><span class="sxs-lookup"><span data-stu-id="ee49f-102">WPF Windows Overview</span></span>
<span data-ttu-id="ee49f-103">Os usuários interagem com aplicativos autônomos da Windows Presentation Foundation (WPF) através do windows.</span><span class="sxs-lookup"><span data-stu-id="ee49f-103">Users interact with Windows Presentation Foundation (WPF) standalone applications through windows.</span></span> <span data-ttu-id="ee49f-104">O objetivo principal de uma janela é hospedar conteúdo que visualiza dados e permite aos usuários interagir com os dados.</span><span class="sxs-lookup"><span data-stu-id="ee49f-104">The primary purpose of a window is to host content that visualizes data and enables users to interact with data.</span></span> <span data-ttu-id="ee49f-105">Aplicativos WPF autônomos fornecem suas próprias janelas usando a <xref:System.Windows.Window> classe.</span><span class="sxs-lookup"><span data-stu-id="ee49f-105">Standalone WPF applications provide their own windows by using the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="ee49f-106">Este tópico <xref:System.Windows.Window> introduz antes de cobrir os fundamentos da criação e gerenciamento de janelas em aplicativos autônomos.</span><span class="sxs-lookup"><span data-stu-id="ee49f-106">This topic introduces <xref:System.Windows.Window> before covering the fundamentals of creating and managing windows in standalone applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee49f-107">Os aplicativos WPF hospedados no navegador, incluindo xbaps (xbaps) e páginas soltas, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] não fornecem suas próprias janelas.</span><span class="sxs-lookup"><span data-stu-id="ee49f-107">Browser-hosted WPF applications, including XAML browser applications (XBAPs) and loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pages, don't provide their own windows.</span></span> <span data-ttu-id="ee49f-108">Em vez disso, eles estão hospedados em janelas fornecidas pelo Windows Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="ee49f-108">Instead, they are hosted in windows provided by Windows Internet Explorer.</span></span> <span data-ttu-id="ee49f-109">Consulte [a visão geral dos aplicativos do navegador WPF XAML](wpf-xaml-browser-applications-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ee49f-109">See [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a><span data-ttu-id="ee49f-110">A classe Window</span><span class="sxs-lookup"><span data-stu-id="ee49f-110">The Window Class</span></span>  
 <span data-ttu-id="ee49f-111">A figura a seguir ilustra as partes constituintes de uma janela:</span><span class="sxs-lookup"><span data-stu-id="ee49f-111">The following figure illustrates the constituent parts of a window:</span></span>  
  
 ![Captura de tela que mostra elementos da janela.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 <span data-ttu-id="ee49f-113">Uma janela é dividida em duas áreas: a área de não cliente e a área de cliente.</span><span class="sxs-lookup"><span data-stu-id="ee49f-113">A window is divided into two areas: the non-client area and client area.</span></span>  
  
 <span data-ttu-id="ee49f-114">A *área não-cliente* de uma janela é implementada pelo WPF e inclui as partes de uma janela que são comuns à maioria das janelas, incluindo as seguintes:</span><span class="sxs-lookup"><span data-stu-id="ee49f-114">The *non-client area* of a window is implemented by WPF and includes the parts of a window that are common to most windows, including the following:</span></span>  
  
- <span data-ttu-id="ee49f-115">Uma borda.</span><span class="sxs-lookup"><span data-stu-id="ee49f-115">A border.</span></span>  
  
- <span data-ttu-id="ee49f-116">Uma barra de título.</span><span class="sxs-lookup"><span data-stu-id="ee49f-116">A title bar.</span></span>  
  
- <span data-ttu-id="ee49f-117">Um ícone.</span><span class="sxs-lookup"><span data-stu-id="ee49f-117">An icon.</span></span>  
  
- <span data-ttu-id="ee49f-118">Botões Minimizar, Maximizar e Restaurar.</span><span class="sxs-lookup"><span data-stu-id="ee49f-118">Minimize, Maximize, and Restore buttons.</span></span>  
  
- <span data-ttu-id="ee49f-119">Um botão Fechar.</span><span class="sxs-lookup"><span data-stu-id="ee49f-119">A Close button.</span></span>  
  
- <span data-ttu-id="ee49f-120">Um menu Sistema com itens de menu que permitem aos usuários minimizar, maximizar, restaurar, mover, redimensionar e fechar uma janela.</span><span class="sxs-lookup"><span data-stu-id="ee49f-120">A System menu with menu items that allow users to minimize, maximize, restore, move, resize, and close a window.</span></span>  
  
 <span data-ttu-id="ee49f-121">A *área cliente* de uma janela é a área dentro da área não cliente de uma janela e é usada por desenvolvedores para adicionar conteúdo específico de aplicativos, como barras de menu, barras de ferramentas e controles.</span><span class="sxs-lookup"><span data-stu-id="ee49f-121">The *client area* of a window is the area within a window's non-client area and is used by developers to add application-specific content, such as menu bars, tool bars, and controls.</span></span>  
  
 <span data-ttu-id="ee49f-122">No WPF, uma janela é <xref:System.Windows.Window> encapsulada pela classe que você usa para fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ee49f-122">In WPF, a window is encapsulated by the <xref:System.Windows.Window> class that you use to do the following:</span></span>  
  
- <span data-ttu-id="ee49f-123">Exibir uma janela.</span><span class="sxs-lookup"><span data-stu-id="ee49f-123">Display a window.</span></span>  
  
- <span data-ttu-id="ee49f-124">Configurar o tamanho, posição e aparência de uma janela.</span><span class="sxs-lookup"><span data-stu-id="ee49f-124">Configure the size, position, and appearance of a window.</span></span>  
  
- <span data-ttu-id="ee49f-125">Conteúdo específico do aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="ee49f-125">Host application-specific content.</span></span>  
  
- <span data-ttu-id="ee49f-126">Gerenciar o tempo de vida de uma janela.</span><span class="sxs-lookup"><span data-stu-id="ee49f-126">Manage the lifetime of a window.</span></span>  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a><span data-ttu-id="ee49f-127">Implementar uma janela</span><span class="sxs-lookup"><span data-stu-id="ee49f-127">Implementing a Window</span></span>  
 <span data-ttu-id="ee49f-128">A implementação de uma janela típica compreende tanto a aparência quanto o comportamento, onde *a aparência* define como uma janela olha para os usuários e o *comportamento* define a forma como uma janela funciona à medida que os usuários interagem com ela.</span><span class="sxs-lookup"><span data-stu-id="ee49f-128">The implementation of a typical window comprises both appearance and behavior, where *appearance* defines how a window looks to users and *behavior* defines the way a window functions as users interact with it.</span></span> <span data-ttu-id="ee49f-129">No WPF, você pode implementar a aparência e [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] o comportamento de uma janela usando código ou marcação.</span><span class="sxs-lookup"><span data-stu-id="ee49f-129">In WPF, you can implement the appearance and behavior of a window using either code or [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 <span data-ttu-id="ee49f-130">Em geral, no entanto, o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aparecimento de uma janela é implementado usando marcação, e seu comportamento é implementado usando código-atrás, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ee49f-130">In general, however, the appearance of a window is implemented using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and its behavior is implemented using code-behind, as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 <span data-ttu-id="ee49f-131">Para habilitar um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de marcação e um arquivo de código para trabalhar em conjunto, são necessários os seguintes:</span><span class="sxs-lookup"><span data-stu-id="ee49f-131">To enable a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup file and code-behind file to work together, the following are required:</span></span>  
  
- <span data-ttu-id="ee49f-132">Na marcação, `Window` o elemento `x:Class` deve incluir o atributo.</span><span class="sxs-lookup"><span data-stu-id="ee49f-132">In markup, the `Window` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="ee49f-133">Quando o aplicativo é construído, a existência do arquivo `x:Class` de marcação faz `partial` com que o <xref:System.Windows.Window> Microsoft build engine (MSBuild) crie uma classe que deriva e tenha o nome especificado pelo atributo. `x:Class`</span><span class="sxs-lookup"><span data-stu-id="ee49f-133">When the application is built, the existence of `x:Class` in the markup file causes Microsoft build engine (MSBuild) to create a `partial` class that derives from <xref:System.Windows.Window> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="ee49f-134">Isso requer a adição de uma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] declaração de `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` namespace XML para o esquema ( ).</span><span class="sxs-lookup"><span data-stu-id="ee49f-134">This requires the addition of an XML namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="ee49f-135">A `partial` classe gerada `InitializeComponent` implementa o método, que é chamado para registrar os eventos e definir as propriedades que são implementadas na marcação.</span><span class="sxs-lookup"><span data-stu-id="ee49f-135">The generated `partial` class implements the `InitializeComponent` method, which is called to register the events and set the properties that are implemented in markup.</span></span>  
  
- <span data-ttu-id="ee49f-136">No code-behind, a classe `partial` deve ser uma classe com `x:Class` o mesmo nome especificado pelo <xref:System.Windows.Window>atributo na marcação, e deve derivar de .</span><span class="sxs-lookup"><span data-stu-id="ee49f-136">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Window>.</span></span> <span data-ttu-id="ee49f-137">Isso permite que o arquivo de `partial` código traseiro seja associado à classe gerada para o arquivo de marcação quando o aplicativo é construído (consulte [Construindo um aplicativo WPF](building-a-wpf-application-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="ee49f-137">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](building-a-wpf-application-wpf.md)).</span></span>  
  
- <span data-ttu-id="ee49f-138">No código atrás, <xref:System.Windows.Window> a classe deve implementar `InitializeComponent` um construtor que chame o método.</span><span class="sxs-lookup"><span data-stu-id="ee49f-138">In code-behind, the <xref:System.Windows.Window> class must implement a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="ee49f-139">`InitializeComponent`é implementado pela classe gerada `partial` do arquivo de marcação para registrar eventos e definir propriedades definidas na marcação.</span><span class="sxs-lookup"><span data-stu-id="ee49f-139">`InitializeComponent` is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee49f-140">Quando você adiciona <xref:System.Windows.Window> um novo ao seu <xref:System.Windows.Window> projeto usando o Visual Studio, o é implementado usando marcação e código atrás, e inclui a configuração necessária para criar a associação entre a marcação e os arquivos de código-atrás como descrito aqui.</span><span class="sxs-lookup"><span data-stu-id="ee49f-140">When you add a new <xref:System.Windows.Window> to your project by using Visual Studio, the <xref:System.Windows.Window> is implemented using both markup and code-behind, and includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>  
  
 <span data-ttu-id="ee49f-141">Com essa configuração em vigor, você pode se [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] concentrar em definir a aparência da janela na marcação e implementar seu comportamento no code-behind.</span><span class="sxs-lookup"><span data-stu-id="ee49f-141">With this configuration in place, you can focus on defining the appearance of the window in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and implementing its behavior in code-behind.</span></span> <span data-ttu-id="ee49f-142">O exemplo a seguir mostra uma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] janela com um botão, implementada na <xref:System.Windows.Controls.Primitives.ButtonBase.Click> marcação, e um manipulador de eventos para o evento do botão, implementado no code-behind.</span><span class="sxs-lookup"><span data-stu-id="ee49f-142">The following example shows a window with a button, implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, implemented in code-behind.</span></span>  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a><span data-ttu-id="ee49f-143">Configurar uma definição de janela para MSBuild</span><span class="sxs-lookup"><span data-stu-id="ee49f-143">Configuring a Window Definition for MSBuild</span></span>  
 <span data-ttu-id="ee49f-144">A forma como você implementa sua janela determina como ela está configurada para o MSBuild.</span><span class="sxs-lookup"><span data-stu-id="ee49f-144">How you implement your window determines how it is configured for MSBuild.</span></span> <span data-ttu-id="ee49f-145">Para uma janela definida [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usando marcação e código atrás:</span><span class="sxs-lookup"><span data-stu-id="ee49f-145">For a window that is defined using both [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind:</span></span>  
  
- <span data-ttu-id="ee49f-146">Os arquivos de marcação XAML `Page` são configurados como itens do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="ee49f-146">XAML markup files are configured as MSBuild `Page` items.</span></span>  
  
- <span data-ttu-id="ee49f-147">Os arquivos por trás do código `Compile` são configurados como itens do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="ee49f-147">Code-behind files are configured as MSBuild `Compile` items.</span></span>  
  
 <span data-ttu-id="ee49f-148">Isso é mostrado no seguinte arquivo de projeto MSBuild.</span><span class="sxs-lookup"><span data-stu-id="ee49f-148">This is shown in the following MSBuild project file.</span></span>  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 <span data-ttu-id="ee49f-149">Para obter informações sobre a construção de aplicativos WPF, consulte [Construindo um aplicativo WPF](building-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="ee49f-149">For information about building WPF applications, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a><span data-ttu-id="ee49f-150">Tempo de vida de janela</span><span class="sxs-lookup"><span data-stu-id="ee49f-150">Window Lifetime</span></span>  
 <span data-ttu-id="ee49f-151">Assim como com qualquer classe, uma janela tem um tempo de vida que começa quando ela é instanciada pela primeira vez, fato após o qual ela é aberta, ativada e desativada e, eventualmente, fechada.</span><span class="sxs-lookup"><span data-stu-id="ee49f-151">As with any class, a window has a lifetime that begins when it is first instantiated, after which it is opened, activated and deactivated, and eventually closed.</span></span>  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a><span data-ttu-id="ee49f-152">Abrir uma janela</span><span class="sxs-lookup"><span data-stu-id="ee49f-152">Opening a Window</span></span>  
 <span data-ttu-id="ee49f-153">Para abrir uma janela, você primeiro cria uma instância dela, o que é demonstrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ee49f-153">To open a window, you first create an instance of it, which is demonstrated in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 <span data-ttu-id="ee49f-154">Neste exemplo, `MarkupAndCodeBehindWindow` o é instanciado quando o aplicativo <xref:System.Windows.Application.Startup> é iniciado, o que ocorre quando o evento é levantado.</span><span class="sxs-lookup"><span data-stu-id="ee49f-154">In this example, the `MarkupAndCodeBehindWindow` is instantiated when the application starts, which occurs when the <xref:System.Windows.Application.Startup> event is raised.</span></span>  
  
 <span data-ttu-id="ee49f-155">Quando uma janela é instanciada, uma referência a ela é automaticamente adicionada <xref:System.Windows.Application> a uma <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>lista de janelas que é gerenciada pelo objeto (ver ).</span><span class="sxs-lookup"><span data-stu-id="ee49f-155">When a window is instantiated, a reference to it is automatically added to a list of windows that is managed by the <xref:System.Windows.Application> object (see <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="ee49f-156">Além disso, a primeira janela a ser instancinada <xref:System.Windows.Application> é, por padrão, definida como a janela principal do aplicativo (ver <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="ee49f-156">Additionally, the first window to be instantiated is, by default, set by <xref:System.Windows.Application> as the main application window (see <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="ee49f-157">A janela é finalmente <xref:System.Windows.Window.Show%2A> aberta chamando o método; o resultado é mostrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="ee49f-157">The window is finally opened by calling the <xref:System.Windows.Window.Show%2A> method; the result is shown in the following figure.</span></span>  
  
 ![Uma janela aberta chamando Window.Show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 <span data-ttu-id="ee49f-159">Uma janela que é <xref:System.Windows.Window.Show%2A> aberta por chamada é uma janela modeless, o que significa que o aplicativo opera em um modo que permite que os usuários ativem outras janelas no mesmo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ee49f-159">A window that is opened by calling <xref:System.Windows.Window.Show%2A> is a modeless window, which means that the application operates in a mode that allows users to activate other windows in the same application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee49f-160"><xref:System.Windows.Window.ShowDialog%2A>é chamado para abrir janelas, como caixas de diálogo modally.</span><span class="sxs-lookup"><span data-stu-id="ee49f-160"><xref:System.Windows.Window.ShowDialog%2A> is called to open windows such as dialog boxes modally.</span></span> <span data-ttu-id="ee49f-161">Consulte [a visão geral das caixas de diálogo](dialog-boxes-overview.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="ee49f-161">See [Dialog Boxes Overview](dialog-boxes-overview.md) for more information.</span></span>  
  
 <span data-ttu-id="ee49f-162">Quando <xref:System.Windows.Window.Show%2A> é chamada, uma janela executa o trabalho de inicialização antes de ser mostrado para estabelecer uma infra-estrutura que lhe permita receber a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="ee49f-162">When <xref:System.Windows.Window.Show%2A> is called, a window performs initialization work before it is shown to establish infrastructure that allows it to receive user input.</span></span> <span data-ttu-id="ee49f-163">Quando a janela é <xref:System.Windows.Window.SourceInitialized> inicializada, o evento é levantado e a janela é mostrada.</span><span class="sxs-lookup"><span data-stu-id="ee49f-163">When the window is initialized, the <xref:System.Windows.Window.SourceInitialized> event is raised and the window is shown.</span></span>  
  
 <span data-ttu-id="ee49f-164">Como um <xref:System.Windows.Application.StartupUri%2A> atalho, pode ser definido para especificar a primeira janela aberta automaticamente quando um aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="ee49f-164">As a shortcut, <xref:System.Windows.Application.StartupUri%2A> can be set to specify the first window that is opened automatically when an application starts.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 <span data-ttu-id="ee49f-165">Quando o aplicativo é iniciado, a <xref:System.Windows.Application.StartupUri%2A> janela especificada pelo valor de é aberta modelessly; internamente, a janela é <xref:System.Windows.Window.Show%2A> aberta chamando seu método.</span><span class="sxs-lookup"><span data-stu-id="ee49f-165">When the application starts, the window specified by the value of <xref:System.Windows.Application.StartupUri%2A> is opened modelessly; internally, the window is opened by calling its <xref:System.Windows.Window.Show%2A> method.</span></span>  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a><span data-ttu-id="ee49f-166">Posse de janela</span><span class="sxs-lookup"><span data-stu-id="ee49f-166">Window Ownership</span></span>  
 <span data-ttu-id="ee49f-167">Uma janela que é <xref:System.Windows.Window.Show%2A> aberta usando o método não tem uma relação implícita com a janela que o criou; os usuários podem interagir com qualquer janela independentemente da outra, o que significa que qualquer janela pode fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ee49f-167">A window that is opened by using the <xref:System.Windows.Window.Show%2A> method does not have an implicit relationship with the window that created it; users can interact with either window independently of the other, which means that either window can do the following:</span></span>  
  
- <span data-ttu-id="ee49f-168">Cubra a outra (a menos <xref:System.Windows.Window.Topmost%2A> que uma `true`das janelas tenha sua propriedade definida para ).</span><span class="sxs-lookup"><span data-stu-id="ee49f-168">Cover the other (unless one of the windows has its <xref:System.Windows.Window.Topmost%2A> property set to `true`).</span></span>  
  
- <span data-ttu-id="ee49f-169">Ser minimizada, maximizada e restaurada sem afetar a outra.</span><span class="sxs-lookup"><span data-stu-id="ee49f-169">Be minimized, maximized, and restored without affecting the other.</span></span>  
  
 <span data-ttu-id="ee49f-170">Algumas janelas requerem uma relação com a janela que as abre.</span><span class="sxs-lookup"><span data-stu-id="ee49f-170">Some windows require a relationship with the window that opens them.</span></span> <span data-ttu-id="ee49f-171">Por exemplo, um aplicativo IDE (Integrated Development Environment, ambiente de desenvolvimento integrado) pode abrir janelas de propriedade e janelas de ferramentas cujo comportamento típico é cobrir a janela que as cria.</span><span class="sxs-lookup"><span data-stu-id="ee49f-171">For example, an Integrated Development Environment (IDE) application may open property windows and tool windows whose typical behavior is to cover the window that creates them.</span></span> <span data-ttu-id="ee49f-172">Além disso, janelas desse tipo devem sempre fechar, minimizar, maximizar e restaurar em conjunto com a janela que as criou.</span><span class="sxs-lookup"><span data-stu-id="ee49f-172">Furthermore, such windows should always close, minimize, maximize, and restore in concert with the window that created them.</span></span> <span data-ttu-id="ee49f-173">Tal relação pode ser estabelecida fazendo com que uma janela <xref:System.Windows.Window.Owner%2A> *possua* outra, e é alcançada definindo a propriedade da janela *própria* com uma referência à janela do *proprietário.*</span><span class="sxs-lookup"><span data-stu-id="ee49f-173">Such a relationship can be established by making one window *own* another, and is achieved by setting the <xref:System.Windows.Window.Owner%2A> property of the *owned window* with a reference to the *owner window*.</span></span> <span data-ttu-id="ee49f-174">Isso é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ee49f-174">This is shown in the following example.</span></span>  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 <span data-ttu-id="ee49f-175">Depois que a posse é estabelecida:</span><span class="sxs-lookup"><span data-stu-id="ee49f-175">After ownership is established:</span></span>  
  
- <span data-ttu-id="ee49f-176">A janela de propriedade pode referenciar sua <xref:System.Windows.Window.Owner%2A> janela de proprietário inspecionando o valor de sua propriedade.</span><span class="sxs-lookup"><span data-stu-id="ee49f-176">The owned window can reference its owner window by inspecting the value of its <xref:System.Windows.Window.Owner%2A> property.</span></span>  
  
- <span data-ttu-id="ee49f-177">A janela do proprietário pode descobrir todas as janelas <xref:System.Windows.Window.OwnedWindows%2A> que possui inspecionando o valor de sua propriedade.</span><span class="sxs-lookup"><span data-stu-id="ee49f-177">The owner window can discover all the windows it owns by inspecting the value of its <xref:System.Windows.Window.OwnedWindows%2A> property.</span></span>  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a><span data-ttu-id="ee49f-178">Impedindo a ativação de janela</span><span class="sxs-lookup"><span data-stu-id="ee49f-178">Preventing Window Activation</span></span>  
 <span data-ttu-id="ee49f-179">Existem cenários em que as janelas não devem ser ativadas quando mostradas, como janelas de conversação de um aplicativo estilo mensageiro da Internet ou janelas de notificação de um aplicativo de e-mail.</span><span class="sxs-lookup"><span data-stu-id="ee49f-179">There are scenarios where windows should not be activated when shown, such as conversation windows of an Internet messenger-style application or notification windows of an email application.</span></span>  
  
 <span data-ttu-id="ee49f-180">Se o aplicativo tiver uma janela que não deve ser <xref:System.Windows.Window.ShowActivated%2A> ativada `false` quando <xref:System.Windows.Window.Show%2A> mostrada, você pode definir sua propriedade antes de chamar o método pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="ee49f-180">If your application has a window that shouldn't be activated when shown, you can set its <xref:System.Windows.Window.ShowActivated%2A> property to `false` before calling the <xref:System.Windows.Window.Show%2A> method for the first time.</span></span> <span data-ttu-id="ee49f-181">Como consequência disso:</span><span class="sxs-lookup"><span data-stu-id="ee49f-181">As a consequence:</span></span>  
  
- <span data-ttu-id="ee49f-182">A janela não é ativada.</span><span class="sxs-lookup"><span data-stu-id="ee49f-182">The window is not activated.</span></span>  
  
- <span data-ttu-id="ee49f-183">O evento <xref:System.Windows.Window.Activated> da janela não está levantado.</span><span class="sxs-lookup"><span data-stu-id="ee49f-183">The window's <xref:System.Windows.Window.Activated> event is not raised.</span></span>  
  
- <span data-ttu-id="ee49f-184">A janela ativada no momento permanece ativada.</span><span class="sxs-lookup"><span data-stu-id="ee49f-184">The currently activated window remains activated.</span></span>  
  
 <span data-ttu-id="ee49f-185">A janela se tornará ativada, no entanto, assim que o usuário ativá-la clicando na área de cliente ou então na área não cliente.</span><span class="sxs-lookup"><span data-stu-id="ee49f-185">The window will become activated, however, as soon as the user activates it by clicking either the client or non-client area.</span></span> <span data-ttu-id="ee49f-186">Nesse caso:</span><span class="sxs-lookup"><span data-stu-id="ee49f-186">In this case:</span></span>  
  
- <span data-ttu-id="ee49f-187">A janela é ativada.</span><span class="sxs-lookup"><span data-stu-id="ee49f-187">The window is activated.</span></span>  
  
- <span data-ttu-id="ee49f-188">O evento <xref:System.Windows.Window.Activated> da janela foi levantado.</span><span class="sxs-lookup"><span data-stu-id="ee49f-188">The window's <xref:System.Windows.Window.Activated> event is raised.</span></span>  
  
- <span data-ttu-id="ee49f-189">A janela ativada anteriormente é desativada.</span><span class="sxs-lookup"><span data-stu-id="ee49f-189">The previously activated window is deactivated.</span></span>  
  
- <span data-ttu-id="ee49f-190">As janelas <xref:System.Windows.Window.Deactivated> e <xref:System.Windows.Window.Activated> os eventos são posteriormente levantados como esperado em resposta às ações do usuário.</span><span class="sxs-lookup"><span data-stu-id="ee49f-190">The window's <xref:System.Windows.Window.Deactivated> and <xref:System.Windows.Window.Activated> events are subsequently raised as expected in response to user actions.</span></span>  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a><span data-ttu-id="ee49f-191">Ativação de janela</span><span class="sxs-lookup"><span data-stu-id="ee49f-191">Window Activation</span></span>  
 <span data-ttu-id="ee49f-192">Quando uma janela é aberta pela primeira vez, ela <xref:System.Windows.Window.ShowActivated%2A> se `false`torna a janela ativa (a menos que seja mostrada com set para ).</span><span class="sxs-lookup"><span data-stu-id="ee49f-192">When a window is first opened, it becomes the active window (unless it is shown with <xref:System.Windows.Window.ShowActivated%2A> set to `false`).</span></span> <span data-ttu-id="ee49f-193">A *janela ativa* é a janela que está capturando a entrada do usuário no momento, como traçados de teclas e cliques do mouse.</span><span class="sxs-lookup"><span data-stu-id="ee49f-193">The *active window* is the window that is currently capturing user input, such as key strokes and mouse clicks.</span></span> <span data-ttu-id="ee49f-194">Quando uma janela se torna <xref:System.Windows.Window.Activated> ativa, ela levanta o evento.</span><span class="sxs-lookup"><span data-stu-id="ee49f-194">When a window becomes active, it raises the <xref:System.Windows.Window.Activated> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee49f-195">Quando uma janela é <xref:System.Windows.FrameworkElement.Loaded> aberta <xref:System.Windows.Window.ContentRendered> pela primeira vez, <xref:System.Windows.Window.Activated> os eventos e eventos são levantados somente após o evento ser levantado.</span><span class="sxs-lookup"><span data-stu-id="ee49f-195">When a window is first opened, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.Window.ContentRendered> events are raised only after the <xref:System.Windows.Window.Activated> event is raised.</span></span> <span data-ttu-id="ee49f-196">Com isso em mente, uma janela pode <xref:System.Windows.Window.ContentRendered> ser efetivamente considerada aberta quando é levantada.</span><span class="sxs-lookup"><span data-stu-id="ee49f-196">With this in mind, a window can effectively be considered opened when <xref:System.Windows.Window.ContentRendered> is raised.</span></span>  
  
 <span data-ttu-id="ee49f-197">Depois que uma janela fica ativa, um usuário pode ativar outra janela no mesmo aplicativo ou então ativar outro aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ee49f-197">After a window becomes active, a user can activate another window in the same application, or activate another application.</span></span> <span data-ttu-id="ee49f-198">Quando isso acontece, a janela ativa atualmente <xref:System.Windows.Window.Deactivated> fica desativada e levanta o evento.</span><span class="sxs-lookup"><span data-stu-id="ee49f-198">When that happens, the currently active window becomes deactivated and raises the <xref:System.Windows.Window.Deactivated> event.</span></span> <span data-ttu-id="ee49f-199">Da mesma forma, quando o usuário seleciona uma janela atualmente <xref:System.Windows.Window.Activated> desativada, a janela fica ativa novamente e é levantada.</span><span class="sxs-lookup"><span data-stu-id="ee49f-199">Likewise, when the user selects a currently deactivated window, the window becomes active again and <xref:System.Windows.Window.Activated> is raised.</span></span>  
  
 <span data-ttu-id="ee49f-200">Uma razão comum para lidar <xref:System.Windows.Window.Activated> e <xref:System.Windows.Window.Deactivated> é ativar e desativar funcionalidades que só podem ser executadas quando uma janela está ativa.</span><span class="sxs-lookup"><span data-stu-id="ee49f-200">One common reason to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> is to enable and disable functionality that can only run when a window is active.</span></span> <span data-ttu-id="ee49f-201">Por exemplo, algumas janelas exibem conteúdo interativo que requer constante atenção ou entrada do usuário, incluindo players de vídeo e jogos.</span><span class="sxs-lookup"><span data-stu-id="ee49f-201">For example, some windows display interactive content that requires constant user input or attention, including games and video players.</span></span> <span data-ttu-id="ee49f-202">O exemplo a seguir é um reprodutor <xref:System.Windows.Window.Activated> <xref:System.Windows.Window.Deactivated> de vídeo simplificado que demonstra como lidar e implementar esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="ee49f-202">The following example is a simplified video player that demonstrates how to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> to implement this behavior.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 <span data-ttu-id="ee49f-203">Outros tipos de aplicativos podem ainda executar códigos em segundo plano quando uma janela é desativada.</span><span class="sxs-lookup"><span data-stu-id="ee49f-203">Other types of applications may still run code in the background when a window is deactivated.</span></span> <span data-ttu-id="ee49f-204">Por exemplo, um cliente de email pode continuar a sondagem do servidor de email enquanto o usuário está usando outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ee49f-204">For example, a mail client may continue polling the mail server while the user is using other applications.</span></span> <span data-ttu-id="ee49f-205">Aplicativos como esses geralmente apresentam comportamento diferente ou adicional enquanto a janela principal está desativada.</span><span class="sxs-lookup"><span data-stu-id="ee49f-205">Applications like these often provide different or additional behavior while the main window is deactivated.</span></span> <span data-ttu-id="ee49f-206">Em relação ao programa de email, isso pode significar tanto adicionar o novo item de email à caixa de entrada quanto adicionar um ícone de notificação à bandeja do sistema.</span><span class="sxs-lookup"><span data-stu-id="ee49f-206">With respect to the mail program, this may mean both adding the new mail item to the inbox and adding a notification icon to the system tray.</span></span> <span data-ttu-id="ee49f-207">Um ícone de notificação só precisa ser exibido quando a janela do e-mail não estiver ativa, o que pode ser determinado inspecionando a <xref:System.Windows.Window.IsActive%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="ee49f-207">A notification icon need only be displayed when the mail window isn't active, which can be determined by inspecting the <xref:System.Windows.Window.IsActive%2A> property.</span></span>  
  
 <span data-ttu-id="ee49f-208">Se uma tarefa em segundo plano for concluída, uma janela <xref:System.Windows.Window.Activate%2A> pode querer notificar o usuário com mais urgência, chamando o método.</span><span class="sxs-lookup"><span data-stu-id="ee49f-208">If a background task completes, a window may want to notify the user more urgently by calling <xref:System.Windows.Window.Activate%2A> method.</span></span> <span data-ttu-id="ee49f-209">Se o usuário estiver interagindo com <xref:System.Windows.Window.Activate%2A> outro aplicativo ativado quando for chamado, o botão da barra de tarefas da janela será acionado.</span><span class="sxs-lookup"><span data-stu-id="ee49f-209">If the user is interacting with another application activated when <xref:System.Windows.Window.Activate%2A> is called, the window's taskbar button flashes.</span></span> <span data-ttu-id="ee49f-210">Se um usuário estiver interagindo com <xref:System.Windows.Window.Activate%2A> o aplicativo atual, a chamada levará a janela para o primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="ee49f-210">If a user is interacting with the current application, calling <xref:System.Windows.Window.Activate%2A> will bring the window to the foreground.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee49f-211">Você pode lidar com a <xref:System.Windows.Application.Activated?displayProperty=nameWithType> <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> ativação do escopo do aplicativo usando os eventos e eventos.</span><span class="sxs-lookup"><span data-stu-id="ee49f-211">You can handle application-scope activation using the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> and <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> events.</span></span>  
  
<a name="Closing_a_Window"></a>
### <a name="closing-a-window"></a><span data-ttu-id="ee49f-212">Fechar uma janela</span><span class="sxs-lookup"><span data-stu-id="ee49f-212">Closing a Window</span></span>  
 <span data-ttu-id="ee49f-213">O fim da vida de uma janela se começa a se aproximar quando um usuário a fecha.</span><span class="sxs-lookup"><span data-stu-id="ee49f-213">The life of a window starts coming to an end when a user closes it.</span></span> <span data-ttu-id="ee49f-214">Uma janela pode ser fechada pelo uso de elementos na área de não cliente, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ee49f-214">A window can be closed by using elements in the non-client area, including the following:</span></span>  
  
- <span data-ttu-id="ee49f-215">O item **Fechar** do menu **Sistema.**</span><span class="sxs-lookup"><span data-stu-id="ee49f-215">The **Close** item of the **System** menu.</span></span>  
  
- <span data-ttu-id="ee49f-216">Pressionar ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="ee49f-216">Pressing ALT+F4.</span></span>  
  
- <span data-ttu-id="ee49f-217">Pressionando o botão **Fechar.**</span><span class="sxs-lookup"><span data-stu-id="ee49f-217">Pressing the **Close** button.</span></span>  
  
 <span data-ttu-id="ee49f-218">Você pode fornecer mecanismos adicionais à área de cliente para fechar uma janela, sendo que os mais comuns deles incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="ee49f-218">You can provide additional mechanisms to the client area to close a window, the more common of which include the following:</span></span>  
  
- <span data-ttu-id="ee49f-219">Um item **Sair** no menu **Arquivo,** normalmente para janelas principais de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ee49f-219">An **Exit** item in the **File** menu, typically for main application windows.</span></span>  
  
- <span data-ttu-id="ee49f-220">Um item **Fechar** no menu **Arquivo,** normalmente em uma janela de aplicativo secundária.</span><span class="sxs-lookup"><span data-stu-id="ee49f-220">A **Close** item in the **File** menu, typically on a secondary application window.</span></span>  
  
- <span data-ttu-id="ee49f-221">Um botão **Cancelar,** normalmente em uma caixa de diálogo modal.</span><span class="sxs-lookup"><span data-stu-id="ee49f-221">A **Cancel** button, typically on a modal dialog box.</span></span>  
  
- <span data-ttu-id="ee49f-222">Um botão **Fechar,** normalmente em uma caixa de diálogo modeless.</span><span class="sxs-lookup"><span data-stu-id="ee49f-222">A **Close** button, typically on a modeless dialog box.</span></span>  
  
 <span data-ttu-id="ee49f-223">Para fechar uma janela em resposta a um desses <xref:System.Windows.Window.Close%2A> mecanismos personalizados, você precisa chamar o método.</span><span class="sxs-lookup"><span data-stu-id="ee49f-223">To close a window in response to one of these custom mechanisms, you need to call the <xref:System.Windows.Window.Close%2A> method.</span></span> <span data-ttu-id="ee49f-224">O exemplo a seguir implementa a capacidade de fechar uma janela escolhendo a **saída** no menu **Arquivo.**</span><span class="sxs-lookup"><span data-stu-id="ee49f-224">The following example implements the ability to close a window by choosing the **Exit** on the **File** menu.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 <span data-ttu-id="ee49f-225">Quando uma janela fecha, ela <xref:System.Windows.Window.Closing> levanta <xref:System.Windows.Window.Closed>dois eventos: e .</span><span class="sxs-lookup"><span data-stu-id="ee49f-225">When a window closes, it raises two events: <xref:System.Windows.Window.Closing> and <xref:System.Windows.Window.Closed>.</span></span>  
  
 <span data-ttu-id="ee49f-226"><xref:System.Windows.Window.Closing>é levantada antes que a janela feche, e fornece um mecanismo pelo qual o fechamento da janela pode ser evitado.</span><span class="sxs-lookup"><span data-stu-id="ee49f-226"><xref:System.Windows.Window.Closing> is raised before the window closes, and it provides a mechanism by which window closure can be prevented.</span></span> <span data-ttu-id="ee49f-227">Uma razão comum para evitar o fechamento da janela é caso o conteúdo da janela contenha dados modificados.</span><span class="sxs-lookup"><span data-stu-id="ee49f-227">One common reason to prevent window closure is if window content contains modified data.</span></span> <span data-ttu-id="ee49f-228">Nesta situação, <xref:System.Windows.Window.Closing> o evento pode ser tratado para determinar se os dados estão sujos e, se for o caso, perguntar ao usuário se deve continuar fechando a janela sem salvar os dados ou cancelar o fechamento da janela.</span><span class="sxs-lookup"><span data-stu-id="ee49f-228">In this situation, the <xref:System.Windows.Window.Closing> event can be handled to determine whether data is dirty and, if so, to ask the user whether to either continue closing the window without saving the data or to cancel window closure.</span></span> <span data-ttu-id="ee49f-229">O exemplo a seguir mostra os <xref:System.Windows.Window.Closing>principais aspectos do manuseio .</span><span class="sxs-lookup"><span data-stu-id="ee49f-229">The following example shows the key aspects of handling <xref:System.Windows.Window.Closing>.</span></span>  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <span data-ttu-id="ee49f-230">O <xref:System.Windows.Window.Closing> manipulador de <xref:System.ComponentModel.CancelEventArgs>eventos é aprovado `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> a , `true` que implementa a propriedade que você definiu para evitar que uma janela feche.</span><span class="sxs-lookup"><span data-stu-id="ee49f-230">The <xref:System.Windows.Window.Closing> event handler is passed a <xref:System.ComponentModel.CancelEventArgs>, which implements the `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property that you set to `true` to prevent a window from closing.</span></span>  
  
 <span data-ttu-id="ee49f-231">Se <xref:System.Windows.Window.Closing> não for manuseado, ou for manuseado, mas não cancelado, a janela será fechada.</span><span class="sxs-lookup"><span data-stu-id="ee49f-231">If <xref:System.Windows.Window.Closing> is not handled, or it is handled but not canceled, the window will close.</span></span> <span data-ttu-id="ee49f-232">Pouco antes de uma <xref:System.Windows.Window.Closed> janela realmente fechar, é levantada.</span><span class="sxs-lookup"><span data-stu-id="ee49f-232">Just before a window actually closes, <xref:System.Windows.Window.Closed> is raised.</span></span> <span data-ttu-id="ee49f-233">Neste ponto, uma janela não pode ser impedida de fechar.</span><span class="sxs-lookup"><span data-stu-id="ee49f-233">At this point, a window cannot be prevented from closing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee49f-234">Um aplicativo pode ser configurado para desligar automaticamente quando a <xref:System.Windows.Application.MainWindow%2A>janela principal do aplicativo fecha (veja) ou a última janela fecha.</span><span class="sxs-lookup"><span data-stu-id="ee49f-234">An application can be configured to shut down automatically when either the main application window closes (see <xref:System.Windows.Application.MainWindow%2A>) or the last window closes.</span></span> <span data-ttu-id="ee49f-235">Para obter detalhes, consulte <xref:System.Windows.Application.ShutdownMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee49f-235">For details, see <xref:System.Windows.Application.ShutdownMode%2A>.</span></span>  
  
 <span data-ttu-id="ee49f-236">Embora uma janela possa ser explicitamente fechada através de mecanismos fornecidos nas áreas não cliente e cliente, uma janela também pode ser implicitamente fechada como resultado de comportamento em outras partes do aplicativo ou Windows, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ee49f-236">While a window can be explicitly closed through mechanisms provided in the non-client and client areas, a window can also be implicitly closed as a result of behavior in other parts of the application or Windows, including the following:</span></span>  
  
- <span data-ttu-id="ee49f-237">Um usuário faz logoff ou desliga o Windows.</span><span class="sxs-lookup"><span data-stu-id="ee49f-237">A user logs off or shuts down Windows.</span></span>  
  
- <span data-ttu-id="ee49f-238">O dono de uma <xref:System.Windows.Window.Owner%2A>janela fecha (veja ).</span><span class="sxs-lookup"><span data-stu-id="ee49f-238">A window's owner closes (see <xref:System.Windows.Window.Owner%2A>).</span></span>  
  
- <span data-ttu-id="ee49f-239">A janela principal da <xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnMainWindowClose>aplicação está fechada e é .</span><span class="sxs-lookup"><span data-stu-id="ee49f-239">The main application window is closed and <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>  
  
- <span data-ttu-id="ee49f-240"><xref:System.Windows.Application.Shutdown%2A> é chamado.</span><span class="sxs-lookup"><span data-stu-id="ee49f-240"><xref:System.Windows.Application.Shutdown%2A> is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee49f-241">Uma janela não pode ser reaberta depois que é fechada.</span><span class="sxs-lookup"><span data-stu-id="ee49f-241">A window cannot be reopened after it is closed.</span></span>  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a><span data-ttu-id="ee49f-242">Eventos de tempo de vida da janela</span><span class="sxs-lookup"><span data-stu-id="ee49f-242">Window Lifetime Events</span></span>  
 <span data-ttu-id="ee49f-243">A ilustração a seguir mostra a seqüência dos principais eventos durante a vida de uma janela:</span><span class="sxs-lookup"><span data-stu-id="ee49f-243">The following illustration shows the sequence of the principal events in the lifetime of a window:</span></span>  
  
 ![Diagrama que mostra eventos na vida de uma janela.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 <span data-ttu-id="ee49f-245">A ilustração a seguir mostra a seqüência dos principais<xref:System.Windows.Window.ShowActivated%2A> eventos durante `false` a vida de uma janela que é mostrada sem ativação (é definida para antes da janela ser mostrada):</span><span class="sxs-lookup"><span data-stu-id="ee49f-245">The following illustration shows the sequence of the principal events in the lifetime of a window that is shown without activation (<xref:System.Windows.Window.ShowActivated%2A> is set to `false` before the window is shown):</span></span>  
  
 ![Diagrama que mostra eventos na vida de uma janela sem ativação.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a><span data-ttu-id="ee49f-247">Localização da janela</span><span class="sxs-lookup"><span data-stu-id="ee49f-247">Window Location</span></span>  
 <span data-ttu-id="ee49f-248">Enquanto uma janela estiver aberta, ela terá uma localização nas dimensões x e y em relação à área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ee49f-248">While a window is open, it has a location in the x and y dimensions relative to the desktop.</span></span> <span data-ttu-id="ee49f-249">Este local pode ser determinado <xref:System.Windows.Window.Left%2A> <xref:System.Windows.Window.Top%2A> inspecionando as propriedades e propriedades, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="ee49f-249">This location can be determined by inspecting the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties, respectively.</span></span> <span data-ttu-id="ee49f-250">Você pode definir essas propriedades para alterar o local da janela.</span><span class="sxs-lookup"><span data-stu-id="ee49f-250">You can set these properties to change the location of the window.</span></span>  
  
 <span data-ttu-id="ee49f-251">Você também pode especificar <xref:System.Windows.Window> a localização inicial de <xref:System.Windows.Window.WindowStartupLocation%2A> um quando ele <xref:System.Windows.WindowStartupLocation> aparece pela primeira vez definindo a propriedade com um dos seguintes valores de enumeração:</span><span class="sxs-lookup"><span data-stu-id="ee49f-251">You can also specify the initial location of a <xref:System.Windows.Window> when it first appears by setting the <xref:System.Windows.Window.WindowStartupLocation%2A> property with one of the following <xref:System.Windows.WindowStartupLocation> enumeration values:</span></span>  
  
- <span data-ttu-id="ee49f-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (padrão)</span><span class="sxs-lookup"><span data-stu-id="ee49f-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (default)</span></span>  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 <span data-ttu-id="ee49f-253">Se o local de <xref:System.Windows.WindowStartupLocation.Manual>inicialização <xref:System.Windows.Window.Left%2A> for <xref:System.Windows.Window.Top%2A> especificado como <xref:System.Windows.Window> , e as propriedades e não foram definidas, pedirá ao Windows que um local seja exibido.</span><span class="sxs-lookup"><span data-stu-id="ee49f-253">If the startup location is specified as <xref:System.Windows.WindowStartupLocation.Manual>, and the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties have not been set, <xref:System.Windows.Window> will ask Windows for a location to appear in.</span></span>  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a><span data-ttu-id="ee49f-254">Janela superior e ordem Z</span><span class="sxs-lookup"><span data-stu-id="ee49f-254">Topmost Windows and Z-Order</span></span>  
 <span data-ttu-id="ee49f-255">Além de ter uma localização x e y, uma janela também tem uma localização na dimensão z, que determina a posição vertical em relação a outras janelas.</span><span class="sxs-lookup"><span data-stu-id="ee49f-255">Besides having an x and y location, a window also has a location in the z dimension, which determines its vertical position with respect to other windows.</span></span> <span data-ttu-id="ee49f-256">Isso é conhecido como a ordem z da janela, e há dois tipos: ordem z normal e ordem z superior.</span><span class="sxs-lookup"><span data-stu-id="ee49f-256">This is known as the window's z-order, and there are two types: normal z-order and topmost z-order.</span></span> <span data-ttu-id="ee49f-257">A localização de uma janela na *ordem z normal* é determinada por estar ativa ou não.</span><span class="sxs-lookup"><span data-stu-id="ee49f-257">The location of a window in the *normal z-order* is determined by whether it is currently active or not.</span></span> <span data-ttu-id="ee49f-258">Por padrão, uma janela está localizada na ordem z normal.</span><span class="sxs-lookup"><span data-stu-id="ee49f-258">By default, a window is located in the normal z-order.</span></span> <span data-ttu-id="ee49f-259">A localização de uma janela na *ordem z superior* também é determinada por estar ativa ou não.</span><span class="sxs-lookup"><span data-stu-id="ee49f-259">The location of a window in the *topmost z-order* is also determined by whether it is currently active or not.</span></span> <span data-ttu-id="ee49f-260">Além disso, janelas na ordem z superior sempre estão localizadas acima das janelas na ordem z normal.</span><span class="sxs-lookup"><span data-stu-id="ee49f-260">Furthermore, windows in the topmost z-order are always located above windows in the normal z-order.</span></span> <span data-ttu-id="ee49f-261">Uma janela está localizada na ordem z mais <xref:System.Windows.Window.Topmost%2A> superior, definindo sua propriedade para `true`.</span><span class="sxs-lookup"><span data-stu-id="ee49f-261">A window is located in the topmost z-order by setting its <xref:System.Windows.Window.Topmost%2A> property to `true`.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 <span data-ttu-id="ee49f-262">Dentro de cada ordem z, a janela ativa no momento aparece acima de todas as outras janelas na mesma ordem z.</span><span class="sxs-lookup"><span data-stu-id="ee49f-262">Within each z-order, the currently active window appears above all other windows in the same z-order.</span></span>  
  
<a name="WindowSize"></a>
## <a name="window-size"></a><span data-ttu-id="ee49f-263">Tamanho da janela</span><span class="sxs-lookup"><span data-stu-id="ee49f-263">Window Size</span></span>  
 <span data-ttu-id="ee49f-264">Além de ter uma localização de desktop, uma janela tem um tamanho que <xref:System.Windows.Window.SizeToContent%2A>é determinado por várias propriedades, incluindo as várias propriedades de largura e altura e .</span><span class="sxs-lookup"><span data-stu-id="ee49f-264">Besides having a desktop location, a window has a size that is determined by several properties, including the various width and height properties and <xref:System.Windows.Window.SizeToContent%2A>.</span></span>  
  
 <span data-ttu-id="ee49f-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>e <xref:System.Windows.FrameworkElement.MaxWidth%2A> são usados para gerenciar o intervalo de larguras que uma janela pode ter durante sua vida útil, e são configurados como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ee49f-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.MaxWidth%2A> are used to manage the range of widths that a window can have during its lifetime, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 <span data-ttu-id="ee49f-266">A altura da <xref:System.Windows.FrameworkElement.MinHeight%2A>janela <xref:System.Windows.FrameworkElement.Height%2A>é <xref:System.Windows.FrameworkElement.MaxHeight%2A>gerenciada por , e , e são configuradas como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ee49f-266">Window height is managed by <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 <span data-ttu-id="ee49f-267">Já que os diversos valores de largura e de altura especificam um intervalo, é possível que a largura e altura de uma janela redimensionável estejam em qualquer lugar dentro do intervalo especificado para a respectiva dimensão.</span><span class="sxs-lookup"><span data-stu-id="ee49f-267">Because the various width values and height values each specify a range, it is possible for the width and height of a resizable window to be anywhere within the specified range for the respective dimension.</span></span> <span data-ttu-id="ee49f-268">Para detectar sua largura e <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A>altura atuais, inspecione e, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="ee49f-268">To detect its current width and height, inspect <xref:System.Windows.FrameworkElement.ActualWidth%2A> and <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectively.</span></span>  
  
 <span data-ttu-id="ee49f-269">Se você quiser que a largura e a altura da sua janela tenham um tamanho que <xref:System.Windows.Window.SizeToContent%2A> se encaixe no tamanho do conteúdo da janela, você pode usar a propriedade, que tem os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="ee49f-269">If you'd like the width and height of your window to have a size that fits to the size of the window's content, you can use the <xref:System.Windows.Window.SizeToContent%2A> property, which has the following values:</span></span>  
  
- <span data-ttu-id="ee49f-270"><xref:System.Windows.SizeToContent.Manual>.</span><span class="sxs-lookup"><span data-stu-id="ee49f-270"><xref:System.Windows.SizeToContent.Manual>.</span></span> <span data-ttu-id="ee49f-271">Sem efeito (padrão).</span><span class="sxs-lookup"><span data-stu-id="ee49f-271">No effect (default).</span></span>  
  
- <span data-ttu-id="ee49f-272"><xref:System.Windows.SizeToContent.Width>.</span><span class="sxs-lookup"><span data-stu-id="ee49f-272"><xref:System.Windows.SizeToContent.Width>.</span></span> <span data-ttu-id="ee49f-273">Ajuste à largura de conteúdo, que <xref:System.Windows.FrameworkElement.MinWidth%2A> tem <xref:System.Windows.FrameworkElement.MaxWidth%2A> o mesmo efeito de definir ambos e para a largura do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="ee49f-273">Fit to content width, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
- <span data-ttu-id="ee49f-274"><xref:System.Windows.SizeToContent.Height>.</span><span class="sxs-lookup"><span data-stu-id="ee49f-274"><xref:System.Windows.SizeToContent.Height>.</span></span> <span data-ttu-id="ee49f-275">Ajuste à altura do conteúdo, que <xref:System.Windows.FrameworkElement.MinHeight%2A> tem <xref:System.Windows.FrameworkElement.MaxHeight%2A> o mesmo efeito de definir tanto quanto à altura do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="ee49f-275">Fit to content height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content.</span></span>  
  
- <span data-ttu-id="ee49f-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span><span class="sxs-lookup"><span data-stu-id="ee49f-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span></span> <span data-ttu-id="ee49f-277">Ajuste-se à largura e altura do conteúdo, <xref:System.Windows.FrameworkElement.MaxHeight%2A> que tem o mesmo efeito <xref:System.Windows.FrameworkElement.MinWidth%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> de definir tanto <xref:System.Windows.FrameworkElement.MinHeight%2A> quanto à altura do conteúdo, e definir tanto a largura do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="ee49f-277">Fit to content width and height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content, and setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
 <span data-ttu-id="ee49f-278">O exemplo a seguir mostra uma janela que se dimensiona automaticamente para ajustar-se ao próprio conteúdo, verticalmente e horizontalmente, quando mostrada pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="ee49f-278">The following example shows a window that automatically sizes to fit its content, both vertically and horizontally, when first shown.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 <span data-ttu-id="ee49f-279">O exemplo a seguir <xref:System.Windows.Window.SizeToContent%2A> mostra como definir a propriedade em código para especificar como uma janela redimensiona para se adequar ao seu conteúdo .</span><span class="sxs-lookup"><span data-stu-id="ee49f-279">The following example shows how to set the <xref:System.Windows.Window.SizeToContent%2A> property in code to specify how a window resizes to fit its content    .</span></span>
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a><span data-ttu-id="ee49f-280">Ordem de precedência para propriedades de dimensionamento</span><span class="sxs-lookup"><span data-stu-id="ee49f-280">Order of Precedence for Sizing Properties</span></span>  
 <span data-ttu-id="ee49f-281">Essencialmente, as diversas propriedades de tamanhos de uma janela são combinadas para definir o intervalo de largura e altura de uma janela redimensionável.</span><span class="sxs-lookup"><span data-stu-id="ee49f-281">Essentially, the various sizes properties of a window combine to define the range of width and height for a resizable window.</span></span> <span data-ttu-id="ee49f-282">Para garantir que um intervalo <xref:System.Windows.Window> válido seja mantido, avalia os valores das propriedades de tamanho usando as seguintes ordens de precedência.</span><span class="sxs-lookup"><span data-stu-id="ee49f-282">To ensure a valid range is maintained, <xref:System.Windows.Window> evaluates the values of the size properties using the following orders of precedence.</span></span>  
  
 <span data-ttu-id="ee49f-283">**Para propriedades de altura:**</span><span class="sxs-lookup"><span data-stu-id="ee49f-283">**For Height Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="ee49f-284">**Para propriedades de largura:**</span><span class="sxs-lookup"><span data-stu-id="ee49f-284">**For Width Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="ee49f-285">A ordem de precedência também pode determinar o tamanho de uma <xref:System.Windows.Window.WindowState%2A> janela quando ela é maximizada, que é gerenciada com a propriedade.</span><span class="sxs-lookup"><span data-stu-id="ee49f-285">The order of precedence can also determine the size of a window when it is maximized, which is managed with the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="WindowState"></a>
## <a name="window-state"></a><span data-ttu-id="ee49f-286">Estado da janela</span><span class="sxs-lookup"><span data-stu-id="ee49f-286">Window State</span></span>  
 <span data-ttu-id="ee49f-287">Durante o tempo de vida de uma janela redimensionável, ela pode ter três estados: normal, minimizada e maximizada.</span><span class="sxs-lookup"><span data-stu-id="ee49f-287">During the lifetime of a resizable window, it can have three states: normal, minimized, and maximized.</span></span> <span data-ttu-id="ee49f-288">Uma janela com um estado *normal* é o estado padrão de uma janela.</span><span class="sxs-lookup"><span data-stu-id="ee49f-288">A window with a *normal* state is the default state of a window.</span></span> <span data-ttu-id="ee49f-289">Uma janela com esse estado permitirá que um usuário a mova e a redimensione usando uma alça de redimensionamento ou a borda, se ela for redimensionável.</span><span class="sxs-lookup"><span data-stu-id="ee49f-289">A window with this state allows a user to move and resize it by using a resize grip or the border, if it is resizable.</span></span>  
  
 <span data-ttu-id="ee49f-290">Uma janela com um estado *minimizado* entra <xref:System.Windows.Window.ShowInTaskbar%2A> em `true`colapso no botão da barra de tarefas se estiver definida como ; caso contrário, ele colapsa para o menor tamanho possível que pode ser e se realoca para o canto inferior esquerdo da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ee49f-290">A window with a *minimized* state collapses to its task bar button if <xref:System.Windows.Window.ShowInTaskbar%2A> is set to `true`; otherwise, it collapses to the smallest possible size it can be and relocates itself to the bottom-left corner of the desktop.</span></span> <span data-ttu-id="ee49f-291">Nenhum tipo de janela minimizada pode ser redimensionado usando uma borda ou alça redimensionável, embora uma janela minimizada não mostrada na barra de tarefas possa ser arrastada pela área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ee49f-291">Neither type of minimized window can be resized using a border or resize grip, although a minimized window that isn't shown in the task bar can be dragged around the desktop.</span></span>  
  
 <span data-ttu-id="ee49f-292">Uma janela com um estado *maximizado* expande-se para o tamanho <xref:System.Windows.FrameworkElement.MaxWidth%2A>máximo <xref:System.Windows.FrameworkElement.MaxHeight%2A>que <xref:System.Windows.Window.SizeToContent%2A> pode ser, que será tão grande quanto a sua , e as propriedades ditam.</span><span class="sxs-lookup"><span data-stu-id="ee49f-292">A window with a *maximized* state expands to the maximum size it can be, which will only be as large as its <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.Window.SizeToContent%2A> properties dictate.</span></span> <span data-ttu-id="ee49f-293">Assim como ocorre com uma janela minimizada, uma janela maximizada não pode ser redimensionada usando uma alça de redimensionamento ou arrastando a borda.</span><span class="sxs-lookup"><span data-stu-id="ee49f-293">Like a minimized window, a maximized window cannot be resized by using a resize grip or by dragging the border.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee49f-294">Os valores <xref:System.Windows.Window.Top%2A> <xref:System.Windows.Window.Left%2A>da <xref:System.Windows.FrameworkElement.Width%2A>janela <xref:System.Windows.FrameworkElement.Height%2A> sempre representam os valores para o estado normal, mesmo quando a janela é maximizada ou minimizada.</span><span class="sxs-lookup"><span data-stu-id="ee49f-294">The values of the <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.Height%2A> properties of a window always represent the values for the normal state, even when the window is currently maximized or minimized.</span></span>  
  
 <span data-ttu-id="ee49f-295">O estado de uma janela pode <xref:System.Windows.Window.WindowState%2A> ser configurado definindo sua <xref:System.Windows.WindowState> propriedade, que pode ter um dos seguintes valores de enumeração:</span><span class="sxs-lookup"><span data-stu-id="ee49f-295">The state of a window can be configured by setting its <xref:System.Windows.Window.WindowState%2A> property, which can have one of the following <xref:System.Windows.WindowState> enumeration values:</span></span>  
  
- <span data-ttu-id="ee49f-296"><xref:System.Windows.WindowState.Normal> (padrão)</span><span class="sxs-lookup"><span data-stu-id="ee49f-296"><xref:System.Windows.WindowState.Normal> (default)</span></span>  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 <span data-ttu-id="ee49f-297">O exemplo a seguir mostra como criar uma janela que é mostrada como maximizada quando é aberta.</span><span class="sxs-lookup"><span data-stu-id="ee49f-297">The following example shows how to create a window that is shown as maximized when it opens.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 <span data-ttu-id="ee49f-298">Em geral, você <xref:System.Windows.Window.WindowState%2A> deve definir para configurar o estado inicial de uma janela.</span><span class="sxs-lookup"><span data-stu-id="ee49f-298">In general, you should set <xref:System.Windows.Window.WindowState%2A> to configure the initial state of a window.</span></span> <span data-ttu-id="ee49f-299">Assim que uma janela redimensionável é exibida, os usuários podem pressionar os botões minimizar, maximizar e restaurar na barra de título da janela para alterar o estado desta.</span><span class="sxs-lookup"><span data-stu-id="ee49f-299">Once a resizable window is shown, users can press the minimize, maximize, and restore buttons on the window's title bar to change the window state.</span></span>  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a><span data-ttu-id="ee49f-300">Aparência da janela</span><span class="sxs-lookup"><span data-stu-id="ee49f-300">Window Appearance</span></span>  
 <span data-ttu-id="ee49f-301">Você pode alterar a aparência da área de cliente de uma janela adicionando conteúdo específico de janela a ela, por exemplo, botões, rótulos e caixas de texto.</span><span class="sxs-lookup"><span data-stu-id="ee49f-301">You change the appearance of the client area of a window by adding window-specific content to it, such as buttons, labels, and text boxes.</span></span> <span data-ttu-id="ee49f-302">Para configurar a área não <xref:System.Windows.Window> cliente, fornece <xref:System.Windows.Window.Icon%2A> várias propriedades, que <xref:System.Windows.Window.Title%2A> incluem definir o ícone de uma janela e definir seu título.</span><span class="sxs-lookup"><span data-stu-id="ee49f-302">To configure the non-client area, <xref:System.Windows.Window> provides several properties, which include <xref:System.Windows.Window.Icon%2A> to set a window's icon and <xref:System.Windows.Window.Title%2A> to set its title.</span></span>  
  
 <span data-ttu-id="ee49f-303">Você também pode alterar a aparência e o comportamento da borda da área de não cliente configurando o modo de redimensionamento da janela, o estilo da janela e definindo se essa janela aparece ou não como um botão na barra de tarefas da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ee49f-303">You can also change the appearance and behavior of non-client area border by configuring a window's resize mode, window style, and whether it appears as a button in the desktop task bar.</span></span>  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a><span data-ttu-id="ee49f-304">Modo de redimensionamento</span><span class="sxs-lookup"><span data-stu-id="ee49f-304">Resize Mode</span></span>  
 <span data-ttu-id="ee49f-305">Dependendo da <xref:System.Windows.Window.WindowStyle%2A> propriedade, você pode controlar como (e se) os usuários podem redimensionar a janela.</span><span class="sxs-lookup"><span data-stu-id="ee49f-305">Depending on the <xref:System.Windows.Window.WindowStyle%2A> property, you can control how (and if) users can resize the window.</span></span> <span data-ttu-id="ee49f-306">A escolha do estilo de janela afeta se um usuário pode redimensionar a janela arrastando sua borda com o mouse, se os botões **Minimizar**, **Maximizar**e **Redimensionar** aparecem na área não cliente e, se aparecerem, se estiverem habilitados.</span><span class="sxs-lookup"><span data-stu-id="ee49f-306">The choice of window style affects whether a user can resize the window by dragging its border with the mouse, whether the **Minimize**, **Maximize**, and **Resize** buttons appear on the non-client area, and, if they do appear, whether they are enabled.</span></span>  
  
 <span data-ttu-id="ee49f-307">Você pode configurar como uma janela redimensiona definindo sua <xref:System.Windows.Window.ResizeMode%2A> propriedade, que pode ser um dos seguintes <xref:System.Windows.ResizeMode> valores de enumeração:</span><span class="sxs-lookup"><span data-stu-id="ee49f-307">You can configure how a window resizes by setting its <xref:System.Windows.Window.ResizeMode%2A> property, which can be one of the following <xref:System.Windows.ResizeMode> enumeration values:</span></span>  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <span data-ttu-id="ee49f-308"><xref:System.Windows.ResizeMode.CanResize> (padrão)</span><span class="sxs-lookup"><span data-stu-id="ee49f-308"><xref:System.Windows.ResizeMode.CanResize> (default)</span></span>  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 <span data-ttu-id="ee49f-309">Como <xref:System.Windows.Window.WindowStyle%2A>com , o modo de redimensionamento de uma janela é improvável de mudar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] durante sua vida útil, o que significa que você provavelmente vai configurá-lo a partir da marcação.</span><span class="sxs-lookup"><span data-stu-id="ee49f-309">As with <xref:System.Windows.Window.WindowStyle%2A>, the resize mode of a window is unlikely to change during its lifetime, which means that you'll most likely set it from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 <span data-ttu-id="ee49f-310">Observe que você pode detectar se uma janela é maximizada, minimizada ou restaurada inspecionando a <xref:System.Windows.Window.WindowState%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="ee49f-310">Note that you can detect whether a window is maximized, minimized, or restored by inspecting the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="Window_Style"></a>
### <a name="window-style"></a><span data-ttu-id="ee49f-311">Estilo de Janela</span><span class="sxs-lookup"><span data-stu-id="ee49f-311">Window Style</span></span>  
 <span data-ttu-id="ee49f-312">A borda que é exposta da área de não cliente de uma janela é adequada para a maioria dos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ee49f-312">The border that is exposed from the non-client area of a window is suitable for most applications.</span></span> <span data-ttu-id="ee49f-313">No entanto, existem circunstâncias em que diferentes tipos de bordas são necessários ou em que nenhuma borda é necessária, dependendo do tipo de janela.</span><span class="sxs-lookup"><span data-stu-id="ee49f-313">However, there are circumstances where different types of borders are needed, or no borders are needed at all, depending on the type of window.</span></span>  
  
 <span data-ttu-id="ee49f-314">Para controlar que tipo de borda uma <xref:System.Windows.Window.WindowStyle%2A> janela obtém, você <xref:System.Windows.WindowStyle> define sua propriedade com um dos seguintes valores da enumeração:</span><span class="sxs-lookup"><span data-stu-id="ee49f-314">To control what type of border a window gets, you set its <xref:System.Windows.Window.WindowStyle%2A> property with one of the following values of the <xref:System.Windows.WindowStyle> enumeration:</span></span>  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <span data-ttu-id="ee49f-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (padrão)</span><span class="sxs-lookup"><span data-stu-id="ee49f-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (default)</span></span>  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 <span data-ttu-id="ee49f-316">O efeito desses estilos de janela são ilustrados na seguinte figura:</span><span class="sxs-lookup"><span data-stu-id="ee49f-316">The effect of these window styles are illustrated in the following figure:</span></span>  
  
 ![Ilustração dos estilos de borda da janela.](./media/wpf-windows-overview/window-border-styles.png)  
  
 <span data-ttu-id="ee49f-318">Você pode <xref:System.Windows.Window.WindowStyle%2A> definir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usando marcação ou código; porque é improvável que mude durante a vida útil de uma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] janela, você provavelmente irá configurá-la usando marcação.</span><span class="sxs-lookup"><span data-stu-id="ee49f-318">You can set <xref:System.Windows.Window.WindowStyle%2A> using either [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup or code; because it is unlikely to change during the lifetime of a window, you will most likely configure it using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a><span data-ttu-id="ee49f-319">Estilo de janela não retangular</span><span class="sxs-lookup"><span data-stu-id="ee49f-319">Non-Rectangular Window Style</span></span>  
 <span data-ttu-id="ee49f-320">Há também situações em <xref:System.Windows.Window.WindowStyle%2A> que os estilos de fronteira que permitem que você tenha não são suficientes.</span><span class="sxs-lookup"><span data-stu-id="ee49f-320">There are also situations where the border styles that <xref:System.Windows.Window.WindowStyle%2A> allows you to have are not sufficient.</span></span> <span data-ttu-id="ee49f-321">Por exemplo, você pode querer criar um aplicativo com uma borda não retangular, como o Microsoft Windows Media Player usa.</span><span class="sxs-lookup"><span data-stu-id="ee49f-321">For example, you may want to create an application with a non-rectangular border, like Microsoft Windows Media Player uses.</span></span>  
  
 <span data-ttu-id="ee49f-322">Por exemplo, considere a janela de bolha de fala mostrada na seguinte figura:</span><span class="sxs-lookup"><span data-stu-id="ee49f-322">For example, consider the speech bubble window shown in the following figure:</span></span>  
  
 ![Uma janela de bolha de fala que diz "Me Arraste-me".](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 <span data-ttu-id="ee49f-324">Esse tipo de janela pode ser <xref:System.Windows.Window.WindowStyle%2A> criada <xref:System.Windows.WindowStyle.None>definindo a propriedade <xref:System.Windows.Window> para , e usando suporte especial que tem para transparência.</span><span class="sxs-lookup"><span data-stu-id="ee49f-324">This type of window can be created by setting the <xref:System.Windows.Window.WindowStyle%2A> property to <xref:System.Windows.WindowStyle.None>, and by using special support that <xref:System.Windows.Window> has for transparency.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 <span data-ttu-id="ee49f-325">Essa combinação de valores instrui a janela a ser renderizada completamente transparente.</span><span class="sxs-lookup"><span data-stu-id="ee49f-325">This combination of values instructs the window to render completely transparent.</span></span> <span data-ttu-id="ee49f-326">Nesse estado, os adornos da área de não cliente da janela (o menu Fechar, botões Minimizar, Maximizar e Restaurar e assim por diante) não podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="ee49f-326">In this state, the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used.</span></span> <span data-ttu-id="ee49f-327">Consequentemente, você precisa fornecer os seus próprios.</span><span class="sxs-lookup"><span data-stu-id="ee49f-327">Consequently, you need to provide your own.</span></span>  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a><span data-ttu-id="ee49f-328">Presença da barra de tarefas</span><span class="sxs-lookup"><span data-stu-id="ee49f-328">Task Bar Presence</span></span>  

<span data-ttu-id="ee49f-329">A aparência padrão de uma janela inclui um botão de barra de tarefas, como o mostrado na seguinte figura:</span><span class="sxs-lookup"><span data-stu-id="ee49f-329">The default appearance of a window includes a taskbar button, like the one shown in the following figure:</span></span>

 ![Captura de tela que mostra uma janela com um botão de barra de tarefas.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 <span data-ttu-id="ee49f-331">Alguns tipos de janelas não possuem um botão de barra de tarefas, como caixas de mensagens e caixas de diálogo (ver [Visão geral das caixas de diálogo](dialog-boxes-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="ee49f-331">Some types of windows don't have a task bar button, such as message boxes and dialog boxes (see [Dialog Boxes Overview](dialog-boxes-overview.md)).</span></span> <span data-ttu-id="ee49f-332">Você pode controlar se o botão de barra <xref:System.Windows.Window.ShowInTaskbar%2A> de`true` tarefas para uma janela é mostrado definindo a propriedade (por padrão).</span><span class="sxs-lookup"><span data-stu-id="ee49f-332">You can control whether the task bar button for a window is shown by setting the <xref:System.Windows.Window.ShowInTaskbar%2A> property (`true` by default).</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a><span data-ttu-id="ee49f-333">Considerações de segurança</span><span class="sxs-lookup"><span data-stu-id="ee49f-333">Security Considerations</span></span>  
 <span data-ttu-id="ee49f-334"><xref:System.Windows.Window>requer `UnmanagedCode` permissão de segurança para ser instanciado.</span><span class="sxs-lookup"><span data-stu-id="ee49f-334"><xref:System.Windows.Window> requires `UnmanagedCode` security permission to be instantiated.</span></span> <span data-ttu-id="ee49f-335">Para aplicativos instalados e iniciados no computador local, isso se encaixa no conjunto de permissões concedidas ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ee49f-335">For applications installed on and launched from the local machine, this falls within the set of permissions that are granted to the application.</span></span>  
  
 <span data-ttu-id="ee49f-336">No entanto, isso está fora do conjunto de permissões concedidas a aplicativos que são lançados da região de internet ou intranet local usando o ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="ee49f-336">However, this falls outside the set of permissions granted to applications that are launched from the Internet or Local intranet zone using ClickOnce.</span></span> <span data-ttu-id="ee49f-337">Consequentemente, os usuários receberão um aviso de segurança ClickOnce e precisarão elevar a permissão definida para o aplicativo para total confiança.</span><span class="sxs-lookup"><span data-stu-id="ee49f-337">Consequently, users will receive a ClickOnce security warning and will need to elevate the permission set for the application to full trust.</span></span>  
  
 <span data-ttu-id="ee49f-338">Além disso, os XBAPs não podem mostrar janelas ou caixas de diálogo por padrão.</span><span class="sxs-lookup"><span data-stu-id="ee49f-338">Additionally, XBAPs cannot show windows or dialog boxes by default.</span></span> <span data-ttu-id="ee49f-339">Para uma discussão sobre considerações independentes de segurança de aplicativos, consulte [WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).</span><span class="sxs-lookup"><span data-stu-id="ee49f-339">For a discussion on standalone application security considerations, see [WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).</span></span>  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a><span data-ttu-id="ee49f-340">Outros tipos de janelas</span><span class="sxs-lookup"><span data-stu-id="ee49f-340">Other Types of Windows</span></span>  
 <span data-ttu-id="ee49f-341"><xref:System.Windows.Navigation.NavigationWindow>é uma janela projetada para hospedar conteúdo navegável.</span><span class="sxs-lookup"><span data-stu-id="ee49f-341"><xref:System.Windows.Navigation.NavigationWindow> is a window that is designed to host navigable content.</span></span> <span data-ttu-id="ee49f-342">Para obter mais informações, consulte [Visão geral da navegação](navigation-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="ee49f-342">For more information, see [Navigation Overview](navigation-overview.md)).</span></span>  
  
 <span data-ttu-id="ee49f-343">Caixas de diálogo são janelas que geralmente são usadas para coletar informações de um usuário para concluir uma função.</span><span class="sxs-lookup"><span data-stu-id="ee49f-343">Dialog boxes are windows that are often used to gather information from a user to complete a function.</span></span> <span data-ttu-id="ee49f-344">Por exemplo, quando um usuário deseja abrir um arquivo, a caixa de diálogo **Arquivo Aberto** geralmente é exibida por um aplicativo para obter o nome do arquivo do usuário.</span><span class="sxs-lookup"><span data-stu-id="ee49f-344">For example, when a user wants to open a file, the **Open File** dialog box is usually displayed by an application to get the file name from the user.</span></span> <span data-ttu-id="ee49f-345">Para obter mais informações, consulte [Visão geral das caixas de diálogo](dialog-boxes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ee49f-345">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee49f-346">Confira também</span><span class="sxs-lookup"><span data-stu-id="ee49f-346">See also</span></span>

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [<span data-ttu-id="ee49f-347">Visão geral das caixas de diálogo</span><span class="sxs-lookup"><span data-stu-id="ee49f-347">Dialog Boxes Overview</span></span>](dialog-boxes-overview.md)
- [<span data-ttu-id="ee49f-348">Compilando um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="ee49f-348">Building a WPF Application</span></span>](building-a-wpf-application-wpf.md)
