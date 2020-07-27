---
title: 'Passo a passo: habilitar arrastar e soltar em um controle de usuário'
description: Saiba como criar um controle de usuário personalizado que possa participar da transferência de dados do tipo "arrastar e soltar" em Windows Presentation Foundation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: 12ad47035a09995094014841b083062743fc2574
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168283"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="b479e-103">Passo a passo: habilitar arrastar e soltar em um controle de usuário</span><span class="sxs-lookup"><span data-stu-id="b479e-103">Walkthrough: Enabling Drag and Drop on a User Control</span></span>

<span data-ttu-id="b479e-104">Este passo a passo demonstra como criar um controle de usuário personalizado que pode participar na transferência de dados por arrastar e soltar no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b479e-104">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>

<span data-ttu-id="b479e-105">Neste tutorial, você criará um WPF personalizado <xref:System.Windows.Controls.UserControl> que representa uma forma de círculo.</span><span class="sxs-lookup"><span data-stu-id="b479e-105">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="b479e-106">Você implementará a funcionalidade no controle para permitir a transferência de dados por meio de arrastar e soltar.</span><span class="sxs-lookup"><span data-stu-id="b479e-106">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="b479e-107">Por exemplo, se você arrastar de um controle do círculo para outro, os dados de cor de preenchimento serão copiados do círculo de origem para o destino.</span><span class="sxs-lookup"><span data-stu-id="b479e-107">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="b479e-108">Se você arrastar de um controle de círculo para um <xref:System.Windows.Controls.TextBox> , a representação de cadeia de caracteres da cor de preenchimento será copiada para o <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="b479e-108">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="b479e-109">Você também criará um pequeno aplicativo que contém dois controles de painel e um <xref:System.Windows.Controls.TextBox> para testar a funcionalidade de arrastar e soltar.</span><span class="sxs-lookup"><span data-stu-id="b479e-109">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="b479e-110">Será gravado um código que permite que os painéis processem os dados do círculo que foram soltos, o que permitirá mover ou copiar círculos da coleção de filhos de um painel para o outro.</span><span class="sxs-lookup"><span data-stu-id="b479e-110">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>

<span data-ttu-id="b479e-111">Este passo a passo ilustra as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="b479e-111">This walkthrough illustrates the following tasks:</span></span>

- <span data-ttu-id="b479e-112">Crie um controle de usuário personalizado.</span><span class="sxs-lookup"><span data-stu-id="b479e-112">Create a custom user control.</span></span>

- <span data-ttu-id="b479e-113">Habilite o controle de usuário como uma fonte de arrastar.</span><span class="sxs-lookup"><span data-stu-id="b479e-113">Enable the user control to be a drag source.</span></span>

- <span data-ttu-id="b479e-114">Habilite o controle de usuário como um destino de soltar.</span><span class="sxs-lookup"><span data-stu-id="b479e-114">Enable the user control to be a drop target.</span></span>

- <span data-ttu-id="b479e-115">Habilite um painel para receber dados que foram soltos pelo controle de usuário.</span><span class="sxs-lookup"><span data-stu-id="b479e-115">Enable a panel to receive data dropped from the user control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b479e-116">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="b479e-116">Prerequisites</span></span>

<span data-ttu-id="b479e-117">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="b479e-117">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="b479e-118">Criar o projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="b479e-118">Create the Application Project</span></span>
 <span data-ttu-id="b479e-119">Nesta seção, você criará a infraestrutura do aplicativo, que inclui uma página principal com dois painéis e um <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="b479e-119">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>

1. <span data-ttu-id="b479e-120">Crie um novo projeto de aplicativo do WPF no Visual Basic ou no Visual C#, chamado `DragDropExample`.</span><span class="sxs-lookup"><span data-stu-id="b479e-120">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="b479e-121">Para obter mais informações, confira [Passo a passo: Meu primeiro aplicativo de área de trabalho do WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="b479e-121">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

2. <span data-ttu-id="b479e-122">Abra MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="b479e-122">Open MainWindow.xaml.</span></span>

3. <span data-ttu-id="b479e-123">Adicione a marcação a seguir entre as marcas de abertura e de fechamento <xref:System.Windows.Controls.Grid> .</span><span class="sxs-lookup"><span data-stu-id="b479e-123">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>

     <span data-ttu-id="b479e-124">Essa marcação cria a interface do usuário para o aplicativo de teste.</span><span class="sxs-lookup"><span data-stu-id="b479e-124">This markup creates the user interface for the test application.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a><span data-ttu-id="b479e-125">Adicionar um novo controle de usuário ao projeto</span><span class="sxs-lookup"><span data-stu-id="b479e-125">Add a New User Control to the Project</span></span>
 <span data-ttu-id="b479e-126">Nesta seção, você adicionará um novo controle de usuário ao projeto.</span><span class="sxs-lookup"><span data-stu-id="b479e-126">In this section, you will add a new user control to the project.</span></span>

