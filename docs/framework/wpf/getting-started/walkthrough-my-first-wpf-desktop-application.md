---
title: Criar um aplicativo WPF no Visual Studio
ms.date: 03/20/2019
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
ms.openlocfilehash: 9d0abd18b2242ab21e8a915caac1ff9e3216acd0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617268"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="cf11b-102">Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF</span><span class="sxs-lookup"><span data-stu-id="cf11b-102">Walkthrough: My first WPF desktop application</span></span>

<span data-ttu-id="cf11b-103">Este artigo mostra como desenvolver um aplicativo de desktop do Windows Presentation Foundation (WPF) que inclui os elementos que são comuns à maioria dos aplicativos do WPF: Extensible Application Markup Language (XAML) marcação, code-behind, definições de aplicativo, controles, layout, vinculação de dados e estilos.</span><span class="sxs-lookup"><span data-stu-id="cf11b-103">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="cf11b-104">Para desenvolver o aplicativo, você usará o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cf11b-104">To develop the application, you'll use Visual Studio.</span></span> 

<span data-ttu-id="cf11b-105">Este passo a passo inclui as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="cf11b-105">This walkthrough includes the following steps:</span></span>

- <span data-ttu-id="cf11b-106">Use XAML para criar a aparência da interface do usuário do aplicativo (UI).</span><span class="sxs-lookup"><span data-stu-id="cf11b-106">Use XAML to design the appearance of the application's user interface (UI).</span></span>

- <span data-ttu-id="cf11b-107">Escreva código para criar o comportamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf11b-107">Write code to build the application's behavior.</span></span>

- <span data-ttu-id="cf11b-108">Crie uma definição de aplicativo para gerenciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf11b-108">Create an application definition to manage the application.</span></span>

- <span data-ttu-id="cf11b-109">Adicionar controles e criar o layout para compor o interface do usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf11b-109">Add controls and create the layout to compose the application UI.</span></span>

- <span data-ttu-id="cf11b-110">Crie estilos para uma aparência consistente em toda a interface do usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf11b-110">Create styles for a consistent appearance throughout the application's UI.</span></span>

- <span data-ttu-id="cf11b-111">Vincular a interface do usuário aos dados, tanto para preencher a interface do usuário de dados para manter os dados e interface do usuário sincronizado.</span><span class="sxs-lookup"><span data-stu-id="cf11b-111">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="cf11b-112">Ao final do passo a passo, você será criado um aplicativo do Windows que permite aos usuários exibir relatórios de despesas para pessoas selecionadas autônomo.</span><span class="sxs-lookup"><span data-stu-id="cf11b-112">By the end of the walkthrough, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="cf11b-113">O aplicativo é composto de várias páginas do WPF que são hospedadas em uma janela de estilo de navegador.</span><span class="sxs-lookup"><span data-stu-id="cf11b-113">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="cf11b-114">O código de exemplo que é usado para criar este passo a passo está disponível para o Visual Basic e C# na [código de exemplo de aplicativo do passo a passo WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span><span class="sxs-lookup"><span data-stu-id="cf11b-114">The sample code that is used to build this walkthrough is available for both Visual Basic and C# at [Walkthrough WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="cf11b-115">Você pode alternar o idioma de código do código de exemplo entre o C# e Visual Basic usando o **\< />** lista suspensa no canto superior direito deste artigo.</span><span class="sxs-lookup"><span data-stu-id="cf11b-115">You can toggle the code language of the sample code between C# and Visual Basic by using the **\</>** drop-down on the upper right side of this article.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cf11b-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="cf11b-116">Prerequisites</span></span>

