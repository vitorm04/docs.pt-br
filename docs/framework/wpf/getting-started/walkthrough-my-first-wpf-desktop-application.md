---
title: Crie seu primeiro aplicativo WPF no Visual Studio 2019 - .NET Framework
titleSuffix: ''
ms.date: 09/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
ms.topic: tutorial
ms.custom: mvc,vs-dotnet
ms.openlocfilehash: facb9ebebd9ce1904886a946277185ac2c2e4bc4
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463920"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a><span data-ttu-id="065db-102">Tutorial: Crie seu primeiro aplicativo WPF no Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="065db-102">Tutorial: Create your first WPF application in Visual Studio 2019</span></span>

<span data-ttu-id="065db-103">Este artigo mostra como desenvolver um aplicativo de desktop do Windows Presentation Foundation (WPF) que inclui os elementos que são comuns à maioria dos aplicativos WPF: marcação XAML (Extensible Application Markup Language, xaml), code-behind, definições de aplicativos, controles, layout, vinculação de dados e estilos.</span><span class="sxs-lookup"><span data-stu-id="065db-103">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="065db-104">Para desenvolver o aplicativo, você usará o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="065db-104">To develop the application, you'll use Visual Studio.</span></span>

<span data-ttu-id="065db-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="065db-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="065db-106">Crie um projeto WPF.</span><span class="sxs-lookup"><span data-stu-id="065db-106">Create a WPF project.</span></span>
> - <span data-ttu-id="065db-107">Use XAML para projetar a aparência da interface de usuário do aplicativo (UI).</span><span class="sxs-lookup"><span data-stu-id="065db-107">Use XAML to design the appearance of the application's user interface (UI).</span></span>
> - <span data-ttu-id="065db-108">Escreva código para construir o comportamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="065db-108">Write code to build the application's behavior.</span></span>
> - <span data-ttu-id="065db-109">Crie uma definição de aplicativo para gerenciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="065db-109">Create an application definition to manage the application.</span></span>
> - <span data-ttu-id="065db-110">Adicione controles e crie o layout para compor a interface do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="065db-110">Add controls and create the layout to compose the application UI.</span></span>
> - <span data-ttu-id="065db-111">Crie estilos para uma aparência consistente em toda a interface do ida do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="065db-111">Create styles for a consistent appearance throughout the application's UI.</span></span>
> - <span data-ttu-id="065db-112">Vincule a ui a dados, tanto para preencher a ui a partir de dados quanto para manter os dados e a UI sincronizados.</span><span class="sxs-lookup"><span data-stu-id="065db-112">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="065db-113">No final do tutorial, você terá construído um aplicativo autônomo do Windows que permite que os usuários visualizem relatórios de despesas para pessoas selecionadas.</span><span class="sxs-lookup"><span data-stu-id="065db-113">By the end of the tutorial, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="065db-114">O aplicativo é composto por várias páginas WPF que estão hospedadas em uma janela no estilo navegador.</span><span class="sxs-lookup"><span data-stu-id="065db-114">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="065db-115">O código de exemplo usado neste tutorial está disponível tanto para visual basic quanto c# no [Tutorial WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span><span class="sxs-lookup"><span data-stu-id="065db-115">The sample code that is used in this tutorial is available for both Visual Basic and C# at [Tutorial WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="065db-116">Você pode alternar a linguagem de código do código de amostra entre C# e Visual Basic usando o seletor de idiomas no topo desta página.</span><span class="sxs-lookup"><span data-stu-id="065db-116">You can toggle the code language of the sample code between C# and Visual Basic by using the language selector on top of this page.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="065db-117">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="065db-117">Prerequisites</span></span>

