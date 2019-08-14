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
ms.openlocfilehash: 9d5b5b8a479efd3918dc23616aa331cc07a901ac
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972193"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="142de-102">Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF</span><span class="sxs-lookup"><span data-stu-id="142de-102">Walkthrough: My first WPF desktop application</span></span>

<span data-ttu-id="142de-103">Este artigo mostra como desenvolver um aplicativo de área de trabalho Windows Presentation Foundation (WPF) que inclui os elementos comuns à maioria dos aplicativos WPF: Marcação de Extensible Application Markup Language (XAML), code-behind, definições de aplicativo, controles, layout, vinculação de dados e estilos.</span><span class="sxs-lookup"><span data-stu-id="142de-103">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="142de-104">Para desenvolver o aplicativo, você usará o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="142de-104">To develop the application, you'll use Visual Studio.</span></span> 

<span data-ttu-id="142de-105">Este passo a passos inclui as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="142de-105">This walkthrough includes the following steps:</span></span>

- <span data-ttu-id="142de-106">Use o XAML para criar a aparência da interface do usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="142de-106">Use XAML to design the appearance of the application's user interface (UI).</span></span>

- <span data-ttu-id="142de-107">Escreva o código para criar o comportamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="142de-107">Write code to build the application's behavior.</span></span>

- <span data-ttu-id="142de-108">Crie uma definição de aplicativo para gerenciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="142de-108">Create an application definition to manage the application.</span></span>

- <span data-ttu-id="142de-109">Adicione controles e crie o layout para compor a interface do usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="142de-109">Add controls and create the layout to compose the application UI.</span></span>

- <span data-ttu-id="142de-110">Crie estilos para uma aparência consistente em toda a interface do usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="142de-110">Create styles for a consistent appearance throughout the application's UI.</span></span>

- <span data-ttu-id="142de-111">Associe a interface do usuário aos dados para popular a interface do usuário de dados e manter os dados e a interface do usuário sincronizados.</span><span class="sxs-lookup"><span data-stu-id="142de-111">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="142de-112">Ao final do passo a passo, você terá criado um aplicativo autônomo do Windows que permite aos usuários exibir relatórios de despesas para as pessoas selecionadas.</span><span class="sxs-lookup"><span data-stu-id="142de-112">By the end of the walkthrough, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="142de-113">O aplicativo é composto por várias páginas do WPF que são hospedadas em uma janela em estilo de navegador.</span><span class="sxs-lookup"><span data-stu-id="142de-113">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="142de-114">O código de exemplo que é usado para criar este tutorial está disponível para os Visual Basic C# e no [exemplo de código de aplicativo WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span><span class="sxs-lookup"><span data-stu-id="142de-114">The sample code that is used to build this walkthrough is available for both Visual Basic and C# at [Walkthrough WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="142de-115">Você pode alternar o idioma de código do código de exemplo C# entre e Visual Basic usando a **\< />** lista suspensa no lado superior direito deste artigo.</span><span class="sxs-lookup"><span data-stu-id="142de-115">You can toggle the code language of the sample code between C# and Visual Basic by using the **\</>** drop-down on the upper right side of this article.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="142de-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="142de-116">Prerequisites</span></span>