- <span data-ttu-id="cf11b-117">Visual Studio 2017 ou posterior</span><span class="sxs-lookup"><span data-stu-id="cf11b-117">Visual Studio 2017 or later</span></span>

   <span data-ttu-id="cf11b-118">Para obter mais informações sobre como instalar a versão mais recente do Visual Studio, consulte [instalar o Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="cf11b-118">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="cf11b-119">Este artigo usa o Visual Studio de 2019.</span><span class="sxs-lookup"><span data-stu-id="cf11b-119">This article uses Visual Studio 2019.</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="cf11b-120">Criar o projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="cf11b-120">Create the application project</span></span>

<span data-ttu-id="cf11b-121">A primeira etapa é criar a infraestrutura de aplicativo, que inclui uma definição de aplicativo, duas páginas e uma imagem.</span><span class="sxs-lookup"><span data-stu-id="cf11b-121">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="cf11b-122">Criar um novo projeto de aplicativo do WPF no Visual Basic ou Visual c# denominado **`ExpenseIt`**:</span><span class="sxs-lookup"><span data-stu-id="cf11b-122">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="cf11b-123">Abra o Visual Studio e selecione **arquivo** > **New** > **projeto**.</span><span class="sxs-lookup"><span data-stu-id="cf11b-123">Open Visual Studio and select **File** > **New** > **Project**.</span></span>

      <span data-ttu-id="cf11b-124">O **criar um novo projeto** caixa de diálogo é aberta.</span><span class="sxs-lookup"><span data-stu-id="cf11b-124">The **Create a new project** dialog opens.</span></span>

      ![Criar uma caixa de diálogo Novo projeto](./media/gettingstartedfigure0a.png)

   2. <span data-ttu-id="cf11b-126">No **linguagem** lista suspensa, selecione **C#** ou **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="cf11b-126">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>

   3. <span data-ttu-id="cf11b-127">Selecione o **aplicativo WPF (.NET Framework)** modelo e selecione **próxima**.</span><span class="sxs-lookup"><span data-stu-id="cf11b-127">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span> 
    
   4. <span data-ttu-id="cf11b-128">Selecione **criar um novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="cf11b-128">Select **Create a new project**.</span></span>

      <span data-ttu-id="cf11b-129">O **configurar um novo projeto** caixa de diálogo é aberta.</span><span class="sxs-lookup"><span data-stu-id="cf11b-129">The **Configure a new project** dialog opens.</span></span>

      ![Configurar uma caixa de diálogo Novo projeto](./media/gettingstartedfigure0c.png)

   5. <span data-ttu-id="cf11b-131">Insira o nome do projeto **`ExpenseIt`** e, em seguida, selecione **criar**.</span><span class="sxs-lookup"><span data-stu-id="cf11b-131">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      <span data-ttu-id="cf11b-132">Visual Studio cria o projeto e abre o designer para a janela do aplicativo padrão chamado **MainWindow. XAML**.</span><span class="sxs-lookup"><span data-stu-id="cf11b-132">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="cf11b-133">Abra *Application. XAML* (Visual Basic) ou *App. XAML* (c#).</span><span class="sxs-lookup"><span data-stu-id="cf11b-133">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="cf11b-134">Esse arquivo XAML define um aplicativo WPF e quaisquer recursos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf11b-134">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="cf11b-135">Você também usar esse arquivo para especificar a interface do usuário, nesse caso *MainWindow. XAML*, que mostra automaticamente quando o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="cf11b-135">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="cf11b-136">O XAML deve ser semelhante ao seguinte no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="cf11b-136">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="cf11b-137">E semelhante ao seguinte em C#:</span><span class="sxs-lookup"><span data-stu-id="cf11b-137">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="cf11b-138">Abra *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="cf11b-138">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="cf11b-139">Esse arquivo XAML é a janela principal do seu aplicativo e exibe o conteúdo criado em páginas.</span><span class="sxs-lookup"><span data-stu-id="cf11b-139">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="cf11b-140">O <xref:System.Windows.Window> classe define as propriedades de uma janela, como seu título, tamanho ou ícone e manipula eventos, como fechar ou ocultar.</span><span class="sxs-lookup"><span data-stu-id="cf11b-140">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="cf11b-141">Alterar o <xref:System.Windows.Window> elemento para um <xref:System.Windows.Navigation.NavigationWindow>, como mostra o XAML a seguir:</span><span class="sxs-lookup"><span data-stu-id="cf11b-141">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="cf11b-142">Este aplicativo navega para um conteúdo diferente dependendo da entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="cf11b-142">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="cf11b-143">É por isso que o principal <xref:System.Windows.Window> precisa ser alterado para um <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="cf11b-143">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="cf11b-144"><xref:System.Windows.Navigation.NavigationWindow> herda todas as propriedades de <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="cf11b-144"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="cf11b-145">O <xref:System.Windows.Navigation.NavigationWindow> elemento no arquivo XAML cria uma instância do <xref:System.Windows.Navigation.NavigationWindow> classe.</span><span class="sxs-lookup"><span data-stu-id="cf11b-145">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="cf11b-146">Para obter mais informações, consulte [visão geral da navegação](../app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cf11b-146">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="cf11b-147">Remover o <xref:System.Windows.Controls.Grid> elementos entre o <xref:System.Windows.Navigation.NavigationWindow> marcas.</span><span class="sxs-lookup"><span data-stu-id="cf11b-147">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="cf11b-148">Alterar as propriedades a seguir no código XAML para o <xref:System.Windows.Navigation.NavigationWindow> elemento:</span><span class="sxs-lookup"><span data-stu-id="cf11b-148">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="cf11b-149">Defina as <xref:System.Windows.Window.Title%2A> propriedade para "`ExpenseIt`".</span><span class="sxs-lookup"><span data-stu-id="cf11b-149">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="cf11b-150">Defina o <xref:System.Windows.FrameworkElement.Height%2A> propriedade para 350 pixels.</span><span class="sxs-lookup"><span data-stu-id="cf11b-150">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="cf11b-151">Defina o <xref:System.Windows.FrameworkElement.Width%2A> propriedade para 500 pixels.</span><span class="sxs-lookup"><span data-stu-id="cf11b-151">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="cf11b-152">O XAML deve ser semelhante ao seguinte para o Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="cf11b-152">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="cf11b-153">E com o seguinte para C#:</span><span class="sxs-lookup"><span data-stu-id="cf11b-153">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="cf11b-154">Abra *. XAML. vb* ou *MainWindow.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="cf11b-154">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="cf11b-155">Esse arquivo é um arquivo code-behind que contém o código para manipular os eventos declarados em *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="cf11b-155">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="cf11b-156">Esse arquivo contém uma classe parcial para a janela definida no XAML.</span><span class="sxs-lookup"><span data-stu-id="cf11b-156">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="cf11b-157">Se você estiver usando o C#, altere o `MainWindow` classe derivar <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="cf11b-157">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="cf11b-158">(No Visual Basic, isso ocorre automaticamente quando você altera a janela no XAML.) O C# código agora deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="cf11b-158">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="cf11b-159">Adicionar arquivos ao aplicativo</span><span class="sxs-lookup"><span data-stu-id="cf11b-159">Add files to the application</span></span>

<span data-ttu-id="cf11b-160">Nesta seção, você adicionará duas páginas e uma imagem ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf11b-160">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="cf11b-161">Adicione uma nova página ao projeto e denomine *`ExpenseItHome.xaml`*:</span><span class="sxs-lookup"><span data-stu-id="cf11b-161">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="cf11b-162">Na **Gerenciador de soluções**, clique com botão direito no **`ExpenseIt`** nó do projeto e escolha **Add** > **página**.</span><span class="sxs-lookup"><span data-stu-id="cf11b-162">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="cf11b-163">No **Adicionar Novo Item** caixa de diálogo, o **página (WPF)** modelo já está selecionado.</span><span class="sxs-lookup"><span data-stu-id="cf11b-163">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="cf11b-164">Insira o nome **`ExpenseItHome`** e, em seguida, selecione **Add**.</span><span class="sxs-lookup"><span data-stu-id="cf11b-164">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="cf11b-165">Esta página é a primeira página que é exibida quando o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="cf11b-165">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="cf11b-166">Ela mostrará uma lista de pessoas para selecionar, para mostrar um relatório de despesas.</span><span class="sxs-lookup"><span data-stu-id="cf11b-166">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="cf11b-167">Abra *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="cf11b-167">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="cf11b-168">Defina as <xref:System.Windows.Controls.Page.Title%2A> para "`ExpenseIt - Home`".</span><span class="sxs-lookup"><span data-stu-id="cf11b-168">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="cf11b-169">Defina as `DesignHeight` e `DesignWidth` valores de elemento para 300 pixels.</span><span class="sxs-lookup"><span data-stu-id="cf11b-169">Set the `DesignHeight` and `DesignWidth` element values to 300 pixels.</span></span>

    <span data-ttu-id="cf11b-170">O XAML agora aparece da seguinte maneira para o Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="cf11b-170">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="cf11b-171">E com o seguinte para C#:</span><span class="sxs-lookup"><span data-stu-id="cf11b-171">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="cf11b-172">Abra *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="cf11b-172">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="cf11b-173">Adicionar um <xref:System.Windows.Navigation.NavigationWindow.Source%2A> propriedade para o <xref:System.Windows.Navigation.NavigationWindow> elemento e defini-lo como "`ExpenseItHome.xaml`".</span><span class="sxs-lookup"><span data-stu-id="cf11b-173">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="cf11b-174">Isso define *`ExpenseItHome.xaml`* ser a primeira página aberta quando o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="cf11b-174">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span> 

    <span data-ttu-id="cf11b-175">Exemplo de XAML no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="cf11b-175">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="cf11b-176">E, em C#:</span><span class="sxs-lookup"><span data-stu-id="cf11b-176">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="cf11b-177">Você também pode definir a **fonte** propriedade no **diversos** categoria da **propriedades** janela.</span><span class="sxs-lookup"><span data-stu-id="cf11b-177">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Propriedade de origem na janela Propriedades](./media/properties-source.png)

1. <span data-ttu-id="cf11b-179">Adicione outra nova página do WPF ao projeto e denomine *ExpenseReportPage*::</span><span class="sxs-lookup"><span data-stu-id="cf11b-179">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="cf11b-180">Na **Gerenciador de soluções**, clique com botão direito no **`ExpenseIt`** nó do projeto e escolha **Add** > **página**.</span><span class="sxs-lookup"><span data-stu-id="cf11b-180">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="cf11b-181">No **Adicionar Novo Item** caixa de diálogo, selecione o **página (WPF)** modelo.</span><span class="sxs-lookup"><span data-stu-id="cf11b-181">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="cf11b-182">Insira o nome **ExpenseReportPage**e, em seguida, selecione **Add**.</span><span class="sxs-lookup"><span data-stu-id="cf11b-182">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="cf11b-183">Essa página mostrará o relatório de despesas da pessoa que está selecionada na **`ExpenseItHome`** página.</span><span class="sxs-lookup"><span data-stu-id="cf11b-183">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="cf11b-184">Abra *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="cf11b-184">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="cf11b-185">Defina as <xref:System.Windows.Controls.Page.Title%2A> para "`ExpenseIt - View Expense`".</span><span class="sxs-lookup"><span data-stu-id="cf11b-185">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="cf11b-186">Defina as `DesignHeight` e `DesignWidth` valores de elemento para 300 pixels.</span><span class="sxs-lookup"><span data-stu-id="cf11b-186">Set the `DesignHeight` and `DesignWidth` element values to 300 pixels.</span></span>

    <span data-ttu-id="cf11b-187">*ExpenseReportPage. XAML* agora é semelhante ao seguinte no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="cf11b-187">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="cf11b-188">E semelhante ao seguinte em C#:</span><span class="sxs-lookup"><span data-stu-id="cf11b-188">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="cf11b-189">Abra *Expenseithome* e *ExpenseReportPage*, ou *ExpenseItHome.xaml.cs* e *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="cf11b-189">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="cf11b-190">Quando você cria um novo arquivo de página, o Visual Studio cria automaticamente seus *de lógica* arquivo.</span><span class="sxs-lookup"><span data-stu-id="cf11b-190">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="cf11b-191">Esses arquivos code-behind manipulam a lógica para responder à entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="cf11b-191">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="cf11b-192">Seu código deve ser semelhante ao seguinte para **`ExpenseItHome`**:</span><span class="sxs-lookup"><span data-stu-id="cf11b-192">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="cf11b-193">E com o seguinte para **ExpenseReportPage**:</span><span class="sxs-lookup"><span data-stu-id="cf11b-193">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="cf11b-194">Adicione uma imagem chamada *watermark* ao projeto.</span><span class="sxs-lookup"><span data-stu-id="cf11b-194">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="cf11b-195">Você pode criar sua própria imagem, copie o arquivo de código de exemplo ou obtê-lo [aqui](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span><span class="sxs-lookup"><span data-stu-id="cf11b-195">You can create your own image, copy the file from the sample code, or get it [here](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>

    1. <span data-ttu-id="cf11b-196">Clique com botão direito no nó do projeto e selecione **Add** > **Item existente**, ou pressione **Shift**+**Alt** + **Um**.</span><span class="sxs-lookup"><span data-stu-id="cf11b-196">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="cf11b-197">No **Adicionar Item existente** caixa de diálogo, defina o filtro de arquivo como **todos os arquivos** ou **arquivos de imagem**, navegue até o arquivo de imagem que você deseja usar e, em seguida, selecione **adicionar** .</span><span class="sxs-lookup"><span data-stu-id="cf11b-197">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="cf11b-198">Compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="cf11b-198">Build and run the application</span></span>

1. <span data-ttu-id="cf11b-199">Para compilar e executar o aplicativo, pressione **F5** ou selecione **iniciar depuração** do **depurar** menu.</span><span class="sxs-lookup"><span data-stu-id="cf11b-199">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="cf11b-200">A ilustração a seguir mostra o aplicativo com o <xref:System.Windows.Navigation.NavigationWindow> botões:</span><span class="sxs-lookup"><span data-stu-id="cf11b-200">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Captura de tela de exemplo de ExpenseIt](./media/gettingstartedfigure1.png)

2. <span data-ttu-id="cf11b-202">Feche o aplicativo para retornar ao Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cf11b-202">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="cf11b-203">Criar o layout</span><span class="sxs-lookup"><span data-stu-id="cf11b-203">Create the layout</span></span>

<span data-ttu-id="cf11b-204">Layout oferece uma maneira ordenada para posicionar os elementos de interface do usuário e também gerencia o tamanho e a posição desses elementos quando uma interface do usuário é redimensionado.</span><span class="sxs-lookup"><span data-stu-id="cf11b-204">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="cf11b-205">Normalmente, você cria um layout com um dos seguintes controles de layout:</span><span class="sxs-lookup"><span data-stu-id="cf11b-205">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="cf11b-206"><xref:System.Windows.Controls.Canvas> -Define uma área na qual você pode posicionar explicitamente elementos filho usando coordenadas são relativas à área da tela.</span><span class="sxs-lookup"><span data-stu-id="cf11b-206"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="cf11b-207"><xref:System.Windows.Controls.DockPanel> -Define uma área onde você pode organizar elementos filho horizontal ou verticalmente, relativos uns aos outros.</span><span class="sxs-lookup"><span data-stu-id="cf11b-207"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="cf11b-208"><xref:System.Windows.Controls.Grid> -Define uma área de grade flexível que consiste em linhas e colunas.</span><span class="sxs-lookup"><span data-stu-id="cf11b-208"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="cf11b-209"><xref:System.Windows.Controls.StackPanel> -Organiza elementos filho em uma única linha que pode ser orientada horizontal ou verticalmente.</span><span class="sxs-lookup"><span data-stu-id="cf11b-209"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="cf11b-210"><xref:System.Windows.Controls.VirtualizingStackPanel> -Organiza e virtualiza conteúdo em uma única linha que é orientada horizontal ou verticalmente.</span><span class="sxs-lookup"><span data-stu-id="cf11b-210"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="cf11b-211"><xref:System.Windows.Controls.WrapPanel> -Coloca os elementos filho na posição sequencial da esquerda para a direita, quebrando o conteúdo para a próxima linha na borda da caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="cf11b-211"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="cf11b-212">A ordenação posterior ocorre sequencialmente de cima para baixo ou da direita para a esquerda, dependendo do valor da propriedade Orientation.</span><span class="sxs-lookup"><span data-stu-id="cf11b-212">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="cf11b-213">Cada um desses controles de layout dá suporte a um determinado tipo de layout para seus elementos filho.</span><span class="sxs-lookup"><span data-stu-id="cf11b-213">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="cf11b-214">`ExpenseIt` as páginas podem ser redimensionadas e cada página tem elementos que são organizados horizontalmente e verticalmente juntamente com outros elementos.</span><span class="sxs-lookup"><span data-stu-id="cf11b-214">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="cf11b-215">Neste exemplo, o <xref:System.Windows.Controls.Grid> é usado como o elemento de layout para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf11b-215">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="cf11b-216">Para obter mais informações sobre <xref:System.Windows.Controls.Panel> elementos, consulte [visão geral de painéis](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cf11b-216">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="cf11b-217">Para obter mais informações sobre layout, consulte [Layout](../advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="cf11b-217">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="cf11b-218">Nesta seção, você cria uma tabela de coluna única com três linhas e uma margem de 10 pixels adicionando definições de linha e coluna para o <xref:System.Windows.Controls.Grid> na *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="cf11b-218">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="cf11b-219">Na *`ExpenseItHome.xaml`*, defina as <xref:System.Windows.FrameworkElement.Margin%2A> propriedade no <xref:System.Windows.Controls.Grid> elemento a ser "10,0,10,10", que corresponde às margens esquerda, superior, direita e inferior:</span><span class="sxs-lookup"><span data-stu-id="cf11b-219">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="cf11b-220">Você também pode definir a **margem** os valores na **propriedades** janela, na **Layout** categoria:</span><span class="sxs-lookup"><span data-stu-id="cf11b-220">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Valores de margem na janela Propriedades](./media/properties-margin.png)

2. <span data-ttu-id="cf11b-222">Adicione o seguinte XAML entre o <xref:System.Windows.Controls.Grid> marcas para criar as definições de linha e coluna:</span><span class="sxs-lookup"><span data-stu-id="cf11b-222">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="cf11b-223">O <xref:System.Windows.Controls.RowDefinition.Height%2A> de duas linhas é definido como <xref:System.Windows.GridLength.Auto%2A>, o que significa que as linhas são dimensionadas com base no conteúdo de linhas.</span><span class="sxs-lookup"><span data-stu-id="cf11b-223">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="cf11b-224">O padrão <xref:System.Windows.Controls.RowDefinition.Height%2A> é <xref:System.Windows.GridUnitType.Star> dimensionamento, o que significa que a altura da linha é uma proporção ponderada do espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="cf11b-224">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="cf11b-225">Por exemplo, se duas linhas tiverem uma <xref:System.Windows.Controls.RowDefinition.Height%2A> de "\*", cada um deles tem uma altura que será a metade do espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="cf11b-225">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="cf11b-226">Seu <xref:System.Windows.Controls.Grid> agora deve conter o seguinte XAML:</span><span class="sxs-lookup"><span data-stu-id="cf11b-226">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="cf11b-227">Adicionar controles</span><span class="sxs-lookup"><span data-stu-id="cf11b-227">Add controls</span></span>

<span data-ttu-id="cf11b-228">Nesta seção, você atualizará a página inicial da interface do usuário para mostrar uma lista de pessoas, em que você selecione uma pessoa para exibir seus relatórios de despesas.</span><span class="sxs-lookup"><span data-stu-id="cf11b-228">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="cf11b-229">Os controles são objetos da interface do usuário que permitem aos usuários interagir com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf11b-229">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="cf11b-230">Para obter mais informações, consulte [Controles](../controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="cf11b-230">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="cf11b-231">Para criar essa interface do usuário, você adicionará os seguintes elementos para *`ExpenseItHome.xaml`*:</span><span class="sxs-lookup"><span data-stu-id="cf11b-231">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="cf11b-232">Um <xref:System.Windows.Controls.ListBox> (para obter a lista de pessoas).</span><span class="sxs-lookup"><span data-stu-id="cf11b-232">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="cf11b-233">Um <xref:System.Windows.Controls.Label> (para o cabeçalho da lista).</span><span class="sxs-lookup"><span data-stu-id="cf11b-233">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="cf11b-234">Um <xref:System.Windows.Controls.Button> (para clicar para exibir o relatório de despesas para a pessoa que está selecionada na lista).</span><span class="sxs-lookup"><span data-stu-id="cf11b-234">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="cf11b-235">Cada controle é colocado em uma linha do <xref:System.Windows.Controls.Grid> definindo o <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> propriedade anexada.</span><span class="sxs-lookup"><span data-stu-id="cf11b-235">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="cf11b-236">Para obter mais informações sobre propriedades anexadas, consulte [visão geral das propriedades anexadas](../advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cf11b-236">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="cf11b-237">Na *`ExpenseItHome.xaml`*, adicione o seguinte XAML em algum lugar entre o <xref:System.Windows.Controls.Grid> marcas:</span><span class="sxs-lookup"><span data-stu-id="cf11b-237">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="cf11b-238">Você também pode criar os controles arrastando-os do **caixa de ferramentas** janela para a janela de design e, em seguida, definir suas propriedades na **propriedades** janela.</span><span class="sxs-lookup"><span data-stu-id="cf11b-238">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="cf11b-239">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf11b-239">Build and run the application.</span></span>

    <span data-ttu-id="cf11b-240">A ilustração a seguir mostra os controles que você criou:</span><span class="sxs-lookup"><span data-stu-id="cf11b-240">The following illustration shows the controls you created:</span></span>

    ![Captura de tela de exemplo de ExpenseIt](./media/gettingstartedfigure2.png)

3. <span data-ttu-id="cf11b-242">Feche o aplicativo para retornar ao Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cf11b-242">Close the application to return to Visual Studio.</span></span>

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="cf11b-243">Adicionar uma imagem e um título</span><span class="sxs-lookup"><span data-stu-id="cf11b-243">Add an image and a title</span></span>

<span data-ttu-id="cf11b-244">Nesta seção, você vai atualizar a home page da interface do usuário com uma imagem e um título de página.</span><span class="sxs-lookup"><span data-stu-id="cf11b-244">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="cf11b-245">Na *`ExpenseItHome.xaml`*, adicione outra coluna para o <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> fixa <xref:System.Windows.Controls.ColumnDefinition.Width%2A> de 230 pixels:</span><span class="sxs-lookup"><span data-stu-id="cf11b-245">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. <span data-ttu-id="cf11b-246">Adicionar outra linha para o <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, para um total de quatro linhas:</span><span class="sxs-lookup"><span data-stu-id="cf11b-246">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. <span data-ttu-id="cf11b-247">Mova os controles para a segunda coluna, definindo o <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> propriedade como 1 em cada um dos três controles (da borda, ListBox e botão).</span><span class="sxs-lookup"><span data-stu-id="cf11b-247">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="cf11b-248">Mova cada controle uma linha para baixo ao incrementar sua <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> valor 1 para cada um dos três controles (da borda, ListBox e botão) e para o elemento Border.</span><span class="sxs-lookup"><span data-stu-id="cf11b-248">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="cf11b-249">O XAML para os três controles agora é semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="cf11b-249">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="cf11b-250">Definir a <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> propriedade para o *watermark* arquivo de imagem, adicionando o XAML a seguir em qualquer lugar entre os `<Grid>` e `</Grid>` marcas:</span><span class="sxs-lookup"><span data-stu-id="cf11b-250">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="cf11b-251">Antes do <xref:System.Windows.Controls.Border> elemento, adicionar um <xref:System.Windows.Controls.Label> com o conteúdo "Exibir relatório de despesas".</span><span class="sxs-lookup"><span data-stu-id="cf11b-251">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="cf11b-252">Esse rótulo é o título da página.</span><span class="sxs-lookup"><span data-stu-id="cf11b-252">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="cf11b-253">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf11b-253">Build and run the application.</span></span>

<span data-ttu-id="cf11b-254">A ilustração a seguir mostra os resultados de que você acabou de adicionar:</span><span class="sxs-lookup"><span data-stu-id="cf11b-254">The following illustration shows the results of what you just added:</span></span>

![Captura de tela de exemplo de ExpenseIt](./media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="cf11b-256">Adicionar código para manipular eventos</span><span class="sxs-lookup"><span data-stu-id="cf11b-256">Add code to handle events</span></span>

1. <span data-ttu-id="cf11b-257">Na *`ExpenseItHome.xaml`*, adicione uma <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos para o <xref:System.Windows.Controls.Button> elemento.</span><span class="sxs-lookup"><span data-stu-id="cf11b-257">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="cf11b-258">Para obter mais informações, confira [Como: Crie um manipulador de eventos simples](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cf11b-258">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="cf11b-259">Abra *`ExpenseItHome.xaml.vb`* ou *`ExpenseItHome.xaml.cs`*.</span><span class="sxs-lookup"><span data-stu-id="cf11b-259">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="cf11b-260">Adicione o seguinte código para o `ExpenseItHome` classe para adicionar um botão de manipulador de eventos de clique.</span><span class="sxs-lookup"><span data-stu-id="cf11b-260">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="cf11b-261">O manipulador de eventos abre o **ExpenseReportPage** página.</span><span class="sxs-lookup"><span data-stu-id="cf11b-261">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="cf11b-262">Criar a interface do usuário para ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="cf11b-262">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="cf11b-263">*ExpenseReportPage. XAML* exibe o relatório de despesas para a pessoa que está selecionada na **`ExpenseItHome`** página.</span><span class="sxs-lookup"><span data-stu-id="cf11b-263">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="cf11b-264">Nesta seção, você criará a interface do usuário para **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="cf11b-264">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="cf11b-265">Você também adicionará o plano de fundo e cores de preenchimento para os vários elementos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="cf11b-265">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="cf11b-266">Abra *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="cf11b-266">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="cf11b-267">Adicione o seguinte XAML entre o <xref:System.Windows.Controls.Grid> marcas:</span><span class="sxs-lookup"><span data-stu-id="cf11b-267">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="cf11b-268">Essa interface do usuário é semelhante à *`ExpenseItHome.xaml`*, exceto os dados do relatório são exibidos em um <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="cf11b-268">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="cf11b-269">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf11b-269">Build and run the application.</span></span>

4. <span data-ttu-id="cf11b-270">Selecione o **exibição** botão.</span><span class="sxs-lookup"><span data-stu-id="cf11b-270">Select the **View** button.</span></span>

    <span data-ttu-id="cf11b-271">A página de relatório de despesas é exibida.</span><span class="sxs-lookup"><span data-stu-id="cf11b-271">The expense report page appears.</span></span> <span data-ttu-id="cf11b-272">Além disso, observe que o botão de navegação regressiva está habilitado.</span><span class="sxs-lookup"><span data-stu-id="cf11b-272">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="cf11b-273">A ilustração a seguir mostra os elementos de interface do usuário adicionados ao *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="cf11b-273">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![Captura de tela de exemplo de ExpenseIt](./media/gettingstartedfigure4.png)

## <a name="style-controls"></a><span data-ttu-id="cf11b-275">Controles de estilo</span><span class="sxs-lookup"><span data-stu-id="cf11b-275">Style controls</span></span>

<span data-ttu-id="cf11b-276">A aparência de vários elementos geralmente é o mesmo para todos os elementos do mesmo tipo em uma interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="cf11b-276">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="cf11b-277">Interface do usuário usa [estilos](../controls/styling-and-templating.md) para fazer com que as aparências reutilizáveis entre vários elementos.</span><span class="sxs-lookup"><span data-stu-id="cf11b-277">UI uses [styles](../controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="cf11b-278">A capacidade de reutilização dos estilos ajuda a simplificar o gerenciamento e a criação de XAML.</span><span class="sxs-lookup"><span data-stu-id="cf11b-278">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="cf11b-279">Esta seção substitui os atributos por elemento que foram definidos nas etapas anteriores com estilos.</span><span class="sxs-lookup"><span data-stu-id="cf11b-279">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="cf11b-280">Abra *Application. XAML* ou *App. XAML*.</span><span class="sxs-lookup"><span data-stu-id="cf11b-280">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="cf11b-281">Adicione o seguinte XAML entre o <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> marcas:</span><span class="sxs-lookup"><span data-stu-id="cf11b-281">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="cf11b-282">Esse XAML adiciona os seguintes estilos:</span><span class="sxs-lookup"><span data-stu-id="cf11b-282">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="cf11b-283">`headerTextStyle`: Para formatar o título da página <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="cf11b-283">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="cf11b-284">`labelStyle`: Para formatar o <xref:System.Windows.Controls.Label> controles.</span><span class="sxs-lookup"><span data-stu-id="cf11b-284">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="cf11b-285">`columnHeaderStyle`: Para formatar o <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="cf11b-285">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="cf11b-286">`listHeaderStyle`: Para formatar o cabeçalho da lista <xref:System.Windows.Controls.Border> controles.</span><span class="sxs-lookup"><span data-stu-id="cf11b-286">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="cf11b-287">`listHeaderTextStyle`: Para formatar o cabeçalho da lista <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="cf11b-287">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="cf11b-288">`buttonStyle`: Para formatar a <xref:System.Windows.Controls.Button> em `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="cf11b-288">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="cf11b-289">Observe que os estilos são recursos e seus filhos a <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> elemento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf11b-289">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="cf11b-290">Nesse local, os estilos são aplicados a todos os elementos em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf11b-290">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="cf11b-291">Para obter um exemplo do uso de recursos em um aplicativo .NET, consulte [usar recursos do aplicativo](../advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="cf11b-291">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="cf11b-292">Na *`ExpenseItHome.xaml`*, substitua tudo entre os <xref:System.Windows.Controls.Grid> elementos com o XAML a seguir:</span><span class="sxs-lookup"><span data-stu-id="cf11b-292">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="cf11b-293">As propriedades como <xref:System.Windows.VerticalAlignment> e <xref:System.Windows.Media.FontFamily> que definem a aparência de cada controle são removidas e substituídas ao aplicar os estilos.</span><span class="sxs-lookup"><span data-stu-id="cf11b-293">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="cf11b-294">Por exemplo, o `headerTextStyle` é aplicado a "Exibir relatório de despesas" <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="cf11b-294">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="cf11b-295">Abra *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="cf11b-295">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="cf11b-296">Substitua tudo entre os <xref:System.Windows.Controls.Grid> elementos com o XAML a seguir:</span><span class="sxs-lookup"><span data-stu-id="cf11b-296">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="cf11b-297">Esse XAML adiciona estilos para o <xref:System.Windows.Controls.Label> e <xref:System.Windows.Controls.Border> elementos.</span><span class="sxs-lookup"><span data-stu-id="cf11b-297">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="cf11b-298">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf11b-298">Build and run the application.</span></span> <span data-ttu-id="cf11b-299">A aparência da janela é o mesmo que anteriormente.</span><span class="sxs-lookup"><span data-stu-id="cf11b-299">The window appearance is the same as previously.</span></span>

    ![Captura de tela de exemplo de ExpenseIt](./media/gettingstartedfigure4.png)

7. <span data-ttu-id="cf11b-301">Feche o aplicativo para retornar ao Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cf11b-301">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="cf11b-302">Associar dados a um controle</span><span class="sxs-lookup"><span data-stu-id="cf11b-302">Bind data to a control</span></span>

<span data-ttu-id="cf11b-303">Nesta seção, você criará os dados XML que estão associados a vários controles.</span><span class="sxs-lookup"><span data-stu-id="cf11b-303">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="cf11b-304">Na *`ExpenseItHome.xaml`*, após a abertura <xref:System.Windows.Controls.Grid> elemento, adicione o XAML a seguir para criar um <xref:System.Windows.Data.XmlDataProvider> que contém os dados para cada pessoa:</span><span class="sxs-lookup"><span data-stu-id="cf11b-304">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="cf11b-305">Os dados são criados como um <xref:System.Windows.Controls.Grid> recursos.</span><span class="sxs-lookup"><span data-stu-id="cf11b-305">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="cf11b-306">Normalmente, esses dados seriam carregados como um arquivo, mas para simplificar os dados são adicionados embutidos.</span><span class="sxs-lookup"><span data-stu-id="cf11b-306">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="cf11b-307">Dentro de `<Grid.Resources>` elemento, adicione o seguinte `<xref:System.Windows.DataTemplate>` elemento, que define como exibir os dados no <xref:System.Windows.Controls.ListBox>, após o `<XmlDataProvider>` elemento:</span><span class="sxs-lookup"><span data-stu-id="cf11b-307">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="cf11b-308">Para obter mais informações sobre modelos de dados, consulte [visão geral de modelagem de dados](../data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cf11b-308">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="cf11b-309">Substitua a <xref:System.Windows.Controls.ListBox> com o XAML a seguir:</span><span class="sxs-lookup"><span data-stu-id="cf11b-309">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="cf11b-310">Esse XAML associa a <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade do <xref:System.Windows.Controls.ListBox> à fonte de dados e aplica o modelo de dados como o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="cf11b-310">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="cf11b-311">Conectar dados aos controles</span><span class="sxs-lookup"><span data-stu-id="cf11b-311">Connect data to controls</span></span>

<span data-ttu-id="cf11b-312">Em seguida, você adicionará código para recuperar o nome que está selecionado na **`ExpenseItHome`** da página e passá-lo para o construtor da **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="cf11b-312">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="cf11b-313">**ExpenseReportPage** define seu contexto de dados com o item passado, que é o que os controles definidos no *ExpenseReportPage* associar a.</span><span class="sxs-lookup"><span data-stu-id="cf11b-313">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="cf11b-314">Abra *ExpenseReportPage.xaml.vb* ou *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="cf11b-314">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="cf11b-315">Adicione um construtor que utiliza um objeto para passar os dados do relatório de despesas da pessoa selecionada.</span><span class="sxs-lookup"><span data-stu-id="cf11b-315">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="cf11b-316">Abra *`ExpenseItHome.xaml.vb`* ou *`ExpenseItHome.xaml.cs`*.</span><span class="sxs-lookup"><span data-stu-id="cf11b-316">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="cf11b-317">Alterar o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos para chamar o novo construtor passando os dados de relatório de despesas da pessoa selecionada.</span><span class="sxs-lookup"><span data-stu-id="cf11b-317">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="cf11b-318">Dados de estilo com modelos de dados</span><span class="sxs-lookup"><span data-stu-id="cf11b-318">Style data with data templates</span></span>

<span data-ttu-id="cf11b-319">Nesta seção, você atualizará a interface do usuário para cada item nas listas de associação de dados usando modelos de dados.</span><span class="sxs-lookup"><span data-stu-id="cf11b-319">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="cf11b-320">Abra *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="cf11b-320">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="cf11b-321">Associar o conteúdo do "Nome" e "Departamento" <xref:System.Windows.Controls.Label> propriedade da fonte de elementos para os dados apropriados.</span><span class="sxs-lookup"><span data-stu-id="cf11b-321">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="cf11b-322">Para obter mais informações sobre associação de dados, consulte [visão geral da vinculação de dados](../data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cf11b-322">For more information about data binding, see [Data binding overview](../data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="cf11b-323">Após a abertura <xref:System.Windows.Controls.Grid> elemento, adicione os seguintes modelos de dados, que definem como exibir os dados de relatório de despesas:</span><span class="sxs-lookup"><span data-stu-id="cf11b-323">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="cf11b-324">Substitua os <xref:System.Windows.Controls.DataGridTextColumn> elementos com <xref:System.Windows.Controls.DataGridTemplateColumn> sob o <xref:System.Windows.Controls.DataGrid> elemento e aplicar os modelos a eles.</span><span class="sxs-lookup"><span data-stu-id="cf11b-324">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="cf11b-325">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf11b-325">Build and run the application.</span></span>

6. <span data-ttu-id="cf11b-326">Selecione uma pessoa e, em seguida, selecione a **exibição** botão.</span><span class="sxs-lookup"><span data-stu-id="cf11b-326">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="cf11b-327">A ilustração a seguir mostra as duas páginas do `ExpenseIt` aplicativo com controles, layout, estilos, vinculação de dados e modelos de dados aplicados:</span><span class="sxs-lookup"><span data-stu-id="cf11b-327">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Capturas de tela de exemplo de ExpenseIt](./media/gettingstartedfigure5.png)

> [!NOTE]
> <span data-ttu-id="cf11b-329">Este exemplo demonstra um recurso específico do WPF e não segue todas as práticas recomendadas para coisas como segurança, localização e acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="cf11b-329">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="cf11b-330">Para obter uma cobertura abrangente do WPF e as práticas recomendadas de desenvolvimento de aplicativo .NET, consulte os tópicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="cf11b-330">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="cf11b-331">Acessibilidade</span><span class="sxs-lookup"><span data-stu-id="cf11b-331">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
>
> - [<span data-ttu-id="cf11b-332">Segurança</span><span class="sxs-lookup"><span data-stu-id="cf11b-332">Security</span></span>](../security-wpf.md)
>
> - [<span data-ttu-id="cf11b-333">Globalização e localização do WPF</span><span class="sxs-lookup"><span data-stu-id="cf11b-333">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
>
> - [<span data-ttu-id="cf11b-334">Desempenho do WPF</span><span class="sxs-lookup"><span data-stu-id="cf11b-334">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="cf11b-335">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="cf11b-335">Next steps</span></span>

<span data-ttu-id="cf11b-336">Neste passo a passo, você aprendeu várias técnicas para a criação de uma interface do usuário usando o Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="cf11b-336">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="cf11b-337">Agora você deve ter uma compreensão básica dos blocos de construção de um aplicativo .NET de associação de dados.</span><span class="sxs-lookup"><span data-stu-id="cf11b-337">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="cf11b-338">Para obter mais informações sobre os modelos de arquitetura e programação do WPF, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="cf11b-338">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="cf11b-339">Arquitetura do WPF</span><span class="sxs-lookup"><span data-stu-id="cf11b-339">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="cf11b-340">Visão geral do XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="cf11b-340">XAML overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="cf11b-341">Visão geral das propriedades de dependência</span><span class="sxs-lookup"><span data-stu-id="cf11b-341">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="cf11b-342">Layout</span><span class="sxs-lookup"><span data-stu-id="cf11b-342">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="cf11b-343">Para obter mais informações sobre como criar aplicativos, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="cf11b-343">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="cf11b-344">Desenvolvimento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="cf11b-344">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="cf11b-345">Controles</span><span class="sxs-lookup"><span data-stu-id="cf11b-345">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="cf11b-346">Visão geral da associação de dados</span><span class="sxs-lookup"><span data-stu-id="cf11b-346">Data binding overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="cf11b-347">Elementos gráficos e multimídia</span><span class="sxs-lookup"><span data-stu-id="cf11b-347">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="cf11b-348">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="cf11b-348">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="cf11b-349">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf11b-349">See also</span></span>

- [<span data-ttu-id="cf11b-350">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="cf11b-350">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="cf11b-351">Visão geral de modelagem de dados</span><span class="sxs-lookup"><span data-stu-id="cf11b-351">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="cf11b-352">Compilar um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="cf11b-352">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="cf11b-353">Estilos e modelos</span><span class="sxs-lookup"><span data-stu-id="cf11b-353">Styles and templates</span></span>](../controls/styles-and-templates.md)
