---
title: Introdução ao WPF
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
dev_langs:
- csharp
- vb
ms.openlocfilehash: d8ea49bbe400c5ec478a94ad7c1adb759af28abb
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454200"
---
# <a name="wpf-overview"></a><span data-ttu-id="516c6-102">Visão geral do WPF</span><span class="sxs-lookup"><span data-stu-id="516c6-102">WPF overview</span></span>

<span data-ttu-id="516c6-103">O Windows Presentation Foundation (WPF) permite criar aplicativos para cliente de área de trabalho do Windows com experiências de usuário visualmente impressionantes.</span><span class="sxs-lookup"><span data-stu-id="516c6-103">Windows Presentation Foundation (WPF) lets you create desktop client applications for Windows with visually stunning user experiences.</span></span>

![Amostra de interface do usuário do Contoso Healthcare](media/introduction-to-wpf/wpfintrofigure24.png)

<span data-ttu-id="516c6-105">O núcleo do WPF é um mecanismo de renderização que não depende da resolução e baseado em vetor, criado para tirar proveito de hardwares gráficos modernos.</span><span class="sxs-lookup"><span data-stu-id="516c6-105">The core of WPF is a resolution-independent and vector-based rendering engine that is built to take advantage of modern graphics hardware.</span></span> <span data-ttu-id="516c6-106">O WPF estende o núcleo com um conjunto abrangente de funcionalidades de desenvolvimento de aplicativos que incluem linguagem XAML, controles, associação de dados, layout, elementos gráficos 2D e 3D, animação, estilos, modelos, documentos, mídia, texto e tipografia.</span><span class="sxs-lookup"><span data-stu-id="516c6-106">WPF extends the core with a comprehensive set of application-development features that include Extensible Application Markup Language (XAML), controls, data binding, layout, 2D and 3D graphics, animation, styles, templates, documents, media, text, and typography.</span></span> <span data-ttu-id="516c6-107">O WPF faz parte do .NET; portanto, você pode criar aplicativos que incorporam outros elementos da API .NET.</span><span class="sxs-lookup"><span data-stu-id="516c6-107">WPF is part of .NET, so you can build applications that incorporate other elements of the .NET API.</span></span>

<span data-ttu-id="516c6-108">Esta visão geral é destinada para principiantes e aborda os principais conceitos e funcionalidades do WPF.</span><span class="sxs-lookup"><span data-stu-id="516c6-108">This overview is intended for newcomers and covers the key capabilities and concepts of WPF.</span></span>

## <a name="program-with-wpf"></a><span data-ttu-id="516c6-109">Programar com o WPF</span><span class="sxs-lookup"><span data-stu-id="516c6-109">Program with WPF</span></span>

<span data-ttu-id="516c6-110">O WPF existe como um subconjunto de tipos .NET que (geralmente) estão localizados no namespace <xref:System.Windows>.</span><span class="sxs-lookup"><span data-stu-id="516c6-110">WPF exists as a subset of .NET types that are (for the most part) located in the <xref:System.Windows> namespace.</span></span> <span data-ttu-id="516c6-111">Se você tiver criado aplicativos com o .NET anteriormente usando tecnologias gerenciadas como ASP.NET e Windows Forms, a experiência essencial do WPF em programação deverá ser conhecida; você cria instâncias de classes, define propriedades, chama métodos e manipula eventos usando sua linguagem de programação .NET favorita como C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="516c6-111">If you have previously built applications with .NET using managed technologies like ASP.NET and Windows Forms, the fundamental WPF programming experience should be familiar; you instantiate classes, set properties, call methods, and handle events, using your favorite .NET programming language, such as C# or Visual Basic.</span></span>