1. <span data-ttu-id="b479e-127">No menu Projeto, selecione **Adicionar controle de usuário**.</span><span class="sxs-lookup"><span data-stu-id="b479e-127">On the Project menu, select **Add User Control**.</span></span>

2. <span data-ttu-id="b479e-128">Na caixa de diálogo **Adicionar novo item** , altere o nome para `Circle.xaml` e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="b479e-128">In the **Add New Item** dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>

     <span data-ttu-id="b479e-129">O Circle.xaml e seu code-behind são adicionados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="b479e-129">Circle.xaml and its code-behind is added to the project.</span></span>

3. <span data-ttu-id="b479e-130">Abra o Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="b479e-130">Open Circle.xaml.</span></span>

     <span data-ttu-id="b479e-131">Esse arquivo conterá os elementos de interface do usuário do controle de usuário.</span><span class="sxs-lookup"><span data-stu-id="b479e-131">This file will contain the user interface elements of the user control.</span></span>

4. <span data-ttu-id="b479e-132">Adicione a seguinte marcação à raiz <xref:System.Windows.Controls.Grid> para criar um controle de usuário simples que tenha um círculo azul como sua interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="b479e-132">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. <span data-ttu-id="b479e-133">Abra Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="b479e-133">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

6. <span data-ttu-id="b479e-134">No C#, adicione o código a seguir após o construtor sem parâmetros para criar um construtor de cópia.</span><span class="sxs-lookup"><span data-stu-id="b479e-134">In C#, add the following code after the parameterless constructor to create a copy constructor.</span></span> <span data-ttu-id="b479e-135">Em Visual Basic, adicione o código a seguir para criar um construtor sem parâmetros e um construtor de cópia.</span><span class="sxs-lookup"><span data-stu-id="b479e-135">In Visual Basic, add the following code to create both a parameterless constructor and a copy constructor.</span></span>

     <span data-ttu-id="b479e-136">Para permitir que o controle de usuário seja copiado, você pode adicionar um método de construtor de cópia no arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="b479e-136">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="b479e-137">No controle de usuário simplificado do círculo, será copiado apenas o preenchimento e o tamanho do controle de usuário.</span><span class="sxs-lookup"><span data-stu-id="b479e-137">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a><span data-ttu-id="b479e-138">Adicionar o controle de usuário à janela principal</span><span class="sxs-lookup"><span data-stu-id="b479e-138">Add the user control to the main window</span></span>

