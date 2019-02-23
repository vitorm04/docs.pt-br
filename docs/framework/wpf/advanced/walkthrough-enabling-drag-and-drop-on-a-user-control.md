---
title: 'Passo a passo: Habilitando arrastar e soltar em um controle de usuário'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: a2aa1d09b922809f42fe14bd674c2a87b9e5a3f8
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747789"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="47723-102">Passo a passo: Habilitando arrastar e soltar em um controle de usuário</span><span class="sxs-lookup"><span data-stu-id="47723-102">Walkthrough: Enabling Drag and Drop on a User Control</span></span>

<span data-ttu-id="47723-103">Este passo a passo demonstra como criar um controle de usuário personalizado que pode participar na transferência de dados por arrastar e soltar no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="47723-103">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>

<span data-ttu-id="47723-104">Neste passo a passo, você criará um WPF personalizado <xref:System.Windows.Controls.UserControl> que representa uma forma de círculo.</span><span class="sxs-lookup"><span data-stu-id="47723-104">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="47723-105">Você implementará a funcionalidade no controle para permitir a transferência de dados por meio de arrastar e soltar.</span><span class="sxs-lookup"><span data-stu-id="47723-105">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="47723-106">Por exemplo, se você arrastar de um controle do círculo para outro, os dados de cor de preenchimento serão copiados do círculo de origem para o destino.</span><span class="sxs-lookup"><span data-stu-id="47723-106">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="47723-107">Se você arrastar de um controle do círculo para uma <xref:System.Windows.Controls.TextBox>, a representação de cadeia de caracteres da cor de preenchimento é copiada para o <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="47723-107">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="47723-108">Você também criará um aplicativo pequeno que contém dois controles de painel e um <xref:System.Windows.Controls.TextBox> para testar a funcionalidade de arrastar e soltar.</span><span class="sxs-lookup"><span data-stu-id="47723-108">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="47723-109">Será gravado um código que permite que os painéis processem os dados do círculo que foram soltos, o que permitirá mover ou copiar círculos da coleção de filhos de um painel para o outro.</span><span class="sxs-lookup"><span data-stu-id="47723-109">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>

<span data-ttu-id="47723-110">Esta explicação passo a passo ilustra as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="47723-110">This walkthrough illustrates the following tasks:</span></span>

-   <span data-ttu-id="47723-111">Crie um controle de usuário personalizado.</span><span class="sxs-lookup"><span data-stu-id="47723-111">Create a custom user control.</span></span>

-   <span data-ttu-id="47723-112">Habilite o controle de usuário como uma fonte de arrastar.</span><span class="sxs-lookup"><span data-stu-id="47723-112">Enable the user control to be a drag source.</span></span>

-   <span data-ttu-id="47723-113">Habilite o controle de usuário como um destino de soltar.</span><span class="sxs-lookup"><span data-stu-id="47723-113">Enable the user control to be a drop target.</span></span>

-   <span data-ttu-id="47723-114">Habilite um painel para receber dados que foram soltos pelo controle de usuário.</span><span class="sxs-lookup"><span data-stu-id="47723-114">Enable a panel to receive data dropped from the user control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="47723-115">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="47723-115">Prerequisites</span></span>

<span data-ttu-id="47723-116">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="47723-116">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="47723-117">Criar o projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="47723-117">Create the Application Project</span></span>
 <span data-ttu-id="47723-118">Nesta seção, você criará a infraestrutura de aplicativo, que inclui uma página principal com dois painéis e uma <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="47723-118">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>

1.  <span data-ttu-id="47723-119">Crie um novo projeto de aplicativo do WPF no Visual Basic ou no Visual C#, chamado `DragDropExample`.</span><span class="sxs-lookup"><span data-stu-id="47723-119">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="47723-120">Para obter mais informações, confira [Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="47723-120">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

2.  <span data-ttu-id="47723-121">Abra MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="47723-121">Open MainWindow.xaml.</span></span>

3.  <span data-ttu-id="47723-122">Adicione a seguinte marcação entre a abertura e fechamento <xref:System.Windows.Controls.Grid> marcas.</span><span class="sxs-lookup"><span data-stu-id="47723-122">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>

     <span data-ttu-id="47723-123">Essa marcação cria a interface do usuário para o aplicativo de teste.</span><span class="sxs-lookup"><span data-stu-id="47723-123">This markup creates the user interface for the test application.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a><span data-ttu-id="47723-124">Adicionar um novo controle de usuário ao projeto</span><span class="sxs-lookup"><span data-stu-id="47723-124">Add a New User Control to the Project</span></span>
 <span data-ttu-id="47723-125">Nesta seção, você adicionará um novo controle de usuário ao projeto.</span><span class="sxs-lookup"><span data-stu-id="47723-125">In this section, you will add a new user control to the project.</span></span>