<span data-ttu-id="516c6-112">O WPF inclui constructos de programação adicionais que aprimoram as propriedades e eventos: [propriedades de dependência](advanced/dependency-properties-overview.md) e [eventos roteados](advanced/routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="516c6-112">WPF includes additional programming constructs that enhance properties and events: [dependency properties](advanced/dependency-properties-overview.md) and [routed events](advanced/routed-events-overview.md).</span></span>

## <a name="markup-and-code-behind"></a><span data-ttu-id="516c6-113">Marcação e code-behind</span><span class="sxs-lookup"><span data-stu-id="516c6-113">Markup and code-behind</span></span>

<span data-ttu-id="516c6-114">O WPF permite que você desenvolva um aplicativo usando *marcação* e *code-behind*, uma experiência com a qual os desenvolvedores do ASP.NET devem estar familiarizados.</span><span class="sxs-lookup"><span data-stu-id="516c6-114">WPF lets you develop an application using both *markup* and *code-behind*, an experience with which ASP.NET developers should be familiar.</span></span> <span data-ttu-id="516c6-115">Você geralmente usa marcação XAML para implementar a aparência de um aplicativo enquanto usa linguagens de programação gerenciadas (code-behind) para implementar seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="516c6-115">You generally use XAML markup to implement the appearance of an application while using managed programming languages (code-behind) to implement its behavior.</span></span> <span data-ttu-id="516c6-116">Essa separação de aparência e comportamento apresenta os seguintes benefícios:</span><span class="sxs-lookup"><span data-stu-id="516c6-116">This separation of appearance and behavior has the following benefits:</span></span>

- <span data-ttu-id="516c6-117">Custos de desenvolvimento e manutenção são reduzidos, pois a marcação específica da aparência não está acoplada ao comportamento específico do código.</span><span class="sxs-lookup"><span data-stu-id="516c6-117">Development and maintenance costs are reduced because appearance-specific markup is not tightly coupled with behavior-specific code.</span></span>

- <span data-ttu-id="516c6-118">O desenvolvimento é mais eficiente porque os designers podem implementar a aparência de um aplicativo simultaneamente com os desenvolvedores que estão implementando o comportamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="516c6-118">Development is more efficient because designers can implement an application's appearance simultaneously with developers who are implementing the application's behavior.</span></span>

- <span data-ttu-id="516c6-119">A [globalização e localização](advanced/wpf-globalization-and-localization-overview.md) de aplicativos WPF é simplificada.</span><span class="sxs-lookup"><span data-stu-id="516c6-119">[Globalization and localization](advanced/wpf-globalization-and-localization-overview.md) for WPF applications is simplified.</span></span>

### <a name="markup"></a><span data-ttu-id="516c6-120">Marcação</span><span class="sxs-lookup"><span data-stu-id="516c6-120">Markup</span></span>

<span data-ttu-id="516c6-121">O XAML é uma linguagem de marcação baseada em XML que implementa a aparência de um aplicativo de forma declarativa.</span><span class="sxs-lookup"><span data-stu-id="516c6-121">XAML is an XML-based markup language that implements an application's appearance declaratively.</span></span> <span data-ttu-id="516c6-122">Normalmente, ele é usado para criar janelas, caixas de diálogo, páginas e controles de usuário e para preenchê-los com controles, formas e elementos gráficos.</span><span class="sxs-lookup"><span data-stu-id="516c6-122">You typically use it to create windows, dialog boxes, pages, and user controls, and to fill them with controls, shapes, and graphics.</span></span>

<span data-ttu-id="516c6-123">O exemplo a seguir usa XAML para implementar a aparência de uma janela que contém um único botão:</span><span class="sxs-lookup"><span data-stu-id="516c6-123">The following example uses XAML to implement the appearance of a window that contains a single button:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

<span data-ttu-id="516c6-124">Especificamente, esse XAML define uma janela e um botão usando os elementos `Window` e `Button`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="516c6-124">Specifically, this XAML defines a window and a button by using the `Window` and `Button` elements, respectively.</span></span> <span data-ttu-id="516c6-125">Cada elemento é configurado com atributos, como o atributo `Title` do elemento `Window` para especificar o texto da barra de título da janela.</span><span class="sxs-lookup"><span data-stu-id="516c6-125">Each element is configured with attributes, such as the `Window` element's `Title` attribute to specify the window's title-bar text.</span></span> <span data-ttu-id="516c6-126">Em tempo de execução, o WPF converte os elementos e atributos que estão definidos na marcação para instâncias de classes do WPF.</span><span class="sxs-lookup"><span data-stu-id="516c6-126">At run time, WPF converts the elements and attributes that are defined in markup to instances of WPF classes.</span></span> <span data-ttu-id="516c6-127">Por exemplo, o elemento `Window` é convertido em uma instância da classe <xref:System.Windows.Window>, cuja propriedade <xref:System.Windows.Window.Title%2A> é o valor do atributo `Title`.</span><span class="sxs-lookup"><span data-stu-id="516c6-127">For example, the `Window` element is converted to an instance of the <xref:System.Windows.Window> class whose <xref:System.Windows.Window.Title%2A> property is the value of the `Title` attribute.</span></span>

<span data-ttu-id="516c6-128">A figura a seguir mostra a interface do usuário (IU) que é definida pelo XAML no exemplo anterior:</span><span class="sxs-lookup"><span data-stu-id="516c6-128">The following figure shows the user interface (UI) that is defined by the XAML in the previous example:</span></span>

![Uma janela que contém um botão](media/introduction-to-wpf/wpfintrofigure10.png)

<span data-ttu-id="516c6-130">Já que o XAML é baseado em XML, a interface do usuário que você escreve com ele é montada em uma hierarquia de elementos aninhados conhecida como uma [árvore de elementos](advanced/trees-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="516c6-130">Since XAML is XML-based, the UI that you compose with it is assembled in a hierarchy of nested elements known as an [element tree](advanced/trees-in-wpf.md).</span></span> <span data-ttu-id="516c6-131">A árvore de elementos fornece uma maneira lógica e intuitiva para criar e gerenciar interfaces do usuário.</span><span class="sxs-lookup"><span data-stu-id="516c6-131">The element tree provides a logical and intuitive way to create and manage UIs.</span></span>

### <a name="code-behind"></a><span data-ttu-id="516c6-132">Code-behind</span><span class="sxs-lookup"><span data-stu-id="516c6-132">Code-behind</span></span>

<span data-ttu-id="516c6-133">O comportamento principal de um aplicativo é implementar a funcionalidade que responde às interações do usuário, incluindo a manipulação de eventos (por exemplo, clicar em um menu, barra de ferramentas ou botão) e chamar a lógica de negócios e lógica de acesso a dados como resposta.</span><span class="sxs-lookup"><span data-stu-id="516c6-133">The main behavior of an application is to implement the functionality that responds to user interactions, including handling events (for example, clicking a menu, tool bar, or button) and calling business logic and data access logic in response.</span></span> <span data-ttu-id="516c6-134">No WPF, esse comportamento é implementado no código que está associado à marcação.</span><span class="sxs-lookup"><span data-stu-id="516c6-134">In WPF, this behavior is implemented in code that is associated with markup.</span></span> <span data-ttu-id="516c6-135">Esse tipo de código é conhecido como code-behind.</span><span class="sxs-lookup"><span data-stu-id="516c6-135">This type of code is known as code-behind.</span></span> <span data-ttu-id="516c6-136">O exemplo a seguir mostra a marcação atualizada do exemplo anterior e o code-behind:</span><span class="sxs-lookup"><span data-stu-id="516c6-136">The following example shows the updated markup from the previous example and the code-behind:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.AWindow"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button" Click="button_Click">Click Me!</Button>

</Window>
```

```csharp
using System.Windows; // Window, RoutedEventArgs, MessageBox 

namespace SDKSample
{
    public partial class AWindow : Window
    {
        public AWindow()
        {
            // InitializeComponent call is required to merge the UI 
            // that is defined in markup with this class, including  
            // setting properties and registering event handlers
            InitializeComponent();
        }

        void button_Click(object sender, RoutedEventArgs e)
        {
            // Show message box when button is clicked.
            MessageBox.Show("Hello, Windows Presentation Foundation!");
        }
    }
}
```

```vb
Namespace SDKSample

    Partial Public Class AWindow
        Inherits System.Windows.Window

        Public Sub New()

            ' InitializeComponent call is required to merge the UI 
            ' that is defined in markup with this class, including  
            ' setting properties and registering event handlers
            InitializeComponent()

        End Sub 

        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)

            ' Show message box when button is clicked.
            MessageBox.Show("Hello, Windows Presentation Foundation!")

        End Sub 

    End Class 

End Namespace
```

<span data-ttu-id="516c6-137">Neste exemplo, o code-behind implementa uma classe derivada da classe <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="516c6-137">In this example, the code-behind implements a class that derives from the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="516c6-138">O atributo `x:Class` é usado para associar a marcação com a classe code-behind.</span><span class="sxs-lookup"><span data-stu-id="516c6-138">The `x:Class` attribute is used to associate the markup with the code-behind class.</span></span> <span data-ttu-id="516c6-139">`InitializeComponent` é chamado de construtor da classe code-behind para mesclar a interface do usuário que é definida na marcação com a classe code-behind.</span><span class="sxs-lookup"><span data-stu-id="516c6-139">`InitializeComponent` is called from the code-behind class's constructor to merge the UI that is defined in markup with the code-behind class.</span></span> <span data-ttu-id="516c6-140">(`InitializeComponent` é gerado para você quando seu aplicativo é criado, motivo pelo qual você não precisa implementá-lo manualmente.) A combinação de `x:Class` e `InitializeComponent` garantir que sua implementação seja inicializada corretamente sempre que for criada.</span><span class="sxs-lookup"><span data-stu-id="516c6-140">(`InitializeComponent` is generated for you when your application is built, which is why you don't need to implement it manually.) The combination of `x:Class` and `InitializeComponent` ensure that your implementation is correctly initialized whenever it is created.</span></span> <span data-ttu-id="516c6-141">A classe code-behind também implementa um manipulador de eventos para o evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click> do botão.</span><span class="sxs-lookup"><span data-stu-id="516c6-141">The code-behind class also implements an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span> <span data-ttu-id="516c6-142">Quando o botão é clicado, o manipulador de eventos mostra uma caixa de mensagem ao chamar o método <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="516c6-142">When the button is clicked, the event handler shows a message box by calling the <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> method.</span></span>

<span data-ttu-id="516c6-143">A figura a seguir mostra o resultado quando o botão é clicado:</span><span class="sxs-lookup"><span data-stu-id="516c6-143">The following figure shows the result when the button is clicked:</span></span>

![Um MessageBox](media/introduction-to-wpf/wpfintrofigure25.png)

## <a name="controls"></a><span data-ttu-id="516c6-145">Controles</span><span class="sxs-lookup"><span data-stu-id="516c6-145">Controls</span></span>

<span data-ttu-id="516c6-146">As experiências de usuário que são entregues pelo modelo de aplicativo são controles construídos.</span><span class="sxs-lookup"><span data-stu-id="516c6-146">The user experiences that are delivered by the application model are constructed controls.</span></span> <span data-ttu-id="516c6-147">No WPF, *controle* é um termo abrangente que se aplica a uma categoria de classes do WPF que são hospedadas em uma janela ou uma página, que têm uma interface do usuário e que implementam um comportamento.</span><span class="sxs-lookup"><span data-stu-id="516c6-147">In WPF, *control* is an umbrella term that applies to a category of WPF classes that are hosted in either a window or a page, have a user interface, and implement some behavior.</span></span>

<span data-ttu-id="516c6-148">Para obter mais informações, consulte [Controles](controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="516c6-148">For more information, see [Controls](controls/index.md).</span></span>

### <a name="wpf-controls-by-function"></a><span data-ttu-id="516c6-149">Controles do WPF por função</span><span class="sxs-lookup"><span data-stu-id="516c6-149">WPF controls by function</span></span>

<span data-ttu-id="516c6-150">Os controles internos do WPF são listados aqui:</span><span class="sxs-lookup"><span data-stu-id="516c6-150">The built-in WPF controls are listed here:</span></span>

- <span data-ttu-id="516c6-151">**Botões**: <xref:System.Windows.Controls.Button> e <xref:System.Windows.Controls.Primitives.RepeatButton>.</span><span class="sxs-lookup"><span data-stu-id="516c6-151">**Buttons**: <xref:System.Windows.Controls.Button> and <xref:System.Windows.Controls.Primitives.RepeatButton>.</span></span>

- <span data-ttu-id="516c6-152">**Exibição de dados**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>e <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="516c6-152">**Data Display**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>, and <xref:System.Windows.Controls.TreeView>.</span></span>

- <span data-ttu-id="516c6-153">**Exibição e a seleção de dados**: <xref:System.Windows.Controls.Calendar> e <xref:System.Windows.Controls.DatePicker>.</span><span class="sxs-lookup"><span data-stu-id="516c6-153">**Date Display and Selection**: <xref:System.Windows.Controls.Calendar> and <xref:System.Windows.Controls.DatePicker>.</span></span>

- <span data-ttu-id="516c6-154">**Caixas de diálogo**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog> e <xref:Microsoft.Win32.SaveFileDialog>.</span><span class="sxs-lookup"><span data-stu-id="516c6-154">**Dialog Boxes**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>, and <xref:Microsoft.Win32.SaveFileDialog>.</span></span>

- <span data-ttu-id="516c6-155">**Tinta digital**: <xref:System.Windows.Controls.InkCanvas> e <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="516c6-155">**Digital Ink**: <xref:System.Windows.Controls.InkCanvas> and <xref:System.Windows.Controls.InkPresenter>.</span></span>

- <span data-ttu-id="516c6-156">**Documentos**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer> e <xref:System.Windows.Controls.StickyNoteControl>.</span><span class="sxs-lookup"><span data-stu-id="516c6-156">**Documents**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, and <xref:System.Windows.Controls.StickyNoteControl>.</span></span>

- <span data-ttu-id="516c6-157">**Entrada**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox> e <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="516c6-157">**Input**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Controls.PasswordBox>.</span></span>

- <span data-ttu-id="516c6-158">**Layout**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window> e <xref:System.Windows.Controls.WrapPanel>.</span><span class="sxs-lookup"><span data-stu-id="516c6-158">**Layout**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>, and <xref:System.Windows.Controls.WrapPanel>.</span></span>

- <span data-ttu-id="516c6-159">**Mídia**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement> e <xref:System.Windows.Controls.SoundPlayerAction>.</span><span class="sxs-lookup"><span data-stu-id="516c6-159">**Media**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>, and <xref:System.Windows.Controls.SoundPlayerAction>.</span></span>

- <span data-ttu-id="516c6-160">**Menus**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu> e <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="516c6-160">**Menus**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>, and <xref:System.Windows.Controls.ToolBar>.</span></span>

- <span data-ttu-id="516c6-161">**Navegação**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow> e <xref:System.Windows.Controls.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="516c6-161">**Navigation**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, and <xref:System.Windows.Controls.TabControl>.</span></span>

- <span data-ttu-id="516c6-162">**Seleção**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton> e <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="516c6-162">**Selection**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, and <xref:System.Windows.Controls.Slider>.</span></span>

- <span data-ttu-id="516c6-163">**Informações do usuário**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock> e <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="516c6-163">**User Information**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>, and <xref:System.Windows.Controls.ToolTip>.</span></span>

## <a name="input-and-commands"></a><span data-ttu-id="516c6-164">Entrada e comandos</span><span class="sxs-lookup"><span data-stu-id="516c6-164">Input and commands</span></span>

<span data-ttu-id="516c6-165">Controles normalmente detectam e respondem a entradas do usuário.</span><span class="sxs-lookup"><span data-stu-id="516c6-165">Controls most often detect and respond to user input.</span></span> <span data-ttu-id="516c6-166">O [sistema de entrada do WPF](advanced/input-overview.md) usa tanto os eventos diretos como os roteados para dar suporte a entrada de texto, foco de gerenciamento e posicionamento do mouse.</span><span class="sxs-lookup"><span data-stu-id="516c6-166">The [WPF input system](advanced/input-overview.md) uses both direct and routed events to support text input, focus management, and mouse positioning.</span></span>

<span data-ttu-id="516c6-167">Aplicativos muitas vezes têm requisitos de entrada complexos.</span><span class="sxs-lookup"><span data-stu-id="516c6-167">Applications often have complex input requirements.</span></span> <span data-ttu-id="516c6-168">O WPF fornece um [sistema de comando](advanced/commanding-overview.md) que separa as ações de entrada do usuário do código que responde a essas ações.</span><span class="sxs-lookup"><span data-stu-id="516c6-168">WPF provides a [command system](advanced/commanding-overview.md) that separates user-input actions from the code that responds to those actions.</span></span>

## <a name="layout"></a><span data-ttu-id="516c6-169">Layout</span><span class="sxs-lookup"><span data-stu-id="516c6-169">Layout</span></span>

<span data-ttu-id="516c6-170">Quando você cria uma interface do usuário, você organiza os controles por local e tamanho para formar um layout.</span><span class="sxs-lookup"><span data-stu-id="516c6-170">When you create a user interface, you arrange your controls by location and size to form a layout.</span></span> <span data-ttu-id="516c6-171">Um requisito chave de qualquer layout é se adaptar a alterações no tamanho da janela e exibir as configurações.</span><span class="sxs-lookup"><span data-stu-id="516c6-171">A key requirement of any layout is to adapt to changes in window size and display settings.</span></span> <span data-ttu-id="516c6-172">Em vez de forçá-lo a escrever o código para adaptar um layout nessas circunstâncias, o WPF fornece um sistema de layout extensível e de primeira classe para você.</span><span class="sxs-lookup"><span data-stu-id="516c6-172">Rather than forcing you to write the code to adapt a layout in these circumstances, WPF provides a first-class, extensible layout system for you.</span></span>

<span data-ttu-id="516c6-173">A base do sistema de layout é o posicionamento relativo, que aumenta a capacidade de se adaptar às modificações da janela e condições de exibição.</span><span class="sxs-lookup"><span data-stu-id="516c6-173">The cornerstone of the layout system is relative positioning, which increases the ability to adapt to changing window and display conditions.</span></span> <span data-ttu-id="516c6-174">Além disso, o sistema de layout gerencia a negociação entre os controles para determinar o layout.</span><span class="sxs-lookup"><span data-stu-id="516c6-174">In addition, the layout system manages the negotiation between controls to determine the layout.</span></span> <span data-ttu-id="516c6-175">A negociação é um processo de duas etapas: primeiro, um controle informa ao pai o local e tamanho requerido; segundo, o pai informa ao controle qual espaço ele pode ter.</span><span class="sxs-lookup"><span data-stu-id="516c6-175">The negotiation is a two-step process: first, a control tells its parent what location and size it requires; second, the parent tells the control what space it can have.</span></span>

<span data-ttu-id="516c6-176">O sistema de layout é exposto aos controles filho por meio de classes base do WPF.</span><span class="sxs-lookup"><span data-stu-id="516c6-176">The layout system is exposed to child controls through base WPF classes.</span></span> <span data-ttu-id="516c6-177">Para layouts comuns, como grades, empilhamento e encaixe, o WPF inclui vários controles de layout:</span><span class="sxs-lookup"><span data-stu-id="516c6-177">For common layouts such as grids, stacking, and docking, WPF includes several layout controls:</span></span>

- <span data-ttu-id="516c6-178"><xref:System.Windows.Controls.Canvas>: os controles filho fornecem seus próprios layouts.</span><span class="sxs-lookup"><span data-stu-id="516c6-178"><xref:System.Windows.Controls.Canvas>: Child controls provide their own layout.</span></span>

- <span data-ttu-id="516c6-179"><xref:System.Windows.Controls.DockPanel>: os controles filho são alinhados com as bordas do painel.</span><span class="sxs-lookup"><span data-stu-id="516c6-179"><xref:System.Windows.Controls.DockPanel>: Child controls are aligned to the edges of the panel.</span></span>

- <span data-ttu-id="516c6-180"><xref:System.Windows.Controls.Grid>: os controles filho são posicionados por linhas e colunas.</span><span class="sxs-lookup"><span data-stu-id="516c6-180"><xref:System.Windows.Controls.Grid>: Child controls are positioned by rows and columns.</span></span>

- <span data-ttu-id="516c6-181"><xref:System.Windows.Controls.StackPanel>: os controles filho são empilhados verticalmente ou horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="516c6-181"><xref:System.Windows.Controls.StackPanel>: Child controls are stacked either vertically or horizontally.</span></span>

- <span data-ttu-id="516c6-182"><xref:System.Windows.Controls.VirtualizingStackPanel>: os controles filho são virtualizados e organizados em uma única linha, que é orientada horizontal ou verticalmente.</span><span class="sxs-lookup"><span data-stu-id="516c6-182"><xref:System.Windows.Controls.VirtualizingStackPanel>: Child controls are virtualized and arranged on a single line that is either horizontally or vertically oriented.</span></span>

- <span data-ttu-id="516c6-183"><xref:System.Windows.Controls.WrapPanel>: os controles filho são posicionados na ordem da esquerda para a direita e, quando há mais controles na linha atual do que o espaço permite, sofrem quebra automática para a próxima linha.</span><span class="sxs-lookup"><span data-stu-id="516c6-183"><xref:System.Windows.Controls.WrapPanel>: Child controls are positioned in left-to-right order and wrapped to the next line when there are more controls on the current line than space allows.</span></span>

<span data-ttu-id="516c6-184">O exemplo a seguir usa uma <xref:System.Windows.Controls.DockPanel> para dispor vários controles de <xref:System.Windows.Controls.TextBox>:</span><span class="sxs-lookup"><span data-stu-id="516c6-184">The following example uses a <xref:System.Windows.Controls.DockPanel> to lay out several <xref:System.Windows.Controls.TextBox> controls:</span></span>

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_1.xaml)]

<span data-ttu-id="516c6-185">O <xref:System.Windows.Controls.DockPanel> permite que os controles <xref:System.Windows.Controls.TextBox> filho informem como organizá-los.</span><span class="sxs-lookup"><span data-stu-id="516c6-185">The <xref:System.Windows.Controls.DockPanel> allows the child <xref:System.Windows.Controls.TextBox> controls to tell it how to arrange them.</span></span> <span data-ttu-id="516c6-186">Para fazer isso, o <xref:System.Windows.Controls.DockPanel> implementa uma propriedade anexada `Dock` que é exposta aos controles filho para permitir que cada um especifique um estilo de encaixe.</span><span class="sxs-lookup"><span data-stu-id="516c6-186">To do this, the <xref:System.Windows.Controls.DockPanel> implements a `Dock` attached property that is exposed to the child controls to allow each of them to specify a dock style.</span></span>

> [!NOTE]
> <span data-ttu-id="516c6-187">Uma propriedade que é implementada por um controle pai para uso por controles filho é uma constructo do WPF chamado de [propriedade anexada](advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="516c6-187">A property that's implemented by a parent control for use by child controls is a WPF construct called an [attached property](advanced/attached-properties-overview.md).</span></span>

<span data-ttu-id="516c6-188">A figura a seguir mostra o resultado da marcação XAML no exemplo anterior:</span><span class="sxs-lookup"><span data-stu-id="516c6-188">The following figure shows the result of the XAML markup in the preceding example:</span></span>

![Página DockPanel](media/introduction-to-wpf/wpfintrofigure11.png)

## <a name="data-binding"></a><span data-ttu-id="516c6-190">Associação de dados</span><span class="sxs-lookup"><span data-stu-id="516c6-190">Data binding</span></span>

<span data-ttu-id="516c6-191">A maioria dos aplicativos são criados para fornecer aos usuários os meios para exibir e editar dados.</span><span class="sxs-lookup"><span data-stu-id="516c6-191">Most applications are created to provide users with the means to view and edit data.</span></span> <span data-ttu-id="516c6-192">Para aplicativos WPF, o trabalho de armazenar e acessar dados já é fornecido por tecnologias, como SQL Server e ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="516c6-192">For WPF applications, the work of storing and accessing data is already provided for by technologies such as SQL Server and ADO .NET.</span></span> <span data-ttu-id="516c6-193">Depois que os dados são acessados e carregados em objetos gerenciados do aplicativo, começa o trabalho pesado para os aplicativos WPF.</span><span class="sxs-lookup"><span data-stu-id="516c6-193">After the data is accessed and loaded into an application's managed objects, the hard work for WPF applications begins.</span></span> <span data-ttu-id="516c6-194">Essencialmente, isso envolve duas coisas:</span><span class="sxs-lookup"><span data-stu-id="516c6-194">Essentially, this involves two things:</span></span>

1. <span data-ttu-id="516c6-195">Copiar os dados dos objetos gerenciados para controles, nos quais os dados podem ser exibidos e editados.</span><span class="sxs-lookup"><span data-stu-id="516c6-195">Copying the data from the managed objects into controls, where the data can be displayed and edited.</span></span>

2. <span data-ttu-id="516c6-196">Assegurar que as alterações feitas nos dados usando controles sejam copiadas para os objetos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="516c6-196">Ensuring that changes made to data by using controls are copied back to the managed objects.</span></span>

<span data-ttu-id="516c6-197">Para simplificar o desenvolvimento de aplicativos, o WPF fornece um mecanismo de vinculação de dados para executar essas etapas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="516c6-197">To simplify application development, WPF provides a data binding engine to automatically perform these steps.</span></span> <span data-ttu-id="516c6-198">A unidade principal do mecanismo de associação de dados é a classe <xref:System.Windows.Data.Binding>, cujo trabalho é associar um controle (o destino da associação) a um objeto de dados (a origem da associação).</span><span class="sxs-lookup"><span data-stu-id="516c6-198">The core unit of the data binding engine is the <xref:System.Windows.Data.Binding> class, whose job is to bind a control (the binding target) to a data object (the binding source).</span></span> <span data-ttu-id="516c6-199">Essa relação é ilustrada pela figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="516c6-199">This relationship is illustrated by the following figure:</span></span>

![Diagrama de associação de dados básica](media/introduction-to-wpf/databindingmostbasic.png)

<span data-ttu-id="516c6-201">O exemplo a seguir demonstra como associar um <xref:System.Windows.Controls.TextBox> a uma instância de um objeto `Person` personalizado.</span><span class="sxs-lookup"><span data-stu-id="516c6-201">The next example demonstrates how to bind a <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object.</span></span> <span data-ttu-id="516c6-202">A implementação de `Person` é mostrada no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="516c6-202">The `Person` implementation is shown in the following code:</span></span>

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_2.cs)]

<span data-ttu-id="516c6-203">A marcação a seguir associa o <xref:System.Windows.Controls.TextBox> a uma instância de um objeto de `Person` personalizado:</span><span class="sxs-lookup"><span data-stu-id="516c6-203">The following markup binds the <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object:</span></span>

```xaml
 <Window
     xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
     xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
     x:Class="SDKSample.DataBindingWindow">

   <!-- Bind the TextBox to the data source (TextBox.Text to Person.Name) -->
   <TextBox Name="personNameTextBox" Text="{Binding Path=Name}" />

 </Window>
```

[!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_6.vb)]
[!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_6.cs)]

<span data-ttu-id="516c6-204">Neste exemplo, a classe `Person` é instanciada no code-behind e é definida como o contexto de dados para o `DataBindingWindow`.</span><span class="sxs-lookup"><span data-stu-id="516c6-204">In this example, the `Person` class is instantiated in code-behind and is set as the data context for the `DataBindingWindow`.</span></span> <span data-ttu-id="516c6-205">Na marcação, a propriedade <xref:System.Windows.Controls.TextBox.Text%2A> do <xref:System.Windows.Controls.TextBox> está associada à propriedade `Person.Name` (usando a sintaxe XAML "`{Binding ... }`").</span><span class="sxs-lookup"><span data-stu-id="516c6-205">In markup, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> is bound to the `Person.Name` property (using the "`{Binding ... }`" XAML syntax).</span></span> <span data-ttu-id="516c6-206">Esse XAML solicita que o WPF associe o controle <xref:System.Windows.Controls.TextBox> ao objeto `Person` armazenado na propriedade <xref:System.Windows.FrameworkElement.DataContext%2A> da janela.</span><span class="sxs-lookup"><span data-stu-id="516c6-206">This XAML tells WPF to bind the <xref:System.Windows.Controls.TextBox> control to the `Person` object that is stored in the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the window.</span></span>

<span data-ttu-id="516c6-207">O mecanismo de vinculação de dados do WPF fornece suporte adicional que inclui a validação, classificação, filtragem e agrupamento.</span><span class="sxs-lookup"><span data-stu-id="516c6-207">The WPF data binding engine provides additional support that includes validation, sorting, filtering, and grouping.</span></span> <span data-ttu-id="516c6-208">Além disso, a vinculação de dados dá suporte ao uso de modelos de dados para criar a interface do usuário personalizada para dados associados quando a interface do usuário exibida pelos controles WPF padrão não é apropriada.</span><span class="sxs-lookup"><span data-stu-id="516c6-208">Furthermore, data binding supports the use of data templates to create custom user interface for bound data when the user interface displayed by the standard WPF controls is not appropriate.</span></span>

<span data-ttu-id="516c6-209">Para obter mais informações, confira [Visão geral de associação de dados](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="516c6-209">For more information, see [Data binding overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

## <a name="graphics"></a><span data-ttu-id="516c6-210">Gráficos</span><span class="sxs-lookup"><span data-stu-id="516c6-210">Graphics</span></span>

<span data-ttu-id="516c6-211">O WPF introduz um conjunto amplo, escalonável e flexível de funcionalidades gráficas com os seguintes benefícios:</span><span class="sxs-lookup"><span data-stu-id="516c6-211">WPF introduces an extensive, scalable, and flexible set of graphics features that have the following benefits:</span></span>

- <span data-ttu-id="516c6-212">**Elementos gráficos independentes de resolução e de dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="516c6-212">**Resolution-independent and device-independent graphics**.</span></span> <span data-ttu-id="516c6-213">A unidade básica de medida no sistema gráfico do WPF é o pixel independente de dispositivo, que é 1/96 de polegada, independentemente da resolução de tela e que fornece a base para a renderização independente de resolução e de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="516c6-213">The basic unit of measurement in the WPF graphics system is the device-independent pixel, which is 1/96th of an inch, regardless of actual screen resolution, and provides the foundation for resolution-independent and device-independent rendering.</span></span> <span data-ttu-id="516c6-214">Cada pixel independente de dispositivo pode ser dimensionado automaticamente para corresponder à configuração de dpi (pontos por polegada) do sistema em que ele é renderizado.</span><span class="sxs-lookup"><span data-stu-id="516c6-214">Each device-independent pixel automatically scales to match the dots-per-inch (dpi) setting of the system it renders on.</span></span>

- <span data-ttu-id="516c6-215">**Maior precisão**.</span><span class="sxs-lookup"><span data-stu-id="516c6-215">**Improved precision**.</span></span> <span data-ttu-id="516c6-216">O sistema de coordenadas do WPF é medido com números de ponto flutuante de precisão dupla em vez de precisão simples.</span><span class="sxs-lookup"><span data-stu-id="516c6-216">The WPF coordinate system is measured with double-precision floating-point numbers rather than single-precision.</span></span> <span data-ttu-id="516c6-217">Transformações e valores opacidade também são expressos com precisão dupla.</span><span class="sxs-lookup"><span data-stu-id="516c6-217">Transformations and opacity values are also expressed as double-precision.</span></span> <span data-ttu-id="516c6-218">O WPF também dá suporte a uma gama de cores (scRGB) e oferece suporte integrado para gerenciar entradas de diferentes espaços de cores.</span><span class="sxs-lookup"><span data-stu-id="516c6-218">WPF also supports a wide color gamut (scRGB) and provides integrated support for managing inputs from different color spaces.</span></span>

- <span data-ttu-id="516c6-219">**Suporte a animação e elementos gráficos avançados**.</span><span class="sxs-lookup"><span data-stu-id="516c6-219">**Advanced graphics and animation support**.</span></span> <span data-ttu-id="516c6-220">O WPF simplifica a programação de elementos gráficos ao gerenciar cenas de animação para você; não é necessário se preocupar sobre o processamento da cena, loops de renderização e interpolação bilinear.</span><span class="sxs-lookup"><span data-stu-id="516c6-220">WPF simplifies graphics programming by managing animation scenes for you; there is no need to worry about scene processing, rendering loops, and bilinear interpolation.</span></span> <span data-ttu-id="516c6-221">Além disso, o WPF dá suporte a teste de clique e suporte completo a composição alfa.</span><span class="sxs-lookup"><span data-stu-id="516c6-221">Additionally, WPF provides hit-testing support and full alpha-compositing support.</span></span>

- <span data-ttu-id="516c6-222">**Aceleração de hardware**.</span><span class="sxs-lookup"><span data-stu-id="516c6-222">**Hardware acceleration**.</span></span> <span data-ttu-id="516c6-223">Sistema gráfico do WPF tira proveito do hardware gráfico para minimizar o uso da CPU.</span><span class="sxs-lookup"><span data-stu-id="516c6-223">The WPF graphics system takes advantage of graphics hardware to minimize CPU usage.</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="516c6-224">Formas 2D</span><span class="sxs-lookup"><span data-stu-id="516c6-224">2D shapes</span></span>

<span data-ttu-id="516c6-225">O WPF fornece uma biblioteca de formas vetoriais 2D comuns como retângulos e elipses, que são mostradas na ilustração a seguir:</span><span class="sxs-lookup"><span data-stu-id="516c6-225">WPF provides a library of common vector-drawn 2D shapes, such as the rectangles and ellipses that are shown in the following illustration:</span></span>

![Elipses e retângulos](media/introduction-to-wpf/wpfintrofigure4.PNG)

<span data-ttu-id="516c6-227">Uma funcionalidade interessante de formas é que elas não são apenas para exibição; as formas implementam muitas das funcionalidades que você espera dos controles, incluindo entrada de teclado e de mouse.</span><span class="sxs-lookup"><span data-stu-id="516c6-227">An interesting capability of shapes is that they are not just for display; shapes implement many of the features that you expect from controls, including keyboard and mouse input.</span></span> <span data-ttu-id="516c6-228">O exemplo a seguir mostra o <xref:System.Windows.UIElement.MouseUp> evento de um <xref:System.Windows.Shapes.Ellipse> que está sendo manipulado:</span><span class="sxs-lookup"><span data-stu-id="516c6-228">The following example shows the <xref:System.Windows.UIElement.MouseUp> event of an <xref:System.Windows.Shapes.Ellipse> being handled:</span></span>

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_8.cs)]

<span data-ttu-id="516c6-229">A figura a seguir mostra o que é produzido pelo código anterior:</span><span class="sxs-lookup"><span data-stu-id="516c6-229">The following figure shows what is produced by the preceding code:</span></span>

![Uma janela com o texto "você clicou na elipse&#33"](media/introduction-to-wpf/wpfintrofigure12.png)

<span data-ttu-id="516c6-231">Para obter mais informações, confira [Visão geral de formas e desenho básico no WPF](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="516c6-231">For more information, see [Shapes and basic drawing in WPF overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="516c6-232">Geometrias 2D</span><span class="sxs-lookup"><span data-stu-id="516c6-232">2D geometries</span></span>

<span data-ttu-id="516c6-233">As formas 2D fornecidas pelo WPF abrangem o conjunto padrão de formas básicas.</span><span class="sxs-lookup"><span data-stu-id="516c6-233">The 2D shapes provided by WPF cover the standard set of basic shapes.</span></span> <span data-ttu-id="516c6-234">No entanto, talvez seja necessário criar formas personalizadas para facilitar o design de uma interface do usuário personalizada.</span><span class="sxs-lookup"><span data-stu-id="516c6-234">However, you may need to create custom shapes to facilitate the design of a customized user interface.</span></span> <span data-ttu-id="516c6-235">Para essa finalidade, o WPF fornece geometrias.</span><span class="sxs-lookup"><span data-stu-id="516c6-235">For this purpose, WPF provides geometries.</span></span> <span data-ttu-id="516c6-236">A figura a seguir demonstra o uso de geometrias para criar uma forma personalizada que pode ser desenhada diretamente, usada como um pincel ou usada para recortar outras formas e controles.</span><span class="sxs-lookup"><span data-stu-id="516c6-236">The following figure demonstrates the use of geometries to create a custom shape that can be drawn directly, used as a brush, or used to clip other shapes and controls.</span></span>

<span data-ttu-id="516c6-237">Os objetos <xref:System.Windows.Shapes.Path> podem ser usados para desenhar formas fechadas ou abertas, várias formas e até mesmo formas curvas.</span><span class="sxs-lookup"><span data-stu-id="516c6-237"><xref:System.Windows.Shapes.Path> objects can be used to draw closed or open shapes, multiple shapes, and even curved shapes.</span></span>

<span data-ttu-id="516c6-238">Os objetos <xref:System.Windows.Media.Geometry> podem ser usados para recorte, teste de clique e renderização de dados gráficos 2D.</span><span class="sxs-lookup"><span data-stu-id="516c6-238"><xref:System.Windows.Media.Geometry> objects can be used for clipping, hit-testing, and rendering 2D graphic data.</span></span>

![Vários usos de um demarcador](media/introduction-to-wpf/wpfintrofigure5.png)

<span data-ttu-id="516c6-240">Para obter mais informações, confira [Visão geral de geometria](graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="516c6-240">For more information, see [Geometry overview](graphics-multimedia/geometry-overview.md).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="516c6-241">Efeitos 2D</span><span class="sxs-lookup"><span data-stu-id="516c6-241">2D effects</span></span>

<span data-ttu-id="516c6-242">Um subconjunto de funcionalidades 2D do WPF inclui efeitos visuais como gradientes, bitmaps, desenhos, pintura com vídeos, rotação, dimensionamento e distorção.</span><span class="sxs-lookup"><span data-stu-id="516c6-242">A subset of WPF 2D capabilities includes visual effects, such as gradients, bitmaps, drawings, painting with videos, rotation, scaling, and skewing.</span></span> <span data-ttu-id="516c6-243">Todos eles são obtidos com pincéis; a figura a seguir mostra alguns exemplos:</span><span class="sxs-lookup"><span data-stu-id="516c6-243">These are all achieved with brushes; the following figure shows some examples:</span></span>

![Ilustração de diferentes pincéis](media/introduction-to-wpf/wpfintrofigure6.png)

<span data-ttu-id="516c6-245">Para obter mais informações, confira [Visão geral de pincéis do WPF](graphics-multimedia/wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="516c6-245">For more information, see [WPF brushes overview](graphics-multimedia/wpf-brushes-overview.md).</span></span>

### <a name="3d-rendering"></a><span data-ttu-id="516c6-246">Renderização 3D</span><span class="sxs-lookup"><span data-stu-id="516c6-246">3D rendering</span></span>

<span data-ttu-id="516c6-247">O WPF também inclui funcionalidades de renderização 3D que se integram com elementos gráficos em 2D para permitir a criação de interfaces do usuário mais interessantes e empolgantes.</span><span class="sxs-lookup"><span data-stu-id="516c6-247">WPF also includes 3D rendering capabilities that integrate with 2-d graphics to allow the creation of more exciting and interesting user interfaces.</span></span> <span data-ttu-id="516c6-248">Por exemplo, a figura a seguir mostra imagens 2D renderizadas em formas 3D:</span><span class="sxs-lookup"><span data-stu-id="516c6-248">For example, the following figure shows 2D images rendered onto 3D shapes:</span></span>

![Captura de tela de exemplo do Visual3D](media/introduction-to-wpf/wpfintrofigure13.png)

<span data-ttu-id="516c6-250">Para obter mais informações, confira [Visão geral de elementos gráficos 3D](graphics-multimedia/3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="516c6-250">For more information, see [3D graphics overview](graphics-multimedia/3-d-graphics-overview.md).</span></span>

## <a name="animation"></a><span data-ttu-id="516c6-251">Animação</span><span class="sxs-lookup"><span data-stu-id="516c6-251">Animation</span></span>

<span data-ttu-id="516c6-252">O suporte a animação do WPF permite que você faça os controles crescerem, tremerem, rodarem e esmaecerem, para criar transições de página interessantes e muito mais.</span><span class="sxs-lookup"><span data-stu-id="516c6-252">WPF animation support lets you make controls grow, shake, spin, and fade, to create interesting page transitions, and more.</span></span> <span data-ttu-id="516c6-253">Você pode animar a maioria das classes do WPF, até mesmo classes personalizadas.</span><span class="sxs-lookup"><span data-stu-id="516c6-253">You can animate most WPF classes, even custom classes.</span></span> <span data-ttu-id="516c6-254">A figura a seguir mostra uma animação simples em ação:</span><span class="sxs-lookup"><span data-stu-id="516c6-254">The following figure shows a simple animation in action:</span></span>

![Imagens de um cubo animado](media/introduction-to-wpf/wpfintrofigure7.png)

<span data-ttu-id="516c6-256">Para obter mais informações, confira [Visão geral de animação](graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="516c6-256">For more information, see [Animation overview](graphics-multimedia/animation-overview.md).</span></span>

## <a name="media"></a><span data-ttu-id="516c6-257">Mídia</span><span class="sxs-lookup"><span data-stu-id="516c6-257">Media</span></span>

<span data-ttu-id="516c6-258">Uma maneira de transmitir conteúdo rico é pelo uso de mídia audiovisual.</span><span class="sxs-lookup"><span data-stu-id="516c6-258">One way to convey rich content is through the use of audiovisual media.</span></span> <span data-ttu-id="516c6-259">O WPF dá suporte especial para imagens, áudio e vídeo.</span><span class="sxs-lookup"><span data-stu-id="516c6-259">WPF provides special support for images, video, and audio.</span></span>

### <a name="images"></a><span data-ttu-id="516c6-260">Imagens</span><span class="sxs-lookup"><span data-stu-id="516c6-260">Images</span></span>

<span data-ttu-id="516c6-261">Imagens são comuns à maioria dos aplicativos e o WPF fornece várias maneiras de usá-las.</span><span class="sxs-lookup"><span data-stu-id="516c6-261">Images are common to most applications, and WPF provides several ways to use them.</span></span> <span data-ttu-id="516c6-262">A figura a seguir mostra uma interface do usuário com uma caixa de listagem que contém imagens em miniatura.</span><span class="sxs-lookup"><span data-stu-id="516c6-262">The following figure shows a user interface with a list box that contains thumbnail images.</span></span> <span data-ttu-id="516c6-263">Quando uma miniatura é selecionada, a imagem é mostrada em tamanho normal.</span><span class="sxs-lookup"><span data-stu-id="516c6-263">When a thumbnail is selected, the image is shown full-size.</span></span>

![Imagens em miniatura e uma imagem em tamanho original](media/introduction-to-wpf/wpfintrofigure8.png)

<span data-ttu-id="516c6-265">Para obter mais informações, confira [Visão geral de geração de imagens](graphics-multimedia/imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="516c6-265">For more information, see [Imaging overview](graphics-multimedia/imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="516c6-266">Áudio e vídeo</span><span class="sxs-lookup"><span data-stu-id="516c6-266">Video and audio</span></span>

<span data-ttu-id="516c6-267">O controle <xref:System.Windows.Controls.MediaElement> é capaz de executar áudio e vídeo e é flexível o suficiente para ser a base de um player de mídia personalizado.</span><span class="sxs-lookup"><span data-stu-id="516c6-267">The <xref:System.Windows.Controls.MediaElement> control is capable of playing both video and audio, and it is flexible enough to be the basis for a custom media player.</span></span> <span data-ttu-id="516c6-268">A marcação XAML a seguir implementa um player de mídia:</span><span class="sxs-lookup"><span data-stu-id="516c6-268">The following XAML markup implements a media player:</span></span>

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_9.xaml)]

<span data-ttu-id="516c6-269">A janela na figura a seguir mostra o controle <xref:System.Windows.Controls.MediaElement> em ação:</span><span class="sxs-lookup"><span data-stu-id="516c6-269">The window in the following figure shows the <xref:System.Windows.Controls.MediaElement> control in action:</span></span>

![Um controle MediaElement com áudio e vídeo](media/introduction-to-wpf/wpfintrofigure1.png)

<span data-ttu-id="516c6-271">Para obter mais informações, confira [Elementos gráficos e multimídia](graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="516c6-271">For more information, see [Graphics and multimedia](graphics-multimedia/index.md).</span></span>

## <a name="text-and-typography"></a><span data-ttu-id="516c6-272">Texto e tipografia</span><span class="sxs-lookup"><span data-stu-id="516c6-272">Text and typography</span></span>

<span data-ttu-id="516c6-273">Para facilitar a renderização de texto de alta qualidade, o WPF oferece as seguintes funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="516c6-273">To facilitate high-quality text rendering, WPF offers the following features:</span></span>

- <span data-ttu-id="516c6-274">Suporte a fontes OpenType.</span><span class="sxs-lookup"><span data-stu-id="516c6-274">OpenType font support.</span></span>

- <span data-ttu-id="516c6-275">Aprimoramentos de ClearType.</span><span class="sxs-lookup"><span data-stu-id="516c6-275">ClearType enhancements.</span></span>

- <span data-ttu-id="516c6-276">Alto desempenho que tira proveito da aceleração de hardware.</span><span class="sxs-lookup"><span data-stu-id="516c6-276">High performance that takes advantage of hardware acceleration.</span></span>

- <span data-ttu-id="516c6-277">Integração do texto com mídia, elementos gráficos e animação.</span><span class="sxs-lookup"><span data-stu-id="516c6-277">Integration of text with media, graphics, and animation.</span></span>

- <span data-ttu-id="516c6-278">Mecanismos de fallback e suporte a fontes internacionais.</span><span class="sxs-lookup"><span data-stu-id="516c6-278">International font support and fallback mechanisms.</span></span>

<span data-ttu-id="516c6-279">Como uma demonstração da integração de texto com gráficos, a figura a seguir mostra o aplicativo de decoração de texto:</span><span class="sxs-lookup"><span data-stu-id="516c6-279">As a demonstration of text integration with graphics, the following figure shows the application of text decorations:</span></span>

![Texto com várias decorações](media/introduction-to-wpf/wpfintrofigure23.png)

<span data-ttu-id="516c6-281">Para obter mais informações, consulte [Tipografia na Windows Presentation Foundation](advanced/typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="516c6-281">For more information, see [Typography in Windows Presentation Foundation](advanced/typography-in-wpf.md).</span></span>

## <a name="customize-wpf-apps"></a><span data-ttu-id="516c6-282">Personalizar aplicativos do WPF</span><span class="sxs-lookup"><span data-stu-id="516c6-282">Customize WPF apps</span></span>

<span data-ttu-id="516c6-283">Até aqui, você viu os principais blocos de construção do WPF principal para o desenvolvimento de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="516c6-283">Up to this point, you've seen the core WPF building blocks for developing applications.</span></span> <span data-ttu-id="516c6-284">Você pode usar o modelo de aplicativo para hospedar e entregar conteúdo do aplicativo, que consiste principalmente de controles.</span><span class="sxs-lookup"><span data-stu-id="516c6-284">You use the application model to host and deliver application content, which consists mainly of controls.</span></span> <span data-ttu-id="516c6-285">Para simplificar a organização dos controles em uma interface do usuário e assegurar que a organização seja mantida em caso de alterações no tamanho da janela e configurações de exibição, você deverá usar o sistema de layout do WPF.</span><span class="sxs-lookup"><span data-stu-id="516c6-285">To simplify the arrangement of controls in a user interface, and to ensure the arrangement is maintained in the face of changes to window size and display settings, you use the WPF layout system.</span></span> <span data-ttu-id="516c6-286">Já que a maioria dos aplicativos permite aos usuários interagir com os dados, use a associação de dados para reduzir o trabalho de integração da interface do usuário com os dados.</span><span class="sxs-lookup"><span data-stu-id="516c6-286">Because most applications let users interact with data, you use data binding to reduce the work of integrating your user interface with data.</span></span> <span data-ttu-id="516c6-287">Para melhorar a aparência visual do seu aplicativo, você deve usar a ampla gama de suporte a elementos gráficos, animação e mídia fornecido pelo WPF.</span><span class="sxs-lookup"><span data-stu-id="516c6-287">To enhance the visual appearance of your application, you use the comprehensive range of graphics, animation, and media support provided by WPF.</span></span>

<span data-ttu-id="516c6-288">Muitas vezes, no entanto, os conceitos básicos não são suficientes para criar e gerenciar uma experiência do usuário realmente distinta e visualmente impressionante.</span><span class="sxs-lookup"><span data-stu-id="516c6-288">Often, though, the basics are not enough for creating and managing a truly distinct and visually stunning user experience.</span></span> <span data-ttu-id="516c6-289">Os controles padrão do WPF podem não ser integrados à aparência desejada do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="516c6-289">The standard WPF controls might not integrate with the desired appearance of your application.</span></span> <span data-ttu-id="516c6-290">Os dados podem não ser exibidos da maneira mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="516c6-290">Data might not be displayed in the most effective way.</span></span> <span data-ttu-id="516c6-291">A experiência do usuário geral do seu aplicativo pode não ser adequada para a aparência padrão de temas do Windows.</span><span class="sxs-lookup"><span data-stu-id="516c6-291">Your application's overall user experience may not be suited to the default look and feel of Windows themes.</span></span> <span data-ttu-id="516c6-292">Em muitos aspectos, uma tecnologia de apresentação precisa de extensibilidade visual, assim como qualquer outro tipo de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="516c6-292">In many ways, a presentation technology needs visual extensibility as much as any other type of extensibility.</span></span>

<span data-ttu-id="516c6-293">Por esse motivo, o WPF fornece uma variedade de mecanismos para criar experiências de usuário exclusivas, incluindo um modelo rico de conteúdo para controles, gatilhos, modelos de dados e de controle, estilos, recursos de interface do usuário, temas e capas.</span><span class="sxs-lookup"><span data-stu-id="516c6-293">For this reason, WPF provides a variety of mechanisms for creating unique user experiences, including a rich content model for controls, triggers, control and data templates, styles, user interface resources, and themes and skins.</span></span>

### <a name="content-model"></a><span data-ttu-id="516c6-294">Modelo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="516c6-294">Content model</span></span>

<span data-ttu-id="516c6-295">O principal objetivo da maioria dos controles WPF é exibir conteúdo.</span><span class="sxs-lookup"><span data-stu-id="516c6-295">The main purpose of a majority of the WPF controls is to display content.</span></span> <span data-ttu-id="516c6-296">No WPF, o tipo e o número de itens que podem constituir o conteúdo de um controle são conhecidos como o *modelo de conteúdo* do controle.</span><span class="sxs-lookup"><span data-stu-id="516c6-296">In WPF, the type and number of items that can constitute the content of a control is referred to as the control's *content model*.</span></span> <span data-ttu-id="516c6-297">Alguns controles podem conter um único item e o tipo de conteúdo. Por exemplo, o conteúdo de um <xref:System.Windows.Controls.TextBox> é um valor de cadeia de caracteres que é atribuído à propriedade <xref:System.Windows.Controls.TextBox.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="516c6-297">Some controls can contain a single item and type of content; for example, the content of a <xref:System.Windows.Controls.TextBox> is a string value that is assigned to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="516c6-298">O exemplo a seguir define o conteúdo de um <xref:System.Windows.Controls.TextBox>:</span><span class="sxs-lookup"><span data-stu-id="516c6-298">The following example sets the content of a <xref:System.Windows.Controls.TextBox>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

<span data-ttu-id="516c6-299">A figura a seguir mostra o resultado:</span><span class="sxs-lookup"><span data-stu-id="516c6-299">The following figure shows the result:</span></span>

![Um Controle TextBox que contém texto](media/introduction-to-wpf/wpfintrofigure21.png)

<span data-ttu-id="516c6-301">Outros controles, entretanto, podem conter vários itens de diferentes tipos de conteúdo. O conteúdo de um <xref:System.Windows.Controls.Button>, especificado pela propriedade <xref:System.Windows.Controls.ContentControl.Content%2A>, pode conter uma variedade de itens, incluindo controles de layout, texto, imagens e formas.</span><span class="sxs-lookup"><span data-stu-id="516c6-301">Other controls, however, can contain multiple items of different types of content; the content of a <xref:System.Windows.Controls.Button>, specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property, can contain a variety of items including layout controls, text, images, and shapes.</span></span> <span data-ttu-id="516c6-302">O exemplo a seguir mostra um <xref:System.Windows.Controls.Button> com conteúdo que inclui um <xref:System.Windows.Controls.DockPanel>, um <xref:System.Windows.Controls.Label>, um <xref:System.Windows.Controls.Border>e um <xref:System.Windows.Controls.MediaElement>:</span><span class="sxs-lookup"><span data-stu-id="516c6-302">The following example shows a <xref:System.Windows.Controls.Button> with content that includes a <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Controls.Label>, a <xref:System.Windows.Controls.Border>, and a <xref:System.Windows.Controls.MediaElement>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ButtonContentWindow"
    Title="Button Content">

  <Button Margin="20">
    <!-- Button Content -->
    <DockPanel Width="200" Height="180">
      <Label DockPanel.Dock="Top" HorizontalAlignment="Center">Click Me!</Label>
      <Border Background="Black" BorderBrush="Yellow" BorderThickness="2"
        CornerRadius="2" Margin="5">
        <MediaElement Source="media/wpf.wmv" Stretch="Fill" />
      </Border>
    </DockPanel>
  </Button>
</Window>
```

<span data-ttu-id="516c6-303">A figura a seguir mostra o conteúdo deste botão:</span><span class="sxs-lookup"><span data-stu-id="516c6-303">The following figure shows the content of this button:</span></span>

![Um botão que contém vários tipos de conteúdo](media/introduction-to-wpf/wpfintrofigure22.png)

<span data-ttu-id="516c6-305">Para obter mais informações sobre os tipos de conteúdo compatíveis com vários controles, confira [Modelo de conteúdo do WPF](controls/wpf-content-model.md).</span><span class="sxs-lookup"><span data-stu-id="516c6-305">For more information on the kinds of content that is supported by various controls, see [WPF content model](controls/wpf-content-model.md).</span></span>

### <a name="triggers"></a><span data-ttu-id="516c6-306">Gatilhos</span><span class="sxs-lookup"><span data-stu-id="516c6-306">Triggers</span></span>

<span data-ttu-id="516c6-307">Embora o objetivo principal da marcação XAML seja implementar a aparência de um aplicativo, você também pode usar XAML para implementar alguns aspectos do comportamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="516c6-307">Although the main purpose of XAML markup is to implement an application's appearance, you can also use XAML to implement some aspects of an application's behavior.</span></span> <span data-ttu-id="516c6-308">Um exemplo é o uso de gatilhos para alterar a aparência de um aplicativo com base em interações do usuário.</span><span class="sxs-lookup"><span data-stu-id="516c6-308">One example is the use of triggers to change an application's appearance based on user interactions.</span></span> <span data-ttu-id="516c6-309">Para obter mais informações, consulte [estilos e modelos](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="516c6-309">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="control-templates"></a><span data-ttu-id="516c6-310">Modelos de controle</span><span class="sxs-lookup"><span data-stu-id="516c6-310">Control templates</span></span>

<span data-ttu-id="516c6-311">As interfaces do usuário padrão para controles WPF normalmente são construídas de outros controles e formas.</span><span class="sxs-lookup"><span data-stu-id="516c6-311">The default user interfaces for WPF controls are typically constructed from other controls and shapes.</span></span> <span data-ttu-id="516c6-312">Por exemplo, um <xref:System.Windows.Controls.Button> é composto de dois controles, <xref:Microsoft.Windows.Themes.ButtonChrome> e <xref:System.Windows.Controls.ContentPresenter>.</span><span class="sxs-lookup"><span data-stu-id="516c6-312">For example, a <xref:System.Windows.Controls.Button> is composed of both <xref:Microsoft.Windows.Themes.ButtonChrome> and <xref:System.Windows.Controls.ContentPresenter> controls.</span></span> <span data-ttu-id="516c6-313">O <xref:Microsoft.Windows.Themes.ButtonChrome> fornece a aparência padrão do botão, enquanto o <xref:System.Windows.Controls.ContentPresenter> exibe o conteúdo do botão, conforme especificado pela propriedade <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="516c6-313">The <xref:Microsoft.Windows.Themes.ButtonChrome> provides the standard button appearance, while the <xref:System.Windows.Controls.ContentPresenter> displays the button's content, as specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property.</span></span>

<span data-ttu-id="516c6-314">Às vezes, a aparência padrão de um controle pode ser incongruente com a aparência geral de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="516c6-314">Sometimes the default appearance of a control may be incongruent with the overall appearance of an application.</span></span> <span data-ttu-id="516c6-315">Nesse caso, você pode usar um <xref:System.Windows.Controls.ControlTemplate> para alterar a aparência da interface do usuário do controle sem alterar seu conteúdo e seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="516c6-315">In this case, you can use a <xref:System.Windows.Controls.ControlTemplate> to change the appearance of the control's user interface without changing its content and behavior.</span></span>

<span data-ttu-id="516c6-316">O exemplo a seguir mostra como alterar a aparência de um <xref:System.Windows.Controls.Button> usando uma <xref:System.Windows.Controls.ControlTemplate>:</span><span class="sxs-lookup"><span data-stu-id="516c6-316">The following example shows how to change the appearance of a <xref:System.Windows.Controls.Button> by using a <xref:System.Windows.Controls.ControlTemplate>:</span></span>

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_17.vb)]

