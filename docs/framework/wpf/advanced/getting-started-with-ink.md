---
title: Criar um InkCanvas em um aplicativo do WPF no Visual Studio
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: 600d8528125606c6e1af5b031e2fc31aabb79206
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925038"
---
# <a name="get-started-with-ink-in-wpf"></a><span data-ttu-id="0f79c-102">Introdução a tinta no WPF</span><span class="sxs-lookup"><span data-stu-id="0f79c-102">Get Started with Ink in WPF</span></span>

<span data-ttu-id="0f79c-103">Windows Presentation Foundation (WPF) tem um recurso de tinta que facilita a incorporar tinta digital em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f79c-103">Windows Presentation Foundation (WPF) has an ink feature that makes it easy to incorporate digital ink into your app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0f79c-104">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="0f79c-104">Prerequisites</span></span>

<span data-ttu-id="0f79c-105">Para usar os exemplos a seguir, primeiro [instalar o Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).</span><span class="sxs-lookup"><span data-stu-id="0f79c-105">To use the following examples, first [install Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).</span></span> <span data-ttu-id="0f79c-106">Ele também ajuda a saber como escrever aplicativos básicos do WPF.</span><span class="sxs-lookup"><span data-stu-id="0f79c-106">It also helps to know how to write basic WPF apps.</span></span> <span data-ttu-id="0f79c-107">Para obter ajuda na introdução ao WPF, consulte [instruções passo a passo: meu primeiro aplicativo da área de trabalho do WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="0f79c-107">For help getting started with WPF, see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="quick-start"></a><span data-ttu-id="0f79c-108">Início rápido</span><span class="sxs-lookup"><span data-stu-id="0f79c-108">Quick Start</span></span>

<span data-ttu-id="0f79c-109">Esta seção ajuda você a escrever um aplicativo WPF simple que coleta tinta.</span><span class="sxs-lookup"><span data-stu-id="0f79c-109">This section helps you write a simple WPF application that collects ink.</span></span>

### <a name="got-ink"></a><span data-ttu-id="0f79c-110">Tem tinta?</span><span class="sxs-lookup"><span data-stu-id="0f79c-110">Got Ink?</span></span>

<span data-ttu-id="0f79c-111">Para criar um aplicativo WPF que dê suporte a tinta:</span><span class="sxs-lookup"><span data-stu-id="0f79c-111">To create a WPF app that supports ink:</span></span>

1. <span data-ttu-id="0f79c-112">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0f79c-112">Open Visual Studio.</span></span>

2. <span data-ttu-id="0f79c-113">Criar um novo **aplicativo WPF**.</span><span class="sxs-lookup"><span data-stu-id="0f79c-113">Create a new **WPF App**.</span></span>

   <span data-ttu-id="0f79c-114">No **novo projeto** caixa de diálogo, expanda o **instalado** > **Visual C#** ou **Visual Basic**  >   **Área de trabalho do Windows** categoria.</span><span class="sxs-lookup"><span data-stu-id="0f79c-114">In the **New Project** dialog, expand the **Installed** > **Visual C#** or **Visual Basic** > **Windows Desktop** category.</span></span> <span data-ttu-id="0f79c-115">Em seguida, selecione a **aplicativo WPF (.NET Framework)** modelo de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f79c-115">Then, select the **WPF App (.NET Framework)** app template.</span></span> <span data-ttu-id="0f79c-116">Insira um nome e, em seguida, selecione **Okey**.</span><span class="sxs-lookup"><span data-stu-id="0f79c-116">Enter a name, and then select **OK**.</span></span>

   <span data-ttu-id="0f79c-117">O Visual Studio cria o projeto, e *MainWindow. XAML* abre no designer.</span><span class="sxs-lookup"><span data-stu-id="0f79c-117">Visual Studio creates the project, and *MainWindow.xaml* opens in the designer.</span></span>

3. <span data-ttu-id="0f79c-118">Tipo de `<InkCanvas/>` entre o `<Grid>` marcas.</span><span class="sxs-lookup"><span data-stu-id="0f79c-118">Type `<InkCanvas/>` between the `<Grid>` tags.</span></span>

   ![Designer XAML com marca InkCanvas](media/getting-started-with-ink/inkcanvas-xaml.png)

4. <span data-ttu-id="0f79c-120">Pressione **F5** para iniciar o aplicativo no depurador.</span><span class="sxs-lookup"><span data-stu-id="0f79c-120">Press **F5** to launch your application in the debugger.</span></span>

5. <span data-ttu-id="0f79c-121">Usando um mouse ou caneta, escrever **Olá, mundo** na janela.</span><span class="sxs-lookup"><span data-stu-id="0f79c-121">Using a stylus or mouse, write **hello world** in the window.</span></span>

<span data-ttu-id="0f79c-122">Você escreveu o equivalente em tinta de um aplicativo "Olá, Mundo" com apenas 12 pressionamentos de tecla!</span><span class="sxs-lookup"><span data-stu-id="0f79c-122">You've written the ink equivalent of a "hello world" application with only 12 keystrokes!</span></span>

### <a name="spice-up-your-app"></a><span data-ttu-id="0f79c-123">Aprimore seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="0f79c-123">Spice Up Your App</span></span>

<span data-ttu-id="0f79c-124">Vamos aproveitar alguns recursos do WPF.</span><span class="sxs-lookup"><span data-stu-id="0f79c-124">Let’s take advantage of some features of the WPF.</span></span> <span data-ttu-id="0f79c-125">Substitua tudo entre a abertura e fechamento \<Janela > marcas com a seguinte marcação:</span><span class="sxs-lookup"><span data-stu-id="0f79c-125">Replace everything between the opening and closing \<Window> tags with the following markup:</span></span>

```xaml
<Page>
  <InkCanvas Name="myInkCanvas" MouseRightButtonUp="RightMouseUpHandler">
    <InkCanvas.Background>
      <LinearGradientBrush>
        <GradientStop Color="Yellow" Offset="0.0" />
          <GradientStop Color="Blue" Offset="0.5" />
            <GradientStop Color="HotPink" Offset="1.0" />
              </LinearGradientBrush>
    </InkCanvas.Background>
  </InkCanvas>
</Page>
```

<span data-ttu-id="0f79c-126">Esse XAML cria um plano de fundo de pincel de gradiente na superfície de tinta.</span><span class="sxs-lookup"><span data-stu-id="0f79c-126">This XAML creates a gradient brush background on your inking surface.</span></span>

![Cores de gradiente na superfície no aplicativo WPF de tinta](media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a><span data-ttu-id="0f79c-128">Adicionar algum código por trás de XAML</span><span class="sxs-lookup"><span data-stu-id="0f79c-128">Add Some Code Behind the XAML</span></span>

<span data-ttu-id="0f79c-129">Embora XAML torne muito fácil projetar a interface do usuário, qualquer aplicativo do mundo real precisa adicionar código para manipular eventos.</span><span class="sxs-lookup"><span data-stu-id="0f79c-129">While XAML makes it very easy to design the user interface, any real-world application needs to add code to handle events.</span></span> <span data-ttu-id="0f79c-130">Aqui está um exemplo simples que ampliará a tinta em resposta a um clique com botão direito do mouse.</span><span class="sxs-lookup"><span data-stu-id="0f79c-130">Here is a simple example that zooms in on the ink in response to a right-click from a mouse.</span></span>

1. <span data-ttu-id="0f79c-131">Defina o `MouseRightButtonUp` manipulador no seu XAML:</span><span class="sxs-lookup"><span data-stu-id="0f79c-131">Set the `MouseRightButtonUp` handler in your XAML:</span></span>

   [!code-xaml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. <span data-ttu-id="0f79c-132">Na **Gerenciador de soluções**, expanda MainWindow. XAML e abra o arquivo code-behind (MainWindow.xaml.cs ou. XAML. vb).</span><span class="sxs-lookup"><span data-stu-id="0f79c-132">In **Solution Explorer**, expand MainWindow.xaml and open the code-behind file (MainWindow.xaml.cs or MainWindow.xaml.vb).</span></span> <span data-ttu-id="0f79c-133">Adicione o seguinte código do manipulador de eventos:</span><span class="sxs-lookup"><span data-stu-id="0f79c-133">Add the following event handler code:</span></span>

   [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. <span data-ttu-id="0f79c-134">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f79c-134">Run the application.</span></span> <span data-ttu-id="0f79c-135">Adicione alguma tinta e, em seguida, clique com o mouse ou executar uma ação de pressionar e segurar equivalente com uma caneta.</span><span class="sxs-lookup"><span data-stu-id="0f79c-135">Add some ink, and then right-click with the mouse or perform a press-and-hold equivalent with a stylus.</span></span>

   <span data-ttu-id="0f79c-136">A exibição amplia cada vez que você clicar com o botão direito do mouse.</span><span class="sxs-lookup"><span data-stu-id="0f79c-136">The display zooms in each time you click with the right mouse button.</span></span>

### <a name="use-procedural-code-instead-of-xaml"></a><span data-ttu-id="0f79c-137">Use o código de procedimento em vez de XAML</span><span class="sxs-lookup"><span data-stu-id="0f79c-137">Use Procedural Code Instead of XAML</span></span>

<span data-ttu-id="0f79c-138">Você pode acessar todos os recursos do WPF do código de procedimento.</span><span class="sxs-lookup"><span data-stu-id="0f79c-138">You can access all WPF features from procedural code.</span></span> <span data-ttu-id="0f79c-139">Siga estas etapas para criar um aplicativo "Olá, mundo da tinta" para o WPF que não usa qualquer XAML em todos os.</span><span class="sxs-lookup"><span data-stu-id="0f79c-139">Follow these steps to create a "Hello Ink World" application for WPF that doesn’t use any XAML at all.</span></span>

1. <span data-ttu-id="0f79c-140">Crie um novo projeto de aplicativo de console no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0f79c-140">Create a new console application project in Visual Studio.</span></span>

   <span data-ttu-id="0f79c-141">No **novo projeto** caixa de diálogo, expanda o **instalado** > **Visual C#** ou **Visual Basic**  >   **Área de trabalho do Windows** categoria.</span><span class="sxs-lookup"><span data-stu-id="0f79c-141">In the **New Project** dialog, expand the **Installed** > **Visual C#** or **Visual Basic** > **Windows Desktop** category.</span></span> <span data-ttu-id="0f79c-142">Em seguida, selecione a **aplicativo de Console (.NET Framework)** modelo de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f79c-142">Then, select the **Console App (.NET Framework)** app template.</span></span> <span data-ttu-id="0f79c-143">Insira um nome e, em seguida, selecione **Okey**.</span><span class="sxs-lookup"><span data-stu-id="0f79c-143">Enter a name, and then select **OK**.</span></span>

1. <span data-ttu-id="0f79c-144">Cole o código a seguir no arquivo Program.cs ou Program. vb:</span><span class="sxs-lookup"><span data-stu-id="0f79c-144">Paste the following code into the Program.cs or Program.vb file:</span></span>

   [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. <span data-ttu-id="0f79c-145">Adicione referências aos assemblies PresentationCore, PresentationFramework e WindowsBase clicando **referências** na **Gerenciador de soluções** e escolhendo **Add Reference**.</span><span class="sxs-lookup"><span data-stu-id="0f79c-145">Add references to the PresentationCore, PresentationFramework, and WindowsBase assemblies by right-clicking on **References** in **Solution Explorer** and choosing **Add Reference**.</span></span>

   ![Gerenciador de referências mostrando PresentationCore e PresentationFramework](media/getting-started-with-ink/references.png)

1. <span data-ttu-id="0f79c-147">Compile o aplicativo pressionando **F5**.</span><span class="sxs-lookup"><span data-stu-id="0f79c-147">Build the application by pressing **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f79c-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f79c-148">See Also</span></span>

- [<span data-ttu-id="0f79c-149">Tinta digital</span><span class="sxs-lookup"><span data-stu-id="0f79c-149">Digital Ink</span></span>](../../../../docs/framework/wpf/advanced/digital-ink.md)
- [<span data-ttu-id="0f79c-150">Coletando tinta</span><span class="sxs-lookup"><span data-stu-id="0f79c-150">Collecting Ink</span></span>](../../../../docs/framework/wpf/advanced/collecting-ink.md)
- [<span data-ttu-id="0f79c-151">Reconhecimento de manuscrito</span><span class="sxs-lookup"><span data-stu-id="0f79c-151">Handwriting Recognition</span></span>](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)
- [<span data-ttu-id="0f79c-152">Armazenando a tinta</span><span class="sxs-lookup"><span data-stu-id="0f79c-152">Storing Ink</span></span>](../../../../docs/framework/wpf/advanced/storing-ink.md)