1. <span data-ttu-id="b479e-139">Abra MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="b479e-139">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="b479e-140">Adicione o XAML a seguir à marca de abertura <xref:System.Windows.Window> para criar uma referência de namespace XML para o aplicativo atual.</span><span class="sxs-lookup"><span data-stu-id="b479e-140">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>

    ```xaml
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. <span data-ttu-id="b479e-141">Na primeira <xref:System.Windows.Controls.StackPanel> , adicione o XAML a seguir para criar duas instâncias do controle de usuário de círculo no primeiro painel.</span><span class="sxs-lookup"><span data-stu-id="b479e-141">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     <span data-ttu-id="b479e-142">O XAML completo para o painel tem a aparência a seguir.</span><span class="sxs-lookup"><span data-stu-id="b479e-142">The full XAML for the panel looks like the following.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a><span data-ttu-id="b479e-143">Implementar eventos de arrastar origem no controle de usuário</span><span class="sxs-lookup"><span data-stu-id="b479e-143">Implement Drag Source Events in the User Control</span></span>
 <span data-ttu-id="b479e-144">Nesta seção, você substituirá o <xref:System.Windows.UIElement.OnMouseMove%2A> método e iniciará a operação de arrastar e soltar.</span><span class="sxs-lookup"><span data-stu-id="b479e-144">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>

 <span data-ttu-id="b479e-145">Se um arrastar for iniciado (um botão do mouse for pressionado e o mouse for movido), você empacotará os dados a serem transferidos para um <xref:System.Windows.DataObject> .</span><span class="sxs-lookup"><span data-stu-id="b479e-145">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="b479e-146">Nesse caso, o controle do círculo empacotará três itens de dados; uma representação de cadeia de caracteres da cor de preenchimento, uma representação dupla da altura e uma cópia de si mesmo.</span><span class="sxs-lookup"><span data-stu-id="b479e-146">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="b479e-147">Para iniciar uma operação do tipo “arrastar e soltar”</span><span class="sxs-lookup"><span data-stu-id="b479e-147">To initiate a drag-and-drop operation</span></span>

1. <span data-ttu-id="b479e-148">Abra Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="b479e-148">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="b479e-149">Adicione a substituição a seguir <xref:System.Windows.UIElement.OnMouseMove%2A> para fornecer manipulação de classe para o <xref:System.Windows.UIElement.MouseMove> evento.</span><span class="sxs-lookup"><span data-stu-id="b479e-149">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     <span data-ttu-id="b479e-150">Essa <xref:System.Windows.UIElement.OnMouseMove%2A> substituição executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="b479e-150">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="b479e-151">Verifica se o botão esquerdo do mouse é pressionado enquanto o mouse se move.</span><span class="sxs-lookup"><span data-stu-id="b479e-151">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>

    - <span data-ttu-id="b479e-152">Empacota os dados de círculo em um <xref:System.Windows.DataObject> .</span><span class="sxs-lookup"><span data-stu-id="b479e-152">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="b479e-153">Nesse caso, o controle do círculo empacota três itens de dados; uma representação de cadeia de caracteres da cor de preenchimento, uma representação dupla da altura e uma cópia de si mesmo.</span><span class="sxs-lookup"><span data-stu-id="b479e-153">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

    - <span data-ttu-id="b479e-154">Chama o <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> método estático para iniciar a operação de arrastar e soltar.</span><span class="sxs-lookup"><span data-stu-id="b479e-154">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="b479e-155">Você passa os três parâmetros a seguir para o <xref:System.Windows.DragDrop.DoDragDrop%2A> método:</span><span class="sxs-lookup"><span data-stu-id="b479e-155">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>

        - <span data-ttu-id="b479e-156">`dragSource` – Uma referência para esse controle.</span><span class="sxs-lookup"><span data-stu-id="b479e-156">`dragSource` – A reference to this control.</span></span>

        - <span data-ttu-id="b479e-157">`data`– O <xref:System.Windows.DataObject> criado no código anterior.</span><span class="sxs-lookup"><span data-stu-id="b479e-157">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>

        - <span data-ttu-id="b479e-158">`allowedEffects`– As operações de arrastar e soltar permitidas, que são <xref:System.Windows.DragDropEffects.Copy> ou <xref:System.Windows.DragDropEffects.Move> .</span><span class="sxs-lookup"><span data-stu-id="b479e-158">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="b479e-159">Selecione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b479e-159">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="b479e-160">Clique em um dos controles de círculo e arraste-o sobre os painéis, o outro círculo e o <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="b479e-160">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="b479e-161">Ao arrastar sobre o <xref:System.Windows.Controls.TextBox> , o cursor é alterado para indicar uma movimentação.</span><span class="sxs-lookup"><span data-stu-id="b479e-161">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>

5. <span data-ttu-id="b479e-162">Ao arrastar um círculo sobre o <xref:System.Windows.Controls.TextBox> , pressione a tecla **Ctrl** .</span><span class="sxs-lookup"><span data-stu-id="b479e-162">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the **Ctrl** key.</span></span> <span data-ttu-id="b479e-163">Observe como o cursor muda para indicar uma cópia.</span><span class="sxs-lookup"><span data-stu-id="b479e-163">Notice how the cursor changes to indicate a copy.</span></span>

6. <span data-ttu-id="b479e-164">Arraste e solte um círculo no <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="b479e-164">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="b479e-165">A representação de cadeia de caracteres da cor de preenchimento do círculo é anexada ao <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="b479e-165">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>

     <span data-ttu-id="b479e-166">![Representação da cadeia de caracteres da cor de preenchimento do círculo](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="b479e-166">![String representation of Circle's fill color](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>

<span data-ttu-id="b479e-167">Por padrão, o cursor será alterado durante uma operação do tipo “arrastar e soltar” para indicar qual será o efeito de soltar os dados.</span><span class="sxs-lookup"><span data-stu-id="b479e-167">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="b479e-168">Você pode personalizar os comentários fornecidos ao usuário manipulando o <xref:System.Windows.UIElement.GiveFeedback> evento e definindo um cursor diferente.</span><span class="sxs-lookup"><span data-stu-id="b479e-168">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>

## <a name="give-feedback-to-the-user"></a><span data-ttu-id="b479e-169">Enviar comentários para o usuário</span><span class="sxs-lookup"><span data-stu-id="b479e-169">Give feedback to the user</span></span>

1. <span data-ttu-id="b479e-170">Abra Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="b479e-170">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="b479e-171">Adicione a substituição a seguir <xref:System.Windows.UIElement.OnGiveFeedback%2A> para fornecer manipulação de classe para o <xref:System.Windows.UIElement.GiveFeedback> evento.</span><span class="sxs-lookup"><span data-stu-id="b479e-171">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     <span data-ttu-id="b479e-172">Essa <xref:System.Windows.UIElement.OnGiveFeedback%2A> substituição executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="b479e-172">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="b479e-173">Verifica os <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> valores que são definidos no manipulador de eventos de soltar destino <xref:System.Windows.UIElement.DragOver> .</span><span class="sxs-lookup"><span data-stu-id="b479e-173">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

    - <span data-ttu-id="b479e-174">Define um cursor personalizado com base no <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> valor.</span><span class="sxs-lookup"><span data-stu-id="b479e-174">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="b479e-175">O cursor deve fornecer comentários visuais ao usuário a respeito de qual será o efeito de soltar os dados.</span><span class="sxs-lookup"><span data-stu-id="b479e-175">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>

3. <span data-ttu-id="b479e-176">Selecione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b479e-176">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="b479e-177">Arraste um dos controles de círculo sobre os painéis, o outro círculo e o <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="b479e-177">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="b479e-178">Observe que os cursores são agora os cursores personalizados que você especificou na <xref:System.Windows.UIElement.OnGiveFeedback%2A> substituição.</span><span class="sxs-lookup"><span data-stu-id="b479e-178">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>

     <span data-ttu-id="b479e-179">![Arrastar e soltar com cursores personalizados](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="b479e-179">![Drag and drop with custom cursors](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>

5. <span data-ttu-id="b479e-180">Selecione o texto `green` do <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="b479e-180">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

6. <span data-ttu-id="b479e-181">Arraste o texto `green` para um controle do círculo.</span><span class="sxs-lookup"><span data-stu-id="b479e-181">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="b479e-182">Observe que os cursores padrão são mostrados para indicar os efeitos da operação do tipo “arrastar e soltar”.</span><span class="sxs-lookup"><span data-stu-id="b479e-182">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="b479e-183">O cursor de comentários sempre é definido pela fonte de arrastar.</span><span class="sxs-lookup"><span data-stu-id="b479e-183">The feedback cursor is always set by the drag source.</span></span>

## <a name="implement-drop-target-events-in-the-user-control"></a><span data-ttu-id="b479e-184">Implementar eventos de soltar destino no controle de usuário</span><span class="sxs-lookup"><span data-stu-id="b479e-184">Implement Drop Target Events in the User Control</span></span>
 <span data-ttu-id="b479e-185">Nesta seção, você especificará que o controle de usuário é um destino de soltar, substituirá os métodos que permitem que o controle de usuário seja um destino de soltar e processará os dados soltos nele.</span><span class="sxs-lookup"><span data-stu-id="b479e-185">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="b479e-186">Para permitir que o controle de usuário seja um destino de soltar</span><span class="sxs-lookup"><span data-stu-id="b479e-186">To enable the user control to be a drop target</span></span>

1. <span data-ttu-id="b479e-187">Abra o Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="b479e-187">Open Circle.xaml.</span></span>

2. <span data-ttu-id="b479e-188">Na marca de abertura <xref:System.Windows.Controls.UserControl> , adicione a <xref:System.Windows.UIElement.AllowDrop%2A> propriedade e defina-a como `true` .</span><span class="sxs-lookup"><span data-stu-id="b479e-188">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

<span data-ttu-id="b479e-189">O <xref:System.Windows.UIElement.OnDrop%2A> método é chamado quando a <xref:System.Windows.UIElement.AllowDrop%2A> propriedade é definida como `true` e os dados da fonte de arrastar são descartados no controle de usuário de círculo.</span><span class="sxs-lookup"><span data-stu-id="b479e-189">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="b479e-190">Nesse método, você processará os dados que foram soltos e aplicará os dados ao círculo.</span><span class="sxs-lookup"><span data-stu-id="b479e-190">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>

### <a name="to-process-the-dropped-data"></a><span data-ttu-id="b479e-191">Para processar os dados soltos</span><span class="sxs-lookup"><span data-stu-id="b479e-191">To process the dropped data</span></span>

1. <span data-ttu-id="b479e-192">Abra Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="b479e-192">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="b479e-193">Adicione a substituição a seguir <xref:System.Windows.UIElement.OnDrop%2A> para fornecer manipulação de classe para o <xref:System.Windows.UIElement.Drop> evento.</span><span class="sxs-lookup"><span data-stu-id="b479e-193">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     <span data-ttu-id="b479e-194">Essa <xref:System.Windows.UIElement.OnDrop%2A> substituição executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="b479e-194">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="b479e-195">Usa o <xref:System.Windows.DataObject.GetDataPresent%2A> método para verificar se os dados arrastados contêm um objeto de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b479e-195">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>

    - <span data-ttu-id="b479e-196">Usa o <xref:System.Windows.DataObject.GetData%2A> método para extrair os dados de cadeia de caracteres, se estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="b479e-196">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>

    - <span data-ttu-id="b479e-197">Usa um <xref:System.Windows.Media.BrushConverter> para tentar converter a cadeia de caracteres em um <xref:System.Windows.Media.Brush> .</span><span class="sxs-lookup"><span data-stu-id="b479e-197">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="b479e-198">Se a conversão for bem-sucedida, o aplicará o pincel ao <xref:System.Windows.Shapes.Shape.Fill%2A> do <xref:System.Windows.Shapes.Ellipse> que fornece a interface do usuário do controle de círculo.</span><span class="sxs-lookup"><span data-stu-id="b479e-198">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>

    - <span data-ttu-id="b479e-199">Marca o <xref:System.Windows.UIElement.Drop> evento como manipulado.</span><span class="sxs-lookup"><span data-stu-id="b479e-199">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="b479e-200">O evento de soltar deve ser marcado como manipulado para que os outros elementos que o recebem saibam que foi manipulado pelo controle de usuário do círculo.</span><span class="sxs-lookup"><span data-stu-id="b479e-200">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>

3. <span data-ttu-id="b479e-201">Selecione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b479e-201">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="b479e-202">Selecione o texto `green` no <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="b479e-202">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="b479e-203">Arraste o texto para um controle do círculo e solte-o.</span><span class="sxs-lookup"><span data-stu-id="b479e-203">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="b479e-204">O círculo muda de azul para verde.</span><span class="sxs-lookup"><span data-stu-id="b479e-204">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="b479e-205">![Converter uma cadeia de caracteres em um pincel](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="b479e-205">![Convert a string to a brush](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>

6. <span data-ttu-id="b479e-206">Digite o texto `green` no <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="b479e-206">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="b479e-207">Selecione o texto `gre` no <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="b479e-207">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="b479e-208">Arraste-o para um controle do círculo e solte-o.</span><span class="sxs-lookup"><span data-stu-id="b479e-208">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="b479e-209">Observe que o cursor muda para indicar que é permitido soltar; porém, a cor do círculo não muda, porque `gre` não é uma cor válida.</span><span class="sxs-lookup"><span data-stu-id="b479e-209">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>

9. <span data-ttu-id="b479e-210">Arraste do controle do círculo verde e solte no controle do círculo azul.</span><span class="sxs-lookup"><span data-stu-id="b479e-210">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="b479e-211">O círculo muda de azul para verde.</span><span class="sxs-lookup"><span data-stu-id="b479e-211">The Circle changes from blue to green.</span></span> <span data-ttu-id="b479e-212">Observe que o cursor mostrado depende de se o <xref:System.Windows.Controls.TextBox> círculo ou é a origem do arrasto.</span><span class="sxs-lookup"><span data-stu-id="b479e-212">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>

<span data-ttu-id="b479e-213">Definir a <xref:System.Windows.UIElement.AllowDrop%2A> propriedade para `true` e processar os dados descartados é tudo o que é necessário para permitir que um elemento seja um destino de soltar.</span><span class="sxs-lookup"><span data-stu-id="b479e-213">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="b479e-214">No entanto, para fornecer uma melhor experiência do usuário, você também deve manipular os <xref:System.Windows.UIElement.DragEnter> <xref:System.Windows.UIElement.DragLeave> eventos, e <xref:System.Windows.UIElement.DragOver> .</span><span class="sxs-lookup"><span data-stu-id="b479e-214">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="b479e-215">Nesses eventos, é possível executar verificações e fornecer comentários adicionais ao usuário antes de soltar os dados.</span><span class="sxs-lookup"><span data-stu-id="b479e-215">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>

<span data-ttu-id="b479e-216">Quando dados são arrastados sobre o controle de usuário do círculo, o controle deve notificar a fonte de arrasto se os dados arrastados podem ser processados.</span><span class="sxs-lookup"><span data-stu-id="b479e-216">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="b479e-217">Se o controle não souber como processar os dados, deverá recusá-los quando forem soltos.</span><span class="sxs-lookup"><span data-stu-id="b479e-217">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="b479e-218">Para fazer isso, você manipulará o <xref:System.Windows.UIElement.DragOver> evento e definirá a <xref:System.Windows.DragEventArgs.Effects%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="b479e-218">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>

### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="b479e-219">Para verificar se é permitido soltar os dados</span><span class="sxs-lookup"><span data-stu-id="b479e-219">To verify that the data drop is allowed</span></span>

1. <span data-ttu-id="b479e-220">Abra Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="b479e-220">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="b479e-221">Adicione a substituição a seguir <xref:System.Windows.UIElement.OnDragOver%2A> para fornecer manipulação de classe para o <xref:System.Windows.UIElement.DragOver> evento.</span><span class="sxs-lookup"><span data-stu-id="b479e-221">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     <span data-ttu-id="b479e-222">Essa <xref:System.Windows.UIElement.OnDragOver%2A> substituição executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="b479e-222">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="b479e-223">Define a propriedade <xref:System.Windows.DragEventArgs.Effects%2A> como <xref:System.Windows.DragDropEffects.None>.</span><span class="sxs-lookup"><span data-stu-id="b479e-223">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>

    - <span data-ttu-id="b479e-224">Executa as mesmas verificações que são executadas no <xref:System.Windows.UIElement.OnDrop%2A> método para determinar se o controle de usuário de círculo pode processar os dados arrastados.</span><span class="sxs-lookup"><span data-stu-id="b479e-224">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>

    - <span data-ttu-id="b479e-225">Se o controle de usuário puder processar os dados, o definirá a <xref:System.Windows.DragEventArgs.Effects%2A> propriedade como <xref:System.Windows.DragDropEffects.Copy> ou <xref:System.Windows.DragDropEffects.Move> .</span><span class="sxs-lookup"><span data-stu-id="b479e-225">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="b479e-226">Selecione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b479e-226">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="b479e-227">Selecione o texto `gre` no <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="b479e-227">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="b479e-228">Arraste o texto para um controle do círculo.</span><span class="sxs-lookup"><span data-stu-id="b479e-228">Drag the text to a Circle control.</span></span> <span data-ttu-id="b479e-229">Observe que, agora, o cursor muda para indicar que não é permitido soltar, porque `gre` não é uma cor válida.</span><span class="sxs-lookup"><span data-stu-id="b479e-229">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>

 <span data-ttu-id="b479e-230">É possível aprimorar ainda mais a experiência do usuário por meio da aplicação de uma visualização da operação do tipo “soltar”.</span><span class="sxs-lookup"><span data-stu-id="b479e-230">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="b479e-231">Para o controle de usuário de círculo, você substituirá os <xref:System.Windows.UIElement.OnDragEnter%2A> <xref:System.Windows.UIElement.OnDragLeave%2A> métodos e.</span><span class="sxs-lookup"><span data-stu-id="b479e-231">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="b479e-232">Quando os dados são arrastados sobre o controle, o plano de fundo atual <xref:System.Windows.Shapes.Shape.Fill%2A> é salvo em uma variável de espaço reservado.</span><span class="sxs-lookup"><span data-stu-id="b479e-232">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="b479e-233">Em seguida, a cadeia de caracteres é convertida em um pincel e aplicada ao <xref:System.Windows.Shapes.Ellipse> que fornece a interface do usuário do círculo.</span><span class="sxs-lookup"><span data-stu-id="b479e-233">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="b479e-234">Se os dados forem arrastados para fora do círculo sem serem descartados, o <xref:System.Windows.Shapes.Shape.Fill%2A> valor original será aplicado novamente ao círculo.</span><span class="sxs-lookup"><span data-stu-id="b479e-234">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="b479e-235">Para visualizar os efeitos da operação do tipo “arrastar e soltar”</span><span class="sxs-lookup"><span data-stu-id="b479e-235">To preview the effects of the drag-and-drop operation</span></span>

1. <span data-ttu-id="b479e-236">Abra Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="b479e-236">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="b479e-237">Na classe Circle, declare uma variável privada <xref:System.Windows.Media.Brush> chamada `_previousFill` e a inicialize como `null` .</span><span class="sxs-lookup"><span data-stu-id="b479e-237">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. <span data-ttu-id="b479e-238">Adicione a substituição a seguir <xref:System.Windows.UIElement.OnDragEnter%2A> para fornecer manipulação de classe para o <xref:System.Windows.UIElement.DragEnter> evento.</span><span class="sxs-lookup"><span data-stu-id="b479e-238">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     <span data-ttu-id="b479e-239">Essa <xref:System.Windows.UIElement.OnDragEnter%2A> substituição executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="b479e-239">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="b479e-240">Salva a <xref:System.Windows.Shapes.Shape.Fill%2A> Propriedade do <xref:System.Windows.Shapes.Ellipse> na `_previousFill` variável.</span><span class="sxs-lookup"><span data-stu-id="b479e-240">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>

    - <span data-ttu-id="b479e-241">Executa as mesmas verificações que são executadas no <xref:System.Windows.UIElement.OnDrop%2A> método para determinar se os dados podem ser convertidos em um <xref:System.Windows.Media.Brush> .</span><span class="sxs-lookup"><span data-stu-id="b479e-241">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="b479e-242">Se os dados forem convertidos em um válido, o o <xref:System.Windows.Media.Brush> aplicará ao <xref:System.Windows.Shapes.Shape.Fill%2A> do <xref:System.Windows.Shapes.Ellipse> .</span><span class="sxs-lookup"><span data-stu-id="b479e-242">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>

4. <span data-ttu-id="b479e-243">Adicione a substituição a seguir <xref:System.Windows.UIElement.OnDragLeave%2A> para fornecer manipulação de classe para o <xref:System.Windows.UIElement.DragLeave> evento.</span><span class="sxs-lookup"><span data-stu-id="b479e-243">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     <span data-ttu-id="b479e-244">Essa <xref:System.Windows.UIElement.OnDragLeave%2A> substituição executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="b479e-244">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="b479e-245">Aplica o <xref:System.Windows.Media.Brush> salvo na `_previousFill` variável ao <xref:System.Windows.Shapes.Shape.Fill%2A> do <xref:System.Windows.Shapes.Ellipse> que fornece a interface do usuário do controle de usuários de círculo.</span><span class="sxs-lookup"><span data-stu-id="b479e-245">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>

5. <span data-ttu-id="b479e-246">Selecione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b479e-246">Press **F5** to build and run the application.</span></span>

6. <span data-ttu-id="b479e-247">Selecione o texto `green` no <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="b479e-247">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="b479e-248">Arraste o texto sobre um controle do círculo sem soltá-lo.</span><span class="sxs-lookup"><span data-stu-id="b479e-248">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="b479e-249">O círculo muda de azul para verde.</span><span class="sxs-lookup"><span data-stu-id="b479e-249">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="b479e-250">![Visualizar os efeitos de uma operação arrastar&#45;e&#45;soltar](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="b479e-250">![Preview the effects of a drag&#45;and&#45;drop operation](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>

8. <span data-ttu-id="b479e-251">Arraste o texto para fora do controle do círculo.</span><span class="sxs-lookup"><span data-stu-id="b479e-251">Drag the text away from the Circle control.</span></span> <span data-ttu-id="b479e-252">O círculo volta de verde para azul.</span><span class="sxs-lookup"><span data-stu-id="b479e-252">The Circle changes from green back to blue.</span></span>

## <a name="enable-a-panel-to-receive-dropped-data"></a><span data-ttu-id="b479e-253">Habilitar um painel para receber dados descartados</span><span class="sxs-lookup"><span data-stu-id="b479e-253">Enable a Panel to Receive Dropped Data</span></span>

<span data-ttu-id="b479e-254">Nesta seção, você habilita os painéis que hospedam os controles de usuário de círculo para atuar como destinos de soltar para dados de círculo arrastados.</span><span class="sxs-lookup"><span data-stu-id="b479e-254">In this section, you enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="b479e-255">Você implementará o código que permite mover um círculo de um painel para outro ou para fazer uma cópia de um controle de círculo mantendo pressionada a tecla **Ctrl** enquanto arrasta e solta um círculo.</span><span class="sxs-lookup"><span data-stu-id="b479e-255">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the **Ctrl** key while dragging and dropping a Circle.</span></span>

1. <span data-ttu-id="b479e-256">Abra MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="b479e-256">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="b479e-257">Conforme mostrado no XAML a seguir, em cada um dos <xref:System.Windows.Controls.StackPanel> controles, adicione manipuladores para os <xref:System.Windows.UIElement.DragOver> <xref:System.Windows.UIElement.Drop> eventos e.</span><span class="sxs-lookup"><span data-stu-id="b479e-257">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="b479e-258">Nomeie o <xref:System.Windows.UIElement.DragOver> manipulador de eventos, `panel_DragOver` e nomeie o <xref:System.Windows.UIElement.Drop> manipulador de eventos, `panel_Drop` .</span><span class="sxs-lookup"><span data-stu-id="b479e-258">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. <span data-ttu-id="b479e-259">Abra MainWindows.xaml.cs ou MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="b479e-259">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>

4. <span data-ttu-id="b479e-260">Adicione o código a seguir para o <xref:System.Windows.UIElement.DragOver> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="b479e-260">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     <span data-ttu-id="b479e-261">Esse <xref:System.Windows.UIElement.DragOver> manipulador de eventos executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="b479e-261">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="b479e-262">Verifica se os dados arrastados contêm os dados de "objeto" que foram empacotados no <xref:System.Windows.DataObject> pelo controle de usuário de círculo e passados na chamada para <xref:System.Windows.DragDrop.DoDragDrop%2A> .</span><span class="sxs-lookup"><span data-stu-id="b479e-262">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>

    - <span data-ttu-id="b479e-263">Se os dados de "objeto" estiverem presentes, o verificará se a tecla **Ctrl** foi pressionada.</span><span class="sxs-lookup"><span data-stu-id="b479e-263">If the "Object" data is present, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="b479e-264">Se a tecla **Ctrl** for pressionada, definirá a <xref:System.Windows.DragEventArgs.Effects%2A> propriedade como <xref:System.Windows.DragDropEffects.Copy> .</span><span class="sxs-lookup"><span data-stu-id="b479e-264">If the **Ctrl** key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="b479e-265">Caso contrário, defina a <xref:System.Windows.DragEventArgs.Effects%2A> propriedade como <xref:System.Windows.DragDropEffects.Move> .</span><span class="sxs-lookup"><span data-stu-id="b479e-265">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>

5. <span data-ttu-id="b479e-266">Adicione o código a seguir para o <xref:System.Windows.UIElement.Drop> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="b479e-266">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     <span data-ttu-id="b479e-267">Esse <xref:System.Windows.UIElement.Drop> manipulador de eventos executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="b479e-267">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="b479e-268">Verifica se o <xref:System.Windows.UIElement.Drop> evento já foi tratado.</span><span class="sxs-lookup"><span data-stu-id="b479e-268">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="b479e-269">Por exemplo, se um círculo for descartado em outro círculo que manipula o <xref:System.Windows.UIElement.Drop> evento, você não desejará que o painel que contém o círculo também o manipule.</span><span class="sxs-lookup"><span data-stu-id="b479e-269">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>

    - <span data-ttu-id="b479e-270">Se o <xref:System.Windows.UIElement.Drop> evento não for tratado, o verificará se a tecla **Ctrl** foi pressionada.</span><span class="sxs-lookup"><span data-stu-id="b479e-270">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="b479e-271">Se a tecla **Ctrl** for pressionada quando <xref:System.Windows.UIElement.Drop> acontecer, o fará uma cópia do controle de círculo e a adicionará à <xref:System.Windows.Controls.Panel.Children%2A> coleção do <xref:System.Windows.Controls.StackPanel> .</span><span class="sxs-lookup"><span data-stu-id="b479e-271">If the **Ctrl** key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>

    - <span data-ttu-id="b479e-272">Se a tecla **Ctrl** não for pressionada, o moverá o círculo da <xref:System.Windows.Controls.Panel.Children%2A> coleção de seu painel pai para a <xref:System.Windows.Controls.Panel.Children%2A> coleção do painel em que foi Descartado.</span><span class="sxs-lookup"><span data-stu-id="b479e-272">If the **Ctrl** key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>

    - <span data-ttu-id="b479e-273">Define a <xref:System.Windows.DragEventArgs.Effects%2A> propriedade para notificar o <xref:System.Windows.DragDrop.DoDragDrop%2A> método se uma operação de movimentação ou cópia foi executada.</span><span class="sxs-lookup"><span data-stu-id="b479e-273">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>

6. <span data-ttu-id="b479e-274">Selecione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b479e-274">Press **F5** to build and run the application.</span></span>

7. <span data-ttu-id="b479e-275">Selecione o texto `green` do <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="b479e-275">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="b479e-276">Arraste o texto sobre um controle do círculo e solte-o.</span><span class="sxs-lookup"><span data-stu-id="b479e-276">Drag the text over a Circle control and drop it.</span></span>

9. <span data-ttu-id="b479e-277">Arraste um controle do círculo do painel esquerdo para o painel direito e solte-o.</span><span class="sxs-lookup"><span data-stu-id="b479e-277">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="b479e-278">O círculo é removido da <xref:System.Windows.Controls.Panel.Children%2A> coleção do painel esquerdo e adicionado à coleção Children do painel direito.</span><span class="sxs-lookup"><span data-stu-id="b479e-278">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>

10. <span data-ttu-id="b479e-279">Arraste um controle de círculo do painel no qual ele está no outro painel e solte-o enquanto pressiona a tecla **Ctrl** .</span><span class="sxs-lookup"><span data-stu-id="b479e-279">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the **Ctrl** key.</span></span> <span data-ttu-id="b479e-280">O círculo é copiado e a cópia é adicionada à <xref:System.Windows.Controls.Panel.Children%2A> coleção do painel de recebimento.</span><span class="sxs-lookup"><span data-stu-id="b479e-280">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>

     <span data-ttu-id="b479e-281">![Arrastando um círculo enquanto pressiona a tecla CTRL](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="b479e-281">![Dragging a Circle while pressing the CTRL key](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>

## <a name="see-also"></a><span data-ttu-id="b479e-282">Confira também</span><span class="sxs-lookup"><span data-stu-id="b479e-282">See also</span></span>

- [<span data-ttu-id="b479e-283">Visão geral de arrastar e soltar</span><span class="sxs-lookup"><span data-stu-id="b479e-283">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