<span data-ttu-id="516c6-317">Neste exemplo, a interface do usuário padrão do botão foi substituída por um <xref:System.Windows.Shapes.Ellipse> que tem uma borda azul-escuro e foi preenchido usando um <xref:System.Windows.Media.RadialGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="516c6-317">In this example, the default button user interface has been replaced with an <xref:System.Windows.Shapes.Ellipse> that has a dark blue border and is filled using a <xref:System.Windows.Media.RadialGradientBrush>.</span></span> <span data-ttu-id="516c6-318">O controle <xref:System.Windows.Controls.ContentPresenter> exibe o conteúdo de <xref:System.Windows.Controls.Button>, "Clique-me!"</span><span class="sxs-lookup"><span data-stu-id="516c6-318">The <xref:System.Windows.Controls.ContentPresenter> control displays the content of the <xref:System.Windows.Controls.Button>, "Click Me!"</span></span> <span data-ttu-id="516c6-319">Quando o <xref:System.Windows.Controls.Button> é clicado, o evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click> ainda é gerado como parte do comportamento padrão do controle <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="516c6-319">When the <xref:System.Windows.Controls.Button> is clicked, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event is still raised as part of the <xref:System.Windows.Controls.Button> control's default behavior.</span></span> <span data-ttu-id="516c6-320">O resultado é mostrado na figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="516c6-320">The result is shown in the following figure:</span></span>