- <span data-ttu-id="142de-117">Visual Studio 2017 ou posterior (este artigo usa o Visual Studio 2019)</span><span class="sxs-lookup"><span data-stu-id="142de-117">Visual Studio 2017 or later (this article uses Visual Studio 2019)</span></span>

   <span data-ttu-id="142de-118">Para obter mais informações sobre como instalar a versão mais recente do Visual Studio, consulte [instalar o Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="142de-118">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="142de-119">Criar o projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="142de-119">Create the application project</span></span>

<span data-ttu-id="142de-120">A primeira etapa é criar a infraestrutura do aplicativo, que inclui uma definição de aplicativo, duas páginas e uma imagem.</span><span class="sxs-lookup"><span data-stu-id="142de-120">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="142de-121">Crie um novo projeto de aplicativo WPF em Visual Basic ou C# Visual **`ExpenseIt`** chamado:</span><span class="sxs-lookup"><span data-stu-id="142de-121">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="142de-122">Abra o Visual Studio e selecione **criar um novo projeto** no menu **introdução** .</span><span class="sxs-lookup"><span data-stu-id="142de-122">Open Visual Studio and select **Create a new project** under the **Get started** menu.</span></span>

      <span data-ttu-id="142de-123">A caixa de diálogo **criar um novo projeto** é aberta.</span><span class="sxs-lookup"><span data-stu-id="142de-123">The **Create a new project** dialog opens.</span></span>

   2. <span data-ttu-id="142de-124">Na lista suspensa **idioma** , selecione um **C#** ou **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="142de-124">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>
      
   3. <span data-ttu-id="142de-125">Selecione o modelo **aplicativo do WPF (.NET Framework)** e, em seguida, selecione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="142de-125">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span> 
     
      ![Caixa de diálogo criar um novo projeto](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)
    
      <span data-ttu-id="142de-127">A caixa de diálogo **configurar seu novo projeto** é aberta.</span><span class="sxs-lookup"><span data-stu-id="142de-127">The **Configure your new project** dialog opens.</span></span>

   4. <span data-ttu-id="142de-128">Insira o nome **`ExpenseIt`** do projeto e, em seguida, selecione **criar**.</span><span class="sxs-lookup"><span data-stu-id="142de-128">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      ![Caixa de diálogo Configurar um novo projeto](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      <span data-ttu-id="142de-130">O Visual Studio cria o projeto e abre o designer para a janela do aplicativo padrão chamada **MainWindow. XAML**.</span><span class="sxs-lookup"><span data-stu-id="142de-130">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="142de-131">Abra *Application. XAML* (Visual Basic) ou *app. XAML* (C#).</span><span class="sxs-lookup"><span data-stu-id="142de-131">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="142de-132">Esse arquivo XAML define um aplicativo WPF e qualquer recurso de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="142de-132">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="142de-133">Você também usa esse arquivo para especificar a interface do usuário, nesse caso *MainWindow. XAML*, que mostra automaticamente quando o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="142de-133">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="142de-134">O XAML deve ser semelhante ao seguinte no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="142de-134">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="142de-135">E semelhante ao seguinte no C#:</span><span class="sxs-lookup"><span data-stu-id="142de-135">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="142de-136">Abra *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="142de-136">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="142de-137">Esse arquivo XAML é a janela principal do seu aplicativo e exibe o conteúdo criado em páginas.</span><span class="sxs-lookup"><span data-stu-id="142de-137">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="142de-138">A <xref:System.Windows.Window> classe define as propriedades de uma janela, como seu título, tamanho ou ícone, e manipula eventos, como fechar ou ocultar.</span><span class="sxs-lookup"><span data-stu-id="142de-138">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="142de-139">Altere o <xref:System.Windows.Window> elemento <xref:System.Windows.Navigation.NavigationWindow>para a, conforme mostrado no XAML a seguir:</span><span class="sxs-lookup"><span data-stu-id="142de-139">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="142de-140">Esse aplicativo navega para um conteúdo diferente, dependendo da entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="142de-140">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="142de-141">É por isso que a <xref:System.Windows.Window> principal precisa ser alterada para um <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="142de-141">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="142de-142"><xref:System.Windows.Navigation.NavigationWindow>herda todas as propriedades de <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="142de-142"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="142de-143">O <xref:System.Windows.Navigation.NavigationWindow> elemento no arquivo XAML cria uma instância <xref:System.Windows.Navigation.NavigationWindow> da classe.</span><span class="sxs-lookup"><span data-stu-id="142de-143">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="142de-144">Para obter mais informações, consulte [visão geral de navegação](../app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="142de-144">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="142de-145">Remova os <xref:System.Windows.Controls.Grid> elementos entre as <xref:System.Windows.Navigation.NavigationWindow> marcas.</span><span class="sxs-lookup"><span data-stu-id="142de-145">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="142de-146">Altere as seguintes propriedades no código XAML para o <xref:System.Windows.Navigation.NavigationWindow> elemento:</span><span class="sxs-lookup"><span data-stu-id="142de-146">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="142de-147">Defina a <xref:System.Windows.Window.Title%2A> Propriedade como "`ExpenseIt`".</span><span class="sxs-lookup"><span data-stu-id="142de-147">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="142de-148">Defina a <xref:System.Windows.FrameworkElement.Height%2A> Propriedade como 350 pixels.</span><span class="sxs-lookup"><span data-stu-id="142de-148">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="142de-149">Defina a <xref:System.Windows.FrameworkElement.Width%2A> Propriedade como 500 pixels.</span><span class="sxs-lookup"><span data-stu-id="142de-149">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="142de-150">O XAML deve ser semelhante ao seguinte por Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="142de-150">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="142de-151">E semelhante ao seguinte para C#:</span><span class="sxs-lookup"><span data-stu-id="142de-151">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="142de-152">Abra *MainWindow. XAML. vb* ou *MainWindow.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="142de-152">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="142de-153">Esse arquivo é um arquivo code-behind que contém o código para manipular os eventos declarados em *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="142de-153">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="142de-154">Esse arquivo contém uma classe parcial para a janela definida no XAML.</span><span class="sxs-lookup"><span data-stu-id="142de-154">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="142de-155">Se você estiver usando C#o, altere `MainWindow` a classe da <xref:System.Windows.Navigation.NavigationWindow>qual derivar.</span><span class="sxs-lookup"><span data-stu-id="142de-155">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="142de-156">(Em Visual Basic, isso ocorre automaticamente quando você altera a janela em XAML.) O C# código agora deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="142de-156">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="142de-157">Adicionar arquivos ao aplicativo</span><span class="sxs-lookup"><span data-stu-id="142de-157">Add files to the application</span></span>

<span data-ttu-id="142de-158">Nesta seção, você adicionará duas páginas e uma imagem ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="142de-158">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="142de-159">Adicione uma nova página ao projeto e nomeie- *`ExpenseItHome.xaml`* a:</span><span class="sxs-lookup"><span data-stu-id="142de-159">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="142de-160">Em **Gerenciador de soluções**, clique com o botão direito **`ExpenseIt`** do mouse no nó do projeto e escolha **Adicionar** > **página**.</span><span class="sxs-lookup"><span data-stu-id="142de-160">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="142de-161">Na caixa de diálogo **Adicionar novo item** , o modelo **página (WPF)** já está selecionado.</span><span class="sxs-lookup"><span data-stu-id="142de-161">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="142de-162">Insira o nome **`ExpenseItHome`** e, em seguida, selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="142de-162">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="142de-163">Esta página é a primeira página que é exibida quando o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="142de-163">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="142de-164">Ele mostrará uma lista de pessoas a serem selecionadas, para mostrar um relatório de despesas para o.</span><span class="sxs-lookup"><span data-stu-id="142de-164">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="142de-165">Abra *`ExpenseItHome.xaml`* o.</span><span class="sxs-lookup"><span data-stu-id="142de-165">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="142de-166">Defina como "`ExpenseIt - Home`". <xref:System.Windows.Controls.Page.Title%2A></span><span class="sxs-lookup"><span data-stu-id="142de-166">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="142de-167">Defina os `DesignHeight` valores `DesignWidth` de elemento e como 300 pixels.</span><span class="sxs-lookup"><span data-stu-id="142de-167">Set the `DesignHeight` and `DesignWidth` element values to 300 pixels.</span></span>

    <span data-ttu-id="142de-168">O XAML agora aparece da seguinte maneira para Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="142de-168">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="142de-169">E semelhante ao seguinte para C#:</span><span class="sxs-lookup"><span data-stu-id="142de-169">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="142de-170">Abra *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="142de-170">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="142de-171">Adicione uma <xref:System.Windows.Navigation.NavigationWindow.Source%2A> propriedade <xref:System.Windows.Navigation.NavigationWindow> ao elemento e defina-a como "`ExpenseItHome.xaml`".</span><span class="sxs-lookup"><span data-stu-id="142de-171">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="142de-172">Isso define *`ExpenseItHome.xaml`* como a primeira página aberta quando o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="142de-172">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span> 

    <span data-ttu-id="142de-173">Exemplo de XAML no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="142de-173">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="142de-174">E, em C#:</span><span class="sxs-lookup"><span data-stu-id="142de-174">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="142de-175">Você também pode definir a propriedade **Source** na categoria **Miscellaneous** da janela **Propriedades** .</span><span class="sxs-lookup"><span data-stu-id="142de-175">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Propriedade Source no janela Propriedades](./media/properties-source.png)

1. <span data-ttu-id="142de-177">Adicione outra nova página do WPF ao projeto e nomeie-o como *ExpenseReportPage. XAML*::</span><span class="sxs-lookup"><span data-stu-id="142de-177">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="142de-178">Em **Gerenciador de soluções**, clique com o botão direito **`ExpenseIt`** do mouse no nó do projeto e escolha **Adicionar** > **página**.</span><span class="sxs-lookup"><span data-stu-id="142de-178">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="142de-179">Na caixa de diálogo **Adicionar novo item** , selecione o modelo **página (WPF)** .</span><span class="sxs-lookup"><span data-stu-id="142de-179">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="142de-180">Insira o nome **ExpenseReportPage**e, em seguida, selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="142de-180">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="142de-181">Esta página mostrará o relatório de despesas para a pessoa que está selecionada na **`ExpenseItHome`** página.</span><span class="sxs-lookup"><span data-stu-id="142de-181">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="142de-182">Abra *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="142de-182">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="142de-183">Defina como "`ExpenseIt - View Expense`". <xref:System.Windows.Controls.Page.Title%2A></span><span class="sxs-lookup"><span data-stu-id="142de-183">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="142de-184">Defina os `DesignHeight` valores `DesignWidth` de elemento e como 300 pixels.</span><span class="sxs-lookup"><span data-stu-id="142de-184">Set the `DesignHeight` and `DesignWidth` element values to 300 pixels.</span></span>

    <span data-ttu-id="142de-185">*ExpenseReportPage. XAML* agora é semelhante ao seguinte no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="142de-185">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="142de-186">E semelhante ao seguinte no C#:</span><span class="sxs-lookup"><span data-stu-id="142de-186">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="142de-187">Abra *ExpenseItHome. XAML. vb* e *ExpenseReportPage. XAML. vb*ou *ExpenseItHome.XAML.cs* e *ExpenseReportPage.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="142de-187">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="142de-188">Quando você cria um novo arquivo de paginação, o Visual Studio cria automaticamente seu arquivo *code-behind* .</span><span class="sxs-lookup"><span data-stu-id="142de-188">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="142de-189">Esses arquivos code-behind manipulam a lógica para responder à entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="142de-189">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="142de-190">Seu código deve ser semelhante ao seguinte para **`ExpenseItHome`** :</span><span class="sxs-lookup"><span data-stu-id="142de-190">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="142de-191">E como o seguinte para **ExpenseReportPage**:</span><span class="sxs-lookup"><span data-stu-id="142de-191">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="142de-192">Adicione uma imagem chamada *watermark. png* ao projeto.</span><span class="sxs-lookup"><span data-stu-id="142de-192">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="142de-193">Você pode criar sua própria imagem, copiar o arquivo do código de exemplo ou obtê-lo [aqui](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png).</span><span class="sxs-lookup"><span data-stu-id="142de-193">You can create your own image, copy the file from the sample code, or get it [here](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png).</span></span>

    1. <span data-ttu-id="142de-194">Clique com o botão direito do mouse no nó do projeto e selecione **Adicionar** > **Item existente**ou pressione **Shift**+**ALT**+**A**.</span><span class="sxs-lookup"><span data-stu-id="142de-194">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="142de-195">Na caixa de diálogo **Adicionar item existente** , defina o filtro de arquivo como **todos os** arquivos ou **arquivos de imagem**, navegue até o arquivo de imagem que deseja usar e, em seguida, selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="142de-195">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="142de-196">Compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="142de-196">Build and run the application</span></span>

1. <span data-ttu-id="142de-197">Para compilar e executar o aplicativo, pressione **F5** ou selecione **Iniciar Depuração** no menu **depurar** .</span><span class="sxs-lookup"><span data-stu-id="142de-197">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="142de-198">A ilustração a seguir mostra o aplicativo com <xref:System.Windows.Navigation.NavigationWindow> os botões:</span><span class="sxs-lookup"><span data-stu-id="142de-198">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Aplicativo depois de criá-lo e executá-lo.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. <span data-ttu-id="142de-200">Feche o aplicativo para retornar ao Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="142de-200">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="142de-201">Criar o layout</span><span class="sxs-lookup"><span data-stu-id="142de-201">Create the layout</span></span>

<span data-ttu-id="142de-202">O layout fornece uma maneira ordenada de colocar elementos de interface do usuário e também gerencia o tamanho e a posição desses elementos quando uma interface do usuário é redimensionada.</span><span class="sxs-lookup"><span data-stu-id="142de-202">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="142de-203">Normalmente, você cria um layout com um dos seguintes controles de layout:</span><span class="sxs-lookup"><span data-stu-id="142de-203">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="142de-204"><xref:System.Windows.Controls.Canvas>-Define uma área na qual é possível posicionar explicitamente elementos filho usando coordenadas que são relativas à área da tela.</span><span class="sxs-lookup"><span data-stu-id="142de-204"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="142de-205"><xref:System.Windows.Controls.DockPanel>-Define uma área em que é possível organizar elementos filho horizontal ou verticalmente em relação uns aos outros.</span><span class="sxs-lookup"><span data-stu-id="142de-205"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="142de-206"><xref:System.Windows.Controls.Grid>-Define uma área de grade flexível que consiste em colunas e linhas.</span><span class="sxs-lookup"><span data-stu-id="142de-206"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="142de-207"><xref:System.Windows.Controls.StackPanel>-Organiza os elementos filho em uma única linha que pode ser orientada horizontal ou verticalmente.</span><span class="sxs-lookup"><span data-stu-id="142de-207"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="142de-208"><xref:System.Windows.Controls.VirtualizingStackPanel>-Organiza e virtualiza o conteúdo em uma única linha que é orientada horizontal ou verticalmente.</span><span class="sxs-lookup"><span data-stu-id="142de-208"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="142de-209"><xref:System.Windows.Controls.WrapPanel>-Posiciona os elementos filho na posição sequencial da esquerda para a direita, quebrando o conteúdo para a próxima linha na borda da caixa que o contém.</span><span class="sxs-lookup"><span data-stu-id="142de-209"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="142de-210">A ordenação subsequente ocorre sequencialmente de cima para baixo ou da direita para a esquerda, dependendo do valor da Propriedade Orientation.</span><span class="sxs-lookup"><span data-stu-id="142de-210">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="142de-211">Cada um desses controles de layout dá suporte a um tipo específico de layout para seus elementos filho.</span><span class="sxs-lookup"><span data-stu-id="142de-211">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="142de-212">`ExpenseIt`as páginas podem ser redimensionadas e cada página tem elementos que são organizados horizontal e verticalmente junto com outros elementos.</span><span class="sxs-lookup"><span data-stu-id="142de-212">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="142de-213">Neste exemplo, o <xref:System.Windows.Controls.Grid> é usado como elemento de layout para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="142de-213">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="142de-214">Para obter mais informações <xref:System.Windows.Controls.Panel> sobre elementos, consulte [visão geral dos painéis](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="142de-214">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="142de-215">Para obter mais informações sobre layout, consulte [layout](../advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="142de-215">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="142de-216">Nesta seção, você cria uma tabela de coluna única com três linhas e uma margem de 10 pixels adicionando definições de coluna e linha ao <xref:System.Windows.Controls.Grid> no. *`ExpenseItHome.xaml`*</span><span class="sxs-lookup"><span data-stu-id="142de-216">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="142de-217">No *`ExpenseItHome.xaml`* , defina a <xref:System.Windows.FrameworkElement.Margin%2A> Propriedade no <xref:System.Windows.Controls.Grid> elemento como "10, 0, 10, 10", que corresponde às margens esquerda, superior, direita e inferior:</span><span class="sxs-lookup"><span data-stu-id="142de-217">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="142de-218">Você também pode definir os valores de **margem** na janela **Propriedades** , na categoria **layout** :</span><span class="sxs-lookup"><span data-stu-id="142de-218">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Valores de margem no janela Propriedades](./media/properties-margin.png)

2. <span data-ttu-id="142de-220">Adicione o seguinte XAML entre as <xref:System.Windows.Controls.Grid> marcas para criar as definições de linha e coluna:</span><span class="sxs-lookup"><span data-stu-id="142de-220">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="142de-221">O <xref:System.Windows.Controls.RowDefinition.Height%2A> de duas linhas é definido como <xref:System.Windows.GridLength.Auto%2A>, o que significa que as linhas são dimensionadas com base no conteúdo das linhas.</span><span class="sxs-lookup"><span data-stu-id="142de-221">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="142de-222">O padrão <xref:System.Windows.Controls.RowDefinition.Height%2A> é <xref:System.Windows.GridUnitType.Star> o dimensionamento, o que significa que a altura da linha é uma proporção ponderada do espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="142de-222">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="142de-223">Por exemplo, se duas linhas tiverem um <xref:System.Windows.Controls.RowDefinition.Height%2A> de "\*", cada uma terá uma altura que é metade do espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="142de-223">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="142de-224">Agora <xref:System.Windows.Controls.Grid> , o deve conter o seguinte XAML:</span><span class="sxs-lookup"><span data-stu-id="142de-224">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="142de-225">Adicionar controles</span><span class="sxs-lookup"><span data-stu-id="142de-225">Add controls</span></span>

<span data-ttu-id="142de-226">Nesta seção, você atualizará a interface do usuário do home page para mostrar uma lista de pessoas, onde você seleciona uma pessoa para exibir seu relatório de despesas.</span><span class="sxs-lookup"><span data-stu-id="142de-226">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="142de-227">Os controles são objetos da interface do usuário que permitem aos usuários interagir com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="142de-227">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="142de-228">Para obter mais informações, consulte [Controles](../controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="142de-228">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="142de-229">Para criar essa interface do usuário, você adicionará os seguintes *`ExpenseItHome.xaml`* elementos a:</span><span class="sxs-lookup"><span data-stu-id="142de-229">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="142de-230">A <xref:System.Windows.Controls.ListBox> (para a lista de pessoas).</span><span class="sxs-lookup"><span data-stu-id="142de-230">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="142de-231">A <xref:System.Windows.Controls.Label> (para o cabeçalho da lista).</span><span class="sxs-lookup"><span data-stu-id="142de-231">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="142de-232">A <xref:System.Windows.Controls.Button> (para clicar para exibir o relatório de despesas da pessoa que está selecionada na lista).</span><span class="sxs-lookup"><span data-stu-id="142de-232">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="142de-233">Cada controle é colocado em uma linha do <xref:System.Windows.Controls.Grid> definindo a <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> Propriedade anexada.</span><span class="sxs-lookup"><span data-stu-id="142de-233">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="142de-234">Para obter mais informações sobre propriedades anexadas, consulte [visão geral de propriedades anexadas](../advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="142de-234">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="142de-235">No *`ExpenseItHome.xaml`* , adicione o seguinte XAML em algum lugar <xref:System.Windows.Controls.Grid> entre as marcas:</span><span class="sxs-lookup"><span data-stu-id="142de-235">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="142de-236">Você também pode criar os controles arrastando-os da janela **caixa de ferramentas** para a janela de design e, em seguida, definindo suas propriedades na janela **Propriedades** .</span><span class="sxs-lookup"><span data-stu-id="142de-236">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="142de-237">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="142de-237">Build and run the application.</span></span>

    <span data-ttu-id="142de-238">A ilustração a seguir mostra os controles que você criou:</span><span class="sxs-lookup"><span data-stu-id="142de-238">The following illustration shows the controls you created:</span></span>

![Captura de tela de amostra ExpenseIt exibindo uma lista de nomes](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="142de-240">Adicionar uma imagem e um título</span><span class="sxs-lookup"><span data-stu-id="142de-240">Add an image and a title</span></span>

<span data-ttu-id="142de-241">Nesta seção, você atualizará a interface do usuário do home page com uma imagem e um título de página.</span><span class="sxs-lookup"><span data-stu-id="142de-241">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="142de-242">No *`ExpenseItHome.xaml`* , adicione outra coluna <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> ao com um fixo <xref:System.Windows.Controls.ColumnDefinition.Width%2A> de 230 pixels:</span><span class="sxs-lookup"><span data-stu-id="142de-242">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. <span data-ttu-id="142de-243">Adicione outra linha ao <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, para um total de quatro linhas:</span><span class="sxs-lookup"><span data-stu-id="142de-243">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. <span data-ttu-id="142de-244">Mova os controles para a segunda coluna definindo a <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> Propriedade como 1 em cada um dos três controles (Border, ListBox e Button).</span><span class="sxs-lookup"><span data-stu-id="142de-244">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="142de-245">Mova cada controle para baixo em uma linha incrementando <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> seu valor em 1 para cada um dos três controles (Border, ListBox e Button) e para o elemento Border.</span><span class="sxs-lookup"><span data-stu-id="142de-245">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="142de-246">O XAML para os três controles agora é semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="142de-246">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="142de-247">Defina a <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> propriedade para o arquivo de imagem de *marca d' água. png* , adicionando o XAML a `<Grid>` seguir `</Grid>` em qualquer lugar entre as marcas e:</span><span class="sxs-lookup"><span data-stu-id="142de-247">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="142de-248">Antes do <xref:System.Windows.Controls.Border> elemento, adicione um <xref:System.Windows.Controls.Label> com o conteúdo "Exibir relatório de despesas".</span><span class="sxs-lookup"><span data-stu-id="142de-248">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="142de-249">Este rótulo é o título da página.</span><span class="sxs-lookup"><span data-stu-id="142de-249">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="142de-250">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="142de-250">Build and run the application.</span></span>

<span data-ttu-id="142de-251">A ilustração a seguir mostra os resultados do que você acabou de adicionar:</span><span class="sxs-lookup"><span data-stu-id="142de-251">The following illustration shows the results of what you just added:</span></span>

![Captura de tela de amostra ExpenseIt mostrando a nova tela de fundo e o título da página](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="142de-253">Adicionar código para manipular eventos</span><span class="sxs-lookup"><span data-stu-id="142de-253">Add code to handle events</span></span>

1. <span data-ttu-id="142de-254">No *`ExpenseItHome.xaml`* , adicione um <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos ao <xref:System.Windows.Controls.Button> elemento.</span><span class="sxs-lookup"><span data-stu-id="142de-254">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="142de-255">Para obter mais informações, confira [Como: Crie um manipulador](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))de eventos simples.</span><span class="sxs-lookup"><span data-stu-id="142de-255">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="142de-256">Abra *`ExpenseItHome.xaml.vb`* ou *`ExpenseItHome.xaml.cs`* .</span><span class="sxs-lookup"><span data-stu-id="142de-256">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="142de-257">Adicione o código a seguir à `ExpenseItHome` classe para adicionar um manipulador de eventos de clique de botão.</span><span class="sxs-lookup"><span data-stu-id="142de-257">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="142de-258">O manipulador de eventos abre a página **ExpenseReportPage** .</span><span class="sxs-lookup"><span data-stu-id="142de-258">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="142de-259">Criar a interface do usuário para ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="142de-259">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="142de-260">*ExpenseReportPage. XAML* exibe o relatório de despesas da pessoa que está selecionada na **`ExpenseItHome`** página.</span><span class="sxs-lookup"><span data-stu-id="142de-260">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="142de-261">Nesta seção, você criará a interface do usuário para **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="142de-261">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="142de-262">Você também adicionará cores de plano de fundo e preenchimento aos vários elementos da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="142de-262">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="142de-263">Abra *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="142de-263">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="142de-264">Adicione o XAML a seguir entre <xref:System.Windows.Controls.Grid> as marcas:</span><span class="sxs-lookup"><span data-stu-id="142de-264">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="142de-265">Essa interface do usuário é *`ExpenseItHome.xaml`* semelhante a, exceto que os dados do relatório <xref:System.Windows.Controls.DataGrid>são exibidos em um.</span><span class="sxs-lookup"><span data-stu-id="142de-265">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="142de-266">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="142de-266">Build and run the application.</span></span>

4. <span data-ttu-id="142de-267">Selecione o botão **Exibir** .</span><span class="sxs-lookup"><span data-stu-id="142de-267">Select the **View** button.</span></span>

    <span data-ttu-id="142de-268">A página de relatório de despesas é exibida.</span><span class="sxs-lookup"><span data-stu-id="142de-268">The expense report page appears.</span></span> <span data-ttu-id="142de-269">Observe também que o botão de navegação voltar está habilitado.</span><span class="sxs-lookup"><span data-stu-id="142de-269">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="142de-270">A ilustração a seguir mostra os elementos de interface do usuário adicionados a *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="142de-270">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![Captura de tela de amostra ExpenseIt mostrando a interface do usuário recém-criada para o ExpenseReportPage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a><span data-ttu-id="142de-272">Controles de estilo</span><span class="sxs-lookup"><span data-stu-id="142de-272">Style controls</span></span>

<span data-ttu-id="142de-273">A aparência de vários elementos é geralmente a mesma para todos os elementos do mesmo tipo em uma interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="142de-273">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="142de-274">A interface do usuário usa [estilos](../controls/styling-and-templating.md) para fazer com que as aparências sejam reutilizáveis em vários elementos.</span><span class="sxs-lookup"><span data-stu-id="142de-274">UI uses [styles](../controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="142de-275">A reutilização de estilos ajuda a simplificar a criação e o gerenciamento de XAML.</span><span class="sxs-lookup"><span data-stu-id="142de-275">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="142de-276">Esta seção substitui os atributos por elemento que foram definidos nas etapas anteriores com estilos.</span><span class="sxs-lookup"><span data-stu-id="142de-276">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="142de-277">Abra *Application. XAML* ou *app. XAML*.</span><span class="sxs-lookup"><span data-stu-id="142de-277">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="142de-278">Adicione o XAML a seguir entre <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> as marcas:</span><span class="sxs-lookup"><span data-stu-id="142de-278">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="142de-279">Esse XAML adiciona os seguintes estilos:</span><span class="sxs-lookup"><span data-stu-id="142de-279">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="142de-280">`headerTextStyle`: Para formatar o título <xref:System.Windows.Controls.Label>da página.</span><span class="sxs-lookup"><span data-stu-id="142de-280">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="142de-281">`labelStyle`: Para formatar os <xref:System.Windows.Controls.Label> controles.</span><span class="sxs-lookup"><span data-stu-id="142de-281">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="142de-282">`columnHeaderStyle`: Para formatar o <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="142de-282">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="142de-283">`listHeaderStyle`: Para formatar os controles de <xref:System.Windows.Controls.Border> cabeçalho da lista.</span><span class="sxs-lookup"><span data-stu-id="142de-283">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="142de-284">`listHeaderTextStyle`: Para formatar o cabeçalho <xref:System.Windows.Controls.Label>da lista.</span><span class="sxs-lookup"><span data-stu-id="142de-284">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="142de-285">`buttonStyle`: Para formatar o <xref:System.Windows.Controls.Button> em `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="142de-285">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="142de-286">Observe que os estilos são recursos e filhos do <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> elemento Property.</span><span class="sxs-lookup"><span data-stu-id="142de-286">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="142de-287">Nesse local, os estilos são aplicados a todos os elementos em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="142de-287">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="142de-288">Para obter um exemplo de como usar recursos em um aplicativo .NET, consulte [usar recursos do aplicativo](../advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="142de-288">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="142de-289">No *`ExpenseItHome.xaml`* , substitua tudo entre os <xref:System.Windows.Controls.Grid> elementos com o seguinte XAML:</span><span class="sxs-lookup"><span data-stu-id="142de-289">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="142de-290">As propriedades como <xref:System.Windows.VerticalAlignment> e <xref:System.Windows.Media.FontFamily> que definem a aparência de cada controle são removidas e substituídas ao aplicar os estilos.</span><span class="sxs-lookup"><span data-stu-id="142de-290">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="142de-291">Por exemplo, o `headerTextStyle` é aplicado ao "Exibir relatório de despesas" <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="142de-291">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="142de-292">Abra *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="142de-292">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="142de-293">Substitua tudo entre os <xref:System.Windows.Controls.Grid> elementos com o seguinte XAML:</span><span class="sxs-lookup"><span data-stu-id="142de-293">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="142de-294">Esse XAML adiciona estilos aos <xref:System.Windows.Controls.Label> elementos e. <xref:System.Windows.Controls.Border></span><span class="sxs-lookup"><span data-stu-id="142de-294">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="142de-295">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="142de-295">Build and run the application.</span></span> <span data-ttu-id="142de-296">A aparência da janela é a mesma que a anterior.</span><span class="sxs-lookup"><span data-stu-id="142de-296">The window appearance is the same as previously.</span></span>

    ![Captura de tela de amostra ExpenseIt com a mesma aparência da última seção.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. <span data-ttu-id="142de-298">Feche o aplicativo para retornar ao Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="142de-298">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="142de-299">Associar dados a um controle</span><span class="sxs-lookup"><span data-stu-id="142de-299">Bind data to a control</span></span>

<span data-ttu-id="142de-300">Nesta seção, você criará os dados XML que estão associados a vários controles.</span><span class="sxs-lookup"><span data-stu-id="142de-300">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="142de-301">No *`ExpenseItHome.xaml`* , após o elemento <xref:System.Windows.Controls.Grid> de abertura, adicione o seguinte XAML para criar <xref:System.Windows.Data.XmlDataProvider> um que contenha os dados para cada pessoa:</span><span class="sxs-lookup"><span data-stu-id="142de-301">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="142de-302">Os dados são criados como um <xref:System.Windows.Controls.Grid> recurso.</span><span class="sxs-lookup"><span data-stu-id="142de-302">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="142de-303">Normalmente, esses dados seriam carregados como um arquivo, mas, para simplificar, os dados são adicionados embutidos.</span><span class="sxs-lookup"><span data-stu-id="142de-303">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="142de-304">Dentro do `<Grid.Resources>` elemento, adicione o seguinte `<xref:System.Windows.DataTemplate>` elemento, que define como <xref:System.Windows.Controls.ListBox>exibir os dados no, após o `<XmlDataProvider>` elemento:</span><span class="sxs-lookup"><span data-stu-id="142de-304">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="142de-305">Para obter mais informações sobre modelos de dados, consulte [visão geral de modelagem de dados](../data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="142de-305">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="142de-306">Substitua o existente <xref:System.Windows.Controls.ListBox> pelo seguinte XAML:</span><span class="sxs-lookup"><span data-stu-id="142de-306">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="142de-307">Esse XAML associa a <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade <xref:System.Windows.Controls.ListBox> do à fonte de dados e aplica o modelo de dados como o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="142de-307">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="142de-308">Conectar dados a controles</span><span class="sxs-lookup"><span data-stu-id="142de-308">Connect data to controls</span></span>

<span data-ttu-id="142de-309">Em seguida, você adicionará o código para recuperar o nome selecionado na **`ExpenseItHome`** página e passá-lo para o construtor de **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="142de-309">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="142de-310">**ExpenseReportPage** define seu contexto de dados com o item passado, que é o que os controles definidos no *ExpenseReportPage. XAML* se associam a.</span><span class="sxs-lookup"><span data-stu-id="142de-310">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="142de-311">Abra *ExpenseReportPage.xaml.vb* ou *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="142de-311">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="142de-312">Adicione um construtor que utiliza um objeto para passar os dados do relatório de despesas da pessoa selecionada.</span><span class="sxs-lookup"><span data-stu-id="142de-312">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="142de-313">Abra *`ExpenseItHome.xaml.vb`* ou *`ExpenseItHome.xaml.cs`* .</span><span class="sxs-lookup"><span data-stu-id="142de-313">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="142de-314">Altere o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos para chamar o novo Construtor passando os dados do relatório de despesas da pessoa selecionada.</span><span class="sxs-lookup"><span data-stu-id="142de-314">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="142de-315">Dados de estilo com modelos de dados</span><span class="sxs-lookup"><span data-stu-id="142de-315">Style data with data templates</span></span>

<span data-ttu-id="142de-316">Nesta seção, você atualizará a interface do usuário para cada item nas listas vinculadas a dados usando modelos de dados.</span><span class="sxs-lookup"><span data-stu-id="142de-316">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="142de-317">Abra *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="142de-317">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="142de-318">Associe o conteúdo dos elementos "nome" e "departamento" <xref:System.Windows.Controls.Label> à propriedade de fonte de dados apropriada.</span><span class="sxs-lookup"><span data-stu-id="142de-318">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="142de-319">Para obter mais informações sobre associação de dados, consulte [visão geral da ligação de dados](../data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="142de-319">For more information about data binding, see [Data binding overview](../data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="142de-320">Após o elemento <xref:System.Windows.Controls.Grid> de abertura, adicione os seguintes modelos de dados, que definem como exibir os dados do relatório de despesas:</span><span class="sxs-lookup"><span data-stu-id="142de-320">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="142de-321">Substitua os <xref:System.Windows.Controls.DataGridTextColumn> elementos por <xref:System.Windows.Controls.DataGridTemplateColumn> sob o <xref:System.Windows.Controls.DataGrid> elemento e aplique os modelos a eles.</span><span class="sxs-lookup"><span data-stu-id="142de-321">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="142de-322">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="142de-322">Build and run the application.</span></span>

6. <span data-ttu-id="142de-323">Selecione uma pessoa e, em seguida, selecione o botão **Exibir** .</span><span class="sxs-lookup"><span data-stu-id="142de-323">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="142de-324">A ilustração a seguir mostra as páginas do `ExpenseIt` aplicativo com controles, layout, estilos, vinculação de dados e modelos de dados aplicados:</span><span class="sxs-lookup"><span data-stu-id="142de-324">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Ambas as páginas do aplicativo mostrando a lista de nomes e um relatório de despesas.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> <span data-ttu-id="142de-326">Este exemplo demonstra um recurso específico do WPF e não segue todas as práticas recomendadas para coisas como segurança, localização e acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="142de-326">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="142de-327">Para obter uma cobertura abrangente do WPF e as práticas recomendadas de desenvolvimento de aplicativos .NET, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="142de-327">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="142de-328">Acessibilidade</span><span class="sxs-lookup"><span data-stu-id="142de-328">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
>
> - [<span data-ttu-id="142de-329">Segurança</span><span class="sxs-lookup"><span data-stu-id="142de-329">Security</span></span>](../security-wpf.md)
>
> - [<span data-ttu-id="142de-330">Globalização e localização do WPF</span><span class="sxs-lookup"><span data-stu-id="142de-330">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
>
> - [<span data-ttu-id="142de-331">Desempenho do WPF</span><span class="sxs-lookup"><span data-stu-id="142de-331">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="142de-332">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="142de-332">Next steps</span></span>

<span data-ttu-id="142de-333">Neste tutorial, você aprendeu várias técnicas para criar uma interface do usuário usando Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="142de-333">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="142de-334">Agora você deve ter uma compreensão básica dos blocos de construção de um aplicativo .NET vinculado a dados.</span><span class="sxs-lookup"><span data-stu-id="142de-334">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="142de-335">Para obter mais informações sobre os modelos de arquitetura e programação do WPF, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="142de-335">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="142de-336">Arquitetura do WPF</span><span class="sxs-lookup"><span data-stu-id="142de-336">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="142de-337">Visão geral do XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="142de-337">XAML overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="142de-338">Visão geral das propriedades de dependência</span><span class="sxs-lookup"><span data-stu-id="142de-338">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="142de-339">Layout</span><span class="sxs-lookup"><span data-stu-id="142de-339">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="142de-340">Para obter mais informações sobre como criar aplicativos, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="142de-340">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="142de-341">Desenvolvimento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="142de-341">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="142de-342">Controles</span><span class="sxs-lookup"><span data-stu-id="142de-342">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="142de-343">Visão geral da associação de dados</span><span class="sxs-lookup"><span data-stu-id="142de-343">Data binding overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="142de-344">Gráficos e multimídia</span><span class="sxs-lookup"><span data-stu-id="142de-344">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="142de-345">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="142de-345">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="142de-346">Consulte também</span><span class="sxs-lookup"><span data-stu-id="142de-346">See also</span></span>

- [<span data-ttu-id="142de-347">Visão geral dos painéis</span><span class="sxs-lookup"><span data-stu-id="142de-347">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="142de-348">Visão geral de modelagem de dados</span><span class="sxs-lookup"><span data-stu-id="142de-348">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="142de-349">Compilar um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="142de-349">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="142de-350">Estilos e modelos</span><span class="sxs-lookup"><span data-stu-id="142de-350">Styles and templates</span></span>](../controls/styles-and-templates.md)
