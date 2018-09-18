---
title: Criar um aplicativo WPF no Visual Studio
ms.date: 04/12/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
author: mairaw
ms.author: mairaw
ms.custom: vs-dotnet
ms.openlocfilehash: 1a9c82a0bca25fa1242b29393e41e6eb4ce7f3b9
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46007250"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="00d3b-102">Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF</span><span class="sxs-lookup"><span data-stu-id="00d3b-102">Walkthrough: My first WPF desktop application</span></span>

<span data-ttu-id="00d3b-103">Este artigo mostra como desenvolver um aplicativo simples do Windows Presentation Foundation (WPF) que inclui os elementos que são comuns à maioria dos aplicativos do WPF: marcação de de Extensible Application Markup Language (XAML), código-behind, definições de aplicativo, controles, layout, vinculação de dados e estilos.</span><span class="sxs-lookup"><span data-stu-id="00d3b-103">This article shows you how to develop a simple Windows Presentation Foundation (WPF) application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span>

<span data-ttu-id="00d3b-104">Este passo a passo inclui as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="00d3b-104">This walkthrough includes the following steps:</span></span>

- <span data-ttu-id="00d3b-105">Use XAML para criar a aparência da interface do usuário do aplicativo (UI).</span><span class="sxs-lookup"><span data-stu-id="00d3b-105">Use XAML to design the appearance of the application's user interface (UI).</span></span>

- <span data-ttu-id="00d3b-106">Escreva código para criar o comportamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00d3b-106">Write code to build the application's behavior.</span></span>

- <span data-ttu-id="00d3b-107">Crie uma definição de aplicativo para gerenciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00d3b-107">Create an application definition to manage the application.</span></span>

- <span data-ttu-id="00d3b-108">Adicionar controles e criar o layout para compor o interface do usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00d3b-108">Add controls and create the layout to compose the application UI.</span></span>

- <span data-ttu-id="00d3b-109">Crie estilos para uma aparência consistente em toda a interface de usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00d3b-109">Create styles for a consistent appearance throughout an application's UI.</span></span>

- <span data-ttu-id="00d3b-110">Associe a interface do usuário a dados popular a IU de dados e manter os dados e a interface do usuário sincronizado.</span><span class="sxs-lookup"><span data-stu-id="00d3b-110">Bind the UI to data to both populate the UI from data and keep the data and UI synchronized.</span></span>

<span data-ttu-id="00d3b-111">Ao final do passo a passo, você será criado um aplicativo do Windows que permite aos usuários exibir relatórios de despesas para pessoas selecionadas autônomo.</span><span class="sxs-lookup"><span data-stu-id="00d3b-111">By the end of the walkthrough, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="00d3b-112">O aplicativo é composto de várias páginas do WPF que são hospedadas em uma janela de estilo de navegador.</span><span class="sxs-lookup"><span data-stu-id="00d3b-112">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="00d3b-113">O código de exemplo que é usado para criar este passo a passo está disponível para o Visual Basic e c# na [Introdução à criação de aplicativos WPF](https://go.microsoft.com/fwlink/?LinkID=160008).</span><span class="sxs-lookup"><span data-stu-id="00d3b-113">The sample code that is used to build this walkthrough is available for both Visual Basic and C# at [Introduction to Building WPF Applications](https://go.microsoft.com/fwlink/?LinkID=160008).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="00d3b-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="00d3b-114">Prerequisites</span></span>