![Um botão elíptico e uma segunda janela](media/introduction-to-wpf/wpfintrofigure2.png)

### <a name="data-templates"></a><span data-ttu-id="516c6-322">Modelos de dados</span><span class="sxs-lookup"><span data-stu-id="516c6-322">Data templates</span></span>

<span data-ttu-id="516c6-323">Enquanto um modelo de controle permite que você especifique a aparência de um controle, um modelo de dados permite que você especifique a aparência do conteúdo de um controle.</span><span class="sxs-lookup"><span data-stu-id="516c6-323">Whereas a control template lets you specify the appearance of a control, a data template lets you specify the appearance of a control's content.</span></span> <span data-ttu-id="516c6-324">Modelos de dados são frequentemente usados para aprimorar o modo como os dados associados são exibidos.</span><span class="sxs-lookup"><span data-stu-id="516c6-324">Data templates are frequently used to enhance how bound data is displayed.</span></span> <span data-ttu-id="516c6-325">A figura a seguir mostra a aparência padrão de um <xref:System.Windows.Controls.ListBox> associado a uma coleção de objetos `Task`, em que cada tarefa tem um nome, uma descrição e uma prioridade:</span><span class="sxs-lookup"><span data-stu-id="516c6-325">The following figure shows the default appearance for a <xref:System.Windows.Controls.ListBox> that is bound to a collection of `Task` objects, where each task has a name, description, and priority:</span></span>

