---
title: Visão geral do WPF do Windows
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
ms.openlocfilehash: 8c650ceab57a46cb6dd396111e7a93163a62299f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424937"
---
# <a name="wpf-windows-overview"></a><span data-ttu-id="e18a3-102">Visão geral do WPF do Windows</span><span class="sxs-lookup"><span data-stu-id="e18a3-102">WPF Windows Overview</span></span>
<span data-ttu-id="e18a3-103">Os usuários interagem com aplicativos autônomos do Windows Presentation Foundation (WPF) por meio do Windows.</span><span class="sxs-lookup"><span data-stu-id="e18a3-103">Users interact with Windows Presentation Foundation (WPF) standalone applications through windows.</span></span> <span data-ttu-id="e18a3-104">O objetivo principal de uma janela é hospedar conteúdo que visualiza dados e permite aos usuários interagir com os dados.</span><span class="sxs-lookup"><span data-stu-id="e18a3-104">The primary purpose of a window is to host content that visualizes data and enables users to interact with data.</span></span> <span data-ttu-id="e18a3-105">Os aplicativos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] autônomos fornecem suas próprias janelas usando a classe <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="e18a3-105">Standalone [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications provide their own windows by using the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="e18a3-106">Este tópico apresenta <xref:System.Windows.Window> antes de abranger os conceitos básicos da criação e gerenciamento de janelas em aplicativos autônomos.</span><span class="sxs-lookup"><span data-stu-id="e18a3-106">This topic introduces <xref:System.Windows.Window> before covering the fundamentals of creating and managing windows in standalone applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e18a3-107">Aplicativos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] hospedados no navegador, incluindo aplicativos de navegador XAML (XBAPs) e páginas de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] flexíveis, não fornecem suas próprias janelas.</span><span class="sxs-lookup"><span data-stu-id="e18a3-107">Browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications, including XAML browser applications (XBAPs) and loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pages, don't provide their own windows.</span></span> <span data-ttu-id="e18a3-108">Em vez disso, eles são hospedados no Windows fornecido pelo Windows Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e18a3-108">Instead, they are hosted in windows provided by Windows Internet Explorer.</span></span> <span data-ttu-id="e18a3-109">Consulte [visão geral de aplicativos de navegador XAML WPF](wpf-xaml-browser-applications-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e18a3-109">See [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>  

<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a><span data-ttu-id="e18a3-110">A classe Window</span><span class="sxs-lookup"><span data-stu-id="e18a3-110">The Window Class</span></span>  
 <span data-ttu-id="e18a3-111">A figura a seguir ilustra as partes constituintes de uma janela:</span><span class="sxs-lookup"><span data-stu-id="e18a3-111">The following figure illustrates the constituent parts of a window:</span></span>  
  
 ![Captura de tela que mostra os elementos da janela.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 <span data-ttu-id="e18a3-113">Uma janela é dividida em duas áreas: a área de não cliente e a área de cliente.</span><span class="sxs-lookup"><span data-stu-id="e18a3-113">A window is divided into two areas: the non-client area and client area.</span></span>  
  
 <span data-ttu-id="e18a3-114">A *área de não-cliente* de uma janela é implementada pelo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] e inclui as partes de uma janela que são comuns à maioria das janelas, incluindo as seguintes:</span><span class="sxs-lookup"><span data-stu-id="e18a3-114">The *non-client area* of a window is implemented by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] and includes the parts of a window that are common to most windows, including the following:</span></span>  
  
- <span data-ttu-id="e18a3-115">Uma borda.</span><span class="sxs-lookup"><span data-stu-id="e18a3-115">A border.</span></span>  
  
- <span data-ttu-id="e18a3-116">Uma barra de título.</span><span class="sxs-lookup"><span data-stu-id="e18a3-116">A title bar.</span></span>  
  
- <span data-ttu-id="e18a3-117">Um ícone.</span><span class="sxs-lookup"><span data-stu-id="e18a3-117">An icon.</span></span>  
  
- <span data-ttu-id="e18a3-118">Botões Minimizar, Maximizar e Restaurar.</span><span class="sxs-lookup"><span data-stu-id="e18a3-118">Minimize, Maximize, and Restore buttons.</span></span>  
  
- <span data-ttu-id="e18a3-119">Um botão Fechar.</span><span class="sxs-lookup"><span data-stu-id="e18a3-119">A Close button.</span></span>  
  
- <span data-ttu-id="e18a3-120">Um menu Sistema com itens de menu que permitem aos usuários minimizar, maximizar, restaurar, mover, redimensionar e fechar uma janela.</span><span class="sxs-lookup"><span data-stu-id="e18a3-120">A System menu with menu items that allow users to minimize, maximize, restore, move, resize, and close a window.</span></span>  
  
 <span data-ttu-id="e18a3-121">A *área de cliente* de uma janela é a área dentro de uma área não-cliente da janela e é usada por desenvolvedores para adicionar conteúdo específico do aplicativo, como barras de menu, barras de ferramentas e controles.</span><span class="sxs-lookup"><span data-stu-id="e18a3-121">The *client area* of a window is the area within a window's non-client area and is used by developers to add application-specific content, such as menu bars, tool bars, and controls.</span></span>  
  
 <span data-ttu-id="e18a3-122">No [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], uma janela é encapsulada pela classe <xref:System.Windows.Window> que você usa para fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e18a3-122">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], a window is encapsulated by the <xref:System.Windows.Window> class that you use to do the following:</span></span>  
  
- <span data-ttu-id="e18a3-123">Exibir uma janela.</span><span class="sxs-lookup"><span data-stu-id="e18a3-123">Display a window.</span></span>  
  
- <span data-ttu-id="e18a3-124">Configurar o tamanho, posição e aparência de uma janela.</span><span class="sxs-lookup"><span data-stu-id="e18a3-124">Configure the size, position, and appearance of a window.</span></span>  
  
- <span data-ttu-id="e18a3-125">Conteúdo específico do aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="e18a3-125">Host application-specific content.</span></span>  
  
- <span data-ttu-id="e18a3-126">Gerenciar o tempo de vida de uma janela.</span><span class="sxs-lookup"><span data-stu-id="e18a3-126">Manage the lifetime of a window.</span></span>  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a><span data-ttu-id="e18a3-127">Implementar uma janela</span><span class="sxs-lookup"><span data-stu-id="e18a3-127">Implementing a Window</span></span>  
 <span data-ttu-id="e18a3-128">A implementação de uma janela típica compreende a aparência e o comportamento, em que a *aparência* define como uma janela se parece com os usuários e o *comportamento* define a maneira como uma janela funciona quando os usuários interagem com ela.</span><span class="sxs-lookup"><span data-stu-id="e18a3-128">The implementation of a typical window comprises both appearance and behavior, where *appearance* defines how a window looks to users and *behavior* defines the way a window functions as users interact with it.</span></span> <span data-ttu-id="e18a3-129">No [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], você pode implementar a aparência e o comportamento de uma janela usando o código ou a marcação de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e18a3-129">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], you can implement the appearance and behavior of a window using either code or [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 <span data-ttu-id="e18a3-130">Em geral, no entanto, a aparência de uma janela é implementada usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] marcação, e seu comportamento é implementado usando code-behind, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e18a3-130">In general, however, the appearance of a window is implemented using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and its behavior is implemented using code-behind, as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 <span data-ttu-id="e18a3-131">Para permitir que um arquivo de marcação de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e um arquivo de código-behind funcionem juntos, são necessários os seguintes:</span><span class="sxs-lookup"><span data-stu-id="e18a3-131">To enable a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup file and code-behind file to work together, the following are required:</span></span>  
  
- <span data-ttu-id="e18a3-132">Na marcação, o elemento `Window` deve incluir o atributo `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="e18a3-132">In markup, the `Window` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="e18a3-133">Quando o aplicativo é compilado, a existência de `x:Class` no arquivo de marcação faz com que o Microsoft Build Engine (MSBuild) crie uma classe `partial` que deriva de <xref:System.Windows.Window> e tem o nome que é especificado pelo atributo `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="e18a3-133">When the application is built, the existence of `x:Class` in the markup file causes Microsoft build engine (MSBuild) to create a `partial` class that derives from <xref:System.Windows.Window> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="e18a3-134">Isso requer a adição de uma declaração de namespace de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] para o esquema de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`).</span><span class="sxs-lookup"><span data-stu-id="e18a3-134">This requires the addition of an [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="e18a3-135">A classe `partial` gerada implementa o método `InitializeComponent`, que é chamado para registrar os eventos e definir as propriedades que são implementadas na marcação.</span><span class="sxs-lookup"><span data-stu-id="e18a3-135">The generated `partial` class implements the `InitializeComponent` method, which is called to register the events and set the properties that are implemented in markup.</span></span>  
  
- <span data-ttu-id="e18a3-136">No code-behind, a classe deve ser uma classe `partial` com o mesmo nome que é especificado pelo atributo `x:Class` na marcação e deve derivar de <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="e18a3-136">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Window>.</span></span> <span data-ttu-id="e18a3-137">Isso permite que o arquivo code-behind seja associado à classe `partial` que é gerada para o arquivo de marcação quando o aplicativo é compilado (consulte [criando um aplicativo WPF](building-a-wpf-application-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="e18a3-137">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](building-a-wpf-application-wpf.md)).</span></span>  
  
- <span data-ttu-id="e18a3-138">No code-behind, a classe <xref:System.Windows.Window> deve implementar um construtor que chama o método `InitializeComponent`.</span><span class="sxs-lookup"><span data-stu-id="e18a3-138">In code-behind, the <xref:System.Windows.Window> class must implement a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="e18a3-139">`InitializeComponent` é implementada pela classe gerada `partial` do arquivo de marcação para registrar eventos e definir propriedades que são definidas na marcação.</span><span class="sxs-lookup"><span data-stu-id="e18a3-139">`InitializeComponent` is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e18a3-140">Quando você adiciona um novo <xref:System.Windows.Window> ao seu projeto usando o Visual Studio, o <xref:System.Windows.Window> é implementado usando marcação e code-behind e inclui a configuração necessária para criar a associação entre a marcação e os arquivos code-behind, conforme descrito aqui.</span><span class="sxs-lookup"><span data-stu-id="e18a3-140">When you add a new <xref:System.Windows.Window> to your project by using Visual Studio, the <xref:System.Windows.Window> is implemented using both markup and code-behind, and includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>  
  
 <span data-ttu-id="e18a3-141">Com essa configuração em vigor, você pode se concentrar em definir a aparência da janela na marcação [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e implementar seu comportamento no code-behind.</span><span class="sxs-lookup"><span data-stu-id="e18a3-141">With this configuration in place, you can focus on defining the appearance of the window in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and implementing its behavior in code-behind.</span></span> <span data-ttu-id="e18a3-142">O exemplo a seguir mostra uma janela com um botão, implementado em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] marcação e um manipulador de eventos para o evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click> do botão, implementado no code-behind.</span><span class="sxs-lookup"><span data-stu-id="e18a3-142">The following example shows a window with a button, implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, implemented in code-behind.</span></span>  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a><span data-ttu-id="e18a3-143">Configurar uma definição de janela para MSBuild</span><span class="sxs-lookup"><span data-stu-id="e18a3-143">Configuring a Window Definition for MSBuild</span></span>  
 <span data-ttu-id="e18a3-144">A forma como você implementa sua janela determina como ela é configurada para o MSBuild.</span><span class="sxs-lookup"><span data-stu-id="e18a3-144">How you implement your window determines how it is configured for MSBuild.</span></span> <span data-ttu-id="e18a3-145">Para uma janela que é definida usando a marcação de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e o code-behind:</span><span class="sxs-lookup"><span data-stu-id="e18a3-145">For a window that is defined using both [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind:</span></span>  
  
- <span data-ttu-id="e18a3-146">Os arquivos de marcação XAML são configurados como MSBuild `Page` itens.</span><span class="sxs-lookup"><span data-stu-id="e18a3-146">XAML markup files are configured as MSBuild `Page` items.</span></span>  
  
- <span data-ttu-id="e18a3-147">Os arquivos code-behind são configurados como MSBuild `Compile` itens.</span><span class="sxs-lookup"><span data-stu-id="e18a3-147">Code-behind files are configured as MSBuild `Compile` items.</span></span>  
  
 <span data-ttu-id="e18a3-148">Isso é mostrado no seguinte arquivo de projeto do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="e18a3-148">This is shown in the following MSBuild project file.</span></span>  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 <span data-ttu-id="e18a3-149">Para obter informações sobre como criar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos, consulte [criando um aplicativo WPF](building-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="e18a3-149">For information about building [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a><span data-ttu-id="e18a3-150">Tempo de vida de janela</span><span class="sxs-lookup"><span data-stu-id="e18a3-150">Window Lifetime</span></span>  
 <span data-ttu-id="e18a3-151">Assim como com qualquer classe, uma janela tem um tempo de vida que começa quando ela é instanciada pela primeira vez, fato após o qual ela é aberta, ativada e desativada e, eventualmente, fechada.</span><span class="sxs-lookup"><span data-stu-id="e18a3-151">As with any class, a window has a lifetime that begins when it is first instantiated, after which it is opened, activated and deactivated, and eventually closed.</span></span>  

<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a><span data-ttu-id="e18a3-152">Abrir uma janela</span><span class="sxs-lookup"><span data-stu-id="e18a3-152">Opening a Window</span></span>  
 <span data-ttu-id="e18a3-153">Para abrir uma janela, você primeiro cria uma instância dela, o que é demonstrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e18a3-153">To open a window, you first create an instance of it, which is demonstrated in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 <span data-ttu-id="e18a3-154">Neste exemplo, a `MarkupAndCodeBehindWindow` é instanciada quando o aplicativo é iniciado, o que ocorre quando o evento <xref:System.Windows.Application.Startup> é gerado.</span><span class="sxs-lookup"><span data-stu-id="e18a3-154">In this example, the `MarkupAndCodeBehindWindow` is instantiated when the application starts, which occurs when the <xref:System.Windows.Application.Startup> event is raised.</span></span>  
  
 <span data-ttu-id="e18a3-155">Quando uma janela é instanciada, uma referência a ela é adicionada automaticamente a uma lista de janelas gerenciadas pelo objeto <xref:System.Windows.Application> (consulte <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="e18a3-155">When a window is instantiated, a reference to it is automatically added to a list of windows that is managed by the <xref:System.Windows.Application> object (see <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="e18a3-156">Além disso, a primeira janela a ser instanciada é, por padrão, definida por <xref:System.Windows.Application> como a janela principal do aplicativo (consulte <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="e18a3-156">Additionally, the first window to be instantiated is, by default, set by <xref:System.Windows.Application> as the main application window (see <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="e18a3-157">A janela é finalmente aberta chamando o método <xref:System.Windows.Window.Show%2A>; o resultado é mostrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="e18a3-157">The window is finally opened by calling the <xref:System.Windows.Window.Show%2A> method; the result is shown in the following figure.</span></span>  
  
 ![Uma janela aberta chamando janela. show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 <span data-ttu-id="e18a3-159">Uma janela que é aberta chamando <xref:System.Windows.Window.Show%2A> é uma janela não sem-modo, o que significa que o aplicativo opera em um modo que permite aos usuários ativar outras janelas no mesmo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e18a3-159">A window that is opened by calling <xref:System.Windows.Window.Show%2A> is a modeless window, which means that the application operates in a mode that allows users to activate other windows in the same application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e18a3-160"><xref:System.Windows.Window.ShowDialog%2A> é chamado para abrir janelas como caixas de diálogo modalmente.</span><span class="sxs-lookup"><span data-stu-id="e18a3-160"><xref:System.Windows.Window.ShowDialog%2A> is called to open windows such as dialog boxes modally.</span></span> <span data-ttu-id="e18a3-161">Consulte [visão geral das caixas de diálogo](dialog-boxes-overview.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="e18a3-161">See [Dialog Boxes Overview](dialog-boxes-overview.md) for more information.</span></span>  
  
 <span data-ttu-id="e18a3-162">Quando <xref:System.Windows.Window.Show%2A> é chamado, uma janela executa o trabalho de inicialização antes de ser mostrada para estabelecer a infraestrutura que permite que ele receba a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="e18a3-162">When <xref:System.Windows.Window.Show%2A> is called, a window performs initialization work before it is shown to establish infrastructure that allows it to receive user input.</span></span> <span data-ttu-id="e18a3-163">Quando a janela é inicializada, o evento <xref:System.Windows.Window.SourceInitialized> é gerado e a janela é mostrada.</span><span class="sxs-lookup"><span data-stu-id="e18a3-163">When the window is initialized, the <xref:System.Windows.Window.SourceInitialized> event is raised and the window is shown.</span></span>  
  
 <span data-ttu-id="e18a3-164">Como um atalho, <xref:System.Windows.Application.StartupUri%2A> pode ser definido para especificar a primeira janela que é aberta automaticamente quando um aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="e18a3-164">As a shortcut, <xref:System.Windows.Application.StartupUri%2A> can be set to specify the first window that is opened automatically when an application starts.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 <span data-ttu-id="e18a3-165">Quando o aplicativo é iniciado, a janela especificada pelo valor de <xref:System.Windows.Application.StartupUri%2A> é aberta modelessly; internamente, a janela é aberta chamando seu método <xref:System.Windows.Window.Show%2A>.</span><span class="sxs-lookup"><span data-stu-id="e18a3-165">When the application starts, the window specified by the value of <xref:System.Windows.Application.StartupUri%2A> is opened modelessly; internally, the window is opened by calling its <xref:System.Windows.Window.Show%2A> method.</span></span>  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a><span data-ttu-id="e18a3-166">Posse de janela</span><span class="sxs-lookup"><span data-stu-id="e18a3-166">Window Ownership</span></span>  
 <span data-ttu-id="e18a3-167">Uma janela que é aberta usando o método <xref:System.Windows.Window.Show%2A> não tem uma relação implícita com a janela que a criou; os usuários podem interagir com qualquer uma das janelas independentemente da outra, o que significa que qualquer uma das janelas pode fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e18a3-167">A window that is opened by using the <xref:System.Windows.Window.Show%2A> method does not have an implicit relationship with the window that created it; users can interact with either window independently of the other, which means that either window can do the following:</span></span>  
  
- <span data-ttu-id="e18a3-168">Cubra o outro (a menos que uma das janelas tenha sua propriedade <xref:System.Windows.Window.Topmost%2A> definida como `true`).</span><span class="sxs-lookup"><span data-stu-id="e18a3-168">Cover the other (unless one of the windows has its <xref:System.Windows.Window.Topmost%2A> property set to `true`).</span></span>  
  
- <span data-ttu-id="e18a3-169">Ser minimizada, maximizada e restaurada sem afetar a outra.</span><span class="sxs-lookup"><span data-stu-id="e18a3-169">Be minimized, maximized, and restored without affecting the other.</span></span>  
  
 <span data-ttu-id="e18a3-170">Algumas janelas requerem uma relação com a janela que as abre.</span><span class="sxs-lookup"><span data-stu-id="e18a3-170">Some windows require a relationship with the window that opens them.</span></span> <span data-ttu-id="e18a3-171">Por exemplo, um aplicativo IDE (ambiente de desenvolvimento integrado) pode abrir janelas de propriedades e janelas de ferramentas cujo comportamento típico é abordar a janela que as cria.</span><span class="sxs-lookup"><span data-stu-id="e18a3-171">For example, an Integrated Development Environment (IDE) application may open property windows and tool windows whose typical behavior is to cover the window that creates them.</span></span> <span data-ttu-id="e18a3-172">Além disso, janelas desse tipo devem sempre fechar, minimizar, maximizar e restaurar em conjunto com a janela que as criou.</span><span class="sxs-lookup"><span data-stu-id="e18a3-172">Furthermore, such windows should always close, minimize, maximize, and restore in concert with the window that created them.</span></span> <span data-ttu-id="e18a3-173">Tal relação pode ser estabelecida fazendo uma janela *própria* e é obtida definindo a propriedade <xref:System.Windows.Window.Owner%2A> da *janela de propriedade* com uma referência à *janela do proprietário*.</span><span class="sxs-lookup"><span data-stu-id="e18a3-173">Such a relationship can be established by making one window *own* another, and is achieved by setting the <xref:System.Windows.Window.Owner%2A> property of the *owned window* with a reference to the *owner window*.</span></span> <span data-ttu-id="e18a3-174">Isso é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e18a3-174">This is shown in the following example.</span></span>  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 <span data-ttu-id="e18a3-175">Depois que a posse é estabelecida:</span><span class="sxs-lookup"><span data-stu-id="e18a3-175">After ownership is established:</span></span>  
  
- <span data-ttu-id="e18a3-176">A janela de propriedade pode referenciar sua janela do proprietário inspecionando o valor de sua propriedade <xref:System.Windows.Window.Owner%2A>.</span><span class="sxs-lookup"><span data-stu-id="e18a3-176">The owned window can reference its owner window by inspecting the value of its <xref:System.Windows.Window.Owner%2A> property.</span></span>  
  
- <span data-ttu-id="e18a3-177">A janela do proprietário pode descobrir todas as janelas que ela possui inspecionando o valor de sua propriedade <xref:System.Windows.Window.OwnedWindows%2A>.</span><span class="sxs-lookup"><span data-stu-id="e18a3-177">The owner window can discover all the windows it owns by inspecting the value of its <xref:System.Windows.Window.OwnedWindows%2A> property.</span></span>  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a><span data-ttu-id="e18a3-178">Impedindo a ativação de janela</span><span class="sxs-lookup"><span data-stu-id="e18a3-178">Preventing Window Activation</span></span>  
 <span data-ttu-id="e18a3-179">Há cenários em que o Windows não deve ser ativado quando mostrado, como janelas de conversa de um aplicativo no estilo Internet Messenger ou janelas de notificação de um aplicativo de email.</span><span class="sxs-lookup"><span data-stu-id="e18a3-179">There are scenarios where windows should not be activated when shown, such as conversation windows of an Internet messenger-style application or notification windows of an email application.</span></span>  
  
 <span data-ttu-id="e18a3-180">Se seu aplicativo tiver uma janela que não deve ser ativada quando for mostrado, você poderá definir sua propriedade <xref:System.Windows.Window.ShowActivated%2A> como `false` antes de chamar o método <xref:System.Windows.Window.Show%2A> pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="e18a3-180">If your application has a window that shouldn't be activated when shown, you can set its <xref:System.Windows.Window.ShowActivated%2A> property to `false` before calling the <xref:System.Windows.Window.Show%2A> method for the first time.</span></span> <span data-ttu-id="e18a3-181">Como consequência disso:</span><span class="sxs-lookup"><span data-stu-id="e18a3-181">As a consequence:</span></span>  
  
- <span data-ttu-id="e18a3-182">A janela não é ativada.</span><span class="sxs-lookup"><span data-stu-id="e18a3-182">The window is not activated.</span></span>  
  
- <span data-ttu-id="e18a3-183">O evento de <xref:System.Windows.Window.Activated> da janela não é gerado.</span><span class="sxs-lookup"><span data-stu-id="e18a3-183">The window's <xref:System.Windows.Window.Activated> event is not raised.</span></span>  
  
- <span data-ttu-id="e18a3-184">A janela ativada no momento permanece ativada.</span><span class="sxs-lookup"><span data-stu-id="e18a3-184">The currently activated window remains activated.</span></span>  
  
 <span data-ttu-id="e18a3-185">A janela se tornará ativada, no entanto, assim que o usuário ativá-la clicando na área de cliente ou então na área não cliente.</span><span class="sxs-lookup"><span data-stu-id="e18a3-185">The window will become activated, however, as soon as the user activates it by clicking either the client or non-client area.</span></span> <span data-ttu-id="e18a3-186">Nesse caso:</span><span class="sxs-lookup"><span data-stu-id="e18a3-186">In this case:</span></span>  
  
- <span data-ttu-id="e18a3-187">A janela é ativada.</span><span class="sxs-lookup"><span data-stu-id="e18a3-187">The window is activated.</span></span>  
  
- <span data-ttu-id="e18a3-188">O evento de <xref:System.Windows.Window.Activated> da janela é gerado.</span><span class="sxs-lookup"><span data-stu-id="e18a3-188">The window's <xref:System.Windows.Window.Activated> event is raised.</span></span>  
  
- <span data-ttu-id="e18a3-189">A janela ativada anteriormente é desativada.</span><span class="sxs-lookup"><span data-stu-id="e18a3-189">The previously activated window is deactivated.</span></span>  
  
- <span data-ttu-id="e18a3-190">Os eventos de <xref:System.Windows.Window.Deactivated> e <xref:System.Windows.Window.Activated> da janela são gerados posteriormente conforme o esperado em resposta às ações do usuário.</span><span class="sxs-lookup"><span data-stu-id="e18a3-190">The window's <xref:System.Windows.Window.Deactivated> and <xref:System.Windows.Window.Activated> events are subsequently raised as expected in response to user actions.</span></span>  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a><span data-ttu-id="e18a3-191">Ativação de janela</span><span class="sxs-lookup"><span data-stu-id="e18a3-191">Window Activation</span></span>  
 <span data-ttu-id="e18a3-192">Quando uma janela é aberta pela primeira vez, ela se torna a janela ativa (a menos que seja mostrado com <xref:System.Windows.Window.ShowActivated%2A> definido como `false`).</span><span class="sxs-lookup"><span data-stu-id="e18a3-192">When a window is first opened, it becomes the active window (unless it is shown with <xref:System.Windows.Window.ShowActivated%2A> set to `false`).</span></span> <span data-ttu-id="e18a3-193">A *janela ativa* é a janela que está atualmente capturando a entrada do usuário, como traços de tecla e cliques do mouse.</span><span class="sxs-lookup"><span data-stu-id="e18a3-193">The *active window* is the window that is currently capturing user input, such as key strokes and mouse clicks.</span></span> <span data-ttu-id="e18a3-194">Quando uma janela se torna ativa, ela gera o evento <xref:System.Windows.Window.Activated>.</span><span class="sxs-lookup"><span data-stu-id="e18a3-194">When a window becomes active, it raises the <xref:System.Windows.Window.Activated> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e18a3-195">Quando uma janela é aberta pela primeira vez, os eventos <xref:System.Windows.FrameworkElement.Loaded> e <xref:System.Windows.Window.ContentRendered> são gerados somente depois que o evento <xref:System.Windows.Window.Activated> é gerado.</span><span class="sxs-lookup"><span data-stu-id="e18a3-195">When a window is first opened, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.Window.ContentRendered> events are raised only after the <xref:System.Windows.Window.Activated> event is raised.</span></span> <span data-ttu-id="e18a3-196">Com isso em mente, uma janela pode ser efetivamente considerada aberta quando <xref:System.Windows.Window.ContentRendered> é gerada.</span><span class="sxs-lookup"><span data-stu-id="e18a3-196">With this in mind, a window can effectively be considered opened when <xref:System.Windows.Window.ContentRendered> is raised.</span></span>  
  
 <span data-ttu-id="e18a3-197">Depois que uma janela fica ativa, um usuário pode ativar outra janela no mesmo aplicativo ou então ativar outro aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e18a3-197">After a window becomes active, a user can activate another window in the same application, or activate another application.</span></span> <span data-ttu-id="e18a3-198">Quando isso acontece, a janela ativa no momento torna-se desativada e gera o evento <xref:System.Windows.Window.Deactivated>.</span><span class="sxs-lookup"><span data-stu-id="e18a3-198">When that happens, the currently active window becomes deactivated and raises the <xref:System.Windows.Window.Deactivated> event.</span></span> <span data-ttu-id="e18a3-199">Da mesma forma, quando o usuário seleciona uma janela desativada no momento, a janela fica ativa novamente e <xref:System.Windows.Window.Activated> é gerada.</span><span class="sxs-lookup"><span data-stu-id="e18a3-199">Likewise, when the user selects a currently deactivated window, the window becomes active again and <xref:System.Windows.Window.Activated> is raised.</span></span>  
  
 <span data-ttu-id="e18a3-200">Um motivo comum para lidar com <xref:System.Windows.Window.Activated> e <xref:System.Windows.Window.Deactivated> é habilitar e desabilitar a funcionalidade que só pode ser executada quando uma janela está ativa.</span><span class="sxs-lookup"><span data-stu-id="e18a3-200">One common reason to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> is to enable and disable functionality that can only run when a window is active.</span></span> <span data-ttu-id="e18a3-201">Por exemplo, algumas janelas exibem conteúdo interativo que requer constante atenção ou entrada do usuário, incluindo players de vídeo e jogos.</span><span class="sxs-lookup"><span data-stu-id="e18a3-201">For example, some windows display interactive content that requires constant user input or attention, including games and video players.</span></span> <span data-ttu-id="e18a3-202">O exemplo a seguir é um player de vídeo simplificado que demonstra como lidar com <xref:System.Windows.Window.Activated> e <xref:System.Windows.Window.Deactivated> para implementar esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="e18a3-202">The following example is a simplified video player that demonstrates how to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> to implement this behavior.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 <span data-ttu-id="e18a3-203">Outros tipos de aplicativos podem ainda executar códigos em segundo plano quando uma janela é desativada.</span><span class="sxs-lookup"><span data-stu-id="e18a3-203">Other types of applications may still run code in the background when a window is deactivated.</span></span> <span data-ttu-id="e18a3-204">Por exemplo, um cliente de email pode continuar a sondagem do servidor de email enquanto o usuário está usando outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e18a3-204">For example, a mail client may continue polling the mail server while the user is using other applications.</span></span> <span data-ttu-id="e18a3-205">Aplicativos como esses geralmente apresentam comportamento diferente ou adicional enquanto a janela principal está desativada.</span><span class="sxs-lookup"><span data-stu-id="e18a3-205">Applications like these often provide different or additional behavior while the main window is deactivated.</span></span> <span data-ttu-id="e18a3-206">Em relação ao programa de email, isso pode significar tanto adicionar o novo item de email à caixa de entrada quanto adicionar um ícone de notificação à bandeja do sistema.</span><span class="sxs-lookup"><span data-stu-id="e18a3-206">With respect to the mail program, this may mean both adding the new mail item to the inbox and adding a notification icon to the system tray.</span></span> <span data-ttu-id="e18a3-207">Um ícone de notificação só precisa ser exibido quando a janela de email não estiver ativa, o que pode ser determinado inspecionando a propriedade <xref:System.Windows.Window.IsActive%2A>.</span><span class="sxs-lookup"><span data-stu-id="e18a3-207">A notification icon need only be displayed when the mail window isn't active, which can be determined by inspecting the <xref:System.Windows.Window.IsActive%2A> property.</span></span>  
  
 <span data-ttu-id="e18a3-208">Se uma tarefa em segundo plano for concluída, uma janela pode querer notificar o usuário de forma mais urgente chamando <xref:System.Windows.Window.Activate%2A> método.</span><span class="sxs-lookup"><span data-stu-id="e18a3-208">If a background task completes, a window may want to notify the user more urgently by calling <xref:System.Windows.Window.Activate%2A> method.</span></span> <span data-ttu-id="e18a3-209">Se o usuário estiver interagindo com outro aplicativo ativado quando <xref:System.Windows.Window.Activate%2A> for chamado, o botão da barra de tarefas da janela piscará.</span><span class="sxs-lookup"><span data-stu-id="e18a3-209">If the user is interacting with another application activated when <xref:System.Windows.Window.Activate%2A> is called, the window's taskbar button flashes.</span></span> <span data-ttu-id="e18a3-210">Se um usuário estiver interagindo com o aplicativo atual, chamar <xref:System.Windows.Window.Activate%2A> levará a janela para o primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="e18a3-210">If a user is interacting with the current application, calling <xref:System.Windows.Window.Activate%2A> will bring the window to the foreground.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e18a3-211">Você pode manipular a ativação de escopo de aplicativo usando os eventos <xref:System.Windows.Application.Activated?displayProperty=nameWithType> e <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e18a3-211">You can handle application-scope activation using the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> and <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> events.</span></span>  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a><span data-ttu-id="e18a3-212">Fechar uma janela</span><span class="sxs-lookup"><span data-stu-id="e18a3-212">Closing a Window</span></span>  
 <span data-ttu-id="e18a3-213">O fim da vida de uma janela se começa a se aproximar quando um usuário a fecha.</span><span class="sxs-lookup"><span data-stu-id="e18a3-213">The life of a window starts coming to an end when a user closes it.</span></span> <span data-ttu-id="e18a3-214">Uma janela pode ser fechada pelo uso de elementos na área de não cliente, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e18a3-214">A window can be closed by using elements in the non-client area, including the following:</span></span>  
  
- <span data-ttu-id="e18a3-215">O item **fechar** do menu do **sistema** .</span><span class="sxs-lookup"><span data-stu-id="e18a3-215">The **Close** item of the **System** menu.</span></span>  
  
- <span data-ttu-id="e18a3-216">Pressionar ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="e18a3-216">Pressing ALT+F4.</span></span>  
  
- <span data-ttu-id="e18a3-217">Pressionando o botão **fechar** .</span><span class="sxs-lookup"><span data-stu-id="e18a3-217">Pressing the **Close** button.</span></span>  
  
 <span data-ttu-id="e18a3-218">Você pode fornecer mecanismos adicionais à área de cliente para fechar uma janela, sendo que os mais comuns deles incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="e18a3-218">You can provide additional mechanisms to the client area to close a window, the more common of which include the following:</span></span>  
  
- <span data-ttu-id="e18a3-219">Um item de **saída** no menu **arquivo** , normalmente para janelas de aplicativo principal.</span><span class="sxs-lookup"><span data-stu-id="e18a3-219">An **Exit** item in the **File** menu, typically for main application windows.</span></span>  
  
- <span data-ttu-id="e18a3-220">Um item de **fechamento** no menu **arquivo** , normalmente em uma janela de aplicativo secundário.</span><span class="sxs-lookup"><span data-stu-id="e18a3-220">A **Close** item in the **File** menu, typically on a secondary application window.</span></span>  
  
- <span data-ttu-id="e18a3-221">Um botão de **cancelamento** , normalmente em uma caixa de diálogo modal.</span><span class="sxs-lookup"><span data-stu-id="e18a3-221">A **Cancel** button, typically on a modal dialog box.</span></span>  
  
- <span data-ttu-id="e18a3-222">Um botão **fechar** , normalmente em uma caixa de diálogo sem janela restrita.</span><span class="sxs-lookup"><span data-stu-id="e18a3-222">A **Close** button, typically on a modeless dialog box.</span></span>  
  
 <span data-ttu-id="e18a3-223">Para fechar uma janela em resposta a um desses mecanismos personalizados, você precisa chamar o método <xref:System.Windows.Window.Close%2A>.</span><span class="sxs-lookup"><span data-stu-id="e18a3-223">To close a window in response to one of these custom mechanisms, you need to call the <xref:System.Windows.Window.Close%2A> method.</span></span> <span data-ttu-id="e18a3-224">O exemplo a seguir implementa a capacidade de fechar uma janela escolhendo **sair** no menu **arquivo** .</span><span class="sxs-lookup"><span data-stu-id="e18a3-224">The following example implements the ability to close a window by choosing the **Exit** on the **File** menu.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 <span data-ttu-id="e18a3-225">Quando uma janela é fechada, ela gera dois eventos: <xref:System.Windows.Window.Closing> e <xref:System.Windows.Window.Closed>.</span><span class="sxs-lookup"><span data-stu-id="e18a3-225">When a window closes, it raises two events: <xref:System.Windows.Window.Closing> and <xref:System.Windows.Window.Closed>.</span></span>  
  
 <span data-ttu-id="e18a3-226"><xref:System.Windows.Window.Closing> é gerado antes da janela ser fechada e fornece um mecanismo pelo qual o fechamento da janela pode ser impedido.</span><span class="sxs-lookup"><span data-stu-id="e18a3-226"><xref:System.Windows.Window.Closing> is raised before the window closes, and it provides a mechanism by which window closure can be prevented.</span></span> <span data-ttu-id="e18a3-227">Uma razão comum para evitar o fechamento da janela é caso o conteúdo da janela contenha dados modificados.</span><span class="sxs-lookup"><span data-stu-id="e18a3-227">One common reason to prevent window closure is if window content contains modified data.</span></span> <span data-ttu-id="e18a3-228">Nessa situação, o evento <xref:System.Windows.Window.Closing> pode ser tratado para determinar se os dados estão sujos e, em caso afirmativo, perguntar ao usuário se deseja continuar fechando a janela sem salvar os dados ou cancelar o fechamento da janela.</span><span class="sxs-lookup"><span data-stu-id="e18a3-228">In this situation, the <xref:System.Windows.Window.Closing> event can be handled to determine whether data is dirty and, if so, to ask the user whether to either continue closing the window without saving the data or to cancel window closure.</span></span> <span data-ttu-id="e18a3-229">O exemplo a seguir mostra os principais aspectos do tratamento de <xref:System.Windows.Window.Closing>.</span><span class="sxs-lookup"><span data-stu-id="e18a3-229">The following example shows the key aspects of handling <xref:System.Windows.Window.Closing>.</span></span>  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <span data-ttu-id="e18a3-230">O manipulador de eventos <xref:System.Windows.Window.Closing> é passado por um <xref:System.ComponentModel.CancelEventArgs>, que implementa a propriedade <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> `Boolean`que você define como `true` para impedir que uma janela seja fechada.</span><span class="sxs-lookup"><span data-stu-id="e18a3-230">The <xref:System.Windows.Window.Closing> event handler is passed a <xref:System.ComponentModel.CancelEventArgs>, which implements the `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property that you set to `true` to prevent a window from closing.</span></span>  
  
 <span data-ttu-id="e18a3-231">Se <xref:System.Windows.Window.Closing> não for manipulada ou for manipulada, mas não cancelada, a janela será fechada.</span><span class="sxs-lookup"><span data-stu-id="e18a3-231">If <xref:System.Windows.Window.Closing> is not handled, or it is handled but not canceled, the window will close.</span></span> <span data-ttu-id="e18a3-232">Logo antes de uma janela ser realmente fechada, <xref:System.Windows.Window.Closed> é gerado.</span><span class="sxs-lookup"><span data-stu-id="e18a3-232">Just before a window actually closes, <xref:System.Windows.Window.Closed> is raised.</span></span> <span data-ttu-id="e18a3-233">Neste ponto, uma janela não pode ser impedida de fechar.</span><span class="sxs-lookup"><span data-stu-id="e18a3-233">At this point, a window cannot be prevented from closing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e18a3-234">Um aplicativo pode ser configurado para ser desligado automaticamente quando a janela principal do aplicativo é fechada (consulte <xref:System.Windows.Application.MainWindow%2A>) ou a última janela é fechada.</span><span class="sxs-lookup"><span data-stu-id="e18a3-234">An application can be configured to shut down automatically when either the main application window closes (see <xref:System.Windows.Application.MainWindow%2A>) or the last window closes.</span></span> <span data-ttu-id="e18a3-235">Para obter detalhes, consulte <xref:System.Windows.Application.ShutdownMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="e18a3-235">For details, see <xref:System.Windows.Application.ShutdownMode%2A>.</span></span>  
  
 <span data-ttu-id="e18a3-236">Embora uma janela possa ser fechada explicitamente por meio de mecanismos fornecidos nas áreas não cliente e cliente, uma janela também pode ser fechada implicitamente como resultado de um comportamento em outras partes do aplicativo ou do Windows, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e18a3-236">While a window can be explicitly closed through mechanisms provided in the non-client and client areas, a window can also be implicitly closed as a result of behavior in other parts of the application or Windows, including the following:</span></span>  
  
