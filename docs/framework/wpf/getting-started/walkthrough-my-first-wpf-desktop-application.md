---
title: "Passo a passo: Meu aplicativo da área de trabalho primeiro do WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
caps.latest.revision: "71"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3667d507f4c35174c1e888c9781b5f74ffd496a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="93b82-102">Passo a passo: Meu aplicativo da área de trabalho primeiro do WPF</span><span class="sxs-lookup"><span data-stu-id="93b82-102">Walkthrough: My first WPF desktop application</span></span>
<span data-ttu-id="93b82-103">Este passo a passo fornece uma introdução ao desenvolvimento de um [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] aplicativo que inclui os elementos que são comuns à maioria [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos: [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] marcação, por trás do código, definições de aplicativo, controles, layout associação de dados e estilos.</span><span class="sxs-lookup"><span data-stu-id="93b82-103">This walkthrough provides an introduction to the development of a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application that includes the elements that are common to most [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications: [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> 
  
 <span data-ttu-id="93b82-104">Este passo a passo o orienta o desenvolvimento de um simples [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativo usando as etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="93b82-104">This walkthrough guides you through the development of a simple [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application using the following steps.</span></span> 
  
-   <span data-ttu-id="93b82-105">Definindo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para criar a aparência do aplicativo [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="93b82-105">Defining [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to design the appearance of the application's [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="93b82-106">Gravando o código para criar o comportamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93b82-106">Writing code to build the application's behavior.</span></span> 
  
-   <span data-ttu-id="93b82-107">Criando uma definição de aplicativo para gerenciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93b82-107">Creating an application definition to manage the application.</span></span> 
  
-   <span data-ttu-id="93b82-108">Adicionando controles e criar o layout para compor o aplicativo [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="93b82-108">Adding controls and creating the layout to compose the application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="93b82-109">Criando estilos para criar uma aparência consistente em todo um aplicativo [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="93b82-109">Creating styles to create a consistent appearance throughout an application's [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="93b82-110">Associação de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a dados para popular o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de dados e manter os dados e [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] sincronizados.</span><span class="sxs-lookup"><span data-stu-id="93b82-110">Binding the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to data to both populate the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] from data and keep the data and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] synchronized.</span></span> 
  
 <span data-ttu-id="93b82-111">No final do passo a passo, você terá criado um autônomo [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] aplicativo que permite aos usuários exibir relatórios de despesa para pessoas selecionadas.</span><span class="sxs-lookup"><span data-stu-id="93b82-111">By the end of the walkthrough, you will have built a standalone [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="93b82-112">O aplicativo será composto de vários [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] páginas que são hospedadas em uma janela com estilo de navegador.</span><span class="sxs-lookup"><span data-stu-id="93b82-112">The application will be composed of several [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pages that are hosted in a browser-style window.</span></span> 
  
 <span data-ttu-id="93b82-113">O código de exemplo que é usado para este passo a passo de compilação está disponível para ambos [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] e [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] em [Introdução ao criar aplicativos do WPF](http://go.microsoft.com/fwlink/?LinkID=160008).</span><span class="sxs-lookup"><span data-stu-id="93b82-113">The sample code that is used to build this walkthrough is available for both [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] and [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] at  [Introduction to Building WPF Applications](http://go.microsoft.com/fwlink/?LinkID=160008).</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="93b82-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="93b82-114">Prerequisites</span></span>  

- [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="93b82-115">ou posterior</span><span class="sxs-lookup"><span data-stu-id="93b82-115"> or later</span></span>

<span data-ttu-id="93b82-116">Para obter mais informações sobre como instalar a versão mais recente do Visual Studio, consulte [instale o Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="93b82-116">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>
  
## <a name="creating-the-application-project"></a><span data-ttu-id="93b82-117">Criando o projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="93b82-117">Creating the application project</span></span>  
 <span data-ttu-id="93b82-118">Nesta seção, você criará a infraestrutura do aplicativo, que inclui uma definição de aplicativo, duas páginas e uma imagem.</span><span class="sxs-lookup"><span data-stu-id="93b82-118">In this section, you create the application infrastructure, which includes an application definition, two pages, and an image.</span></span> 
  
1. <span data-ttu-id="93b82-119">Crie um novo projeto de aplicativo do WPF no Visual Basic ou no Visual C#, chamado `ExpenseIt`.</span><span class="sxs-lookup"><span data-stu-id="93b82-119">Create a new WPF Application project in Visual Basic or Visual C# named `ExpenseIt`.</span></span> <span data-ttu-id="93b82-120">Para obter mais informações, consulte [Como criar um novo projeto de aplicativo do WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="93b82-120">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span> 
  
    > [!NOTE]
    >  <span data-ttu-id="93b82-121">Este passo a passo usa o <xref:System.Windows.Controls.DataGrid> controle que está disponível no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="93b82-121">This walkthrough uses the <xref:System.Windows.Controls.DataGrid> control that is available in the .NET Framework 4.</span></span> <span data-ttu-id="93b82-122">Ser-se de que seu projeto se destina ao .NET Framework 4 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="93b82-122">Be sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="93b82-123">Para obter mais informações, consulte[como: uma versão do .NET Framework de destino](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="93b82-123">For more information, see[How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span> 
  
2. <span data-ttu-id="93b82-124">Abra o Application.xaml (Visual Basic) ou App.xaml (C#).</span><span class="sxs-lookup"><span data-stu-id="93b82-124">Open Application.xaml (Visual Basic) or App.xaml (C#).</span></span> 
  
     <span data-ttu-id="93b82-125">Isso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo define uma [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativo e os recursos de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93b82-125">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file defines a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application and any application resources.</span></span> <span data-ttu-id="93b82-126">Você também usar esse arquivo para especificar o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] mostra que automaticamente quando o aplicativo é iniciado; nesse caso, MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="93b82-126">You also use this file to specify the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] that automatically shows when the application starts; in this case, MainWindow.xaml.</span></span> 
  
     <span data-ttu-id="93b82-127">O [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] deve se parecer com no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="93b82-127">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]  
  
     <span data-ttu-id="93b82-128">Ou assim no C#:</span><span class="sxs-lookup"><span data-stu-id="93b82-128">Or like this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]  
  
3. <span data-ttu-id="93b82-129">Abra MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="93b82-129">Open MainWindow.xaml.</span></span> 
  
     <span data-ttu-id="93b82-130">Isso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo é a janela principal do seu aplicativo e exibe o conteúdo criado nas páginas.</span><span class="sxs-lookup"><span data-stu-id="93b82-130">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="93b82-131">O <xref:System.Windows.Window> classe define as propriedades de uma janela, como título, tamanho ou no ícone e trata os eventos, como fechar ou ocultar.</span><span class="sxs-lookup"><span data-stu-id="93b82-131">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span> 
  
4. <span data-ttu-id="93b82-132">Alterar o <xref:System.Windows.Window> elemento para uma <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="93b82-132">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> 
  
     <span data-ttu-id="93b82-133">Este aplicativo navegará para um conteúdo diferente dependendo da interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="93b82-133">This application will navigate to different content depending on the user interaction.</span></span> <span data-ttu-id="93b82-134">Portanto, o principal <xref:System.Windows.Window> precisa ser alterado para um <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="93b82-134">Therefore, the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="93b82-135"><xref:System.Windows.Navigation.NavigationWindow>herda todas as propriedades de <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="93b82-135"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="93b82-136">O <xref:System.Windows.Navigation.NavigationWindow> elemento no arquivo XAML cria uma instância de <xref:System.Windows.Navigation.NavigationWindow> classe.</span><span class="sxs-lookup"><span data-stu-id="93b82-136">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="93b82-137">Para obter mais informações, consulte [Visão geral de navegação](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="93b82-137">For more information, see [Navigation Overview](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span></span> 
  
5. <span data-ttu-id="93b82-138">Alterar as propriedades a seguir sobre o <xref:System.Windows.Navigation.NavigationWindow> elemento:</span><span class="sxs-lookup"><span data-stu-id="93b82-138">Change the following properties on the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>  
  
    -   <span data-ttu-id="93b82-139">Definir o <xref:System.Windows.Window.Title%2A> propriedade como "ExpenseIt".</span><span class="sxs-lookup"><span data-stu-id="93b82-139">Set the <xref:System.Windows.Window.Title%2A> property to "ExpenseIt".</span></span> 
  
    -   <span data-ttu-id="93b82-140">Definir o <xref:System.Windows.FrameworkElement.Width%2A> propriedade para 500 pixels.</span><span class="sxs-lookup"><span data-stu-id="93b82-140">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span> 
  
    -   <span data-ttu-id="93b82-141">Definir o <xref:System.Windows.FrameworkElement.Height%2A> propriedade 350 pixels.</span><span class="sxs-lookup"><span data-stu-id="93b82-141">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span> 
  
    -   <span data-ttu-id="93b82-142">Remover o <xref:System.Windows.Controls.Grid> elementos entre o <xref:System.Windows.Navigation.NavigationWindow> marcas.</span><span class="sxs-lookup"><span data-stu-id="93b82-142">Remove the <xref:System.Windows.Controls.Grid> elements between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span> 
  
     <span data-ttu-id="93b82-143">O [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] deve se parecer com no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="93b82-143">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]  
  
     <span data-ttu-id="93b82-144">Ou assim no C#:</span><span class="sxs-lookup"><span data-stu-id="93b82-144">Or like this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]  
  
6. <span data-ttu-id="93b82-145">Abra MainWindow.xaml.vb ou MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="93b82-145">Open MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span> 
  
     <span data-ttu-id="93b82-146">Esse é um arquivo code-behind que contém o código para manipular os eventos declarados no MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="93b82-146">This file is a code-behind file that contains code to handle the events declared in MainWindow.xaml.</span></span> <span data-ttu-id="93b82-147">Esse arquivo contém uma classe parcial para a janela definida no XAML.</span><span class="sxs-lookup"><span data-stu-id="93b82-147">This file contains a partial class for the window defined in XAML.</span></span> 
  
7. <span data-ttu-id="93b82-148">Se você estiver usando c#, altere o `MainWindow` classe para derivar de <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="93b82-148">If you are using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> 
  
     <span data-ttu-id="93b82-149">No Visual Basic, isso ocorre automaticamente quando você altera a janela no XAML.</span><span class="sxs-lookup"><span data-stu-id="93b82-149">In Visual Basic, this happens automatically when you change the window in XAML.</span></span> 
  
     <span data-ttu-id="93b82-150">Seu código deve ter esta aparência.</span><span class="sxs-lookup"><span data-stu-id="93b82-150">Your code should look like this.</span></span> 
  
    [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
    [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]  
  
## <a name="adding-files-to-the-application"></a><span data-ttu-id="93b82-151">Adicionando arquivos ao aplicativo</span><span class="sxs-lookup"><span data-stu-id="93b82-151">Adding files to the application</span></span>  
 <span data-ttu-id="93b82-152">Nesta seção, você adiciona duas páginas e uma imagem ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93b82-152">In this section, you add two pages and an image to the application.</span></span> 
  
1. <span data-ttu-id="93b82-153">Adicione uma nova página (WPF) ao projeto nomeado `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="93b82-153">Add a new Page (WPF) to the project named `ExpenseItHome.xaml`.</span></span> <span data-ttu-id="93b82-154">Para obter mais informações, consulte [como: adicionar novos itens a um projeto WPF](http://msdn.microsoft.com/en-us/17e6b238-fc32-4385-98ef-2f66ca09d9ad).</span><span class="sxs-lookup"><span data-stu-id="93b82-154">For more information, see [How to: Add New Items to a WPF Project](http://msdn.microsoft.com/en-us/17e6b238-fc32-4385-98ef-2f66ca09d9ad).</span></span> 
  
     <span data-ttu-id="93b82-155">Esta página é a primeira página que será exibida quando o aplicativo for iniciado.</span><span class="sxs-lookup"><span data-stu-id="93b82-155">This page is the first page that is displayed when the application is launched.</span></span> <span data-ttu-id="93b82-156">Ela mostrará uma lista de pessoas na qual um usuário poderá selecionar uma delas para exibir um relatório de despesas.</span><span class="sxs-lookup"><span data-stu-id="93b82-156">It will show a list of people from which a user can select a person to show an expense report for.</span></span> 
  
2. <span data-ttu-id="93b82-157">Abra ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="93b82-157">Open ExpenseItHome.xaml.</span></span> 
  
3. <span data-ttu-id="93b82-158">Definir o <xref:System.Windows.Controls.Page.Title%2A> para "ExpenseIt - Home".</span><span class="sxs-lookup"><span data-stu-id="93b82-158">Set the <xref:System.Windows.Controls.Page.Title%2A> to "ExpenseIt - Home".</span></span> 
  
     <span data-ttu-id="93b82-159">O [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] deve se parecer com no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="93b82-159">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]  
  
     <span data-ttu-id="93b82-160">Ou em C#:</span><span class="sxs-lookup"><span data-stu-id="93b82-160">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]  
  
4. <span data-ttu-id="93b82-161">Abra MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="93b82-161">Open MainWindow.xaml.</span></span> 
  
5. <span data-ttu-id="93b82-162">Definir o <xref:System.Windows.Navigation.NavigationWindow.Source%2A> propriedade o <xref:System.Windows.Navigation.NavigationWindow> para "ExpenseItHome.xaml".</span><span class="sxs-lookup"><span data-stu-id="93b82-162">Set the <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property on the <xref:System.Windows.Navigation.NavigationWindow> to "ExpenseItHome.xaml".</span></span> 
  
     <span data-ttu-id="93b82-163">Isso define ExpenseItHome.xaml para ser a primeira página aberta quando o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="93b82-163">This sets ExpenseItHome.xaml to be the first page opened when the application starts.</span></span> <span data-ttu-id="93b82-164">O [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] deve se parecer com no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="93b82-164">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]  
  
     <span data-ttu-id="93b82-165">Ou em C#:</span><span class="sxs-lookup"><span data-stu-id="93b82-165">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]  
  
6. <span data-ttu-id="93b82-166">Adicione uma nova página (WPF) ao projeto nomeado `ExpenseReportPage.xaml`.</span><span class="sxs-lookup"><span data-stu-id="93b82-166">Add a new Page (WPF) to the project named `ExpenseReportPage.xaml`.</span></span> 
  
     <span data-ttu-id="93b82-167">Esta página mostrará o relatório de despesas para a pessoa que está selecionada no ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="93b82-167">This page will show the expense report for the person that is selected on ExpenseItHome.xaml.</span></span> 
  
7. <span data-ttu-id="93b82-168">Abra ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="93b82-168">Open ExpenseReportPage.xaml.</span></span> 
  
8. <span data-ttu-id="93b82-169">Definir o <xref:System.Windows.Controls.Page.Title%2A> para "ExpenseIt - despesas de exibição".</span><span class="sxs-lookup"><span data-stu-id="93b82-169">Set the <xref:System.Windows.Controls.Page.Title%2A> to "ExpenseIt - View Expense".</span></span> 
  
     <span data-ttu-id="93b82-170">O [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] deve se parecer com no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="93b82-170">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]  
  
     <span data-ttu-id="93b82-171">Ou em C#:</span><span class="sxs-lookup"><span data-stu-id="93b82-171">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]  
  
9. <span data-ttu-id="93b82-172">Abra ExpenseItHome.xaml.vb e ExpenseReportPage.xaml.vb ou ExpenseItHome.xaml.cs e ExpenseReportPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="93b82-172">Open ExpenseItHome.xaml.vb and ExpenseReportPage.xaml.vb, or ExpenseItHome.xaml.cs and ExpenseReportPage.xaml.cs.</span></span> 
  
     <span data-ttu-id="93b82-173">Quando você cria um novo arquivo de paginação, o Visual Studio cria automaticamente um arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="93b82-173">When you create a new Page file, Visual Studio automatically creates a code behind file.</span></span> <span data-ttu-id="93b82-174">Esses arquivos code-behind manipulam a lógica para responder à entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="93b82-174">These code-behind files handle the logic for responding to user input.</span></span> 
  
     <span data-ttu-id="93b82-175">Seu código deve ter esta aparência.</span><span class="sxs-lookup"><span data-stu-id="93b82-175">Your code should look like this.</span></span> 
  
    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]  
  
    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]  
  
10. <span data-ttu-id="93b82-176">Adicione uma imagem chamada watermark.png ao projeto.</span><span class="sxs-lookup"><span data-stu-id="93b82-176">Add an image named watermark.png to the project.</span></span> <span data-ttu-id="93b82-177">Você pode criar sua própria imagem ou copiar o arquivo do código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="93b82-177">You can either create your own image, or copy the file from the sample code.</span></span> <span data-ttu-id="93b82-178">Para obter mais informações, consulte [NIB: como adicionar itens existentes a um projeto](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span><span class="sxs-lookup"><span data-stu-id="93b82-178">For more information, see [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span> 

## <a name="building-and-running-the-application"></a><span data-ttu-id="93b82-179">Criar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="93b82-179">Building and running the application</span></span>  
 <span data-ttu-id="93b82-180">Nesta seção, você vai compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93b82-180">In this section, you build and run the application.</span></span> 
  
1. <span data-ttu-id="93b82-181">Compilar e executar o aplicativo pressionando F5 ou selecione **iniciar depuração** do **depurar** menu.</span><span class="sxs-lookup"><span data-stu-id="93b82-181">Build and run the application by pressing F5 or select **Start Debugging** from the **Debug** menu.</span></span> 
  
     <span data-ttu-id="93b82-182">A ilustração a seguir mostra o aplicativo com o <xref:System.Windows.Navigation.NavigationWindow> botões.</span><span class="sxs-lookup"><span data-stu-id="93b82-182">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons.</span></span> 
  
     <span data-ttu-id="93b82-183">![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")</span><span class="sxs-lookup"><span data-stu-id="93b82-183">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")</span></span>  
  
2. <span data-ttu-id="93b82-184">Feche o aplicativo para retornar ao [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="93b82-184">Close the application to return to [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span> 
  
## <a name="creating-the-layout"></a><span data-ttu-id="93b82-185">Criando o layout</span><span class="sxs-lookup"><span data-stu-id="93b82-185">Creating the layout</span></span>  
 <span data-ttu-id="93b82-186">Layout oferece uma maneira ordenada para colocar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos e também gerencia o tamanho e a posição desses elementos quando um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] é redimensionado.</span><span class="sxs-lookup"><span data-stu-id="93b82-186">Layout provides an ordered way to place [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements, and also manages the size and position of those elements when a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is resized.</span></span> <span data-ttu-id="93b82-187">Normalmente, você cria um layout com um dos seguintes controles de layout:</span><span class="sxs-lookup"><span data-stu-id="93b82-187">You typically create a layout with one of the following layout controls:</span></span>  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 <span data-ttu-id="93b82-188">Cada um desses controles de layout dá suporte a um tipo especial de layout para seus elementos filhos.</span><span class="sxs-lookup"><span data-stu-id="93b82-188">Each of these layout controls supports a special type of layout for its child elements.</span></span> <span data-ttu-id="93b82-189">As páginas ExpenseIt podem ser redimensionadas e cada página tem elementos que são organizados horizontalmente e verticalmente juntamente com outros elementos.</span><span class="sxs-lookup"><span data-stu-id="93b82-189">ExpenseIt pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="93b82-190">Consequentemente, o <xref:System.Windows.Controls.Grid> é o elemento de layout ideal para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93b82-190">Consequently, the <xref:System.Windows.Controls.Grid> is the ideal layout element for the application.</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="93b82-191">Para obter mais informações sobre <xref:System.Windows.Controls.Panel> elementos, consulte [visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="93b82-191">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels Overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span> <span data-ttu-id="93b82-192">Para obter mais informações sobre o layout, consulte [Layout](../../../../docs/framework/wpf/advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="93b82-192">For more information about layout, see [Layout](../../../../docs/framework/wpf/advanced/layout.md).</span></span> 
  
 <span data-ttu-id="93b82-193">Na seção, você criar uma tabela de coluna única com três linhas e uma margem de 10 pixels adicionando definições de coluna e linha para o <xref:System.Windows.Controls.Grid> em ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="93b82-193">In the section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in ExpenseItHome.xaml.</span></span> 
  
1. <span data-ttu-id="93b82-194">Abra ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="93b82-194">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="93b82-195">Definir o <xref:System.Windows.FrameworkElement.Margin%2A> propriedade o <xref:System.Windows.Controls.Grid> elemento para "10,0,10,10", que corresponde às margens esquerda, superior, direita e inferior.</span><span class="sxs-lookup"><span data-stu-id="93b82-195">Set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10" which corresponds to left, top, right and bottom margins.</span></span> 
  
3. <span data-ttu-id="93b82-196">Adicione o seguinte [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] entre o <xref:System.Windows.Controls.Grid> marcas para criar as definições de linha e coluna.</span><span class="sxs-lookup"><span data-stu-id="93b82-196">Add the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions.</span></span> 
  
    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]  
  
     <span data-ttu-id="93b82-197">O <xref:System.Windows.Controls.RowDefinition.Height%2A> de duas linhas é definido como <xref:System.Windows.GridLength.Auto%2A> que significa que as linhas serão dimensionadas de base no conteúdo de linhas.</span><span class="sxs-lookup"><span data-stu-id="93b82-197">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A> which means that the rows will be sized base on the content in the rows.</span></span> <span data-ttu-id="93b82-198">O padrão <xref:System.Windows.Controls.RowDefinition.Height%2A> é <xref:System.Windows.GridUnitType.Star> dimensionamento, o que significa que a linha será uma proporção ponderada do espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="93b82-198">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row will be a weighted proportion of the available space.</span></span> <span data-ttu-id="93b82-199">Por exemplo, se duas linhas tiverem cada uma a altura de "*", eles terão uma altura que será a metade do espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="93b82-199">For example if two rows each have a height of "*", they will each have a height that is half of the available space.</span></span>  
  
     <span data-ttu-id="93b82-200">Seu <xref:System.Windows.Controls.Grid> agora deve se parecer com o XAML a seguir:</span><span class="sxs-lookup"><span data-stu-id="93b82-200">Your <xref:System.Windows.Controls.Grid> should now look like the following XAML:</span></span>  
  
    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]  
  
## <a name="adding-controls"></a><span data-ttu-id="93b82-201">Adicionando controles</span><span class="sxs-lookup"><span data-stu-id="93b82-201">Adding controls</span></span>  
 <span data-ttu-id="93b82-202">Nesta seção, a home page [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] é atualizada para mostrar uma lista de pessoas que os usuários podem selecionar para mostrar o relatório de despesas para uma pessoa.</span><span class="sxs-lookup"><span data-stu-id="93b82-202">In this section, the home page [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is updated to show a list of people that users can select from to show the expense report for a selected person.</span></span> <span data-ttu-id="93b82-203">Os controles são objetos da interface do usuário que permitem aos usuários interagir com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93b82-203">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="93b82-204">Para obter mais informações, consulte [Controles](../../../../docs/framework/wpf/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="93b82-204">For more information, see [Controls](../../../../docs/framework/wpf/controls/index.md).</span></span> 
  
 <span data-ttu-id="93b82-205">Para criar esse [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], os seguintes elementos são adicionados ao ExpenseItHome.xaml:</span><span class="sxs-lookup"><span data-stu-id="93b82-205">To create this [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], the following elements are added to ExpenseItHome.xaml:</span></span>  
  
-   <span data-ttu-id="93b82-206"><xref:System.Windows.Controls.ListBox>(para obter a lista de pessoas).</span><span class="sxs-lookup"><span data-stu-id="93b82-206"><xref:System.Windows.Controls.ListBox> (for the list of people).</span></span> 
  
-   <span data-ttu-id="93b82-207"><xref:System.Windows.Controls.Label>(para o cabeçalho de lista).</span><span class="sxs-lookup"><span data-stu-id="93b82-207"><xref:System.Windows.Controls.Label> (for the list header).</span></span> 
  
-   <span data-ttu-id="93b82-208"><xref:System.Windows.Controls.Button>(para clicar para exibir o relatório de despesas para a pessoa que está selecionada na lista).</span><span class="sxs-lookup"><span data-stu-id="93b82-208"><xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span> 
  
 <span data-ttu-id="93b82-209">Cada controle é colocado em uma linha do <xref:System.Windows.Controls.Grid> definindo o <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> propriedade anexada.</span><span class="sxs-lookup"><span data-stu-id="93b82-209">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="93b82-210">Para obter mais informações sobre propriedades anexadas, consulte [visão geral de propriedades anexado](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="93b82-210">For more information about attached properties, see [Attached Properties Overview](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span></span> 
  
1. <span data-ttu-id="93b82-211">Abra ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="93b82-211">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="93b82-212">Adicione o seguinte [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] entre o <xref:System.Windows.Controls.Grid> marcas.</span><span class="sxs-lookup"><span data-stu-id="93b82-212">Add the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] between the <xref:System.Windows.Controls.Grid> tags.</span></span> 
  
    [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]  
  
3. <span data-ttu-id="93b82-213">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93b82-213">Build and run the application.</span></span> 
  
 <span data-ttu-id="93b82-214">A ilustração a seguir mostra os controles que são criados pelo XAML nesta seção.</span><span class="sxs-lookup"><span data-stu-id="93b82-214">The following illustration shows the controls that are created by the XAML in this section.</span></span> 
  
 <span data-ttu-id="93b82-215">![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")</span><span class="sxs-lookup"><span data-stu-id="93b82-215">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")</span></span>  
  
## <a name="adding-an-image-and-a-title"></a><span data-ttu-id="93b82-216">Adicionar um título e uma imagem</span><span class="sxs-lookup"><span data-stu-id="93b82-216">Adding an image and a title</span></span>  
 <span data-ttu-id="93b82-217">Nesta seção, a home page [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] é atualizada com uma imagem e título da página.</span><span class="sxs-lookup"><span data-stu-id="93b82-217">In this section, the home page [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is updated with an image and a page title.</span></span> 
  
1. <span data-ttu-id="93b82-218">Abra ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="93b82-218">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="93b82-219">Adicione outra coluna para o <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> fixa <xref:System.Windows.Controls.ColumnDefinition.Width%2A> de 230 pixels.</span><span class="sxs-lookup"><span data-stu-id="93b82-219">Add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels.</span></span> 
  
    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]  
  
3. <span data-ttu-id="93b82-220">Adicionar outra linha para o <xref:System.Windows.Controls.Grid.RowDefinitions%2A>.</span><span class="sxs-lookup"><span data-stu-id="93b82-220">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>.</span></span> 
  
    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]  
  
4. <span data-ttu-id="93b82-221">Mover os controles para a segunda coluna, definindo <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> como 1.</span><span class="sxs-lookup"><span data-stu-id="93b82-221">Move the controls to the second column by setting <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> to 1.</span></span> <span data-ttu-id="93b82-222">Mover cada controle para baixo de uma linha, aumentando a <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> em 1.</span><span class="sxs-lookup"><span data-stu-id="93b82-222">Move each control down a row, by increasing the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> by 1.</span></span> 
  
    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]  
  
5. <span data-ttu-id="93b82-223">Definir o <xref:System.Windows.Controls.Panel.Background%2A> do <xref:System.Windows.Controls.Grid> para ser o arquivo de imagem watermark.</span><span class="sxs-lookup"><span data-stu-id="93b82-223">Set the <xref:System.Windows.Controls.Panel.Background%2A> of the <xref:System.Windows.Controls.Grid> to be the watermark.png image file.</span></span> 
  
    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]  
  
6. <span data-ttu-id="93b82-224">Antes do <xref:System.Windows.Controls.Border>, adicionar um <xref:System.Windows.Controls.Label> com o conteúdo "Exibir relatório de despesas" para ser o título da página.</span><span class="sxs-lookup"><span data-stu-id="93b82-224">Before the <xref:System.Windows.Controls.Border>, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report" to be the title of the page.</span></span> 
  
    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]  
  
7. <span data-ttu-id="93b82-225">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93b82-225">Build and run the application.</span></span> 
  
 <span data-ttu-id="93b82-226">A ilustração a seguir mostra os resultados desta seção.</span><span class="sxs-lookup"><span data-stu-id="93b82-226">The following illustration shows the results of this section.</span></span> 
  
 <span data-ttu-id="93b82-227">![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")</span><span class="sxs-lookup"><span data-stu-id="93b82-227">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")</span></span>  
  
## <a name="adding-code-to-handle-events"></a><span data-ttu-id="93b82-228">Adicionando código para tratar eventos</span><span class="sxs-lookup"><span data-stu-id="93b82-228">Adding code to handle events</span></span>  
  
1. <span data-ttu-id="93b82-229">Abra ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="93b82-229">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="93b82-230">Adicionar um <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos para o <xref:System.Windows.Controls.Button> elemento.</span><span class="sxs-lookup"><span data-stu-id="93b82-230">Add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="93b82-231">Para obter mais informações, consulte [Como Criar um Manipulador de Eventos Simples](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480).</span><span class="sxs-lookup"><span data-stu-id="93b82-231">For more information, see [How to: Create a Simple Event Handler](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480).</span></span> 
  
    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]  
  
3. <span data-ttu-id="93b82-232">Abra ExpenseItHome.xaml.vb ou ExpenseItHome.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="93b82-232">Open ExpenseItHome.xaml.vb or ExpenseItHome.xaml.cs.</span></span> 
  
4. <span data-ttu-id="93b82-233">Adicione o seguinte código para o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos, que faz com que a janela navegar até o arquivo ExpenseReportPage.</span><span class="sxs-lookup"><span data-stu-id="93b82-233">Add the following code to the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler, which causes the window to navigate to the ExpenseReportPage.xaml file.</span></span> 
  
    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]  
  
## <a name="creating-the-ui-for-expensereportpage"></a><span data-ttu-id="93b82-234">Criando a interface do usuário para ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="93b82-234">Creating the UI for ExpenseReportPage</span></span>  
 <span data-ttu-id="93b82-235">ExpenseReportPage.xaml exibe o relatório de despesas para a pessoa que foi selecionada no ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="93b82-235">ExpenseReportPage.xaml displays the expense report for the person that was selected on the ExpenseItHome.xaml.</span></span> <span data-ttu-id="93b82-236">Esta seção adiciona controles e cria o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] para ExpenseReportPage.</span><span class="sxs-lookup"><span data-stu-id="93b82-236">This section adds controls and creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] for ExpenseReportPage.xaml.</span></span> <span data-ttu-id="93b82-237">Esta seção também adiciona cores de plano de fundo e preenchimento para os vários [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos.</span><span class="sxs-lookup"><span data-stu-id="93b82-237">This section also adds background and fill colors to the various [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements.</span></span> 
  
1. <span data-ttu-id="93b82-238">Abra ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="93b82-238">Open ExpenseReportPage.xaml.</span></span> 
  
2. <span data-ttu-id="93b82-239">Adicionar o XAML a seguir entre a <xref:System.Windows.Controls.Grid> marcas.</span><span class="sxs-lookup"><span data-stu-id="93b82-239">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags.</span></span> 
  
     <span data-ttu-id="93b82-240">Essa interface do usuário é semelhante para a interface do usuário criado em ExpenseItHome.xaml, exceto os dados de relatório são exibidos em um <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="93b82-240">This UI is similar to the UI created on ExpenseItHome.xaml except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span> 
  
    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]  
  
3. <span data-ttu-id="93b82-241">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93b82-241">Build and run the application.</span></span> 
  
    > [!NOTE]
    >  <span data-ttu-id="93b82-242">Se você receber um erro que o <xref:System.Windows.Controls.DataGrid> não foi encontrado ou não existir, certifique-se de que seu projeto direcionado ao .NET Framework 4 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="93b82-242">If you get an error that the <xref:System.Windows.Controls.DataGrid> was not found or does not exist, make sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="93b82-243">Para obter mais informações, consulte [Como definir uma versão do .NET Framework como destino](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="93b82-243">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span> 
  
4. <span data-ttu-id="93b82-244">Clique o **exibição** botão.</span><span class="sxs-lookup"><span data-stu-id="93b82-244">Click the **View** button.</span></span> 
  
     <span data-ttu-id="93b82-245">A página de relatório de despesas é exibida.</span><span class="sxs-lookup"><span data-stu-id="93b82-245">The expense report page appears.</span></span> 
  
 <span data-ttu-id="93b82-246">A ilustração a seguir mostra o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos adicionados a ExpenseReportPage.</span><span class="sxs-lookup"><span data-stu-id="93b82-246">The following illustration shows the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements added to ExpenseReportPage.xaml.</span></span> <span data-ttu-id="93b82-247">Observe que o botão de navegação regressiva está habilitado.</span><span class="sxs-lookup"><span data-stu-id="93b82-247">Notice that the back navigation button is enabled.</span></span> 
  
 <span data-ttu-id="93b82-248">![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")</span><span class="sxs-lookup"><span data-stu-id="93b82-248">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")</span></span>  
  
## <a name="styling-controls"></a><span data-ttu-id="93b82-249">Controles de estilo</span><span class="sxs-lookup"><span data-stu-id="93b82-249">Styling controls</span></span>  
 <span data-ttu-id="93b82-250">A aparência de vários elementos geralmente pode ser o mesmo para todos os elementos do mesmo tipo em um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="93b82-250">The appearance of various elements can often be the same for all elements of the same type in a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> <span data-ttu-id="93b82-251">A [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] usa estilos para fazer com que as aparências sejam reutilizáveis entre vários elementos.</span><span class="sxs-lookup"><span data-stu-id="93b82-251">[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] uses styles to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="93b82-252">A capacidade de reutilização dos estilos ajuda a simplificar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] criação e gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="93b82-252">The reusability of styles helps to simplify [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] creation and management.</span></span> <span data-ttu-id="93b82-253">Para obter mais informações sobre estilos, consulte [estilos e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="93b82-253">For more information about styles, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span> <span data-ttu-id="93b82-254">Esta seção substitui os atributos por elemento que foram definidos nas etapas anteriores com estilos.</span><span class="sxs-lookup"><span data-stu-id="93b82-254">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span> 
  
1. <span data-ttu-id="93b82-255">Abra Application.xaml ou App.xaml.</span><span class="sxs-lookup"><span data-stu-id="93b82-255">Open Application.xaml or App.xaml.</span></span> 
  
2. <span data-ttu-id="93b82-256">Adicionar o XAML a seguir entre a <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> marcas:</span><span class="sxs-lookup"><span data-stu-id="93b82-256">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>  
  
    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]  
  
     <span data-ttu-id="93b82-257">Isso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] adiciona os seguintes estilos:</span><span class="sxs-lookup"><span data-stu-id="93b82-257">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] adds the following styles:</span></span>  
  
    -  <span data-ttu-id="93b82-258">`headerTextStyle`: para formatar o título da página <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="93b82-258">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span> 
  
    -  <span data-ttu-id="93b82-259">`labelStyle`: para formatar os controles <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="93b82-259">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span> 
  
    -  <span data-ttu-id="93b82-260">`columnHeaderStyle`: para formatar o <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="93b82-260">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span> 
  
    -  <span data-ttu-id="93b82-261">`listHeaderStyle`: para formatar os controles <xref:System.Windows.Controls.Border> do cabeçalho da lista.</span><span class="sxs-lookup"><span data-stu-id="93b82-261">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span> 
  
    -  <span data-ttu-id="93b82-262">`listHeaderTextStyle`: Para formatar o cabeçalho da lista <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="93b82-262">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span> 
  
    -  <span data-ttu-id="93b82-263">`buttonStyle`: Para formatar o <xref:System.Windows.Controls.Button> em ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="93b82-263">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on ExpenseItHome.xaml.</span></span> 
  
     <span data-ttu-id="93b82-264">Observe que os estilos são recursos e seus filhos a <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> elemento property.</span><span class="sxs-lookup"><span data-stu-id="93b82-264">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="93b82-265">Nesse local, os estilos são aplicados a todos os elementos em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93b82-265">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="93b82-266">Para obter um exemplo de uso de recursos em um [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] aplicativo, consulte [usar recursos de aplicativo](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="93b82-266">For an example of using resources in a [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application, see [Use Application Resources](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span></span> 
  
3. <span data-ttu-id="93b82-267">Abra ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="93b82-267">Open ExpenseItHome.xaml.</span></span> 
  
4. <span data-ttu-id="93b82-268">Substituir tudo entre os <xref:System.Windows.Controls.Grid> elementos com o XAML a seguir.</span><span class="sxs-lookup"><span data-stu-id="93b82-268">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]  
  
     <span data-ttu-id="93b82-269">As propriedades como <xref:System.Windows.VerticalAlignment> e <xref:System.Windows.Media.FontFamily> que definem a aparência de cada controle são removidas e substituídas ao aplicar os estilos.</span><span class="sxs-lookup"><span data-stu-id="93b82-269">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="93b82-270">Por exemplo, o `headerTextStyle` é aplicado a "Exibir relatório de despesas" <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="93b82-270">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span> 
  
5. <span data-ttu-id="93b82-271">Abra ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="93b82-271">Open ExpenseReportPage.xaml.</span></span> 
  
6. <span data-ttu-id="93b82-272">Substituir tudo entre os <xref:System.Windows.Controls.Grid> elementos com o XAML a seguir.</span><span class="sxs-lookup"><span data-stu-id="93b82-272">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]  
  
     <span data-ttu-id="93b82-273">Isso adiciona estilos aos elementos <xref:System.Windows.Controls.Label> e <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="93b82-273">This adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span> 
  
7. <span data-ttu-id="93b82-274">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93b82-274">Build and run the application.</span></span> 
  
     <span data-ttu-id="93b82-275">Depois de adicionar o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nesta seção, o aplicativo tem a mesma aparência que tinha antes de ser atualizado com estilos.</span><span class="sxs-lookup"><span data-stu-id="93b82-275">After adding the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] in this section, the application looks the same as it did before being updated with styles.</span></span> 
  
## <a name="binding-data-to-a-control"></a><span data-ttu-id="93b82-276">Associando dados a um controle</span><span class="sxs-lookup"><span data-stu-id="93b82-276">Binding data to a control</span></span>  
 <span data-ttu-id="93b82-277">Nesta seção, você cria o [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] dados que estão associados a vários controles.</span><span class="sxs-lookup"><span data-stu-id="93b82-277">In this section, you create the [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] data that is bound to various controls.</span></span> 
  
1. <span data-ttu-id="93b82-278">Abra ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="93b82-278">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="93b82-279">Após a abertura <xref:System.Windows.Controls.Grid> elemento, adicionar o XAML a seguir para criar um <xref:System.Windows.Data.XmlDataProvider> que contém os dados de cada pessoa.</span><span class="sxs-lookup"><span data-stu-id="93b82-279">After the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person.</span></span> 
  
     <span data-ttu-id="93b82-280">Os dados são criados como um <xref:System.Windows.Controls.Grid> recursos.</span><span class="sxs-lookup"><span data-stu-id="93b82-280">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="93b82-281">Normalmente, isso seria carregado como um arquivo, mas para simplificar, os dados são adicionados embutidos.</span><span class="sxs-lookup"><span data-stu-id="93b82-281">Normally this would be loaded as a file, but for simplicity the data is added inline.</span></span> 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
3. <span data-ttu-id="93b82-282">No <xref:System.Windows.Controls.Grid> recursos, adicione o seguinte <xref:System.Windows.DataTemplate>, que define como exibir os dados de <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="93b82-282">In the <xref:System.Windows.Controls.Grid> resource, add the following <xref:System.Windows.DataTemplate>, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="93b82-283">Para obter mais informações sobre modelos de dados, consulte [Visão geral de modelagem de dados](../../../../docs/framework/wpf/data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="93b82-283">For more information about data templates, see [Data Templating Overview](../../../../docs/framework/wpf/data/data-templating-overview.md).</span></span> 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
4. <span data-ttu-id="93b82-284">Substituir o <xref:System.Windows.Controls.ListBox> com o XAML a seguir.</span><span class="sxs-lookup"><span data-stu-id="93b82-284">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]  
  
     <span data-ttu-id="93b82-285">Este XAML associa o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade o <xref:System.Windows.Controls.ListBox> à fonte de dados e aplica o modelo de dados como o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="93b82-285">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span> 
  
## <a name="connecting-data-to-controls"></a><span data-ttu-id="93b82-286">Conectando a dados a controles</span><span class="sxs-lookup"><span data-stu-id="93b82-286">Connecting data to controls</span></span>  
 <span data-ttu-id="93b82-287">Nesta seção, você escreve o código que recupera o item atual que está selecionado na lista de pessoas na página ExpenseItHome.xaml e passa sua referência para o construtor de `ExpenseReportPage` durante a instanciação.</span><span class="sxs-lookup"><span data-stu-id="93b82-287">In this section, you write the code that retrieves the current item that is selected in the list of people on the ExpenseItHome.xaml page, and passes its reference to the constructor of `ExpenseReportPage` during instantiation.</span></span> <span data-ttu-id="93b82-288">`ExpenseReportPage` define seu contexto de dados com o item passado, ao qual os controles definidos em ExpenseReportPage.xaml serão associados.</span><span class="sxs-lookup"><span data-stu-id="93b82-288">`ExpenseReportPage` sets its data context with the passed item, which is what the controls defined in ExpenseReportPage.xaml will bind to.</span></span> 
  
1. <span data-ttu-id="93b82-289">Abra ExpenseReportPage.xaml.vb ou ExpenseReportPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="93b82-289">Open ExpenseReportPage.xaml.vb or ExpenseReportPage.xaml.cs.</span></span> 
  
2. <span data-ttu-id="93b82-290">Adicione um construtor que utiliza um objeto para passar os dados do relatório de despesas da pessoa selecionada.</span><span class="sxs-lookup"><span data-stu-id="93b82-290">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span> 
  
    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]  
  
3. <span data-ttu-id="93b82-291">Abra ExpenseItHome.xaml.vb ou ExpenseItHome.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="93b82-291">Open ExpenseItHome.xaml.vb or ExpenseItHome.xaml.cs.</span></span> 
  
4. <span data-ttu-id="93b82-292">Alterar o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos para chamar o novo construtor passar os dados de relatório de despesas da pessoa que está selecionado.</span><span class="sxs-lookup"><span data-stu-id="93b82-292">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span> 
  
    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]  
  
## <a name="styling-data-with-data-templates"></a><span data-ttu-id="93b82-293">Dados de estilo com modelos de dados</span><span class="sxs-lookup"><span data-stu-id="93b82-293">Styling data with data templates</span></span>  
 <span data-ttu-id="93b82-294">Nesta seção, você deve atualizar o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] para cada item de dados associado ao listas usando modelos de dados.</span><span class="sxs-lookup"><span data-stu-id="93b82-294">In this section, you update the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] for each item in the data bound lists by using data templates.</span></span> 
  
1. <span data-ttu-id="93b82-295">Abra ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="93b82-295">Open ExpenseReportPage.xaml.</span></span> 
  
2. <span data-ttu-id="93b82-296">Associar o conteúdo do "Nome" e "Departamento" <xref:System.Windows.Controls.Label> a propriedade de fonte de elementos para os dados apropriados.</span><span class="sxs-lookup"><span data-stu-id="93b82-296">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="93b82-297">Para obter mais informações sobre vinculação de dados, veja [Noções básicas de vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="93b82-297">For more information about data binding, see [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span> 
  
    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]  
  
3. <span data-ttu-id="93b82-298">Após a abertura <xref:System.Windows.Controls.Grid> elemento, adicione os seguintes modelos de dados, que definem como exibir os dados de relatório de despesas.</span><span class="sxs-lookup"><span data-stu-id="93b82-298">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data.</span></span>  
    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]  
  
4. <span data-ttu-id="93b82-299">Aplicar os modelos para o <xref:System.Windows.Controls.DataGrid> colunas que exibem a despesa de dados de relatório.</span><span class="sxs-lookup"><span data-stu-id="93b82-299">Apply the templates to the <xref:System.Windows.Controls.DataGrid> columns that display the expense report data.</span></span> 
  
    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]  
  
5. <span data-ttu-id="93b82-300">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93b82-300">Build and run the application.</span></span> 
  
6. <span data-ttu-id="93b82-301">Selecione uma pessoa e clique no **exibição** botão.</span><span class="sxs-lookup"><span data-stu-id="93b82-301">Select a person and click the **View** button.</span></span> 
  
 <span data-ttu-id="93b82-302">A ilustração a seguir mostra as duas páginas do aplicativo ExpenseIt com controles, layout, estilos, vinculação de dados e modelos de dados aplicados.</span><span class="sxs-lookup"><span data-stu-id="93b82-302">The following illustration shows both pages of the ExpenseIt application with controls, layout, styles, data binding, and data templates applied.</span></span> 
  
 <span data-ttu-id="93b82-303">![Capturas de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")</span><span class="sxs-lookup"><span data-stu-id="93b82-303">![ExpenseIt sample screen shots](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="93b82-304">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="93b82-304">Best practices</span></span>  
 <span data-ttu-id="93b82-305">Este exemplo demonstra um recurso específico do WPF e, consequentemente, não segue as práticas recomendadas de desenvolvimento de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="93b82-305">This sample demonstrates a specific feature of WPF and, consequently, does not follow application development best practices.</span></span> <span data-ttu-id="93b82-306">Para uma cobertura abrangente do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] práticas recomendadas de desenvolvimento de aplicativo, consulte os tópicos a seguir, conforme apropriado:</span><span class="sxs-lookup"><span data-stu-id="93b82-306">For comprehensive coverage of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] and the [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application development best practices, see the following topics as appropriate:</span></span>  
  
-   <span data-ttu-id="93b82-307">Acessibilidade – [Práticas recomendadas de acessibilidade](../../../../docs/framework/ui-automation/accessibility-best-practices.md)</span><span class="sxs-lookup"><span data-stu-id="93b82-307">Accessibility - [Accessibility Best Practices](../../../../docs/framework/ui-automation/accessibility-best-practices.md)</span></span>  
  
-   <span data-ttu-id="93b82-308">Segurança - [segurança](../../../../docs/framework/wpf/security-wpf.md)</span><span class="sxs-lookup"><span data-stu-id="93b82-308">Security - [Security](../../../../docs/framework/wpf/security-wpf.md)</span></span>  
  
-   <span data-ttu-id="93b82-309">Localização – [Visão geral de globalização e localização do WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)</span><span class="sxs-lookup"><span data-stu-id="93b82-309">Localization - [WPF Globalization and Localization Overview](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)</span></span>  
  
-   <span data-ttu-id="93b82-310">Desempenho – [Otimizando o desempenho do aplicativo WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)</span><span class="sxs-lookup"><span data-stu-id="93b82-310">Performance - [Optimizing WPF Application Performance](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)</span></span>  
  
## <a name="whats-next"></a><span data-ttu-id="93b82-311">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="93b82-311">What's next</span></span>  
 <span data-ttu-id="93b82-312">Agora você tem um número de técnicas à sua disposição para criar uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] usando [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="93b82-312">You now have a number of techniques at your disposal for creating a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] using [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span> <span data-ttu-id="93b82-313">Agora você deve ter uma compreensão ampla dos blocos de construção básicos de uma associação de dados [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93b82-313">You should now have a broad understanding of the basic building blocks of a data-bound [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application.</span></span> <span data-ttu-id="93b82-314">Este tópico não é exaustivo, mas dará a você uma noção de algumas das possibilidades que você pode descobrir por conta própria, além das técnicas do tópico.</span><span class="sxs-lookup"><span data-stu-id="93b82-314">This topic is by no means exhaustive, but hopefully you also now have a sense of some of the possibilities you might discover on your own beyond the techniques in this topic.</span></span> 
  
 <span data-ttu-id="93b82-315">Para obter mais informações sobre os modelos de arquitetura e programação do WPF, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="93b82-315">For more information about the WPF architecture and programming models, see the following topics:</span></span>  
  
-   [<span data-ttu-id="93b82-316">Arquitetura do WPF</span><span class="sxs-lookup"><span data-stu-id="93b82-316">WPF Architecture</span></span>](../../../../docs/framework/wpf/advanced/wpf-architecture.md)  
  
-   [<span data-ttu-id="93b82-317">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="93b82-317">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
  
-   [<span data-ttu-id="93b82-318">Visão geral das propriedades da dependência</span><span class="sxs-lookup"><span data-stu-id="93b82-318">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
  
-   [<span data-ttu-id="93b82-319">Layout</span><span class="sxs-lookup"><span data-stu-id="93b82-319">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)  
  
 <span data-ttu-id="93b82-320">Para obter mais informações sobre como criar aplicativos, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="93b82-320">For more information about creating applications, see the following topics:</span></span>  
  
-   [<span data-ttu-id="93b82-321">Desenvolvimento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="93b82-321">Application Development</span></span>](../../../../docs/framework/wpf/app-development/index.md)  
  
-   [<span data-ttu-id="93b82-322">Controles</span><span class="sxs-lookup"><span data-stu-id="93b82-322">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)  
  
-   [<span data-ttu-id="93b82-323">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="93b82-323">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
  
-   [<span data-ttu-id="93b82-324">Elementos gráficos e multimídia</span><span class="sxs-lookup"><span data-stu-id="93b82-324">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
  
-   [<span data-ttu-id="93b82-325">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="93b82-325">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
  
## <a name="see-also"></a><span data-ttu-id="93b82-326">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93b82-326">See also</span></span>  
 [<span data-ttu-id="93b82-327">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="93b82-327">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="93b82-328">Visão geral de modelagem dos dados</span><span class="sxs-lookup"><span data-stu-id="93b82-328">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="93b82-329">Compilar um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="93b82-329">Building a WPF Application</span></span>](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [<span data-ttu-id="93b82-330">Estilos e modelos</span><span class="sxs-lookup"><span data-stu-id="93b82-330">Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/styles-and-templates.md)