![Uma caixa de listagem com a aparência padrão](media/introduction-to-wpf/wpfintrofigure18.png)

<span data-ttu-id="516c6-327">A aparência padrão é o que seria esperado de <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="516c6-327">The default appearance is what you would expect from a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="516c6-328">No entanto, a aparência padrão de cada tarefa contém somente o nome da tarefa.</span><span class="sxs-lookup"><span data-stu-id="516c6-328">However, the default appearance of each task contains only the task name.</span></span> <span data-ttu-id="516c6-329">Para mostrar o nome da tarefa, a descrição e a prioridade, a aparência padrão dos itens da lista associada ao controle <xref:System.Windows.Controls.ListBox> deve ser alterada usando um <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="516c6-329">To show the task name, description, and priority, the default appearance of the <xref:System.Windows.Controls.ListBox> control's bound list items must be changed by using a <xref:System.Windows.DataTemplate>.</span></span> <span data-ttu-id="516c6-330">O XAML a seguir define tal <xref:System.Windows.DataTemplate>, que é aplicado a cada tarefa usando o atributo <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>:</span><span class="sxs-lookup"><span data-stu-id="516c6-330">The following XAML defines such a <xref:System.Windows.DataTemplate>, which is applied to each task by using the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> attribute:</span></span>

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="SDKSample.DataTemplateWindow"
  Title="With a Data Template">
  <Window.Resources>
    <!-- Data Template (applied to each bound task item in the task collection) -->
    <DataTemplate x:Key="myTaskTemplate">
      <Border Name="border" BorderBrush="DarkSlateBlue" BorderThickness="2"
        CornerRadius="2" Padding="5" Margin="5">
        <Grid>
          <Grid.RowDefinitions>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
          </Grid.RowDefinitions>
          <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition />
          </Grid.ColumnDefinitions>
          <TextBlock Grid.Row="0" Grid.Column="0" Padding="0,0,5,0" Text="Task Name:"/>
          <TextBlock Grid.Row="0" Grid.Column="1" Text="{Binding Path=TaskName}"/>
          <TextBlock Grid.Row="1" Grid.Column="0" Padding="0,0,5,0" Text="Description:"/>
          <TextBlock Grid.Row="1" Grid.Column="1" Text="{Binding Path=Description}"/>
          <TextBlock Grid.Row="2" Grid.Column="0" Padding="0,0,5,0" Text="Priority:"/>
          <TextBlock Grid.Row="2" Grid.Column="1" Text="{Binding Path=Priority}"/>
        </Grid>
      </Border>
    </DataTemplate>
  </Window.Resources>

  <!-- UI -->
  <DockPanel>
    <!-- Title -->
    <Label DockPanel.Dock="Top" FontSize="18" Margin="5" Content="My Task List:"/>

    <!-- Data template is specified by the ItemTemplate attribute -->
    <ListBox
      ItemsSource="{Binding}"
      ItemTemplate="{StaticResource myTaskTemplate}"
      HorizontalContentAlignment="Stretch"
      IsSynchronizedWithCurrentItem="True"
      Margin="5,0,5,5" />

 </DockPanel>