- <span data-ttu-id="00d3b-115">Visual Studio 2012 ou posterior (Este artigo se baseia no Visual Studio 2017)</span><span class="sxs-lookup"><span data-stu-id="00d3b-115">Visual Studio 2012 or later (this article is based on Visual Studio 2017)</span></span>

   <span data-ttu-id="00d3b-116">Para obter mais informações sobre como instalar a versão mais recente do Visual Studio, consulte [instalar o Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="00d3b-116">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="00d3b-117">Criar o projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="00d3b-117">Create the application project</span></span>

<span data-ttu-id="00d3b-118">A primeira etapa é criar a infraestrutura de aplicativo, que inclui uma definição de aplicativo, duas páginas e uma imagem.</span><span class="sxs-lookup"><span data-stu-id="00d3b-118">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="00d3b-119">Criar um novo projeto de aplicativo do WPF no Visual Basic ou Visual c# denominado **`ExpenseIt`**:</span><span class="sxs-lookup"><span data-stu-id="00d3b-119">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="00d3b-120">Abra o Visual Studio e selecione **arquivo** > **New** > **projeto**.</span><span class="sxs-lookup"><span data-stu-id="00d3b-120">Open Visual Studio and select **File** > **New** > **Project**.</span></span>

      <span data-ttu-id="00d3b-121">O **novo projeto** caixa de diálogo é aberta.</span><span class="sxs-lookup"><span data-stu-id="00d3b-121">The **New Project** dialog opens.</span></span>

   2. <span data-ttu-id="00d3b-122">Sob o **instalados** categoria, expanda o **Visual c#** ou **Visual Basic** nó e, em seguida, selecione **área de trabalho clássica do Windows**.</span><span class="sxs-lookup"><span data-stu-id="00d3b-122">Under the **Installed** category, expand either the **Visual C#** or **Visual Basic** node, and then select **Windows Classic Desktop**.</span></span>

   3. <span data-ttu-id="00d3b-123">Selecione o **aplicativo WPF (.NET Framework)** modelo.</span><span class="sxs-lookup"><span data-stu-id="00d3b-123">Select the **WPF App (.NET Framework)** template.</span></span> <span data-ttu-id="00d3b-124">Insira o nome **`ExpenseIt`** e, em seguida, selecione **Okey**.</span><span class="sxs-lookup"><span data-stu-id="00d3b-124">Enter the name **`ExpenseIt`** and then select **OK**.</span></span>

      ![Caixa de diálogo Nova projeto com o aplicativo do WPF selecionado](media/new-project-dialog.png)

      <span data-ttu-id="00d3b-126">Visual Studio cria o projeto e abre o designer para a janela do aplicativo padrão chamado **MainWindow. XAML**.</span><span class="sxs-lookup"><span data-stu-id="00d3b-126">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="00d3b-127">Este passo a passo usa o <xref:System.Windows.Controls.DataGrid> controle que está disponível no .NET Framework 4 e posterior.</span><span class="sxs-lookup"><span data-stu-id="00d3b-127">This walkthrough uses the <xref:System.Windows.Controls.DataGrid> control that is available in the .NET Framework 4 and later.</span></span> <span data-ttu-id="00d3b-128">Ser-se de que seu projeto tem como alvo o .NET Framework 4 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="00d3b-128">Be sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="00d3b-129">Para obter mais informações, consulte [Como definir uma versão do .NET Framework como destino](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="00d3b-129">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>

2. <span data-ttu-id="00d3b-130">Abra *Application. XAML* (Visual Basic) ou *App. XAML* (c#).</span><span class="sxs-lookup"><span data-stu-id="00d3b-130">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="00d3b-131">Esse arquivo XAML define um aplicativo WPF e quaisquer recursos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00d3b-131">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="00d3b-132">Você também usar esse arquivo para especificar a interface do usuário que mostra automaticamente quando o aplicativo é iniciado; Nesse caso, *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-132">You also use this file to specify the UI that automatically shows when the application starts; in this case, *MainWindow.xaml*.</span></span>

    <span data-ttu-id="00d3b-133">O XAML deve ter esta aparência no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="00d3b-133">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="00d3b-134">Ou assim no C#:</span><span class="sxs-lookup"><span data-stu-id="00d3b-134">Or like this in C#:</span></span>

    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="00d3b-135">Abra *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-135">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="00d3b-136">Esse arquivo XAML é a janela principal do seu aplicativo e exibe o conteúdo criado em páginas.</span><span class="sxs-lookup"><span data-stu-id="00d3b-136">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="00d3b-137">O <xref:System.Windows.Window> classe define as propriedades de uma janela, como seu título, tamanho ou ícone e manipula eventos, como fechar ou ocultar.</span><span class="sxs-lookup"><span data-stu-id="00d3b-137">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="00d3b-138">Alterar o <xref:System.Windows.Window> elemento para um <xref:System.Windows.Navigation.NavigationWindow>, como mostra o XAML a seguir:</span><span class="sxs-lookup"><span data-stu-id="00d3b-138">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="00d3b-139">Este aplicativo navega para um conteúdo diferente dependendo da entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="00d3b-139">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="00d3b-140">É por isso que o principal <xref:System.Windows.Window> precisa ser alterado para um <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="00d3b-140">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="00d3b-141"><xref:System.Windows.Navigation.NavigationWindow> herda todas as propriedades de <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="00d3b-141"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="00d3b-142">O <xref:System.Windows.Navigation.NavigationWindow> elemento no arquivo XAML cria uma instância do <xref:System.Windows.Navigation.NavigationWindow> classe.</span><span class="sxs-lookup"><span data-stu-id="00d3b-142">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="00d3b-143">Para obter mais informações, consulte [visão geral da navegação](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="00d3b-143">For more information, see [Navigation overview](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="00d3b-144">Alterar as propriedades a seguir sobre o <xref:System.Windows.Navigation.NavigationWindow> elemento:</span><span class="sxs-lookup"><span data-stu-id="00d3b-144">Change the following properties on the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="00d3b-145">Defina as <xref:System.Windows.Window.Title%2A> propriedade para "`ExpenseIt`".</span><span class="sxs-lookup"><span data-stu-id="00d3b-145">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="00d3b-146">Defina o <xref:System.Windows.FrameworkElement.Width%2A> propriedade para 500 pixels.</span><span class="sxs-lookup"><span data-stu-id="00d3b-146">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    - <span data-ttu-id="00d3b-147">Defina o <xref:System.Windows.FrameworkElement.Height%2A> propriedade para 350 pixels.</span><span class="sxs-lookup"><span data-stu-id="00d3b-147">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="00d3b-148">Remover o <xref:System.Windows.Controls.Grid> elementos entre o <xref:System.Windows.Navigation.NavigationWindow> marcas.</span><span class="sxs-lookup"><span data-stu-id="00d3b-148">Remove the <xref:System.Windows.Controls.Grid> elements between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

    <span data-ttu-id="00d3b-149">O XAML deve ter esta aparência no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="00d3b-149">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="00d3b-150">Ou assim no C#:</span><span class="sxs-lookup"><span data-stu-id="00d3b-150">Or like this in C#:</span></span>

    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

6. <span data-ttu-id="00d3b-151">Abra *. XAML. vb* ou *MainWindow.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-151">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="00d3b-152">Esse arquivo é um arquivo code-behind que contém o código para manipular os eventos declarados em *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-152">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="00d3b-153">Esse arquivo contém uma classe parcial para a janela definida no XAML.</span><span class="sxs-lookup"><span data-stu-id="00d3b-153">This file contains a partial class for the window defined in XAML.</span></span>

7. <span data-ttu-id="00d3b-154">Se você estiver usando c#, altere o `MainWindow` classe para derivar de <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="00d3b-154">If you are using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="00d3b-155">(No Visual Basic, isso ocorre automaticamente quando você altera a janela no XAML.)</span><span class="sxs-lookup"><span data-stu-id="00d3b-155">(In Visual Basic, this happens automatically when you change the window in XAML.)</span></span>

   <span data-ttu-id="00d3b-156">Seu código deve ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="00d3b-156">Your code should look like this:</span></span>

   [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
   [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]

   > [!TIP]
   > <span data-ttu-id="00d3b-157">Você pode alternar o idioma de código do código de exemplo entre c# e Visual Basic na **linguagem** lista suspensa no canto superior direito deste artigo.</span><span class="sxs-lookup"><span data-stu-id="00d3b-157">You can toggle the code language of the sample code between C# and Visual Basic in the **Language** drop-down on the upper right side of this article.</span></span>

## <a name="add-files-to-the-application"></a><span data-ttu-id="00d3b-158">Adicionar arquivos ao aplicativo</span><span class="sxs-lookup"><span data-stu-id="00d3b-158">Add files to the application</span></span>

<span data-ttu-id="00d3b-159">Nesta seção, você adicionará duas páginas e uma imagem ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00d3b-159">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="00d3b-160">Adicione uma nova página do WPF ao projeto e denomine *`ExpenseItHome.xaml`*:</span><span class="sxs-lookup"><span data-stu-id="00d3b-160">Add a new WPF page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="00d3b-161">Na **Gerenciador de soluções**, clique com botão direito no **`ExpenseIt`** nó do projeto e escolha **Add** > **página**.</span><span class="sxs-lookup"><span data-stu-id="00d3b-161">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="00d3b-162">No **Adicionar Novo Item** caixa de diálogo, o **página (WPF)** modelo já está selecionado.</span><span class="sxs-lookup"><span data-stu-id="00d3b-162">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="00d3b-163">Insira o nome **`ExpenseItHome`** e, em seguida, selecione **Add**.</span><span class="sxs-lookup"><span data-stu-id="00d3b-163">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="00d3b-164">Esta página é a primeira página que é exibida quando o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="00d3b-164">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="00d3b-165">Ela mostrará uma lista de pessoas para selecionar, para mostrar um relatório de despesas.</span><span class="sxs-lookup"><span data-stu-id="00d3b-165">It will show a list of people to select from, to show an expense report for.</span></span>

2. <span data-ttu-id="00d3b-166">Abra *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-166">Open *`ExpenseItHome.xaml`*.</span></span>

3. <span data-ttu-id="00d3b-167">Defina as <xref:System.Windows.Controls.Page.Title%2A> para "`ExpenseIt - Home`".</span><span class="sxs-lookup"><span data-stu-id="00d3b-167">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

    <span data-ttu-id="00d3b-168">O XAML deve ter esta aparência no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="00d3b-168">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="00d3b-169">Ou em C#:</span><span class="sxs-lookup"><span data-stu-id="00d3b-169">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

4. <span data-ttu-id="00d3b-170">Abra *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-170">Open *MainWindow.xaml*.</span></span>

5. <span data-ttu-id="00d3b-171">Defina as <xref:System.Windows.Navigation.NavigationWindow.Source%2A> propriedade no <xref:System.Windows.Navigation.NavigationWindow> para "`ExpenseItHome.xaml`".</span><span class="sxs-lookup"><span data-stu-id="00d3b-171">Set the <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property on the <xref:System.Windows.Navigation.NavigationWindow> to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="00d3b-172">Isso define *`ExpenseItHome.xaml`* ser a primeira página aberta quando o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="00d3b-172">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span> <span data-ttu-id="00d3b-173">O XAML deve ter esta aparência no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="00d3b-173">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="00d3b-174">Ou em C#:</span><span class="sxs-lookup"><span data-stu-id="00d3b-174">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="00d3b-175">Você também pode definir a **fonte** propriedade no **diversos** categoria da **propriedades** janela.</span><span class="sxs-lookup"><span data-stu-id="00d3b-175">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Propriedade de origem na janela Propriedades](media/properties-source.png)

6. <span data-ttu-id="00d3b-177">Adicione outra nova página do WPF ao projeto e denomine *ExpenseReportPage*::</span><span class="sxs-lookup"><span data-stu-id="00d3b-177">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="00d3b-178">Na **Gerenciador de soluções**, clique com botão direito no **`ExpenseIt`** nó do projeto e escolha **Add** > **página**.</span><span class="sxs-lookup"><span data-stu-id="00d3b-178">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="00d3b-179">No **Adicionar Novo Item** caixa de diálogo, o **página (WPF)** modelo já está selecionado.</span><span class="sxs-lookup"><span data-stu-id="00d3b-179">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="00d3b-180">Insira o nome **ExpenseReportPage**e, em seguida, selecione **Add**.</span><span class="sxs-lookup"><span data-stu-id="00d3b-180">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="00d3b-181">Essa página mostrará o relatório de despesas da pessoa que está selecionada na **`ExpenseItHome`** página.</span><span class="sxs-lookup"><span data-stu-id="00d3b-181">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

7. <span data-ttu-id="00d3b-182">Abra *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-182">Open *ExpenseReportPage.xaml*.</span></span>

8. <span data-ttu-id="00d3b-183">Defina as <xref:System.Windows.Controls.Page.Title%2A> para "`ExpenseIt - View Expense`".</span><span class="sxs-lookup"><span data-stu-id="00d3b-183">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

    <span data-ttu-id="00d3b-184">O XAML deve ter esta aparência no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="00d3b-184">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="00d3b-185">Ou em C#:</span><span class="sxs-lookup"><span data-stu-id="00d3b-185">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

9. <span data-ttu-id="00d3b-186">Abra *Expenseithome* e *ExpenseReportPage*, ou *ExpenseItHome.xaml.cs* e *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-186">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="00d3b-187">Quando você cria um novo arquivo de página, o Visual Studio cria automaticamente um *de lógica* arquivo.</span><span class="sxs-lookup"><span data-stu-id="00d3b-187">When you create a new Page file, Visual Studio automatically creates a *code-behind* file.</span></span> <span data-ttu-id="00d3b-188">Esses arquivos code-behind manipulam a lógica para responder à entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="00d3b-188">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="00d3b-189">Seu código deve parecer com isso para **`ExpenseItHome`**:</span><span class="sxs-lookup"><span data-stu-id="00d3b-189">Your code should look like this for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="00d3b-190">E como este para **ExpenseReportPage**:</span><span class="sxs-lookup"><span data-stu-id="00d3b-190">And like this for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

10. <span data-ttu-id="00d3b-191">Adicione uma imagem chamada *watermark* ao projeto.</span><span class="sxs-lookup"><span data-stu-id="00d3b-191">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="00d3b-192">Você pode criar sua própria imagem, copie o arquivo de código de exemplo ou obtê-lo [aqui](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/media/watermark.png).</span><span class="sxs-lookup"><span data-stu-id="00d3b-192">You can create your own image, copy the file from the sample code, or get it [here](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/media/watermark.png).</span></span>

   1. <span data-ttu-id="00d3b-193">Clique com botão direito no nó do projeto e selecione **Add** > **Item existente**, ou pressione **Shift**+**Alt** + **Um**.</span><span class="sxs-lookup"><span data-stu-id="00d3b-193">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

   2. <span data-ttu-id="00d3b-194">No **Adicionar Item existente** caixa de diálogo, navegue até o arquivo de imagem que você deseja usar e, em seguida, selecione **Add**.</span><span class="sxs-lookup"><span data-stu-id="00d3b-194">In the **Add Existing Item** dialog, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="00d3b-195">Compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="00d3b-195">Build and run the application</span></span>

1. <span data-ttu-id="00d3b-196">Para compilar e executar o aplicativo, pressione **F5** ou selecione **iniciar depuração** do **depurar** menu.</span><span class="sxs-lookup"><span data-stu-id="00d3b-196">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="00d3b-197">A ilustração a seguir mostra o aplicativo com o <xref:System.Windows.Navigation.NavigationWindow> botões:</span><span class="sxs-lookup"><span data-stu-id="00d3b-197">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png)

2. <span data-ttu-id="00d3b-199">Feche o aplicativo para retornar ao Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="00d3b-199">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="00d3b-200">Criar o layout</span><span class="sxs-lookup"><span data-stu-id="00d3b-200">Create the layout</span></span>

<span data-ttu-id="00d3b-201">Layout oferece uma maneira ordenada para posicionar os elementos de interface do usuário e também gerencia o tamanho e a posição desses elementos quando uma interface do usuário é redimensionado.</span><span class="sxs-lookup"><span data-stu-id="00d3b-201">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="00d3b-202">Normalmente, você cria um layout com um dos seguintes controles de layout:</span><span class="sxs-lookup"><span data-stu-id="00d3b-202">You typically create a layout with one of the following layout controls:</span></span>

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.VirtualizingStackPanel>
- <xref:System.Windows.Controls.WrapPanel>

<span data-ttu-id="00d3b-203">Cada um desses controles de layout dá suporte a um tipo especial de layout para seus elementos filhos.</span><span class="sxs-lookup"><span data-stu-id="00d3b-203">Each of these layout controls supports a special type of layout for its child elements.</span></span> <span data-ttu-id="00d3b-204">`ExpenseIt` as páginas podem ser redimensionadas e cada página tem elementos que são organizados horizontalmente e verticalmente juntamente com outros elementos.</span><span class="sxs-lookup"><span data-stu-id="00d3b-204">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="00d3b-205">Consequentemente, o <xref:System.Windows.Controls.Grid> é o elemento de layout ideal para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00d3b-205">Consequently, the <xref:System.Windows.Controls.Grid> is the ideal layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="00d3b-206">Para obter mais informações sobre <xref:System.Windows.Controls.Panel> elementos, consulte [visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="00d3b-206">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span> <span data-ttu-id="00d3b-207">Para obter mais informações sobre layout, consulte [Layout](../../../../docs/framework/wpf/advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="00d3b-207">For more information about layout, see [Layout](../../../../docs/framework/wpf/advanced/layout.md).</span></span>

<span data-ttu-id="00d3b-208">Na seção, você criar uma tabela de coluna única com três linhas e uma margem de 10 pixels adicionando definições de linha e coluna para o <xref:System.Windows.Controls.Grid> na *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-208">In the section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="00d3b-209">Abra *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-209">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="00d3b-210">Defina a <xref:System.Windows.FrameworkElement.Margin%2A> propriedade no <xref:System.Windows.Controls.Grid> elemento a ser "10,0,10,10", que corresponde às margens esquerda, superior, direita e inferior:</span><span class="sxs-lookup"><span data-stu-id="00d3b-210">Set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="00d3b-211">Você também pode definir a **margem** os valores na **propriedades** janela, na **Layout** categoria:</span><span class="sxs-lookup"><span data-stu-id="00d3b-211">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Valores de margem na janela Propriedades](media/properties-margin.png)

3. <span data-ttu-id="00d3b-213">Adicione o seguinte XAML entre o <xref:System.Windows.Controls.Grid> marcas para criar as definições de linha e coluna:</span><span class="sxs-lookup"><span data-stu-id="00d3b-213">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="00d3b-214">O <xref:System.Windows.Controls.RowDefinition.Height%2A> de duas linhas é definido como <xref:System.Windows.GridLength.Auto%2A>, que significa que as linhas são dimensionadas de base no conteúdo de linhas.</span><span class="sxs-lookup"><span data-stu-id="00d3b-214">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized base on the content in the rows.</span></span> <span data-ttu-id="00d3b-215">O padrão <xref:System.Windows.Controls.RowDefinition.Height%2A> é <xref:System.Windows.GridUnitType.Star> dimensionamento, o que significa que a altura da linha é uma proporção ponderada do espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="00d3b-215">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="00d3b-216">Por exemplo, se duas linhas tiverem uma <xref:System.Windows.Controls.RowDefinition.Height%2A> de "\*", cada um deles tem uma altura que será a metade do espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="00d3b-216">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="00d3b-217">Seu <xref:System.Windows.Controls.Grid> deve agora parecer como o XAML a seguir:</span><span class="sxs-lookup"><span data-stu-id="00d3b-217">Your <xref:System.Windows.Controls.Grid> should now look like the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="00d3b-218">Adicionar controles</span><span class="sxs-lookup"><span data-stu-id="00d3b-218">Add controls</span></span>

<span data-ttu-id="00d3b-219">Nesta seção, você atualizará a página inicial da interface do usuário para mostrar uma lista das pessoas que um usuário pode selecionar para mostrar o relatório de despesas.</span><span class="sxs-lookup"><span data-stu-id="00d3b-219">In this section, you'll update the home page UI to show a list of people that a user can select from to show the expense report for.</span></span> <span data-ttu-id="00d3b-220">Os controles são objetos da interface do usuário que permitem aos usuários interagir com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00d3b-220">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="00d3b-221">Para obter mais informações, consulte [Controles](../../../../docs/framework/wpf/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="00d3b-221">For more information, see [Controls](../../../../docs/framework/wpf/controls/index.md).</span></span>

<span data-ttu-id="00d3b-222">Para criar essa interface do usuário, você adicionará os seguintes elementos para *`ExpenseItHome.xaml`*:</span><span class="sxs-lookup"><span data-stu-id="00d3b-222">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="00d3b-223"><xref:System.Windows.Controls.ListBox> (para a lista de pessoas).</span><span class="sxs-lookup"><span data-stu-id="00d3b-223"><xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="00d3b-224"><xref:System.Windows.Controls.Label> (para o cabeçalho da lista).</span><span class="sxs-lookup"><span data-stu-id="00d3b-224"><xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="00d3b-225"><xref:System.Windows.Controls.Button> (para clicar para exibir o relatório de despesas para a pessoa que está selecionada na lista).</span><span class="sxs-lookup"><span data-stu-id="00d3b-225"><xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="00d3b-226">Cada controle é colocado em uma linha do <xref:System.Windows.Controls.Grid> definindo o <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> propriedade anexada.</span><span class="sxs-lookup"><span data-stu-id="00d3b-226">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="00d3b-227">Para obter mais informações sobre propriedades anexadas, consulte [visão geral das propriedades anexadas](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="00d3b-227">For more information about attached properties, see [Attached Properties Overview](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="00d3b-228">Abra *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-228">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="00d3b-229">Adicione o seguinte XAML em algum lugar entre o <xref:System.Windows.Controls.Grid> marcas:</span><span class="sxs-lookup"><span data-stu-id="00d3b-229">Add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="00d3b-230">Você também pode criar os controles arrastando-os do **caixa de ferramentas** janela para a janela de design e, em seguida, definir suas propriedades na **propriedades** janela.</span><span class="sxs-lookup"><span data-stu-id="00d3b-230">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

3. <span data-ttu-id="00d3b-231">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00d3b-231">Build and run the application.</span></span>

<span data-ttu-id="00d3b-232">A ilustração a seguir mostra os controles que você acabou de criar:</span><span class="sxs-lookup"><span data-stu-id="00d3b-232">The following illustration shows the controls you just created:</span></span>

![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="00d3b-234">Adicionar uma imagem e um título</span><span class="sxs-lookup"><span data-stu-id="00d3b-234">Add an image and a title</span></span>

<span data-ttu-id="00d3b-235">Nesta seção, você vai atualizar a home page da interface do usuário com uma imagem e um título de página.</span><span class="sxs-lookup"><span data-stu-id="00d3b-235">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="00d3b-236">Abra *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-236">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="00d3b-237">Adicione outra coluna para o <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> fixa <xref:System.Windows.Controls.ColumnDefinition.Width%2A> de 230 pixels:</span><span class="sxs-lookup"><span data-stu-id="00d3b-237">Add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]

3. <span data-ttu-id="00d3b-238">Adicionar outra linha para o <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, para um total de quatro linhas:</span><span class="sxs-lookup"><span data-stu-id="00d3b-238">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]

4. <span data-ttu-id="00d3b-239">Mova os controles para a segunda coluna, definindo o <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> propriedade como 1 em cada um dos três controles (da borda, ListBox e botão).</span><span class="sxs-lookup"><span data-stu-id="00d3b-239">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

5. <span data-ttu-id="00d3b-240">Mova cada controle para baixo uma linha, aumentando seu <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> valor por 1.</span><span class="sxs-lookup"><span data-stu-id="00d3b-240">Move each control down a row, by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1.</span></span>

   <span data-ttu-id="00d3b-241">O XAML para os três controles agora aparece desta forma:</span><span class="sxs-lookup"><span data-stu-id="00d3b-241">The XAML for the three controls now looks like this:</span></span>

    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

6. <span data-ttu-id="00d3b-242">Definir a <xref:System.Windows.Controls.Panel.Background%2A> do <xref:System.Windows.Controls.Grid> seja a *watermark* arquivo de imagem, adicionando o seguinte XAML em algum lugar entre o `<Grid>` e `</Grid>` marcas:</span><span class="sxs-lookup"><span data-stu-id="00d3b-242">Set the <xref:System.Windows.Controls.Panel.Background%2A> of the <xref:System.Windows.Controls.Grid> to be the *watermark.png* image file, by adding the following XAML somewhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

7. <span data-ttu-id="00d3b-243">Antes do <xref:System.Windows.Controls.Border> elemento, adicionar um <xref:System.Windows.Controls.Label> com o conteúdo "Exibir relatório de despesas".</span><span class="sxs-lookup"><span data-stu-id="00d3b-243">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="00d3b-244">Este é o título da página.</span><span class="sxs-lookup"><span data-stu-id="00d3b-244">This is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

8. <span data-ttu-id="00d3b-245">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00d3b-245">Build and run the application.</span></span>

<span data-ttu-id="00d3b-246">A ilustração a seguir mostra os resultados de que você acabou de adicionar:</span><span class="sxs-lookup"><span data-stu-id="00d3b-246">The following illustration shows the results of what you just added:</span></span>

![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="00d3b-248">Adicionar código para manipular eventos</span><span class="sxs-lookup"><span data-stu-id="00d3b-248">Add code to handle events</span></span>

1. <span data-ttu-id="00d3b-249">Abra *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-249">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="00d3b-250">Adicionar um <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos para o <xref:System.Windows.Controls.Button> elemento.</span><span class="sxs-lookup"><span data-stu-id="00d3b-250">Add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="00d3b-251">Para obter mais informações, consulte [como: criar um manipulador de eventos simples](https://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).</span><span class="sxs-lookup"><span data-stu-id="00d3b-251">For more information, see [How to: Create a simple event handler](https://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).</span></span>

    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

3. <span data-ttu-id="00d3b-252">Abra *`ExpenseItHome.xaml.vb`* ou *`ExpenseItHome.xaml.cs`*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-252">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="00d3b-253">Adicione o seguinte código para o `ExpenseItHome` classe para adicionar um botão de manipulador de eventos de clique.</span><span class="sxs-lookup"><span data-stu-id="00d3b-253">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="00d3b-254">O manipulador de eventos abre o **ExpenseReportPage** página.</span><span class="sxs-lookup"><span data-stu-id="00d3b-254">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="00d3b-255">Criar a interface do usuário para ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="00d3b-255">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="00d3b-256">*ExpenseReportPage. XAML* exibe o relatório de despesas para a pessoa que está selecionada na **`ExpenseItHome`** página.</span><span class="sxs-lookup"><span data-stu-id="00d3b-256">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="00d3b-257">Nesta seção, você criará a interface do usuário para **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="00d3b-257">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="00d3b-258">Você também adicionará o plano de fundo e cores de preenchimento para os vários elementos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="00d3b-258">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="00d3b-259">Abra *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-259">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="00d3b-260">Adicione o seguinte XAML entre o <xref:System.Windows.Controls.Grid> marcas:</span><span class="sxs-lookup"><span data-stu-id="00d3b-260">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="00d3b-261">Essa interface do usuário é semelhante à *`ExpenseItHome.xaml`*, exceto os dados do relatório são exibidos em um <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="00d3b-261">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="00d3b-262">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00d3b-262">Build and run the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="00d3b-263">Se você receber um erro que o <xref:System.Windows.Controls.DataGrid> não foi encontrado ou não existir, certifique-se de que seu projeto direcionado ao .NET Framework 4 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="00d3b-263">If you get an error that the <xref:System.Windows.Controls.DataGrid> was not found or does not exist, make sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="00d3b-264">Para obter mais informações, consulte [Como definir uma versão do .NET Framework como destino](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="00d3b-264">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>

4. <span data-ttu-id="00d3b-265">Selecione o **exibição** botão.</span><span class="sxs-lookup"><span data-stu-id="00d3b-265">Select the **View** button.</span></span>

    <span data-ttu-id="00d3b-266">A página de relatório de despesas é exibida.</span><span class="sxs-lookup"><span data-stu-id="00d3b-266">The expense report page appears.</span></span> <span data-ttu-id="00d3b-267">Além disso, observe que o botão de navegação regressiva está habilitado.</span><span class="sxs-lookup"><span data-stu-id="00d3b-267">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="00d3b-268">A ilustração a seguir mostra os elementos de interface do usuário adicionados ao *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-268">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png)

## <a name="style-controls"></a><span data-ttu-id="00d3b-270">Controles de estilo</span><span class="sxs-lookup"><span data-stu-id="00d3b-270">Style controls</span></span>

<span data-ttu-id="00d3b-271">A aparência de vários elementos geralmente é o mesmo para todos os elementos do mesmo tipo em uma interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="00d3b-271">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="00d3b-272">Interface do usuário usa [estilos](../../../../docs/framework/wpf/controls/styling-and-templating.md) para fazer com que as aparências reutilizáveis entre vários elementos.</span><span class="sxs-lookup"><span data-stu-id="00d3b-272">UI uses [styles](../../../../docs/framework/wpf/controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="00d3b-273">A capacidade de reutilização dos estilos ajuda a simplificar o gerenciamento e a criação de XAML.</span><span class="sxs-lookup"><span data-stu-id="00d3b-273">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="00d3b-274">Esta seção substitui os atributos por elemento que foram definidos nas etapas anteriores com estilos.</span><span class="sxs-lookup"><span data-stu-id="00d3b-274">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="00d3b-275">Abra *Application. XAML* ou *App. XAML*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-275">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="00d3b-276">Adicione o seguinte XAML entre o <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> marcas:</span><span class="sxs-lookup"><span data-stu-id="00d3b-276">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="00d3b-277">Esse XAML adiciona os seguintes estilos:</span><span class="sxs-lookup"><span data-stu-id="00d3b-277">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="00d3b-278">`headerTextStyle`: para formatar o título da página <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="00d3b-278">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="00d3b-279">`labelStyle`: para formatar os controles <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="00d3b-279">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="00d3b-280">`columnHeaderStyle`: para formatar o <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="00d3b-280">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="00d3b-281">`listHeaderStyle`: para formatar os controles <xref:System.Windows.Controls.Border> do cabeçalho da lista.</span><span class="sxs-lookup"><span data-stu-id="00d3b-281">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="00d3b-282">`listHeaderTextStyle`: Para formatar o cabeçalho da lista <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="00d3b-282">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="00d3b-283">`buttonStyle`: Para formatar a <xref:System.Windows.Controls.Button> em `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="00d3b-283">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="00d3b-284">Observe que os estilos são recursos e seus filhos a <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> elemento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="00d3b-284">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="00d3b-285">Nesse local, os estilos são aplicados a todos os elementos em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00d3b-285">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="00d3b-286">Para obter um exemplo do uso de recursos em um aplicativo .NET Framework, consulte [usar recursos do aplicativo](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="00d3b-286">For an example of using resources in a .NET Framework application, see [Use Application Resources](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="00d3b-287">Abra *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-287">Open *`ExpenseItHome.xaml`*.</span></span>

4. <span data-ttu-id="00d3b-288">Substitua tudo entre os <xref:System.Windows.Controls.Grid> elementos com o XAML a seguir:</span><span class="sxs-lookup"><span data-stu-id="00d3b-288">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="00d3b-289">As propriedades como <xref:System.Windows.VerticalAlignment> e <xref:System.Windows.Media.FontFamily> que definem a aparência de cada controle são removidas e substituídas ao aplicar os estilos.</span><span class="sxs-lookup"><span data-stu-id="00d3b-289">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="00d3b-290">Por exemplo, o `headerTextStyle` é aplicado a "Exibir relatório de despesas" <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="00d3b-290">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

5. <span data-ttu-id="00d3b-291">Abra *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-291">Open *ExpenseReportPage.xaml*.</span></span>

6. <span data-ttu-id="00d3b-292">Substitua tudo entre os <xref:System.Windows.Controls.Grid> elementos com o XAML a seguir:</span><span class="sxs-lookup"><span data-stu-id="00d3b-292">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="00d3b-293">Isso adiciona estilos aos elementos <xref:System.Windows.Controls.Label> e <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="00d3b-293">This adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="00d3b-294">Associar dados a um controle</span><span class="sxs-lookup"><span data-stu-id="00d3b-294">Bind data to a control</span></span>

<span data-ttu-id="00d3b-295">Nesta seção, você criará os dados XML que estão associados a vários controles.</span><span class="sxs-lookup"><span data-stu-id="00d3b-295">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="00d3b-296">Abra *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-296">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="00d3b-297">Após a abertura <xref:System.Windows.Controls.Grid> elemento, adicione o XAML a seguir para criar um <xref:System.Windows.Data.XmlDataProvider> que contém os dados para cada pessoa:</span><span class="sxs-lookup"><span data-stu-id="00d3b-297">After the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    <span data-ttu-id="00d3b-298">Os dados são criados como um <xref:System.Windows.Controls.Grid> recursos.</span><span class="sxs-lookup"><span data-stu-id="00d3b-298">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="00d3b-299">Normalmente, isso seria carregado como um arquivo, mas para simplificar, os dados são adicionados embutidos.</span><span class="sxs-lookup"><span data-stu-id="00d3b-299">Normally this would be loaded as a file, but for simplicity the data is added inline.</span></span>

3. <span data-ttu-id="00d3b-300">Dentro de `<Grid.Resources>` elemento, adicione o seguinte <xref:System.Windows.DataTemplate>, que define como exibir os dados no <xref:System.Windows.Controls.ListBox>:</span><span class="sxs-lookup"><span data-stu-id="00d3b-300">Within the `<Grid.Resources>` element, add the following <xref:System.Windows.DataTemplate>, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>:</span></span>

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    <span data-ttu-id="00d3b-301">Para obter mais informações sobre modelos de dados, consulte [visão geral de modelagem de dados](../../../../docs/framework/wpf/data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="00d3b-301">For more information about data templates, see [Data templating overview](../../../../docs/framework/wpf/data/data-templating-overview.md).</span></span>

4. <span data-ttu-id="00d3b-302">Substitua a <xref:System.Windows.Controls.ListBox> com o XAML a seguir:</span><span class="sxs-lookup"><span data-stu-id="00d3b-302">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="00d3b-303">Esse XAML associa a <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade do <xref:System.Windows.Controls.ListBox> à fonte de dados e aplica o modelo de dados como o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="00d3b-303">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="00d3b-304">Conectar dados aos controles</span><span class="sxs-lookup"><span data-stu-id="00d3b-304">Connect data to controls</span></span>

<span data-ttu-id="00d3b-305">Em seguida, você adicionará código para recuperar o nome que está selecionado na **`ExpenseItHome`** da página e passá-lo para o construtor da **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="00d3b-305">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="00d3b-306">**ExpenseReportPage** define seu contexto de dados com o item passado, que é o que os controles definidos no *ExpenseReportPage* associar a.</span><span class="sxs-lookup"><span data-stu-id="00d3b-306">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="00d3b-307">Abra *ExpenseReportPage.xaml.vb* ou *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-307">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="00d3b-308">Adicione um construtor que utiliza um objeto para passar os dados do relatório de despesas da pessoa selecionada.</span><span class="sxs-lookup"><span data-stu-id="00d3b-308">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="00d3b-309">Abra *`ExpenseItHome.xaml.vb`* ou *`ExpenseItHome.xaml.cs`*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-309">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="00d3b-310">Alterar o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos para chamar o novo construtor passando os dados de relatório de despesas da pessoa selecionada.</span><span class="sxs-lookup"><span data-stu-id="00d3b-310">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="00d3b-311">Dados de estilo com modelos de dados</span><span class="sxs-lookup"><span data-stu-id="00d3b-311">Style data with data templates</span></span>

<span data-ttu-id="00d3b-312">Nesta seção, você atualizará a interface do usuário para cada item nas listas de associação de dados usando modelos de dados.</span><span class="sxs-lookup"><span data-stu-id="00d3b-312">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="00d3b-313">Abra *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="00d3b-313">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="00d3b-314">Associar o conteúdo do "Nome" e "Departamento" <xref:System.Windows.Controls.Label> propriedade da fonte de elementos para os dados apropriados.</span><span class="sxs-lookup"><span data-stu-id="00d3b-314">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="00d3b-315">Para obter mais informações sobre associação de dados, consulte [visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="00d3b-315">For more information about data binding, see [Data binding overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="00d3b-316">Após a abertura <xref:System.Windows.Controls.Grid> elemento, adicione os seguintes modelos de dados, que definem como exibir os dados de relatório de despesas:</span><span class="sxs-lookup"><span data-stu-id="00d3b-316">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="00d3b-317">Substitua os <xref:System.Windows.Controls.DataGridTextColumn> elementos com <xref:System.Windows.Controls.DataGridTemplateColumn> sob o <xref:System.Windows.Controls.DataGrid> elemento e aplicar os modelos a eles.</span><span class="sxs-lookup"><span data-stu-id="00d3b-317">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="00d3b-318">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00d3b-318">Build and run the application.</span></span>

6. <span data-ttu-id="00d3b-319">Selecione uma pessoa e, em seguida, selecione a **exibição** botão.</span><span class="sxs-lookup"><span data-stu-id="00d3b-319">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="00d3b-320">A ilustração a seguir mostra as duas páginas do `ExpenseIt` aplicativo com controles, layout, estilos, vinculação de dados e modelos de dados aplicados:</span><span class="sxs-lookup"><span data-stu-id="00d3b-320">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Capturas de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png)

> [!NOTE]
> <span data-ttu-id="00d3b-322">Este exemplo demonstra um recurso específico do WPF e não segue todas as práticas recomendadas para coisas como segurança, localização e acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="00d3b-322">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="00d3b-323">Para obter uma cobertura abrangente do WPF e as práticas recomendadas de desenvolvimento de aplicativo do .NET Framework, consulte os tópicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="00d3b-323">For comprehensive coverage of WPF and the .NET Framework application development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="00d3b-324">Acessibilidade</span><span class="sxs-lookup"><span data-stu-id="00d3b-324">Accessibility</span></span>](../../../../docs/framework/ui-automation/accessibility-best-practices.md)
>
> - [<span data-ttu-id="00d3b-325">Segurança</span><span class="sxs-lookup"><span data-stu-id="00d3b-325">Security</span></span>](../../../../docs/framework/wpf/security-wpf.md)
>
> - [<span data-ttu-id="00d3b-326">Globalização e localização do WPF</span><span class="sxs-lookup"><span data-stu-id="00d3b-326">WPF globalization and localization</span></span>](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
>
> - [<span data-ttu-id="00d3b-327">Desempenho do WPF</span><span class="sxs-lookup"><span data-stu-id="00d3b-327">WPF performance</span></span>](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="00d3b-328">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="00d3b-328">Next steps</span></span>

<span data-ttu-id="00d3b-329">Neste passo a passo, você aprendeu várias técnicas para a criação de uma interface do usuário usando o Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="00d3b-329">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="00d3b-330">Agora você deve ter uma compreensão básica dos blocos de construção de um aplicativo do .NET Framework de associação de dados.</span><span class="sxs-lookup"><span data-stu-id="00d3b-330">You should now have a basic understanding of the building blocks of a data-bound, .NET Framework application.</span></span> <span data-ttu-id="00d3b-331">Para obter mais informações sobre os modelos de arquitetura e programação do WPF, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="00d3b-331">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="00d3b-332">Arquitetura do WPF</span><span class="sxs-lookup"><span data-stu-id="00d3b-332">WPF architecture</span></span>](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
- [<span data-ttu-id="00d3b-333">Visão geral do XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="00d3b-333">XAML overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="00d3b-334">Visão geral das propriedades de dependência</span><span class="sxs-lookup"><span data-stu-id="00d3b-334">Dependency properties overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [<span data-ttu-id="00d3b-335">Layout</span><span class="sxs-lookup"><span data-stu-id="00d3b-335">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)

<span data-ttu-id="00d3b-336">Para obter mais informações sobre como criar aplicativos, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="00d3b-336">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="00d3b-337">Desenvolvimento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="00d3b-337">Application development</span></span>](../../../../docs/framework/wpf/app-development/index.md)
- [<span data-ttu-id="00d3b-338">Controles</span><span class="sxs-lookup"><span data-stu-id="00d3b-338">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)
- [<span data-ttu-id="00d3b-339">Visão geral da associação de dados</span><span class="sxs-lookup"><span data-stu-id="00d3b-339">Data binding overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="00d3b-340">Elementos gráficos e multimídia</span><span class="sxs-lookup"><span data-stu-id="00d3b-340">Graphics and multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [<span data-ttu-id="00d3b-341">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="00d3b-341">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="00d3b-342">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00d3b-342">See also</span></span>

- [<span data-ttu-id="00d3b-343">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="00d3b-343">Panels overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
- [<span data-ttu-id="00d3b-344">Visão geral de modelagem de dados</span><span class="sxs-lookup"><span data-stu-id="00d3b-344">Data templating overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [<span data-ttu-id="00d3b-345">Compilar um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="00d3b-345">Build a WPF application</span></span>](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="00d3b-346">Estilos e modelos</span><span class="sxs-lookup"><span data-stu-id="00d3b-346">Styles and templates</span></span>](../../../../docs/framework/wpf/controls/styles-and-templates.md)