1.  <span data-ttu-id="47723-126">No menu Projeto, selecione **Adicionar controle de usuário**.</span><span class="sxs-lookup"><span data-stu-id="47723-126">On the Project menu, select **Add User Control**.</span></span>

2.  <span data-ttu-id="47723-127">No **Adicionar Novo Item** caixa de diálogo, altere o nome a ser `Circle.xaml`e clique em **Add**.</span><span class="sxs-lookup"><span data-stu-id="47723-127">In the **Add New Item** dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>

     <span data-ttu-id="47723-128">O Circle.xaml e seu code-behind são adicionados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="47723-128">Circle.xaml and its code-behind is added to the project.</span></span>

3.  <span data-ttu-id="47723-129">Abra o Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="47723-129">Open Circle.xaml.</span></span>

     <span data-ttu-id="47723-130">Esse arquivo conterá os elementos de interface do usuário do controle de usuário.</span><span class="sxs-lookup"><span data-stu-id="47723-130">This file will contain the user interface elements of the user control.</span></span>

4.  <span data-ttu-id="47723-131">Adicione a seguinte marcação para a raiz <xref:System.Windows.Controls.Grid> para criar um controle de usuário simples que tem um círculo azul como sua interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="47723-131">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>

     [!code-xaml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5.  <span data-ttu-id="47723-132">Abra Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="47723-132">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

6.  <span data-ttu-id="47723-133">No C#, adicione o código a seguir após o construtor padrão para criar um construtor de cópia.</span><span class="sxs-lookup"><span data-stu-id="47723-133">In C#, add the following code after the default constructor to create a copy constructor.</span></span> <span data-ttu-id="47723-134">No Visual Basic, adicione o código a seguir para criar um construtor padrão e um construtor de cópia.</span><span class="sxs-lookup"><span data-stu-id="47723-134">In Visual Basic, add the following code to create both a default constructor and a copy constructor.</span></span>

     <span data-ttu-id="47723-135">Para permitir que o controle de usuário seja copiado, você pode adicionar um método de construtor de cópia no arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="47723-135">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="47723-136">No controle de usuário simplificado do círculo, será copiado apenas o preenchimento e o tamanho do controle de usuário.</span><span class="sxs-lookup"><span data-stu-id="47723-136">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>

     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a><span data-ttu-id="47723-137">Adicionar o controle de usuário para a janela principal</span><span class="sxs-lookup"><span data-stu-id="47723-137">Add the user control to the main window</span></span>

1.  <span data-ttu-id="47723-138">Abra MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="47723-138">Open MainWindow.xaml.</span></span>

2.  <span data-ttu-id="47723-139">Adicionar o XAML a seguir para a abertura <xref:System.Windows.Window> marca para criar uma referência ao namespace XML para o aplicativo atual.</span><span class="sxs-lookup"><span data-stu-id="47723-139">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>

    ```
    xmlns:local="clr-namespace:DragDropExample"
    ```

3.  <span data-ttu-id="47723-140">Na primeira <xref:System.Windows.Controls.StackPanel>, adicione o seguinte XAML para criar duas instâncias do controle de usuário do círculo no primeiro painel.</span><span class="sxs-lookup"><span data-stu-id="47723-140">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>

     [!code-xaml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     <span data-ttu-id="47723-141">O XAML completo para o painel tem a aparência a seguir.</span><span class="sxs-lookup"><span data-stu-id="47723-141">The full XAML for the panel looks like the following.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a><span data-ttu-id="47723-142">Implementar eventos de origem do arrasto no controle de usuário</span><span class="sxs-lookup"><span data-stu-id="47723-142">Implement Drag Source Events in the User Control</span></span>
 <span data-ttu-id="47723-143">Nesta seção, você substituirá o <xref:System.Windows.UIElement.OnMouseMove%2A> método e inicia a operação de arrastar e soltar.</span><span class="sxs-lookup"><span data-stu-id="47723-143">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>

 <span data-ttu-id="47723-144">Se uma operação de arrastar for iniciada (um botão do mouse é pressionado e o mouse é movido), você empacotará os dados a serem transferidos para um <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="47723-144">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="47723-145">Nesse caso, o controle do círculo empacotará três itens de dados; uma representação de cadeia de caracteres da cor de preenchimento, uma representação dupla da altura e uma cópia de si mesmo.</span><span class="sxs-lookup"><span data-stu-id="47723-145">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="47723-146">Para iniciar uma operação do tipo “arrastar e soltar”</span><span class="sxs-lookup"><span data-stu-id="47723-146">To initiate a drag-and-drop operation</span></span>

1.  <span data-ttu-id="47723-147">Abra Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="47723-147">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2.  <span data-ttu-id="47723-148">Adicione o seguinte <xref:System.Windows.UIElement.OnMouseMove%2A> substituição é para fornecer manipulação de classe para o <xref:System.Windows.UIElement.MouseMove> eventos.</span><span class="sxs-lookup"><span data-stu-id="47723-148">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     <span data-ttu-id="47723-149">Isso <xref:System.Windows.UIElement.OnMouseMove%2A> substituição executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="47723-149">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>

    -   <span data-ttu-id="47723-150">Verifica se o botão esquerdo do mouse é pressionado enquanto o mouse se move.</span><span class="sxs-lookup"><span data-stu-id="47723-150">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>

    -   <span data-ttu-id="47723-151">Empacota os dados do círculo em um <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="47723-151">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="47723-152">Nesse caso, o controle do círculo empacota três itens de dados; uma representação de cadeia de caracteres da cor de preenchimento, uma representação dupla da altura e uma cópia de si mesmo.</span><span class="sxs-lookup"><span data-stu-id="47723-152">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

    -   <span data-ttu-id="47723-153">Chama estático <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> método para iniciar a operação de arrastar e soltar.</span><span class="sxs-lookup"><span data-stu-id="47723-153">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="47723-154">Você passa três parâmetros a seguir para o <xref:System.Windows.DragDrop.DoDragDrop%2A> método:</span><span class="sxs-lookup"><span data-stu-id="47723-154">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>

        -   <span data-ttu-id="47723-155">`dragSource` – Uma referência para esse controle.</span><span class="sxs-lookup"><span data-stu-id="47723-155">`dragSource` – A reference to this control.</span></span>

        -   <span data-ttu-id="47723-156">`data` – A <xref:System.Windows.DataObject> criado no código anterior.</span><span class="sxs-lookup"><span data-stu-id="47723-156">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>

        -   <span data-ttu-id="47723-157">`allowedEffects` – As operações de arrastar e soltar permitidas, que são <xref:System.Windows.DragDropEffects.Copy> ou <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="47723-157">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3.  <span data-ttu-id="47723-158">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="47723-158">Press **F5** to build and run the application.</span></span>

4.  <span data-ttu-id="47723-159">Clique em um dos controles do círculo e arraste-o sobre os painéis, o outro círculo e o <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="47723-159">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="47723-160">Ao arrastar sobre a <xref:System.Windows.Controls.TextBox>, o cursor muda para indicar um movimento.</span><span class="sxs-lookup"><span data-stu-id="47723-160">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>

5.  <span data-ttu-id="47723-161">Enquanto arrasta um círculo sobre o <xref:System.Windows.Controls.TextBox>, pressione a **Ctrl** chave.</span><span class="sxs-lookup"><span data-stu-id="47723-161">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the **Ctrl** key.</span></span> <span data-ttu-id="47723-162">Observe como o cursor muda para indicar uma cópia.</span><span class="sxs-lookup"><span data-stu-id="47723-162">Notice how the cursor changes to indicate a copy.</span></span>

6.  <span data-ttu-id="47723-163">Arraste e solte um círculo no <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="47723-163">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="47723-164">A representação de cadeia de caracteres da cor de preenchimento do círculo é acrescentada ao <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="47723-164">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>

     <span data-ttu-id="47723-165">![Representação de cadeia de caracteres da cor de preenchimento do círculo](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="47723-165">![String representation of Circle's fill color](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>

<span data-ttu-id="47723-166">Por padrão, o cursor será alterado durante uma operação do tipo “arrastar e soltar” para indicar qual será o efeito de soltar os dados.</span><span class="sxs-lookup"><span data-stu-id="47723-166">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="47723-167">Você pode personalizar os comentários fornecidos ao usuário manipulando o <xref:System.Windows.UIElement.GiveFeedback> evento e definindo um cursor diferente.</span><span class="sxs-lookup"><span data-stu-id="47723-167">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>

## <a name="give-feedback-to-the-user"></a><span data-ttu-id="47723-168">Fornecer comentários ao usuário</span><span class="sxs-lookup"><span data-stu-id="47723-168">Give feedback to the user</span></span>

1.  <span data-ttu-id="47723-169">Abra Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="47723-169">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2.  <span data-ttu-id="47723-170">Adicione o seguinte <xref:System.Windows.UIElement.OnGiveFeedback%2A> substituição é para fornecer manipulação de classe para o <xref:System.Windows.UIElement.GiveFeedback> eventos.</span><span class="sxs-lookup"><span data-stu-id="47723-170">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     <span data-ttu-id="47723-171">Isso <xref:System.Windows.UIElement.OnGiveFeedback%2A> substituição executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="47723-171">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>

    -   <span data-ttu-id="47723-172">Verifica a <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> valores que são definidos no destino de soltar <xref:System.Windows.UIElement.DragOver> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="47723-172">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

    -   <span data-ttu-id="47723-173">Define um cursor personalizado com base no <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> valor.</span><span class="sxs-lookup"><span data-stu-id="47723-173">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="47723-174">O cursor deve fornecer comentários visuais ao usuário a respeito de qual será o efeito de soltar os dados.</span><span class="sxs-lookup"><span data-stu-id="47723-174">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>

3.  <span data-ttu-id="47723-175">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="47723-175">Press **F5** to build and run the application.</span></span>

4.  <span data-ttu-id="47723-176">Arraste um dos círculo controla ao longo de painéis, o outro círculo, e o <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="47723-176">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="47723-177">Observe que os cursores agora são os cursores personalizados que você especificou no <xref:System.Windows.UIElement.OnGiveFeedback%2A> substituir.</span><span class="sxs-lookup"><span data-stu-id="47723-177">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>

     <span data-ttu-id="47723-178">![Arraste e solte com os cursores personalizados](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="47723-178">![Drag and drop with custom cursors](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>

5.  <span data-ttu-id="47723-179">Selecione o texto `green` do <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="47723-179">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

6.  <span data-ttu-id="47723-180">Arraste o texto `green` para um controle do círculo.</span><span class="sxs-lookup"><span data-stu-id="47723-180">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="47723-181">Observe que os cursores padrão são mostrados para indicar os efeitos da operação do tipo “arrastar e soltar”.</span><span class="sxs-lookup"><span data-stu-id="47723-181">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="47723-182">O cursor de comentários sempre é definido pela fonte de arrastar.</span><span class="sxs-lookup"><span data-stu-id="47723-182">The feedback cursor is always set by the drag source.</span></span>

## <a name="implement-drop-target-events-in-the-user-control"></a><span data-ttu-id="47723-183">Implementar eventos de destino de soltar no controle de usuário</span><span class="sxs-lookup"><span data-stu-id="47723-183">Implement Drop Target Events in the User Control</span></span>
 <span data-ttu-id="47723-184">Nesta seção, você especificará que o controle de usuário é um destino de soltar, substituirá os métodos que permitem que o controle de usuário seja um destino de soltar e processará os dados soltos nele.</span><span class="sxs-lookup"><span data-stu-id="47723-184">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="47723-185">Para permitir que o controle de usuário seja um destino de soltar</span><span class="sxs-lookup"><span data-stu-id="47723-185">To enable the user control to be a drop target</span></span>

1.  <span data-ttu-id="47723-186">Abra o Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="47723-186">Open Circle.xaml.</span></span>

2.  <span data-ttu-id="47723-187">Na abertura <xref:System.Windows.Controls.UserControl> marca, adicione o <xref:System.Windows.UIElement.AllowDrop%2A> propriedade e defini-lo como `true`.</span><span class="sxs-lookup"><span data-stu-id="47723-187">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>

     [!code-xaml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

<span data-ttu-id="47723-188">O <xref:System.Windows.UIElement.OnDrop%2A> método é chamado quando o <xref:System.Windows.UIElement.AllowDrop%2A> estiver definida como `true` e dados de origem do arrasto são soltos no controle de usuário do círculo.</span><span class="sxs-lookup"><span data-stu-id="47723-188">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="47723-189">Nesse método, você processará os dados que foram soltos e aplicará os dados ao círculo.</span><span class="sxs-lookup"><span data-stu-id="47723-189">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>

### <a name="to-process-the-dropped-data"></a><span data-ttu-id="47723-190">Para processar os dados soltos</span><span class="sxs-lookup"><span data-stu-id="47723-190">To process the dropped data</span></span>

1.  <span data-ttu-id="47723-191">Abra Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="47723-191">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2.  <span data-ttu-id="47723-192">Adicione o seguinte <xref:System.Windows.UIElement.OnDrop%2A> substituição é para fornecer manipulação de classe para o <xref:System.Windows.UIElement.Drop> eventos.</span><span class="sxs-lookup"><span data-stu-id="47723-192">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     <span data-ttu-id="47723-193">Isso <xref:System.Windows.UIElement.OnDrop%2A> substituição executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="47723-193">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>

    -   <span data-ttu-id="47723-194">Usa o <xref:System.Windows.DataObject.GetDataPresent%2A> método para verificar se os dados arrastados contêm um objeto de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="47723-194">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>

    -   <span data-ttu-id="47723-195">Usa o <xref:System.Windows.DataObject.GetData%2A> método para extrair os dados de cadeia de caracteres, se ele estiver presente.</span><span class="sxs-lookup"><span data-stu-id="47723-195">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>

    -   <span data-ttu-id="47723-196">Usa um <xref:System.Windows.Media.BrushConverter> para tentar converter a cadeia de caracteres para um <xref:System.Windows.Media.Brush>.</span><span class="sxs-lookup"><span data-stu-id="47723-196">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>

    -   <span data-ttu-id="47723-197">Se a conversão for bem-sucedida, o pincel aplica-se a <xref:System.Windows.Shapes.Shape.Fill%2A> do <xref:System.Windows.Shapes.Ellipse> que fornece a interface do usuário do controle do círculo.</span><span class="sxs-lookup"><span data-stu-id="47723-197">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>

    -   <span data-ttu-id="47723-198">As marcas de <xref:System.Windows.UIElement.Drop> evento como manipulado.</span><span class="sxs-lookup"><span data-stu-id="47723-198">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="47723-199">O evento de soltar deve ser marcado como manipulado para que os outros elementos que o recebem saibam que foi manipulado pelo controle de usuário do círculo.</span><span class="sxs-lookup"><span data-stu-id="47723-199">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>

3.  <span data-ttu-id="47723-200">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="47723-200">Press **F5** to build and run the application.</span></span>

4.  <span data-ttu-id="47723-201">Selecione o texto `green` no <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="47723-201">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5.  <span data-ttu-id="47723-202">Arraste o texto para um controle do círculo e solte-o.</span><span class="sxs-lookup"><span data-stu-id="47723-202">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="47723-203">O círculo muda de azul para verde.</span><span class="sxs-lookup"><span data-stu-id="47723-203">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="47723-204">![Converta uma cadeia de caracteres em um pincel](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="47723-204">![Convert a string to a brush](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>

6.  <span data-ttu-id="47723-205">Digite o texto `green` no <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="47723-205">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7.  <span data-ttu-id="47723-206">Selecione o texto `gre` no <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="47723-206">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

8.  <span data-ttu-id="47723-207">Arraste-o para um controle do círculo e solte-o.</span><span class="sxs-lookup"><span data-stu-id="47723-207">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="47723-208">Observe que o cursor muda para indicar que é permitido soltar; porém, a cor do círculo não muda, porque `gre` não é uma cor válida.</span><span class="sxs-lookup"><span data-stu-id="47723-208">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>

9. <span data-ttu-id="47723-209">Arraste do controle do círculo verde e solte no controle do círculo azul.</span><span class="sxs-lookup"><span data-stu-id="47723-209">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="47723-210">O círculo muda de azul para verde.</span><span class="sxs-lookup"><span data-stu-id="47723-210">The Circle changes from blue to green.</span></span> <span data-ttu-id="47723-211">Observe que a que o cursor mostrado depende se o <xref:System.Windows.Controls.TextBox> ou o círculo é a origem do arrasto.</span><span class="sxs-lookup"><span data-stu-id="47723-211">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>

<span data-ttu-id="47723-212">Definindo o <xref:System.Windows.UIElement.AllowDrop%2A> propriedade para `true` e processar os dados é tudo o que é necessária para habilitar um elemento a ser um destino de soltar.</span><span class="sxs-lookup"><span data-stu-id="47723-212">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="47723-213">No entanto, para fornecer uma melhor experiência de usuário, você deve também lidar com o <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, e <xref:System.Windows.UIElement.DragOver> eventos.</span><span class="sxs-lookup"><span data-stu-id="47723-213">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="47723-214">Nesses eventos, é possível executar verificações e fornecer comentários adicionais ao usuário antes de soltar os dados.</span><span class="sxs-lookup"><span data-stu-id="47723-214">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>

<span data-ttu-id="47723-215">Quando dados são arrastados sobre o controle de usuário do círculo, o controle deve notificar a fonte de arrasto se os dados arrastados podem ser processados.</span><span class="sxs-lookup"><span data-stu-id="47723-215">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="47723-216">Se o controle não souber como processar os dados, deverá recusá-los quando forem soltos.</span><span class="sxs-lookup"><span data-stu-id="47723-216">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="47723-217">Para fazer isso, você irá lidar com o <xref:System.Windows.UIElement.DragOver> evento e defina o <xref:System.Windows.DragEventArgs.Effects%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="47723-217">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>

### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="47723-218">Para verificar se é permitido soltar os dados</span><span class="sxs-lookup"><span data-stu-id="47723-218">To verify that the data drop is allowed</span></span>

1.  <span data-ttu-id="47723-219">Abra Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="47723-219">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2.  <span data-ttu-id="47723-220">Adicione o seguinte <xref:System.Windows.UIElement.OnDragOver%2A> substituição é para fornecer manipulação de classe para o <xref:System.Windows.UIElement.DragOver> eventos.</span><span class="sxs-lookup"><span data-stu-id="47723-220">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     <span data-ttu-id="47723-221">Isso <xref:System.Windows.UIElement.OnDragOver%2A> substituição executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="47723-221">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>

    -   <span data-ttu-id="47723-222">Define a propriedade <xref:System.Windows.DragEventArgs.Effects%2A> como <xref:System.Windows.DragDropEffects.None>.</span><span class="sxs-lookup"><span data-stu-id="47723-222">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>

    -   <span data-ttu-id="47723-223">Executa as mesmas verificações que são executadas no <xref:System.Windows.UIElement.OnDrop%2A> método para determinar se o controle de usuário do círculo pode processar os dados arrastados.</span><span class="sxs-lookup"><span data-stu-id="47723-223">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>

    -   <span data-ttu-id="47723-224">Define se o controle de usuário pode processar os dados, o <xref:System.Windows.DragEventArgs.Effects%2A> propriedade para <xref:System.Windows.DragDropEffects.Copy> ou <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="47723-224">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3.  <span data-ttu-id="47723-225">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="47723-225">Press **F5** to build and run the application.</span></span>

4.  <span data-ttu-id="47723-226">Selecione o texto `gre` no <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="47723-226">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5.  <span data-ttu-id="47723-227">Arraste o texto para um controle do círculo.</span><span class="sxs-lookup"><span data-stu-id="47723-227">Drag the text to a Circle control.</span></span> <span data-ttu-id="47723-228">Observe que, agora, o cursor muda para indicar que não é permitido soltar, porque `gre` não é uma cor válida.</span><span class="sxs-lookup"><span data-stu-id="47723-228">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>

 <span data-ttu-id="47723-229">É possível aprimorar ainda mais a experiência do usuário por meio da aplicação de uma visualização da operação do tipo “soltar”.</span><span class="sxs-lookup"><span data-stu-id="47723-229">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="47723-230">Para o controle de usuário do círculo, você substituirá a <xref:System.Windows.UIElement.OnDragEnter%2A> e <xref:System.Windows.UIElement.OnDragLeave%2A> métodos.</span><span class="sxs-lookup"><span data-stu-id="47723-230">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="47723-231">Quando os dados são arrastados sobre o controle, o plano de fundo atual <xref:System.Windows.Shapes.Shape.Fill%2A> é salvo em uma variável de espaço reservado.</span><span class="sxs-lookup"><span data-stu-id="47723-231">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="47723-232">A cadeia de caracteres, em seguida, é convertida em um pincel e aplicada ao <xref:System.Windows.Shapes.Ellipse> que fornece o círculo interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="47723-232">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="47723-233">Se os dados é arrastados do círculo sem serem soltos, o original <xref:System.Windows.Shapes.Shape.Fill%2A> valor será reaplicado ao círculo.</span><span class="sxs-lookup"><span data-stu-id="47723-233">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="47723-234">Para visualizar os efeitos da operação do tipo “arrastar e soltar”</span><span class="sxs-lookup"><span data-stu-id="47723-234">To preview the effects of the drag-and-drop operation</span></span>

1.  <span data-ttu-id="47723-235">Abra Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="47723-235">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2.  <span data-ttu-id="47723-236">Na classe do círculo, declare uma privada <xref:System.Windows.Media.Brush> variável nomeada `_previousFill` e inicializá-lo para `null`.</span><span class="sxs-lookup"><span data-stu-id="47723-236">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>

     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3.  <span data-ttu-id="47723-237">Adicione o seguinte <xref:System.Windows.UIElement.OnDragEnter%2A> substituição é para fornecer manipulação de classe para o <xref:System.Windows.UIElement.DragEnter> eventos.</span><span class="sxs-lookup"><span data-stu-id="47723-237">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     <span data-ttu-id="47723-238">Isso <xref:System.Windows.UIElement.OnDragEnter%2A> substituição executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="47723-238">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>

    -   <span data-ttu-id="47723-239">Salva o <xref:System.Windows.Shapes.Shape.Fill%2A> propriedade do <xref:System.Windows.Shapes.Ellipse> no `_previousFill` variável.</span><span class="sxs-lookup"><span data-stu-id="47723-239">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>

    -   <span data-ttu-id="47723-240">Executa as mesmas verificações que são executadas na <xref:System.Windows.UIElement.OnDrop%2A> método para determinar se os dados podem ser convertidos para um <xref:System.Windows.Media.Brush>.</span><span class="sxs-lookup"><span data-stu-id="47723-240">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>

    -   <span data-ttu-id="47723-241">Se os dados são convertidos para válida <xref:System.Windows.Media.Brush>, aplica-se ao <xref:System.Windows.Shapes.Shape.Fill%2A> da <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="47723-241">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>

4.  <span data-ttu-id="47723-242">Adicione o seguinte <xref:System.Windows.UIElement.OnDragLeave%2A> substituição é para fornecer manipulação de classe para o <xref:System.Windows.UIElement.DragLeave> eventos.</span><span class="sxs-lookup"><span data-stu-id="47723-242">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     <span data-ttu-id="47723-243">Isso <xref:System.Windows.UIElement.OnDragLeave%2A> substituição executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="47723-243">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>

    -   <span data-ttu-id="47723-244">Aplica-se a <xref:System.Windows.Media.Brush> salvos na `_previousFill` variável para o <xref:System.Windows.Shapes.Shape.Fill%2A> da <xref:System.Windows.Shapes.Ellipse> que fornece a interface do usuário do controle de usuário do círculo.</span><span class="sxs-lookup"><span data-stu-id="47723-244">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>

5.  <span data-ttu-id="47723-245">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="47723-245">Press **F5** to build and run the application.</span></span>

6.  <span data-ttu-id="47723-246">Selecione o texto `green` no <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="47723-246">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7.  <span data-ttu-id="47723-247">Arraste o texto sobre um controle do círculo sem soltá-lo.</span><span class="sxs-lookup"><span data-stu-id="47723-247">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="47723-248">O círculo muda de azul para verde.</span><span class="sxs-lookup"><span data-stu-id="47723-248">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="47723-249">![Visualize os efeitos de uma operação do tipo “arrastar&#45;e&#45;soltar”](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="47723-249">![Preview the effects of a drag&#45;and&#45;drop operation](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>

8.  <span data-ttu-id="47723-250">Arraste o texto para fora do controle do círculo.</span><span class="sxs-lookup"><span data-stu-id="47723-250">Drag the text away from the Circle control.</span></span> <span data-ttu-id="47723-251">O círculo volta de verde para azul.</span><span class="sxs-lookup"><span data-stu-id="47723-251">The Circle changes from green back to blue.</span></span>

## <a name="enable-a-panel-to-receive-dropped-data"></a><span data-ttu-id="47723-252">Habilite um painel para receber dados descartados</span><span class="sxs-lookup"><span data-stu-id="47723-252">Enable a Panel to Receive Dropped Data</span></span>

<span data-ttu-id="47723-253">Nesta seção, você permitirá que os painéis que hospedam controles de usuário do círculo para atuar como destinos de soltar para os dados arrastados do círculo.</span><span class="sxs-lookup"><span data-stu-id="47723-253">In this section, you enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="47723-254">Você implementará o código que permite que você mover um círculo de um painel para outro ou fazer uma cópia de um controle do círculo, mantendo pressionada a **Ctrl** chave enquanto arrasta e solta um círculo.</span><span class="sxs-lookup"><span data-stu-id="47723-254">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the **Ctrl** key while dragging and dropping a Circle.</span></span>

1.  <span data-ttu-id="47723-255">Abra MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="47723-255">Open MainWindow.xaml.</span></span>

2.  <span data-ttu-id="47723-256">Conforme mostrado no XAML a seguir, em cada um dos <xref:System.Windows.Controls.StackPanel> controles, adicione manipuladores para o <xref:System.Windows.UIElement.DragOver> e <xref:System.Windows.UIElement.Drop> eventos.</span><span class="sxs-lookup"><span data-stu-id="47723-256">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="47723-257">Nome do <xref:System.Windows.UIElement.DragOver> manipulador de eventos `panel_DragOver`e nomeie o <xref:System.Windows.UIElement.Drop> manipulador de eventos, `panel_Drop`.</span><span class="sxs-lookup"><span data-stu-id="47723-257">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3.  <span data-ttu-id="47723-258">Abra MainWindows.xaml.cs ou MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="47723-258">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>

4.  <span data-ttu-id="47723-259">Adicione o seguinte código para o <xref:System.Windows.UIElement.DragOver> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="47723-259">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     <span data-ttu-id="47723-260">Isso <xref:System.Windows.UIElement.DragOver> manipulador de eventos executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="47723-260">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>

    -   <span data-ttu-id="47723-261">Verifica se os dados arrastados contêm os dados de "Objeto" que foi empacotados na <xref:System.Windows.DataObject> pelo controle de usuário do círculo e passados na chamada para <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span><span class="sxs-lookup"><span data-stu-id="47723-261">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>

    -   <span data-ttu-id="47723-262">Se os dados de "Objeto" estiverem presente, verifica se o **Ctrl** tecla é pressionada.</span><span class="sxs-lookup"><span data-stu-id="47723-262">If the "Object" data is present, checks whether the **Ctrl** key is pressed.</span></span>

    -   <span data-ttu-id="47723-263">Se o **Ctrl** tecla é pressionada, conjuntos de <xref:System.Windows.DragEventArgs.Effects%2A> propriedade para <xref:System.Windows.DragDropEffects.Copy>.</span><span class="sxs-lookup"><span data-stu-id="47723-263">If the **Ctrl** key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="47723-264">Caso contrário, defina as <xref:System.Windows.DragEventArgs.Effects%2A> propriedade para <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="47723-264">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>

5.  <span data-ttu-id="47723-265">Adicione o seguinte código para o <xref:System.Windows.UIElement.Drop> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="47723-265">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     <span data-ttu-id="47723-266">Isso <xref:System.Windows.UIElement.Drop> manipulador de eventos executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="47723-266">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>

    -   <span data-ttu-id="47723-267">Verifica se o <xref:System.Windows.UIElement.Drop> evento já foi tratado.</span><span class="sxs-lookup"><span data-stu-id="47723-267">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="47723-268">Por exemplo, se um círculo foi solto em outro círculo que manipula o <xref:System.Windows.UIElement.Drop> evento, você não quiser o painel que contém o círculo o manipule também.</span><span class="sxs-lookup"><span data-stu-id="47723-268">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>

    -   <span data-ttu-id="47723-269">Se o <xref:System.Windows.UIElement.Drop> evento não é tratada, verifica se o **Ctrl** tecla é pressionada.</span><span class="sxs-lookup"><span data-stu-id="47723-269">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the **Ctrl** key is pressed.</span></span>

    -   <span data-ttu-id="47723-270">Se o **Ctrl** tecla é pressionada quando o <xref:System.Windows.UIElement.Drop> acontece, faz uma cópia do círculo, controlar e adicioná-lo para o <xref:System.Windows.Controls.Panel.Children%2A> coleção do <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="47723-270">If the **Ctrl** key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>

    -   <span data-ttu-id="47723-271">Se o **Ctrl** chave não estiver pressionada, mova o círculo da <xref:System.Windows.Controls.Panel.Children%2A> coleção do painel pai para o <xref:System.Windows.Controls.Panel.Children%2A> coleção do painel que foi solto.</span><span class="sxs-lookup"><span data-stu-id="47723-271">If the **Ctrl** key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>

    -   <span data-ttu-id="47723-272">Define o <xref:System.Windows.DragEventArgs.Effects%2A> propriedade para notificar o <xref:System.Windows.DragDrop.DoDragDrop%2A> método se uma operação de movimentação ou cópia foi executada.</span><span class="sxs-lookup"><span data-stu-id="47723-272">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>

6.  <span data-ttu-id="47723-273">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="47723-273">Press **F5** to build and run the application.</span></span>

7.  <span data-ttu-id="47723-274">Selecione o texto `green` do <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="47723-274">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

8.  <span data-ttu-id="47723-275">Arraste o texto sobre um controle do círculo e solte-o.</span><span class="sxs-lookup"><span data-stu-id="47723-275">Drag the text over a Circle control and drop it.</span></span>

9. <span data-ttu-id="47723-276">Arraste um controle do círculo do painel esquerdo para o painel direito e solte-o.</span><span class="sxs-lookup"><span data-stu-id="47723-276">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="47723-277">O círculo é removido do <xref:System.Windows.Controls.Panel.Children%2A> coleção do painel esquerdo e adicionado à coleção de filhos do painel à direita.</span><span class="sxs-lookup"><span data-stu-id="47723-277">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>

10. <span data-ttu-id="47723-278">Arraste um controle do círculo do painel que está para outro painel e solte-o ao pressionar o **Ctrl** chave.</span><span class="sxs-lookup"><span data-stu-id="47723-278">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the **Ctrl** key.</span></span> <span data-ttu-id="47723-279">O círculo é copiado e a cópia é adicionada para o <xref:System.Windows.Controls.Panel.Children%2A> coleção do painel destinatário.</span><span class="sxs-lookup"><span data-stu-id="47723-279">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>

     <span data-ttu-id="47723-280">![Arrastando um círculo enquanto pressiona a tecla CTRL](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="47723-280">![Dragging a Circle while pressing the CTRL key](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>

## <a name="see-also"></a><span data-ttu-id="47723-281">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47723-281">See also</span></span>

- [<span data-ttu-id="47723-282">Visão geral de arrastar e soltar</span><span class="sxs-lookup"><span data-stu-id="47723-282">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)