</Window>
```

<span data-ttu-id="516c6-331">A figura a seguir mostra o efeito desse código:</span><span class="sxs-lookup"><span data-stu-id="516c6-331">The following figure shows the effect of this code:</span></span>

![Caixa de listagem que usa um modelo de dados](media/introduction-to-wpf/wpfintrofigure19.png)

<span data-ttu-id="516c6-333">Observe que o <xref:System.Windows.Controls.ListBox> manteve seu comportamento e sua aparência geral. Apenas a aparência do conteúdo que está sendo exibido pela caixa de listagem foi alterada.</span><span class="sxs-lookup"><span data-stu-id="516c6-333">Note that the <xref:System.Windows.Controls.ListBox> has retained its behavior and overall appearance; only the appearance of the content being displayed by the list box has changed.</span></span>

<span data-ttu-id="516c6-334">Para obter mais informações, confira [Visão geral de modelagem de dados](data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="516c6-334">For more information, see [Data templating overview](data/data-templating-overview.md).</span></span>

### <a name="styles"></a><span data-ttu-id="516c6-335">Estilos</span><span class="sxs-lookup"><span data-stu-id="516c6-335">Styles</span></span>

<span data-ttu-id="516c6-336">Os estilos permitem que os desenvolvedores e designers padronizem uma determinada aparência para seus produtos.</span><span class="sxs-lookup"><span data-stu-id="516c6-336">Styles enable developers and designers to standardize on a particular appearance for their product.</span></span> <span data-ttu-id="516c6-337">O WPF fornece um modelo de estilo sólido, cuja base é o elemento <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="516c6-337">WPF provides a strong style model, the foundation of which is the <xref:System.Windows.Style> element.</span></span> <span data-ttu-id="516c6-338">O exemplo a seguir cria um estilo que define a cor do plano de fundo para cada <xref:System.Windows.Controls.Button> em uma janela para `Orange`:</span><span class="sxs-lookup"><span data-stu-id="516c6-338">The following example creates a style that sets the background color for every <xref:System.Windows.Controls.Button> on a window to `Orange`:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.StyleWindow"
    Title="Styles">
  <!-- Style that will be applied to all buttons -->
  <Style TargetType="{x:Type Button}">
    <Setter Property="Background" Value="Orange" />
    <Setter Property="BorderBrush" Value="Crimson" />
    <Setter Property="FontSize" Value="20" />
    <Setter Property="FontWeight" Value="Bold" />
    <Setter Property="Margin" Value="5" />
  </Style>
  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>

  <!-- This label will not have the style applied to it -->
  <Label>Don't Click Me!</Label>

  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>
</Window>
```