- <span data-ttu-id="e18a3-237">Um usuário faz logoff ou desliga o Windows.</span><span class="sxs-lookup"><span data-stu-id="e18a3-237">A user logs off or shuts down Windows.</span></span>  
  
- <span data-ttu-id="e18a3-238">O proprietário de uma janela fecha (consulte <xref:System.Windows.Window.Owner%2A>).</span><span class="sxs-lookup"><span data-stu-id="e18a3-238">A window's owner closes (see <xref:System.Windows.Window.Owner%2A>).</span></span>  
  
- <span data-ttu-id="e18a3-239">A janela principal do aplicativo é fechada e <xref:System.Windows.Application.ShutdownMode%2A> é <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span><span class="sxs-lookup"><span data-stu-id="e18a3-239">The main application window is closed and <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>  
  
- <span data-ttu-id="e18a3-240"><xref:System.Windows.Application.Shutdown%2A> é chamado.</span><span class="sxs-lookup"><span data-stu-id="e18a3-240"><xref:System.Windows.Application.Shutdown%2A> is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e18a3-241">Uma janela não pode ser reaberta depois que é fechada.</span><span class="sxs-lookup"><span data-stu-id="e18a3-241">A window cannot be reopened after it is closed.</span></span>  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a><span data-ttu-id="e18a3-242">Eventos de tempo de vida da janela</span><span class="sxs-lookup"><span data-stu-id="e18a3-242">Window Lifetime Events</span></span>  
 <span data-ttu-id="e18a3-243">A ilustração a seguir mostra a sequência dos eventos principais no tempo de vida de uma janela:</span><span class="sxs-lookup"><span data-stu-id="e18a3-243">The following illustration shows the sequence of the principal events in the lifetime of a window:</span></span>  
  
 ![Diagrama que mostra eventos no tempo de vida de uma janela.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 <span data-ttu-id="e18a3-245">A ilustração a seguir mostra a sequência dos eventos principais no tempo de vida de uma janela que é mostrada sem ativação (<xref:System.Windows.Window.ShowActivated%2A> é definido como `false` antes de a janela ser mostrada):</span><span class="sxs-lookup"><span data-stu-id="e18a3-245">The following illustration shows the sequence of the principal events in the lifetime of a window that is shown without activation (<xref:System.Windows.Window.ShowActivated%2A> is set to `false` before the window is shown):</span></span>  
  
 ![Diagrama que mostra eventos no tempo de vida de uma janela sem ativação.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a><span data-ttu-id="e18a3-247">Localização da janela</span><span class="sxs-lookup"><span data-stu-id="e18a3-247">Window Location</span></span>  
 <span data-ttu-id="e18a3-248">Enquanto uma janela estiver aberta, ela terá uma localização nas dimensões x e y em relação à área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e18a3-248">While a window is open, it has a location in the x and y dimensions relative to the desktop.</span></span> <span data-ttu-id="e18a3-249">Esse local pode ser determinado inspecionando as propriedades <xref:System.Windows.Window.Left%2A> e <xref:System.Windows.Window.Top%2A>, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="e18a3-249">This location can be determined by inspecting the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties, respectively.</span></span> <span data-ttu-id="e18a3-250">Você pode definir essas propriedades para alterar o local da janela.</span><span class="sxs-lookup"><span data-stu-id="e18a3-250">You can set these properties to change the location of the window.</span></span>  
  
 <span data-ttu-id="e18a3-251">Você também pode especificar o local inicial de um <xref:System.Windows.Window> quando ele for exibido pela primeira vez, definindo a propriedade <xref:System.Windows.Window.WindowStartupLocation%2A> com um dos seguintes <xref:System.Windows.WindowStartupLocation> valores de enumeração:</span><span class="sxs-lookup"><span data-stu-id="e18a3-251">You can also specify the initial location of a <xref:System.Windows.Window> when it first appears by setting the <xref:System.Windows.Window.WindowStartupLocation%2A> property with one of the following <xref:System.Windows.WindowStartupLocation> enumeration values:</span></span>  
  
- <span data-ttu-id="e18a3-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (padrão)</span><span class="sxs-lookup"><span data-stu-id="e18a3-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (default)</span></span>  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 <span data-ttu-id="e18a3-253">Se o local de inicialização for especificado como <xref:System.Windows.WindowStartupLocation.Manual>e as propriedades <xref:System.Windows.Window.Left%2A> e <xref:System.Windows.Window.Top%2A> não tiverem sido definidas, <xref:System.Windows.Window> pedirá ao Windows que um local apareça.</span><span class="sxs-lookup"><span data-stu-id="e18a3-253">If the startup location is specified as <xref:System.Windows.WindowStartupLocation.Manual>, and the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties have not been set, <xref:System.Windows.Window> will ask Windows for a location to appear in.</span></span>  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a><span data-ttu-id="e18a3-254">Janela superior e ordem Z</span><span class="sxs-lookup"><span data-stu-id="e18a3-254">Topmost Windows and Z-Order</span></span>  
 <span data-ttu-id="e18a3-255">Além de ter uma localização x e y, uma janela também tem uma localização na dimensão z, que determina a posição vertical em relação a outras janelas.</span><span class="sxs-lookup"><span data-stu-id="e18a3-255">Besides having an x and y location, a window also has a location in the z dimension, which determines its vertical position with respect to other windows.</span></span> <span data-ttu-id="e18a3-256">Isso é conhecido como a ordem z da janela, e há dois tipos: ordem z normal e ordem z superior.</span><span class="sxs-lookup"><span data-stu-id="e18a3-256">This is known as the window's z-order, and there are two types: normal z-order and topmost z-order.</span></span> <span data-ttu-id="e18a3-257">O local de uma janela na *ordem z normal* é determinado pelo fato de estar atualmente ativo ou não.</span><span class="sxs-lookup"><span data-stu-id="e18a3-257">The location of a window in the *normal z-order* is determined by whether it is currently active or not.</span></span> <span data-ttu-id="e18a3-258">Por padrão, uma janela está localizada na ordem z normal.</span><span class="sxs-lookup"><span data-stu-id="e18a3-258">By default, a window is located in the normal z-order.</span></span> <span data-ttu-id="e18a3-259">O local de uma janela na *ordem z superior* também é determinado pelo fato de estar atualmente ativo ou não.</span><span class="sxs-lookup"><span data-stu-id="e18a3-259">The location of a window in the *topmost z-order* is also determined by whether it is currently active or not.</span></span> <span data-ttu-id="e18a3-260">Além disso, janelas na ordem z superior sempre estão localizadas acima das janelas na ordem z normal.</span><span class="sxs-lookup"><span data-stu-id="e18a3-260">Furthermore, windows in the topmost z-order are always located above windows in the normal z-order.</span></span> <span data-ttu-id="e18a3-261">Uma janela está localizada na ordem z superior definindo sua propriedade <xref:System.Windows.Window.Topmost%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="e18a3-261">A window is located in the topmost z-order by setting its <xref:System.Windows.Window.Topmost%2A> property to `true`.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 <span data-ttu-id="e18a3-262">Dentro de cada ordem z, a janela ativa no momento aparece acima de todas as outras janelas na mesma ordem z.</span><span class="sxs-lookup"><span data-stu-id="e18a3-262">Within each z-order, the currently active window appears above all other windows in the same z-order.</span></span>  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a><span data-ttu-id="e18a3-263">Tamanho da janela</span><span class="sxs-lookup"><span data-stu-id="e18a3-263">Window Size</span></span>  
 <span data-ttu-id="e18a3-264">Além de ter um local de área de trabalho, uma janela tem um tamanho que é determinado por várias propriedades, incluindo as várias propriedades width e Height e <xref:System.Windows.Window.SizeToContent%2A>.</span><span class="sxs-lookup"><span data-stu-id="e18a3-264">Besides having a desktop location, a window has a size that is determined by several properties, including the various width and height properties and <xref:System.Windows.Window.SizeToContent%2A>.</span></span>  
  
 <span data-ttu-id="e18a3-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>e <xref:System.Windows.FrameworkElement.MaxWidth%2A> são usados para gerenciar o intervalo de larguras que uma janela pode ter durante seu tempo de vida e são configurados conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e18a3-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.MaxWidth%2A> are used to manage the range of widths that a window can have during its lifetime, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 <span data-ttu-id="e18a3-266">A altura da janela é gerenciada por <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>e <xref:System.Windows.FrameworkElement.MaxHeight%2A>e são configuradas conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e18a3-266">Window height is managed by <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 <span data-ttu-id="e18a3-267">Já que os diversos valores de largura e de altura especificam um intervalo, é possível que a largura e altura de uma janela redimensionável estejam em qualquer lugar dentro do intervalo especificado para a respectiva dimensão.</span><span class="sxs-lookup"><span data-stu-id="e18a3-267">Because the various width values and height values each specify a range, it is possible for the width and height of a resizable window to be anywhere within the specified range for the respective dimension.</span></span> <span data-ttu-id="e18a3-268">Para detectar sua largura e altura atuais, inspecione <xref:System.Windows.FrameworkElement.ActualWidth%2A> e <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="e18a3-268">To detect its current width and height, inspect <xref:System.Windows.FrameworkElement.ActualWidth%2A> and <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectively.</span></span>  
  
 <span data-ttu-id="e18a3-269">Se você quiser que a largura e a altura da janela tenham um tamanho que se ajuste ao tamanho do conteúdo da janela, você poderá usar a propriedade <xref:System.Windows.Window.SizeToContent%2A>, que tem os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="e18a3-269">If you'd like the width and height of your window to have a size that fits to the size of the window's content, you can use the <xref:System.Windows.Window.SizeToContent%2A> property, which has the following values:</span></span>  
  
- <span data-ttu-id="e18a3-270"><xref:System.Windows.SizeToContent.Manual></span><span class="sxs-lookup"><span data-stu-id="e18a3-270"><xref:System.Windows.SizeToContent.Manual>.</span></span> <span data-ttu-id="e18a3-271">Sem efeito (padrão).</span><span class="sxs-lookup"><span data-stu-id="e18a3-271">No effect (default).</span></span>  
  
- <span data-ttu-id="e18a3-272"><xref:System.Windows.SizeToContent.Width></span><span class="sxs-lookup"><span data-stu-id="e18a3-272"><xref:System.Windows.SizeToContent.Width>.</span></span> <span data-ttu-id="e18a3-273">Ajustar à largura do conteúdo, que tem o mesmo efeito que definir <xref:System.Windows.FrameworkElement.MinWidth%2A> e <xref:System.Windows.FrameworkElement.MaxWidth%2A> à largura do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="e18a3-273">Fit to content width, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
- <span data-ttu-id="e18a3-274"><xref:System.Windows.SizeToContent.Height></span><span class="sxs-lookup"><span data-stu-id="e18a3-274"><xref:System.Windows.SizeToContent.Height>.</span></span> <span data-ttu-id="e18a3-275">Ajustar à altura do conteúdo, que tem o mesmo efeito que definir <xref:System.Windows.FrameworkElement.MinHeight%2A> e <xref:System.Windows.FrameworkElement.MaxHeight%2A> a altura do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="e18a3-275">Fit to content height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content.</span></span>  
  
- <span data-ttu-id="e18a3-276"><xref:System.Windows.SizeToContent.WidthAndHeight></span><span class="sxs-lookup"><span data-stu-id="e18a3-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span></span> <span data-ttu-id="e18a3-277">Ajustar à largura e à altura do conteúdo, que tem o mesmo efeito que definir <xref:System.Windows.FrameworkElement.MinHeight%2A> e <xref:System.Windows.FrameworkElement.MaxHeight%2A> à altura do conteúdo, e definir ambos <xref:System.Windows.FrameworkElement.MinWidth%2A> e <xref:System.Windows.FrameworkElement.MaxWidth%2A> como a largura do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="e18a3-277">Fit to content width and height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content, and setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
 <span data-ttu-id="e18a3-278">O exemplo a seguir mostra uma janela que se dimensiona automaticamente para ajustar-se ao próprio conteúdo, verticalmente e horizontalmente, quando mostrada pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="e18a3-278">The following example shows a window that automatically sizes to fit its content, both vertically and horizontally, when first shown.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 <span data-ttu-id="e18a3-279">O exemplo a seguir mostra como definir a propriedade <xref:System.Windows.Window.SizeToContent%2A> no código para especificar como uma janela é redimensionada para se ajustar ao seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="e18a3-279">The following example shows how to set the <xref:System.Windows.Window.SizeToContent%2A> property in code to specify how a window resizes to fit its content    .</span></span>
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a><span data-ttu-id="e18a3-280">Ordem de precedência para propriedades de dimensionamento</span><span class="sxs-lookup"><span data-stu-id="e18a3-280">Order of Precedence for Sizing Properties</span></span>  
 <span data-ttu-id="e18a3-281">Essencialmente, as diversas propriedades de tamanhos de uma janela são combinadas para definir o intervalo de largura e altura de uma janela redimensionável.</span><span class="sxs-lookup"><span data-stu-id="e18a3-281">Essentially, the various sizes properties of a window combine to define the range of width and height for a resizable window.</span></span> <span data-ttu-id="e18a3-282">Para garantir que um intervalo válido seja mantido, <xref:System.Windows.Window> avalia os valores das propriedades de tamanho usando as seguintes ordens de precedência.</span><span class="sxs-lookup"><span data-stu-id="e18a3-282">To ensure a valid range is maintained, <xref:System.Windows.Window> evaluates the values of the size properties using the following orders of precedence.</span></span>  
  
 <span data-ttu-id="e18a3-283">**Para propriedades de altura:**</span><span class="sxs-lookup"><span data-stu-id="e18a3-283">**For Height Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="e18a3-284">**Para propriedades de largura:**</span><span class="sxs-lookup"><span data-stu-id="e18a3-284">**For Width Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="e18a3-285">A ordem de precedência também pode determinar o tamanho de uma janela quando ela é maximizada, que é gerenciada com a propriedade <xref:System.Windows.Window.WindowState%2A>.</span><span class="sxs-lookup"><span data-stu-id="e18a3-285">The order of precedence can also determine the size of a window when it is maximized, which is managed with the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="WindowState"></a>   
## <a name="window-state"></a><span data-ttu-id="e18a3-286">Estado da janela</span><span class="sxs-lookup"><span data-stu-id="e18a3-286">Window State</span></span>  
 <span data-ttu-id="e18a3-287">Durante o tempo de vida de uma janela redimensionável, ela pode ter três estados: normal, minimizada e maximizada.</span><span class="sxs-lookup"><span data-stu-id="e18a3-287">During the lifetime of a resizable window, it can have three states: normal, minimized, and maximized.</span></span> <span data-ttu-id="e18a3-288">Uma janela com um estado *normal* é o estado padrão de uma janela.</span><span class="sxs-lookup"><span data-stu-id="e18a3-288">A window with a *normal* state is the default state of a window.</span></span> <span data-ttu-id="e18a3-289">Uma janela com esse estado permitirá que um usuário a mova e a redimensione usando uma alça de redimensionamento ou a borda, se ela for redimensionável.</span><span class="sxs-lookup"><span data-stu-id="e18a3-289">A window with this state allows a user to move and resize it by using a resize grip or the border, if it is resizable.</span></span>  
  
 <span data-ttu-id="e18a3-290">Uma janela com um estado *minimizado* será recolhida ao botão da barra de tarefas se <xref:System.Windows.Window.ShowInTaskbar%2A> estiver definida como `true`; caso contrário, ele recolhe para o menor tamanho possível que pode ser e se realoque para o canto inferior esquerdo da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e18a3-290">A window with a *minimized* state collapses to its task bar button if <xref:System.Windows.Window.ShowInTaskbar%2A> is set to `true`; otherwise, it collapses to the smallest possible size it can be and relocates itself to the bottom-left corner of the desktop.</span></span> <span data-ttu-id="e18a3-291">Nenhum tipo de janela minimizada pode ser redimensionado usando uma borda ou alça redimensionável, embora uma janela minimizada não mostrada na barra de tarefas possa ser arrastada pela área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e18a3-291">Neither type of minimized window can be resized using a border or resize grip, although a minimized window that isn't shown in the task bar can be dragged around the desktop.</span></span>  
  
 <span data-ttu-id="e18a3-292">Uma janela com um estado *maximizado* se expande para o tamanho máximo que pode ser, que será tão grande quanto suas propriedades <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>e <xref:System.Windows.Window.SizeToContent%2A> ditar.</span><span class="sxs-lookup"><span data-stu-id="e18a3-292">A window with a *maximized* state expands to the maximum size it can be, which will only be as large as its <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.Window.SizeToContent%2A> properties dictate.</span></span> <span data-ttu-id="e18a3-293">Assim como ocorre com uma janela minimizada, uma janela maximizada não pode ser redimensionada usando uma alça de redimensionamento ou arrastando a borda.</span><span class="sxs-lookup"><span data-stu-id="e18a3-293">Like a minimized window, a maximized window cannot be resized by using a resize grip or by dragging the border.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e18a3-294">Os valores das propriedades <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>e <xref:System.Windows.FrameworkElement.Height%2A> de uma janela sempre representam os valores para o estado normal, mesmo quando a janela está atualmente maximizada ou minimizada.</span><span class="sxs-lookup"><span data-stu-id="e18a3-294">The values of the <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.Height%2A> properties of a window always represent the values for the normal state, even when the window is currently maximized or minimized.</span></span>  
  
 <span data-ttu-id="e18a3-295">O estado de uma janela pode ser configurado definindo sua propriedade <xref:System.Windows.Window.WindowState%2A>, que pode ter um dos seguintes valores de enumeração <xref:System.Windows.WindowState>:</span><span class="sxs-lookup"><span data-stu-id="e18a3-295">The state of a window can be configured by setting its <xref:System.Windows.Window.WindowState%2A> property, which can have one of the following <xref:System.Windows.WindowState> enumeration values:</span></span>  
  
- <span data-ttu-id="e18a3-296"><xref:System.Windows.WindowState.Normal> (padrão)</span><span class="sxs-lookup"><span data-stu-id="e18a3-296"><xref:System.Windows.WindowState.Normal> (default)</span></span>  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 <span data-ttu-id="e18a3-297">O exemplo a seguir mostra como criar uma janela que é mostrada como maximizada quando é aberta.</span><span class="sxs-lookup"><span data-stu-id="e18a3-297">The following example shows how to create a window that is shown as maximized when it opens.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 <span data-ttu-id="e18a3-298">Em geral, você deve definir <xref:System.Windows.Window.WindowState%2A> para configurar o estado inicial de uma janela.</span><span class="sxs-lookup"><span data-stu-id="e18a3-298">In general, you should set <xref:System.Windows.Window.WindowState%2A> to configure the initial state of a window.</span></span> <span data-ttu-id="e18a3-299">Assim que uma janela redimensionável é exibida, os usuários podem pressionar os botões minimizar, maximizar e restaurar na barra de título da janela para alterar o estado desta.</span><span class="sxs-lookup"><span data-stu-id="e18a3-299">Once a resizable window is shown, users can press the minimize, maximize, and restore buttons on the window's title bar to change the window state.</span></span>  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a><span data-ttu-id="e18a3-300">Aparência da janela</span><span class="sxs-lookup"><span data-stu-id="e18a3-300">Window Appearance</span></span>  
 <span data-ttu-id="e18a3-301">Você pode alterar a aparência da área de cliente de uma janela adicionando conteúdo específico de janela a ela, por exemplo, botões, rótulos e caixas de texto.</span><span class="sxs-lookup"><span data-stu-id="e18a3-301">You change the appearance of the client area of a window by adding window-specific content to it, such as buttons, labels, and text boxes.</span></span> <span data-ttu-id="e18a3-302">Para configurar a área não cliente, <xref:System.Windows.Window> fornece várias propriedades, que incluem <xref:System.Windows.Window.Icon%2A> para definir o ícone de uma janela e <xref:System.Windows.Window.Title%2A> para definir seu título.</span><span class="sxs-lookup"><span data-stu-id="e18a3-302">To configure the non-client area, <xref:System.Windows.Window> provides several properties, which include <xref:System.Windows.Window.Icon%2A> to set a window's icon and <xref:System.Windows.Window.Title%2A> to set its title.</span></span>  
  
 <span data-ttu-id="e18a3-303">Você também pode alterar a aparência e o comportamento da borda da área de não cliente configurando o modo de redimensionamento da janela, o estilo da janela e definindo se essa janela aparece ou não como um botão na barra de tarefas da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e18a3-303">You can also change the appearance and behavior of non-client area border by configuring a window's resize mode, window style, and whether it appears as a button in the desktop task bar.</span></span>  

<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a><span data-ttu-id="e18a3-304">Modo de redimensionamento</span><span class="sxs-lookup"><span data-stu-id="e18a3-304">Resize Mode</span></span>  
 <span data-ttu-id="e18a3-305">Dependendo da propriedade <xref:System.Windows.Window.WindowStyle%2A>, você pode controlar como (e se) os usuários podem redimensionar a janela.</span><span class="sxs-lookup"><span data-stu-id="e18a3-305">Depending on the <xref:System.Windows.Window.WindowStyle%2A> property, you can control how (and if) users can resize the window.</span></span> <span data-ttu-id="e18a3-306">A escolha do estilo de janela afeta se um usuário pode redimensionar a janela arrastando sua borda com o mouse, se os botões **minimizar**, **maximizar**e **redimensionar** aparecem na área não cliente e, se forem exibidos, se eles estão habilitado.</span><span class="sxs-lookup"><span data-stu-id="e18a3-306">The choice of window style affects whether a user can resize the window by dragging its border with the mouse, whether the **Minimize**, **Maximize**, and **Resize** buttons appear on the non-client area, and, if they do appear, whether they are enabled.</span></span>  
  
 <span data-ttu-id="e18a3-307">Você pode configurar como uma janela é redimensionada definindo sua propriedade <xref:System.Windows.Window.ResizeMode%2A>, que pode ser um dos seguintes valores de enumeração <xref:System.Windows.ResizeMode>:</span><span class="sxs-lookup"><span data-stu-id="e18a3-307">You can configure how a window resizes by setting its <xref:System.Windows.Window.ResizeMode%2A> property, which can be one of the following <xref:System.Windows.ResizeMode> enumeration values:</span></span>  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <span data-ttu-id="e18a3-308"><xref:System.Windows.ResizeMode.CanResize> (padrão)</span><span class="sxs-lookup"><span data-stu-id="e18a3-308"><xref:System.Windows.ResizeMode.CanResize> (default)</span></span>  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 <span data-ttu-id="e18a3-309">Assim como ocorre com <xref:System.Windows.Window.WindowStyle%2A>, o modo de redimensionamento de uma janela é improvável de ser alterado durante seu tempo de vida, o que significa que você provavelmente a definirá de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] marcação.</span><span class="sxs-lookup"><span data-stu-id="e18a3-309">As with <xref:System.Windows.Window.WindowStyle%2A>, the resize mode of a window is unlikely to change during its lifetime, which means that you'll most likely set it from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 <span data-ttu-id="e18a3-310">Observe que você pode detectar se uma janela é maximizada, minimizada ou restaurada inspecionando a propriedade <xref:System.Windows.Window.WindowState%2A>.</span><span class="sxs-lookup"><span data-stu-id="e18a3-310">Note that you can detect whether a window is maximized, minimized, or restored by inspecting the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a><span data-ttu-id="e18a3-311">Estilo de Janela</span><span class="sxs-lookup"><span data-stu-id="e18a3-311">Window Style</span></span>  
 <span data-ttu-id="e18a3-312">A borda que é exposta da área de não cliente de uma janela é adequada para a maioria dos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e18a3-312">The border that is exposed from the non-client area of a window is suitable for most applications.</span></span> <span data-ttu-id="e18a3-313">No entanto, existem circunstâncias em que diferentes tipos de bordas são necessários ou em que nenhuma borda é necessária, dependendo do tipo de janela.</span><span class="sxs-lookup"><span data-stu-id="e18a3-313">However, there are circumstances where different types of borders are needed, or no borders are needed at all, depending on the type of window.</span></span>  
  
 <span data-ttu-id="e18a3-314">Para controlar o tipo de borda que uma janela Obtém, defina sua propriedade <xref:System.Windows.Window.WindowStyle%2A> com um dos seguintes valores da enumeração <xref:System.Windows.WindowStyle>:</span><span class="sxs-lookup"><span data-stu-id="e18a3-314">To control what type of border a window gets, you set its <xref:System.Windows.Window.WindowStyle%2A> property with one of the following values of the <xref:System.Windows.WindowStyle> enumeration:</span></span>  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <span data-ttu-id="e18a3-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (padrão)</span><span class="sxs-lookup"><span data-stu-id="e18a3-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (default)</span></span>  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 <span data-ttu-id="e18a3-316">O efeito desses estilos de janela é ilustrado na figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="e18a3-316">The effect of these window styles are illustrated in the following figure:</span></span>  
  
 ![Ilustração de estilos de borda de janela.](./media/wpf-windows-overview/window-border-styles.png)  
  
 <span data-ttu-id="e18a3-318">Você pode definir <xref:System.Windows.Window.WindowStyle%2A> usando a marcação ou o código de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; Como é improvável que seja alterado durante o tempo de vida de uma janela, você provavelmente a configurará usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] marcação.</span><span class="sxs-lookup"><span data-stu-id="e18a3-318">You can set <xref:System.Windows.Window.WindowStyle%2A> using either [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup or code; because it is unlikely to change during the lifetime of a window, you will most likely configure it using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a><span data-ttu-id="e18a3-319">Estilo de janela não retangular</span><span class="sxs-lookup"><span data-stu-id="e18a3-319">Non-Rectangular Window Style</span></span>  
 <span data-ttu-id="e18a3-320">Há também situações em que os estilos de borda que <xref:System.Windows.Window.WindowStyle%2A> permitem que você não seja suficiente.</span><span class="sxs-lookup"><span data-stu-id="e18a3-320">There are also situations where the border styles that <xref:System.Windows.Window.WindowStyle%2A> allows you to have are not sufficient.</span></span> <span data-ttu-id="e18a3-321">Por exemplo, você pode querer criar um aplicativo com uma borda não retangular, como o Microsoft Windows Media Player usa.</span><span class="sxs-lookup"><span data-stu-id="e18a3-321">For example, you may want to create an application with a non-rectangular border, like Microsoft Windows Media Player uses.</span></span>  
  
 <span data-ttu-id="e18a3-322">Por exemplo, considere a janela de bolha de fala mostrada na figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="e18a3-322">For example, consider the speech bubble window shown in the following figure:</span></span>  
  
 ![Uma janela de bolhas de fala que diz arrastar para mim.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 <span data-ttu-id="e18a3-324">Esse tipo de janela pode ser criado definindo a propriedade <xref:System.Windows.Window.WindowStyle%2A> como <xref:System.Windows.WindowStyle.None>e usando suporte especial que <xref:System.Windows.Window> tem para transparência.</span><span class="sxs-lookup"><span data-stu-id="e18a3-324">This type of window can be created by setting the <xref:System.Windows.Window.WindowStyle%2A> property to <xref:System.Windows.WindowStyle.None>, and by using special support that <xref:System.Windows.Window> has for transparency.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 <span data-ttu-id="e18a3-325">Essa combinação de valores instrui a janela a ser renderizada completamente transparente.</span><span class="sxs-lookup"><span data-stu-id="e18a3-325">This combination of values instructs the window to render completely transparent.</span></span> <span data-ttu-id="e18a3-326">Nesse estado, os adornos da área de não cliente da janela (o menu Fechar, botões Minimizar, Maximizar e Restaurar e assim por diante) não podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="e18a3-326">In this state, the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used.</span></span> <span data-ttu-id="e18a3-327">Consequentemente, você precisa fornecer os seus próprios.</span><span class="sxs-lookup"><span data-stu-id="e18a3-327">Consequently, you need to provide your own.</span></span>  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a><span data-ttu-id="e18a3-328">Presença da barra de tarefas</span><span class="sxs-lookup"><span data-stu-id="e18a3-328">Task Bar Presence</span></span>  

<span data-ttu-id="e18a3-329">A aparência padrão de uma janela inclui um botão da barra de tarefas, como aquele mostrado na figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="e18a3-329">The default appearance of a window includes a taskbar button, like the one shown in the following figure:</span></span>

 ![Captura de tela que mostra uma janela com um botão da barra de tarefas.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 <span data-ttu-id="e18a3-331">Alguns tipos de janelas não têm um botão da barra de tarefas, como caixas de mensagens e caixas de diálogo (consulte [visão geral das caixas de diálogo](dialog-boxes-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="e18a3-331">Some types of windows don't have a task bar button, such as message boxes and dialog boxes (see [Dialog Boxes Overview](dialog-boxes-overview.md)).</span></span> <span data-ttu-id="e18a3-332">Você pode controlar se o botão da barra de tarefas de uma janela é mostrado definindo a propriedade <xref:System.Windows.Window.ShowInTaskbar%2A> (`true` por padrão).</span><span class="sxs-lookup"><span data-stu-id="e18a3-332">You can control whether the task bar button for a window is shown by setting the <xref:System.Windows.Window.ShowInTaskbar%2A> property (`true` by default).</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a><span data-ttu-id="e18a3-333">Considerações sobre segurança</span><span class="sxs-lookup"><span data-stu-id="e18a3-333">Security Considerations</span></span>  
 <span data-ttu-id="e18a3-334"><xref:System.Windows.Window> requer que `UnmanagedCode` permissão de segurança seja instanciada.</span><span class="sxs-lookup"><span data-stu-id="e18a3-334"><xref:System.Windows.Window> requires `UnmanagedCode` security permission to be instantiated.</span></span> <span data-ttu-id="e18a3-335">Para aplicativos instalados e iniciados no computador local, isso se encaixa no conjunto de permissões concedidas ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e18a3-335">For applications installed on and launched from the local machine, this falls within the set of permissions that are granted to the application.</span></span>  
  
 <span data-ttu-id="e18a3-336">No entanto, isso fica fora do conjunto de permissões concedidos a aplicativos iniciados pela Internet ou pela zona da intranet local usando o ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="e18a3-336">However, this falls outside the set of permissions granted to applications that are launched from the Internet or Local intranet zone using ClickOnce.</span></span> <span data-ttu-id="e18a3-337">Consequentemente, os usuários receberão um aviso de segurança do ClickOnce e precisarão elevar o conjunto de permissões do aplicativo para confiança total.</span><span class="sxs-lookup"><span data-stu-id="e18a3-337">Consequently, users will receive a ClickOnce security warning and will need to elevate the permission set for the application to full trust.</span></span>  
  
 <span data-ttu-id="e18a3-338">Além disso, XBAPs não podem mostrar janelas ou caixas de diálogo por padrão.</span><span class="sxs-lookup"><span data-stu-id="e18a3-338">Additionally, XBAPs cannot show windows or dialog boxes by default.</span></span> <span data-ttu-id="e18a3-339">Para obter uma discussão sobre considerações de segurança de aplicativo autônomo, consulte [estratégia de segurança do WPF – segurança da plataforma](../wpf-security-strategy-platform-security.md).</span><span class="sxs-lookup"><span data-stu-id="e18a3-339">For a discussion on standalone application security considerations, see [WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).</span></span>  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a><span data-ttu-id="e18a3-340">Outros tipos de janelas</span><span class="sxs-lookup"><span data-stu-id="e18a3-340">Other Types of Windows</span></span>  
 <span data-ttu-id="e18a3-341"><xref:System.Windows.Navigation.NavigationWindow> é uma janela projetada para hospedar conteúdo navegável.</span><span class="sxs-lookup"><span data-stu-id="e18a3-341"><xref:System.Windows.Navigation.NavigationWindow> is a window that is designed to host navigable content.</span></span> <span data-ttu-id="e18a3-342">Para obter mais informações, consulte [visão geral de navegação](navigation-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="e18a3-342">For more information, see [Navigation Overview](navigation-overview.md)).</span></span>  
  
 <span data-ttu-id="e18a3-343">Caixas de diálogo são janelas que geralmente são usadas para coletar informações de um usuário para concluir uma função.</span><span class="sxs-lookup"><span data-stu-id="e18a3-343">Dialog boxes are windows that are often used to gather information from a user to complete a function.</span></span> <span data-ttu-id="e18a3-344">Por exemplo, quando um usuário deseja abrir um arquivo, a caixa de diálogo **Abrir arquivo** geralmente é exibida por um aplicativo para obter o nome do arquivo do usuário.</span><span class="sxs-lookup"><span data-stu-id="e18a3-344">For example, when a user wants to open a file, the **Open File** dialog box is usually displayed by an application to get the file name from the user.</span></span> <span data-ttu-id="e18a3-345">Para obter mais informações, consulte [Visão geral das caixas de diálogo](dialog-boxes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e18a3-345">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e18a3-346">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e18a3-346">See also</span></span>

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [<span data-ttu-id="e18a3-347">Visão geral das caixas de diálogo</span><span class="sxs-lookup"><span data-stu-id="e18a3-347">Dialog Boxes Overview</span></span>](dialog-boxes-overview.md)
- [<span data-ttu-id="e18a3-348">Compilar um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="e18a3-348">Building a WPF Application</span></span>](building-a-wpf-application-wpf.md)