- <span data-ttu-id="065db-118">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) com a carga **de trabalho de desenvolvimento de desktop .NET** instalada.</span><span class="sxs-lookup"><span data-stu-id="065db-118">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET desktop development** workload installed.</span></span>

   <span data-ttu-id="065db-119">Para obter mais informações sobre a instalação da versão mais recente do Visual Studio, consulte [Install Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="065db-119">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="065db-120">Criar o projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="065db-120">Create the application project</span></span>

<span data-ttu-id="065db-121">O primeiro passo é criar a infra-estrutura do aplicativo, que inclui uma definição de aplicativo, duas páginas e uma imagem.</span><span class="sxs-lookup"><span data-stu-id="065db-121">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="065db-122">Crie um novo projeto de aplicativo WPF **`ExpenseIt`** no Visual Basic ou Visual C# chamado :</span><span class="sxs-lookup"><span data-stu-id="065db-122">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="065db-123">Abra o Visual Studio e selecione **Crie um novo projeto** no menu **'Iniciar'.**</span><span class="sxs-lookup"><span data-stu-id="065db-123">Open Visual Studio and select **Create a new project** under the **Get started** menu.</span></span>

      <span data-ttu-id="065db-124">O **Diálogo Criar um novo projeto** é aberto.</span><span class="sxs-lookup"><span data-stu-id="065db-124">The **Create a new project** dialog opens.</span></span>

   2. <span data-ttu-id="065db-125">Na estada **do idioma,** selecione **C#** ou **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="065db-125">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>

   3. <span data-ttu-id="065db-126">Selecione o modelo **WPF App (.NET Framework)** e selecione **Next**.</span><span class="sxs-lookup"><span data-stu-id="065db-126">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span>

      ![Crie um novo diálogo de projeto](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)

      <span data-ttu-id="065db-128">**O Configure seu novo diálogo** de projeto é aberto.</span><span class="sxs-lookup"><span data-stu-id="065db-128">The **Configure your new project** dialog opens.</span></span>

   4. <span data-ttu-id="065db-129">Digite o **`ExpenseIt`** nome do projeto e selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="065db-129">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      ![Configure uma nova caixa de diálogo de projeto](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      <span data-ttu-id="065db-131">O Visual Studio cria o projeto e abre o designer para a janela de aplicativo padrão chamada **MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="065db-131">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="065db-132">Abra *o Application.xaml* (Visual Basic) ou *o App.xaml* (C#).</span><span class="sxs-lookup"><span data-stu-id="065db-132">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="065db-133">Este arquivo XAML define um aplicativo WPF e quaisquer recursos de aplicação.</span><span class="sxs-lookup"><span data-stu-id="065db-133">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="065db-134">Você também usa este arquivo para especificar a interface do u, neste caso *MainWindow.xaml*, que mostra automaticamente quando o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="065db-134">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="065db-135">Seu XAML deve parecer o seguinte no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="065db-135">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="065db-136">E como o seguinte em C#:</span><span class="sxs-lookup"><span data-stu-id="065db-136">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="065db-137">Abra *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="065db-137">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="065db-138">Este arquivo XAML é a janela principal do seu aplicativo e exibe o conteúdo criado nas páginas.</span><span class="sxs-lookup"><span data-stu-id="065db-138">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="065db-139">A <xref:System.Windows.Window> classe define as propriedades de uma janela, como seu título, tamanho ou ícone, e lida com eventos, como fechar ou ocultar.</span><span class="sxs-lookup"><span data-stu-id="065db-139">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="065db-140">Altere <xref:System.Windows.Window> o <xref:System.Windows.Navigation.NavigationWindow>elemento para a, conforme mostrado no seguinte XAML:</span><span class="sxs-lookup"><span data-stu-id="065db-140">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="065db-141">Este aplicativo navega para diferentes conteúdos, dependendo da entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="065db-141">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="065db-142">É por isso <xref:System.Windows.Window> que o principal <xref:System.Windows.Navigation.NavigationWindow>precisa ser alterado para um .</span><span class="sxs-lookup"><span data-stu-id="065db-142">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="065db-143"><xref:System.Windows.Navigation.NavigationWindow>herda todas as <xref:System.Windows.Window>propriedades de .</span><span class="sxs-lookup"><span data-stu-id="065db-143"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="065db-144">O <xref:System.Windows.Navigation.NavigationWindow> elemento no arquivo XAML cria <xref:System.Windows.Navigation.NavigationWindow> uma instância da classe.</span><span class="sxs-lookup"><span data-stu-id="065db-144">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="065db-145">Para obter mais informações, consulte [Visão geral da navegação](../app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="065db-145">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="065db-146">Remova <xref:System.Windows.Controls.Grid> os elementos <xref:System.Windows.Navigation.NavigationWindow> entre as etiquetas.</span><span class="sxs-lookup"><span data-stu-id="065db-146">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="065db-147">Alterar as seguintes propriedades no código <xref:System.Windows.Navigation.NavigationWindow> XAML para o elemento:</span><span class="sxs-lookup"><span data-stu-id="065db-147">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="065db-148">Defina <xref:System.Windows.Window.Title%2A> a`ExpenseIt`propriedade para ".</span><span class="sxs-lookup"><span data-stu-id="065db-148">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="065db-149">Defina <xref:System.Windows.FrameworkElement.Height%2A> a propriedade em 350 pixels.</span><span class="sxs-lookup"><span data-stu-id="065db-149">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="065db-150">Defina <xref:System.Windows.FrameworkElement.Width%2A> a propriedade para 500 pixels.</span><span class="sxs-lookup"><span data-stu-id="065db-150">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="065db-151">Seu XAML deve parecer o seguinte para Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="065db-151">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="065db-152">E como o seguinte para C#:</span><span class="sxs-lookup"><span data-stu-id="065db-152">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="065db-153">Abra *MainWindow.xaml.vb* ou *MainWindow.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="065db-153">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="065db-154">Este arquivo é um arquivo por trás do código que contém código para lidar com os eventos declarados em *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="065db-154">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="065db-155">Esse arquivo contém uma classe parcial para a janela definida no XAML.</span><span class="sxs-lookup"><span data-stu-id="065db-155">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="065db-156">Se você estiver usando C#, mude `MainWindow` <xref:System.Windows.Navigation.NavigationWindow>a classe para derivar de .</span><span class="sxs-lookup"><span data-stu-id="065db-156">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="065db-157">(No Visual Basic, isso acontece automaticamente quando você altera a janela em XAML.) Seu código C# agora deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="065db-157">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="065db-158">Adicionar arquivos ao aplicativo</span><span class="sxs-lookup"><span data-stu-id="065db-158">Add files to the application</span></span>

<span data-ttu-id="065db-159">Nesta seção, você adicionará duas páginas e uma imagem ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="065db-159">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="065db-160">Adicione uma nova página ao projeto *`ExpenseItHome.xaml`* e nomeie-a:</span><span class="sxs-lookup"><span data-stu-id="065db-160">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="065db-161">No **Solution Explorer,** clique **`ExpenseIt`** com o botão direito do mouse no nó do projeto e escolha **Adicionar** > **página**.</span><span class="sxs-lookup"><span data-stu-id="065db-161">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="065db-162">Na caixa de diálogo **Adicionar novo item,** o modelo **Página (WPF)** já está selecionado.</span><span class="sxs-lookup"><span data-stu-id="065db-162">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="065db-163">Digite **`ExpenseItHome`** o nome e selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="065db-163">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="065db-164">Esta página é a primeira página exibida quando o aplicativo é lançado.</span><span class="sxs-lookup"><span data-stu-id="065db-164">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="065db-165">Ele mostrará uma lista de pessoas para selecionar, para mostrar um relatório de despesas para.</span><span class="sxs-lookup"><span data-stu-id="065db-165">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="065db-166">Abra. *`ExpenseItHome.xaml`*</span><span class="sxs-lookup"><span data-stu-id="065db-166">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="065db-167">Defina <xref:System.Windows.Controls.Page.Title%2A> o`ExpenseIt - Home`"" ".</span><span class="sxs-lookup"><span data-stu-id="065db-167">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="065db-168">Defina `DesignHeight` os 350 pixels e os `DesignWidth` 500 pixels.</span><span class="sxs-lookup"><span data-stu-id="065db-168">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="065db-169">O XAML agora aparece da seguinte forma para Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="065db-169">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="065db-170">E como o seguinte para C#:</span><span class="sxs-lookup"><span data-stu-id="065db-170">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="065db-171">Abra *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="065db-171">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="065db-172">Adicione <xref:System.Windows.Navigation.NavigationWindow.Source%2A> uma propriedade <xref:System.Windows.Navigation.NavigationWindow> ao elemento e`ExpenseItHome.xaml`defina-a como " ".</span><span class="sxs-lookup"><span data-stu-id="065db-172">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="065db-173">Esta *`ExpenseItHome.xaml`* define-se para ser a primeira página aberta quando o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="065db-173">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span>

    <span data-ttu-id="065db-174">Exemplo XAML no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="065db-174">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="065db-175">E em C#:</span><span class="sxs-lookup"><span data-stu-id="065db-175">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="065db-176">Você também pode definir a propriedade **Origem** na categoria **Diversas** da janela **Propriedades.**</span><span class="sxs-lookup"><span data-stu-id="065db-176">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Propriedade de origem na janela Propriedades](./media/properties-source.png)

1. <span data-ttu-id="065db-178">Adicione outra nova página do WPF ao projeto e nomeie-a *ExpenseReportPage.xaml*::</span><span class="sxs-lookup"><span data-stu-id="065db-178">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="065db-179">No **Solution Explorer,** clique **`ExpenseIt`** com o botão direito do mouse no nó do projeto e escolha **Adicionar** > **página**.</span><span class="sxs-lookup"><span data-stu-id="065db-179">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="065db-180">Na **caixa de diálogo Adicionar novo item,** selecione o modelo **Página (WPF).**</span><span class="sxs-lookup"><span data-stu-id="065db-180">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="065db-181">Digite o nome **ExpenseReportPage**e, em seguida, **selecione Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="065db-181">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="065db-182">Esta página mostrará o relatório de despesas **`ExpenseItHome`** para a pessoa selecionada na página.</span><span class="sxs-lookup"><span data-stu-id="065db-182">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="065db-183">Open *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="065db-183">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="065db-184">Defina <xref:System.Windows.Controls.Page.Title%2A> o`ExpenseIt - View Expense`"" ".</span><span class="sxs-lookup"><span data-stu-id="065db-184">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="065db-185">Defina `DesignHeight` os 350 pixels e os `DesignWidth` 500 pixels.</span><span class="sxs-lookup"><span data-stu-id="065db-185">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="065db-186">*ExpenseReportPage.xaml* agora parece o seguinte no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="065db-186">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="065db-187">E como o seguinte em C#:</span><span class="sxs-lookup"><span data-stu-id="065db-187">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="065db-188">*Custo abertoItHome.xaml.vb* e *ExpenseReportPage.xaml.vb*, ou *ExpenseItHome.xaml.cs* e *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="065db-188">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="065db-189">Quando você cria um novo arquivo de página, o Visual Studio cria automaticamente seu arquivo *de código atrás.*</span><span class="sxs-lookup"><span data-stu-id="065db-189">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="065db-190">Esses arquivos code-behind manipulam a lógica para responder à entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="065db-190">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="065db-191">Seu código deve parecer **`ExpenseItHome`** o seguinte para:</span><span class="sxs-lookup"><span data-stu-id="065db-191">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="065db-192">E como o seguinte para **ExpenseReportPage**:</span><span class="sxs-lookup"><span data-stu-id="065db-192">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="065db-193">Adicione uma imagem chamada *watermark.png* ao projeto.</span><span class="sxs-lookup"><span data-stu-id="065db-193">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="065db-194">Você pode criar sua própria imagem, copiar o arquivo do código de amostra ou obtê-lo no repositório [GitHub da Microsoft/WPF-Samples.](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png)</span><span class="sxs-lookup"><span data-stu-id="065db-194">You can create your own image, copy the file from the sample code, or get it from the [microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) GitHub repository.</span></span>

    1. <span data-ttu-id="065db-195">Clique com o botão direito do mouse no nó do projeto e **selecione Adicionar** > **item existente**ou **pressione Shift**+**Alt**+**A**.</span><span class="sxs-lookup"><span data-stu-id="065db-195">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="065db-196">Na **caixa de diálogo Adicionar item existente,** defina o filtro de arquivo para **todos os arquivos** ou arquivos de **imagem,** navegue até o arquivo de imagem que deseja usar e selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="065db-196">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="065db-197">Compile e execute o aplicativo</span><span class="sxs-lookup"><span data-stu-id="065db-197">Build and run the application</span></span>

1. <span data-ttu-id="065db-198">Para criar e executar o aplicativo, pressione **F5** ou selecione **Iniciar depuração** no menu **Depuração.**</span><span class="sxs-lookup"><span data-stu-id="065db-198">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="065db-199">A ilustração a seguir <xref:System.Windows.Navigation.NavigationWindow> mostra o aplicativo com os botões:</span><span class="sxs-lookup"><span data-stu-id="065db-199">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Aplicativo depois de construí-lo e executá-lo.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. <span data-ttu-id="065db-201">Feche o aplicativo para retornar ao Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="065db-201">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="065db-202">Crie o layout</span><span class="sxs-lookup"><span data-stu-id="065db-202">Create the layout</span></span>

<span data-ttu-id="065db-203">O layout fornece uma maneira ordenada de colocar elementos de ida e volta, e também gerencia o tamanho e a posição desses elementos quando uma iu é redimensionada.</span><span class="sxs-lookup"><span data-stu-id="065db-203">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="065db-204">Normalmente, você cria um layout com um dos seguintes controles de layout:</span><span class="sxs-lookup"><span data-stu-id="065db-204">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="065db-205"><xref:System.Windows.Controls.Canvas>- Define uma área dentro da qual você pode posicionar explicitamente elementos infantis usando coordenadas relativas à área do Canvas.</span><span class="sxs-lookup"><span data-stu-id="065db-205"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="065db-206"><xref:System.Windows.Controls.DockPanel>- Define uma área onde você pode organizar elementos infantis horizontal ou verticalmente, em relação um ao outro.</span><span class="sxs-lookup"><span data-stu-id="065db-206"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="065db-207"><xref:System.Windows.Controls.Grid>- Define uma área de grade flexível que consiste em colunas e linhas.</span><span class="sxs-lookup"><span data-stu-id="065db-207"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="065db-208"><xref:System.Windows.Controls.StackPanel>- Organiza elementos infantis em uma única linha que pode ser orientada horizontal ou verticalmente.</span><span class="sxs-lookup"><span data-stu-id="065db-208"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="065db-209"><xref:System.Windows.Controls.VirtualizingStackPanel>- Organiza e virtualiza o conteúdo em uma única linha orientada horizontal ou verticalmente.</span><span class="sxs-lookup"><span data-stu-id="065db-209"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="065db-210"><xref:System.Windows.Controls.WrapPanel>- Posiciona os elementos da criança na posição seqüencial da esquerda para a direita, quebrando o conteúdo para a próxima linha na borda da caixa de contenção.</span><span class="sxs-lookup"><span data-stu-id="065db-210"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="065db-211">A encomenda subseqüente acontece sequencialmente de cima para baixo ou da direita para a esquerda, dependendo do valor da propriedade Orientação.</span><span class="sxs-lookup"><span data-stu-id="065db-211">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="065db-212">Cada um desses controles de layout suporta um tipo específico de layout para seus elementos infantis.</span><span class="sxs-lookup"><span data-stu-id="065db-212">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="065db-213">`ExpenseIt`páginas podem ser redimensionadas, e cada página tem elementos que são organizados horizontal e verticalmente ao lado de outros elementos.</span><span class="sxs-lookup"><span data-stu-id="065db-213">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="065db-214">Neste exemplo, <xref:System.Windows.Controls.Grid> o é usado como elemento de layout para a aplicação.</span><span class="sxs-lookup"><span data-stu-id="065db-214">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="065db-215">Para obter <xref:System.Windows.Controls.Panel> mais informações sobre elementos, consulte [Painéis de visão geral](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="065db-215">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="065db-216">Para obter mais informações sobre layout, consulte [Layout](../advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="065db-216">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="065db-217">Nesta seção, você cria uma tabela de uma única coluna com três linhas e uma <xref:System.Windows.Controls.Grid> *`ExpenseItHome.xaml`* margem de 10 pixels adicionando definições de coluna e linha à entrada .</span><span class="sxs-lookup"><span data-stu-id="065db-217">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="065db-218">Em *`ExpenseItHome.xaml`*, <xref:System.Windows.FrameworkElement.Margin%2A> definir a <xref:System.Windows.Controls.Grid> propriedade no elemento como "10,0,10,10", que corresponde às margens esquerda, superior, direita e inferior:</span><span class="sxs-lookup"><span data-stu-id="065db-218">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="065db-219">Você também pode definir os valores **de Margem** na janela **Propriedades,** na categoria **Layout:**</span><span class="sxs-lookup"><span data-stu-id="065db-219">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Valores de margem na janela Propriedades](./media/properties-margin.png)

2. <span data-ttu-id="065db-221">Adicione o seguinte XAML entre as <xref:System.Windows.Controls.Grid> tags para criar as definições de linha e coluna:</span><span class="sxs-lookup"><span data-stu-id="065db-221">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="065db-222">A <xref:System.Windows.Controls.RowDefinition.Height%2A> de duas linhas <xref:System.Windows.GridLength.Auto%2A>é definida como , o que significa que as linhas são dimensionadas com base no conteúdo nas linhas.</span><span class="sxs-lookup"><span data-stu-id="065db-222">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="065db-223">O <xref:System.Windows.Controls.RowDefinition.Height%2A> padrão <xref:System.Windows.GridUnitType.Star> é o dimensionamento, o que significa que a altura da linha é uma proporção ponderada do espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="065db-223">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="065db-224">Por exemplo, se duas <xref:System.Windows.Controls.RowDefinition.Height%2A> linhas cada uma tem um de "\*", cada uma tem uma altura que é metade do espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="065db-224">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="065db-225">Agora <xref:System.Windows.Controls.Grid> você deve conter o seguinte XAML:</span><span class="sxs-lookup"><span data-stu-id="065db-225">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="065db-226">Adicionar controles</span><span class="sxs-lookup"><span data-stu-id="065db-226">Add controls</span></span>

<span data-ttu-id="065db-227">Nesta seção, você atualizará a ui da página inicial para mostrar uma lista de pessoas, onde você seleciona uma pessoa para exibir seu relatório de despesas.</span><span class="sxs-lookup"><span data-stu-id="065db-227">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="065db-228">Os controles são objetos da interface do usuário que permitem aos usuários interagir com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="065db-228">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="065db-229">Para obter mais informações, consulte [Controles](../controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="065db-229">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="065db-230">Para criar essa iu, você adicionará *`ExpenseItHome.xaml`* os seguintes elementos a:</span><span class="sxs-lookup"><span data-stu-id="065db-230">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="065db-231">A <xref:System.Windows.Controls.ListBox> (para a lista de pessoas).</span><span class="sxs-lookup"><span data-stu-id="065db-231">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="065db-232">A <xref:System.Windows.Controls.Label> (para o cabeçalho da lista).</span><span class="sxs-lookup"><span data-stu-id="065db-232">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="065db-233">A <xref:System.Windows.Controls.Button> (clicar para visualizar o relatório de despesas para a pessoa selecionada na lista).</span><span class="sxs-lookup"><span data-stu-id="065db-233">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="065db-234">Cada controle é colocado em <xref:System.Windows.Controls.Grid> uma <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> linha do definindo a propriedade anexada.</span><span class="sxs-lookup"><span data-stu-id="065db-234">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="065db-235">Para obter mais informações sobre propriedades anexadas, consulte [Visão geral de propriedades anexadas](../advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="065db-235">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="065db-236">Em *`ExpenseItHome.xaml`*, adicione o seguinte XAML em algum lugar entre as <xref:System.Windows.Controls.Grid> tags:</span><span class="sxs-lookup"><span data-stu-id="065db-236">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="065db-237">Você também pode criar os controles arrastando-os da janela **Toolbox** para a janela de design e, em seguida, definindo suas propriedades na janela **Propriedades.**</span><span class="sxs-lookup"><span data-stu-id="065db-237">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="065db-238">Criar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="065db-238">Build and run the application.</span></span>

    <span data-ttu-id="065db-239">A ilustração a seguir mostra os controles que você criou:</span><span class="sxs-lookup"><span data-stu-id="065db-239">The following illustration shows the controls you created:</span></span>

![DespesaA captura de tela de captura de tela de captura de tela exibindo uma lista de nomes](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="065db-241">Adicione uma imagem e um título</span><span class="sxs-lookup"><span data-stu-id="065db-241">Add an image and a title</span></span>

<span data-ttu-id="065db-242">Nesta seção, você atualizará a ui da página inicial com uma imagem e um título de página.</span><span class="sxs-lookup"><span data-stu-id="065db-242">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="065db-243">Em *`ExpenseItHome.xaml`*, adicionar outra <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> coluna <xref:System.Windows.Controls.ColumnDefinition.Width%2A> ao com um fixo de 230 pixels:</span><span class="sxs-lookup"><span data-stu-id="065db-243">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewColumn)]

2. <span data-ttu-id="065db-244">Adicione outra linha <xref:System.Windows.Controls.Grid.RowDefinitions%2A>ao , para um total de quatro linhas:</span><span class="sxs-lookup"><span data-stu-id="065db-244">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewRows)]

3. <span data-ttu-id="065db-245">Mova os controles para a segunda <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> coluna definindo a propriedade para 1 em cada um dos três controles (Border, ListBox e Button).</span><span class="sxs-lookup"><span data-stu-id="065db-245">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="065db-246">Mova cada controle para baixo <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> uma linha, aumentando seu valor em 1 para cada um dos três controles (Border, ListBox e Button) e para o elemento Borda.</span><span class="sxs-lookup"><span data-stu-id="065db-246">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="065db-247">O XAML para os três controles agora parece o seguinte:</span><span class="sxs-lookup"><span data-stu-id="065db-247">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="065db-248">Defina <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> a propriedade no arquivo de imagem *watermark.png,* adicionando o seguinte XAML em qualquer lugar entre as `<Grid>` `</Grid>` tags:</span><span class="sxs-lookup"><span data-stu-id="065db-248">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="065db-249">Antes <xref:System.Windows.Controls.Border> do elemento, <xref:System.Windows.Controls.Label> adicione a com o conteúdo "Exibir relatório de despesas".</span><span class="sxs-lookup"><span data-stu-id="065db-249">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="065db-250">Este rótulo é o título da página.</span><span class="sxs-lookup"><span data-stu-id="065db-250">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="065db-251">Criar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="065db-251">Build and run the application.</span></span>

<span data-ttu-id="065db-252">A ilustração a seguir mostra os resultados do que você acabou de adicionar:</span><span class="sxs-lookup"><span data-stu-id="065db-252">The following illustration shows the results of what you just added:</span></span>

![Captura de tela de exemplo expenseIt mostrando o novo plano de fundo da imagem e o título da página](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="065db-254">Adicionar código para lidar com eventos</span><span class="sxs-lookup"><span data-stu-id="065db-254">Add code to handle events</span></span>

1. <span data-ttu-id="065db-255">Em *`ExpenseItHome.xaml`*, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> adicionar um <xref:System.Windows.Controls.Button> manipulador de eventos ao elemento.</span><span class="sxs-lookup"><span data-stu-id="065db-255">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="065db-256">Para obter mais informações, consulte [Como: Criar um simples manipulador de eventos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="065db-256">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="065db-257">Abra *`ExpenseItHome.xaml.vb`* *`ExpenseItHome.xaml.cs`* ou.</span><span class="sxs-lookup"><span data-stu-id="065db-257">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="065db-258">Adicione o seguinte `ExpenseItHome` código à classe para adicionar um manipulador de eventos clique em botão.</span><span class="sxs-lookup"><span data-stu-id="065db-258">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="065db-259">O manipulador de eventos abre a página **ExpenseReportPage.**</span><span class="sxs-lookup"><span data-stu-id="065db-259">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="065db-260">Criar a ui para relatório de despesas</span><span class="sxs-lookup"><span data-stu-id="065db-260">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="065db-261">*ExpenseReportPage.xaml* exibe o relatório de despesas para **`ExpenseItHome`** a pessoa selecionada na página.</span><span class="sxs-lookup"><span data-stu-id="065db-261">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="065db-262">Nesta seção, você criará a ui para **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="065db-262">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="065db-263">Você também adicionará o plano de fundo e preencherá cores aos vários elementos de ia.</span><span class="sxs-lookup"><span data-stu-id="065db-263">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="065db-264">Open *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="065db-264">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="065db-265">Adicione o seguinte XAML entre as <xref:System.Windows.Controls.Grid> tags:</span><span class="sxs-lookup"><span data-stu-id="065db-265">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="065db-266">Esta ui é *`ExpenseItHome.xaml`* semelhante, exceto que os <xref:System.Windows.Controls.DataGrid>dados do relatório são exibidos em um .</span><span class="sxs-lookup"><span data-stu-id="065db-266">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="065db-267">Criar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="065db-267">Build and run the application.</span></span>

4. <span data-ttu-id="065db-268">Selecione o botão **Exibir.**</span><span class="sxs-lookup"><span data-stu-id="065db-268">Select the **View** button.</span></span>

    <span data-ttu-id="065db-269">A página de relatório de despesas é exibida.</span><span class="sxs-lookup"><span data-stu-id="065db-269">The expense report page appears.</span></span> <span data-ttu-id="065db-270">Observe também que o botão de navegação de volta está ativado.</span><span class="sxs-lookup"><span data-stu-id="065db-270">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="065db-271">A ilustração a seguir mostra os elementos de IA adicionados ao *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="065db-271">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![Captura de tela de exemplo expenseIt mostrando a ui criada para o ExpenseReportPage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a><span data-ttu-id="065db-273">Controles de estilo</span><span class="sxs-lookup"><span data-stu-id="065db-273">Style controls</span></span>

<span data-ttu-id="065db-274">O aparecimento de vários elementos é muitas vezes o mesmo para todos os elementos do mesmo tipo em uma ui.</span><span class="sxs-lookup"><span data-stu-id="065db-274">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="065db-275">A ui usa [estilos](../controls/styling-and-templating.md) para tornar as aparências reutilizáveis em vários elementos.</span><span class="sxs-lookup"><span data-stu-id="065db-275">UI uses [styles](../controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="065db-276">A reutilização dos estilos ajuda a simplificar a criação e o gerenciamento do XAML.</span><span class="sxs-lookup"><span data-stu-id="065db-276">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="065db-277">Esta seção substitui os atributos por elemento que foram definidos nas etapas anteriores com estilos.</span><span class="sxs-lookup"><span data-stu-id="065db-277">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="065db-278">*Abra o Application.xaml* ou *app.xaml*.</span><span class="sxs-lookup"><span data-stu-id="065db-278">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="065db-279">Adicione o seguinte XAML entre as <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span><span class="sxs-lookup"><span data-stu-id="065db-279">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="065db-280">Esse XAML adiciona os seguintes estilos:</span><span class="sxs-lookup"><span data-stu-id="065db-280">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="065db-281">`headerTextStyle`: para formatar o título da página <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="065db-281">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="065db-282">`labelStyle`: para formatar os controles <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="065db-282">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="065db-283">`columnHeaderStyle`: para formatar o <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="065db-283">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="065db-284">`listHeaderStyle`: para formatar os controles <xref:System.Windows.Controls.Border> do cabeçalho da lista.</span><span class="sxs-lookup"><span data-stu-id="065db-284">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="065db-285">`listHeaderTextStyle`: Para formatar <xref:System.Windows.Controls.Label>o cabeçalho da lista .</span><span class="sxs-lookup"><span data-stu-id="065db-285">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="065db-286">`buttonStyle`: Para <xref:System.Windows.Controls.Button> formatar o on `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="065db-286">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="065db-287">Observe que os estilos são <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> recursos e filhos do elemento propriedade.</span><span class="sxs-lookup"><span data-stu-id="065db-287">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="065db-288">Nesse local, os estilos são aplicados a todos os elementos em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="065db-288">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="065db-289">Para um exemplo de uso de recursos em um aplicativo .NET, consulte [Use Application Resources](../advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="065db-289">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="065db-290">Em *`ExpenseItHome.xaml`*, substituir <xref:System.Windows.Controls.Grid> tudo entre os elementos com o seguinte XAML:</span><span class="sxs-lookup"><span data-stu-id="065db-290">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="065db-291">As propriedades como <xref:System.Windows.VerticalAlignment> e <xref:System.Windows.Media.FontFamily> que definem a aparência de cada controle são removidas e substituídas ao aplicar os estilos.</span><span class="sxs-lookup"><span data-stu-id="065db-291">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="065db-292">Por exemplo, `headerTextStyle` o é aplicado ao "Exibir relatório de despesas". <xref:System.Windows.Controls.Label></span><span class="sxs-lookup"><span data-stu-id="065db-292">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="065db-293">Open *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="065db-293">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="065db-294">Substitua tudo <xref:System.Windows.Controls.Grid> entre os elementos pelo seguinte XAML:</span><span class="sxs-lookup"><span data-stu-id="065db-294">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="065db-295">Este XAML adiciona <xref:System.Windows.Controls.Label> estilos <xref:System.Windows.Controls.Border> aos elementos.</span><span class="sxs-lookup"><span data-stu-id="065db-295">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="065db-296">Criar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="065db-296">Build and run the application.</span></span> <span data-ttu-id="065db-297">A aparência da janela é a mesma de antes.</span><span class="sxs-lookup"><span data-stu-id="065db-297">The window appearance is the same as previously.</span></span>

    ![ExpenseIt captura de tela de captura de tela com a mesma aparência da última seção.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. <span data-ttu-id="065db-299">Feche o aplicativo para retornar ao Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="065db-299">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="065db-300">Vincular dados a um controle</span><span class="sxs-lookup"><span data-stu-id="065db-300">Bind data to a control</span></span>

<span data-ttu-id="065db-301">Nesta seção, você criará os dados XML que estão vinculados a vários controles.</span><span class="sxs-lookup"><span data-stu-id="065db-301">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="065db-302">Em *`ExpenseItHome.xaml`*, após <xref:System.Windows.Controls.Grid> o elemento de abertura, adicione <xref:System.Windows.Data.XmlDataProvider> o seguinte XAML para criar um que contenha os dados de cada pessoa:</span><span class="sxs-lookup"><span data-stu-id="065db-302">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="065db-303">Os dados são criados como um <xref:System.Windows.Controls.Grid> recurso.</span><span class="sxs-lookup"><span data-stu-id="065db-303">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="065db-304">Normalmente esses dados seriam carregados como um arquivo, mas para simplificar os dados são adicionados inline.</span><span class="sxs-lookup"><span data-stu-id="065db-304">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="065db-305">Dentro `<Grid.Resources>` do elemento, `<xref:System.Windows.DataTemplate>` adicione o seguinte elemento, que define <xref:System.Windows.Controls.ListBox>como `<XmlDataProvider>` exibir os dados no , após o elemento:</span><span class="sxs-lookup"><span data-stu-id="065db-305">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="065db-306">Para obter mais informações sobre modelos de dados, consulte [Visão geral do templating de dados](../data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="065db-306">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="065db-307">Substitua o <xref:System.Windows.Controls.ListBox> existente pelo seguinte XAML:</span><span class="sxs-lookup"><span data-stu-id="065db-307">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="065db-308">Este XAML vincula <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> a <xref:System.Windows.Controls.ListBox> propriedade da fonte de dados e <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>aplica o modelo de dados como .</span><span class="sxs-lookup"><span data-stu-id="065db-308">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="065db-309">Conecte dados a controles</span><span class="sxs-lookup"><span data-stu-id="065db-309">Connect data to controls</span></span>

<span data-ttu-id="065db-310">Em seguida, você adicionará código para recuperar o **`ExpenseItHome`** nome selecionado na página e passá-lo para o construtor de **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="065db-310">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="065db-311">**ExpenseReportPage** define seu contexto de dados com o item passado, que é o que os controles definidos em *ExpenseReportPage.xaml* bind to.</span><span class="sxs-lookup"><span data-stu-id="065db-311">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="065db-312">*Open ExpenseReportPage.xaml.vb* ou *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="065db-312">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="065db-313">Adicione um construtor que utiliza um objeto para passar os dados do relatório de despesas da pessoa selecionada.</span><span class="sxs-lookup"><span data-stu-id="065db-313">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="065db-314">Abra *`ExpenseItHome.xaml.vb`* *`ExpenseItHome.xaml.cs`* ou.</span><span class="sxs-lookup"><span data-stu-id="065db-314">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="065db-315">Altere <xref:System.Windows.Controls.Primitives.ButtonBase.Click> o manipulador de eventos para chamar o novo construtor passando os dados do relatório de despesas da pessoa selecionada.</span><span class="sxs-lookup"><span data-stu-id="065db-315">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="065db-316">Dados de estilo com modelos de dados</span><span class="sxs-lookup"><span data-stu-id="065db-316">Style data with data templates</span></span>

<span data-ttu-id="065db-317">Nesta seção, você atualizará a ui para cada item nas listas vinculadas a dados usando modelos de dados.</span><span class="sxs-lookup"><span data-stu-id="065db-317">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="065db-318">Open *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="065db-318">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="065db-319">Vincule o conteúdo dos elementos <xref:System.Windows.Controls.Label> "Nome" e "Departamento" à propriedade de origem de dados apropriada.</span><span class="sxs-lookup"><span data-stu-id="065db-319">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="065db-320">Para obter mais informações sobre vinculação de dados, consulte [Visão geral de vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="065db-320">For more information about data binding, see [Data binding overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="065db-321">Após o <xref:System.Windows.Controls.Grid> elemento de abertura, adicione os seguintes modelos de dados, que definem como exibir os dados do relatório de despesas:</span><span class="sxs-lookup"><span data-stu-id="065db-321">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="065db-322">Substitua <xref:System.Windows.Controls.DataGridTextColumn> os <xref:System.Windows.Controls.DataGridTemplateColumn> elementos por sob o <xref:System.Windows.Controls.DataGrid> elemento e aplique os modelos a eles.</span><span class="sxs-lookup"><span data-stu-id="065db-322">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="065db-323">Criar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="065db-323">Build and run the application.</span></span>

6. <span data-ttu-id="065db-324">Selecione uma pessoa e selecione o botão **Exibir.**</span><span class="sxs-lookup"><span data-stu-id="065db-324">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="065db-325">A ilustração a `ExpenseIt` seguir mostra ambas as páginas do aplicativo com controles, layout, estilos, vinculação de dados e modelos de dados aplicados:</span><span class="sxs-lookup"><span data-stu-id="065db-325">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Ambas as páginas do aplicativo mostrando a lista de nomes e um relatório de despesas.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> <span data-ttu-id="065db-327">Esta amostra demonstra uma característica específica do WPF e não segue todas as práticas recomendadas para coisas como segurança, localização e acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="065db-327">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="065db-328">Para obter uma cobertura abrangente das práticas recomendadas de desenvolvimento de aplicativos .NET, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="065db-328">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="065db-329">Acessibilidade</span><span class="sxs-lookup"><span data-stu-id="065db-329">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
> - [<span data-ttu-id="065db-330">Segurança</span><span class="sxs-lookup"><span data-stu-id="065db-330">Security</span></span>](../security-wpf.md)
> - [<span data-ttu-id="065db-331">Globalização e localização do WPF</span><span class="sxs-lookup"><span data-stu-id="065db-331">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
> - [<span data-ttu-id="065db-332">Desempenho do WPF</span><span class="sxs-lookup"><span data-stu-id="065db-332">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="065db-333">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="065db-333">Next steps</span></span>

<span data-ttu-id="065db-334">Neste passo a passo você aprendeu uma série de técnicas para criar uma UI usando o Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="065db-334">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="065db-335">Agora você deve ter uma compreensão básica dos blocos de construção de um aplicativo .NET vinculado a dados.</span><span class="sxs-lookup"><span data-stu-id="065db-335">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="065db-336">Para obter mais informações sobre os modelos de arquitetura e programação do WPF, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="065db-336">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="065db-337">Arquitetura WPF</span><span class="sxs-lookup"><span data-stu-id="065db-337">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="065db-338">Visão geral xaml (WPF)</span><span class="sxs-lookup"><span data-stu-id="065db-338">XAML overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="065db-339">Visão geral das propriedades de dependência</span><span class="sxs-lookup"><span data-stu-id="065db-339">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="065db-340">Layout</span><span class="sxs-lookup"><span data-stu-id="065db-340">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="065db-341">Para obter mais informações sobre como criar aplicativos, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="065db-341">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="065db-342">Desenvolvimento de aplicativo</span><span class="sxs-lookup"><span data-stu-id="065db-342">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="065db-343">Controles</span><span class="sxs-lookup"><span data-stu-id="065db-343">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="065db-344">Visão geral de associação de dados</span><span class="sxs-lookup"><span data-stu-id="065db-344">Data binding overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="065db-345">Gráficos e multimídia</span><span class="sxs-lookup"><span data-stu-id="065db-345">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="065db-346">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="065db-346">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="065db-347">Confira também</span><span class="sxs-lookup"><span data-stu-id="065db-347">See also</span></span>

- [<span data-ttu-id="065db-348">Visão geral dos painéis</span><span class="sxs-lookup"><span data-stu-id="065db-348">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="065db-349">Visão geral do templating de dados</span><span class="sxs-lookup"><span data-stu-id="065db-349">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="065db-350">Construa um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="065db-350">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="065db-351">Estilos e modelos</span><span class="sxs-lookup"><span data-stu-id="065db-351">Styles and templates</span></span>](../controls/styles-and-templates.md)