<span data-ttu-id="516c6-339">Já que esse estilo atinge todos os controles <xref:System.Windows.Controls.Button>, o estilo é aplicado automaticamente a todos os botões na janela, conforme mostrado na figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="516c6-339">Because this style targets all <xref:System.Windows.Controls.Button> controls, the style is automatically applied to all the buttons in the window, as shown in the following figure:</span></span>

![Dois botões alaranjados](media/introduction-to-wpf/wpfintrofigure20.png)

<span data-ttu-id="516c6-341">Para obter mais informações, consulte [estilos e modelos](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="516c6-341">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="resources"></a><span data-ttu-id="516c6-342">Recursos</span><span class="sxs-lookup"><span data-stu-id="516c6-342">Resources</span></span>

<span data-ttu-id="516c6-343">Controles em um aplicativo devem compartilhar a mesma aparência, que pode incluir qualquer coisa de fontes e cores da tela de fundo até estilos, modelos de dados e modelos de controle.</span><span class="sxs-lookup"><span data-stu-id="516c6-343">Controls in an application should share the same appearance, which can include anything from fonts and background colors to control templates, data templates, and styles.</span></span> <span data-ttu-id="516c6-344">Você pode usar o suporte do WPF para recursos de interface do usuário para encapsular esses recursos em um único local para reutilização.</span><span class="sxs-lookup"><span data-stu-id="516c6-344">You can use WPF's support for user interface resources to encapsulate these resources in a single location for reuse.</span></span>

<span data-ttu-id="516c6-345">O exemplo a seguir define uma cor de plano de fundo comum que é compartilhada por um <xref:System.Windows.Controls.Button> e um <xref:System.Windows.Controls.Label>:</span><span class="sxs-lookup"><span data-stu-id="516c6-345">The following example defines a common background color that is shared by a <xref:System.Windows.Controls.Button> and a <xref:System.Windows.Controls.Label>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ResourcesWindow"
    Title="Resources Window">

  <!-- Define window-scoped background color resource -->
  <Window.Resources>
    <SolidColorBrush x:Key="defaultBackground" Color="Red" />
  </Window.Resources>

  <!-- Button background is defined by window-scoped resource -->
  <Button Background="{StaticResource defaultBackground}">One Button</Button>

  <!-- Label background is defined by window-scoped resource -->
  <Label Background="{StaticResource defaultBackground}">One Label</Label>
</Window>
```

<span data-ttu-id="516c6-346">Este exemplo implementa um recurso de cor da tela de fundo usando o elemento da propriedade `Window.Resources`.</span><span class="sxs-lookup"><span data-stu-id="516c6-346">This example implements a background color resource by using the `Window.Resources` property element.</span></span> <span data-ttu-id="516c6-347">Este recurso está disponível para todos os filhos de <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="516c6-347">This resource is available to all children of the <xref:System.Windows.Window>.</span></span> <span data-ttu-id="516c6-348">Há uma variedade de recursos escopos, incluindo os seguintes, listados na ordem em que eles são resolvidos:</span><span class="sxs-lookup"><span data-stu-id="516c6-348">There are a variety of resource scopes, including the following, listed in the order in which they are resolved:</span></span>

1. <span data-ttu-id="516c6-349">Um controle individual (usando a propriedade <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> herdada).</span><span class="sxs-lookup"><span data-stu-id="516c6-349">An individual control (using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

2. <span data-ttu-id="516c6-350">Um <xref:System.Windows.Window> ou um <xref:System.Windows.Controls.Page> (também usando a propriedade herdada <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="516c6-350">A <xref:System.Windows.Window> or a <xref:System.Windows.Controls.Page> (also using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

3. <span data-ttu-id="516c6-351">Um <xref:System.Windows.Application> (usando a propriedade <xref:System.Windows.Application.Resources%2A?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="516c6-351">An <xref:System.Windows.Application> (using the <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> property).</span></span>

<span data-ttu-id="516c6-352">A variedade de escopos oferece flexibilidade em relação à maneira na qual você pode definir e compartilhar seus recursos.</span><span class="sxs-lookup"><span data-stu-id="516c6-352">The variety of scopes gives you flexibility with respect to the way in which you define and share your resources.</span></span>

<span data-ttu-id="516c6-353">Como uma alternativa a associar diretamente os recursos a um escopo específico, você pode compactar um ou mais recursos usando um <xref:System.Windows.ResourceDictionary> separado, que pode ser referenciado em outras partes de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="516c6-353">As an alternative to directly associating your resources with a particular scope, you can package one or more resources by using a separate <xref:System.Windows.ResourceDictionary> that can be referenced in other parts of an application.</span></span> <span data-ttu-id="516c6-354">Por exemplo, o exemplo a seguir define uma cor de plano de fundo padrão em um dicionário de recursos:</span><span class="sxs-lookup"><span data-stu-id="516c6-354">For example, the following example defines a default background color in a resource dictionary:</span></span>

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

<span data-ttu-id="516c6-355">O exemplo a seguir faz referência ao dicionário de recursos definido no exemplo anterior para que ele seja compartilhado em um aplicativo:</span><span class="sxs-lookup"><span data-stu-id="516c6-355">The following example references the resource dictionary defined in the previous example so that it is shared across an application:</span></span>

```xaml
<Application
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.App">

  <Application.Resources>
    <ResourceDictionary>
      <ResourceDictionary.MergedDictionaries>
        <ResourceDictionary Source="BackgroundColorResources.xaml"/>
      </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
  </Application.Resources>
</Application>
```

<span data-ttu-id="516c6-356">Recursos e dicionários de recurso são a base do suporte do WPF a temas e capas.</span><span class="sxs-lookup"><span data-stu-id="516c6-356">Resources and resource dictionaries are the foundation of WPF support for themes and skins.</span></span>

<span data-ttu-id="516c6-357">Para obter mais informações, consulte [Recursos](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="516c6-357">For more information, see [Resources](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="custom-controls"></a><span data-ttu-id="516c6-358">Controles personalizados</span><span class="sxs-lookup"><span data-stu-id="516c6-358">Custom controls</span></span>

<span data-ttu-id="516c6-359">Embora o WPF forneça um host de suporte a personalização, você poderá encontrar situações em que os controles WPF existentes não atendam às necessidades de seu aplicativo ou seus usuários.</span><span class="sxs-lookup"><span data-stu-id="516c6-359">Although WPF provides a host of customization support, you may encounter situations where existing WPF controls do not meet the needs of either your application or its users.</span></span> <span data-ttu-id="516c6-360">Isso pode ocorrer quando:</span><span class="sxs-lookup"><span data-stu-id="516c6-360">This can occur when:</span></span>

- <span data-ttu-id="516c6-361">Não é possível criar a interface do usuário que você precisa ao personalizar a aparência de implementações existentes do WPF.</span><span class="sxs-lookup"><span data-stu-id="516c6-361">The user interface that you require cannot be created by customizing the look and feel of existing WPF implementations.</span></span>

- <span data-ttu-id="516c6-362">Não há suporte para o comportamento que você precisa (ou não é um suporte obtido facilmente) por implementações existentes do WPF.</span><span class="sxs-lookup"><span data-stu-id="516c6-362">The behavior that you require is not supported (or not easily supported) by existing WPF implementations.</span></span>

<span data-ttu-id="516c6-363">Neste ponto, no entanto, você pode tirar proveito de um dos três modelos do WPF para criar um novo controle.</span><span class="sxs-lookup"><span data-stu-id="516c6-363">At this point, however, you can take advantage of one of three WPF models to create a new control.</span></span> <span data-ttu-id="516c6-364">Cada modelo destina-se a um cenário específico e requer que o controle personalizado derive de uma classe base específica do WPF.</span><span class="sxs-lookup"><span data-stu-id="516c6-364">Each model targets a specific scenario and requires your custom control to derive from a particular WPF base class.</span></span> <span data-ttu-id="516c6-365">Os três modelos estão listados aqui:</span><span class="sxs-lookup"><span data-stu-id="516c6-365">The three models are listed here:</span></span>

- <span data-ttu-id="516c6-366">**Modelo de Controle de Usuário**.</span><span class="sxs-lookup"><span data-stu-id="516c6-366">**User Control Model**.</span></span> <span data-ttu-id="516c6-367">Um controle personalizado é derivado de <xref:System.Windows.Controls.UserControl> e é composto de um ou mais controles.</span><span class="sxs-lookup"><span data-stu-id="516c6-367">A custom control derives from <xref:System.Windows.Controls.UserControl> and is composed of one or more other controls.</span></span>

- <span data-ttu-id="516c6-368">**Modelo de Controle**.</span><span class="sxs-lookup"><span data-stu-id="516c6-368">**Control Model**.</span></span> <span data-ttu-id="516c6-369">Um controle personalizado é derivado de <xref:System.Windows.Controls.Control> e é usado para criar implementações que separam seu comportamento de sua aparência usando modelos, como a maioria dos controles do WPF.</span><span class="sxs-lookup"><span data-stu-id="516c6-369">A custom control derives from <xref:System.Windows.Controls.Control> and is used to build implementations that separate their behavior from their appearance using templates, much like the majority of WPF controls.</span></span> <span data-ttu-id="516c6-370">Derivar de <xref:System.Windows.Controls.Control> proporciona mais liberdade para criar uma interface do usuário personalizada de controles de usuário, mas pode exigir mais esforço.</span><span class="sxs-lookup"><span data-stu-id="516c6-370">Deriving from <xref:System.Windows.Controls.Control> allows you more freedom for creating a custom user interface than user controls, but it may require more effort.</span></span>

- <span data-ttu-id="516c6-371">**Modelo de elemento de estrutura**.</span><span class="sxs-lookup"><span data-stu-id="516c6-371">**Framework Element Model**.</span></span> <span data-ttu-id="516c6-372">Um controle personalizado é derivado de <xref:System.Windows.FrameworkElement> quando sua aparência é definida pela lógica de renderização personalizada (e não por modelos).</span><span class="sxs-lookup"><span data-stu-id="516c6-372">A custom control derives from <xref:System.Windows.FrameworkElement> when its appearance is defined by custom rendering logic (not templates).</span></span>

<span data-ttu-id="516c6-373">O exemplo a seguir mostra um controle numérico para cima/para baixo personalizado que deriva de <xref:System.Windows.Controls.UserControl>:</span><span class="sxs-lookup"><span data-stu-id="516c6-373">The following example shows a custom numeric up/down control that derives from <xref:System.Windows.Controls.UserControl>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_34.vb)]

<span data-ttu-id="516c6-374">O exemplo a seguir ilustra o XAML necessário para incorporar o controle de usuário em um <xref:System.Windows.Window>:</span><span class="sxs-lookup"><span data-stu-id="516c6-374">The following example illustrates the XAML that is required to incorporate the user control into a <xref:System.Windows.Window>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_37.xaml)]

<span data-ttu-id="516c6-375">A figura a seguir mostra o controle de `NumericUpDown` hospedado em um <xref:System.Windows.Window>:</span><span class="sxs-lookup"><span data-stu-id="516c6-375">The following figure shows the `NumericUpDown` control hosted in a <xref:System.Windows.Window>:</span></span>

![Um UserControl personalizado](media/introduction-to-wpf/wpfintrofigure3.png)

<span data-ttu-id="516c6-377">Para obter mais informações sobre controles personalizados, confira [Visão geral da criação de controles](controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="516c6-377">For more information on custom controls, see [Control authoring overview](controls/control-authoring-overview.md).</span></span>

## <a name="wpf-best-practices"></a><span data-ttu-id="516c6-378">Melhores práticas do WPF</span><span class="sxs-lookup"><span data-stu-id="516c6-378">WPF best practices</span></span>

<span data-ttu-id="516c6-379">Assim como com qualquer plataforma de desenvolvimento, o WPF pode ser usado de várias maneiras para atingir o resultado desejado.</span><span class="sxs-lookup"><span data-stu-id="516c6-379">As with any development platform, WPF can be used in a variety of ways to achieve the desired result.</span></span> <span data-ttu-id="516c6-380">Como uma maneira de garantir que os aplicativos WPF forneçam a experiência de usuário necessária e atendam às demandas do público em geral, há melhores práticas para acessibilidade, globalização e localização e desempenho.</span><span class="sxs-lookup"><span data-stu-id="516c6-380">As a way of ensuring that your WPF applications provide the required user experience and meet the demands of the audience in general, there are recommended best practices for accessibility, globalization and localization, and performance.</span></span> <span data-ttu-id="516c6-381">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="516c6-381">For more information, see:</span></span>

- [<span data-ttu-id="516c6-382">Acessibilidade</span><span class="sxs-lookup"><span data-stu-id="516c6-382">Accessibility</span></span>](../ui-automation/accessibility-best-practices.md)
- [<span data-ttu-id="516c6-383">Globalização e localização do WPF</span><span class="sxs-lookup"><span data-stu-id="516c6-383">WPF globalization and localization</span></span>](advanced/wpf-globalization-and-localization-overview.md)
- [<span data-ttu-id="516c6-384">Desempenho de aplicativo do WPF</span><span class="sxs-lookup"><span data-stu-id="516c6-384">WPF app performance</span></span>](advanced/optimizing-wpf-application-performance.md)
- [<span data-ttu-id="516c6-385">Segurança do WPF</span><span class="sxs-lookup"><span data-stu-id="516c6-385">WPF security</span></span>](security-wpf.md)

## <a name="next-steps"></a><span data-ttu-id="516c6-386">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="516c6-386">Next steps</span></span>

<span data-ttu-id="516c6-387">Analisamos os principais recursos do WPF.</span><span class="sxs-lookup"><span data-stu-id="516c6-387">We've looked at the key features of WPF.</span></span> <span data-ttu-id="516c6-388">Agora, é hora de criar seu primeiro aplicativo do WPF.</span><span class="sxs-lookup"><span data-stu-id="516c6-388">Now it's time to build your first WPF app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="516c6-389">Passo a passo: meu primeiro aplicativo da área de trabalho do WPF</span><span class="sxs-lookup"><span data-stu-id="516c6-389">Walkthrough: My first WPF desktop app</span></span>](getting-started/walkthrough-my-first-wpf-desktop-application.md)

## <a name="see-also"></a><span data-ttu-id="516c6-390">Consulte também</span><span class="sxs-lookup"><span data-stu-id="516c6-390">See also</span></span>

- [<span data-ttu-id="516c6-391">Introdução ao WPF</span><span class="sxs-lookup"><span data-stu-id="516c6-391">Get started with WPF</span></span>](getting-started/index.md)
- [<span data-ttu-id="516c6-392">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="516c6-392">Windows Presentation Foundation</span></span>](index.md)
- [<span data-ttu-id="516c6-393">Recursos da comunidade do WPF</span><span class="sxs-lookup"><span data-stu-id="516c6-393">WPF community resources</span></span>](getting-started/community-feedback.md)
