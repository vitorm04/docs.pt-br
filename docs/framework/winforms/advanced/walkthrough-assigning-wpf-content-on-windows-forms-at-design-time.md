---
title: 'Instruções passo a passo: atribuindo conteúdo WPF em Windows Forms na hora do design'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
ms.openlocfilehash: 6db75e9d8ec5aeb1a0c7310d39391f8f264649d3
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45585883"
---
# <a name="walkthrough-assigning-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="d473c-102">Instruções passo a passo: atribuindo conteúdo WPF em Windows Forms na hora do design</span><span class="sxs-lookup"><span data-stu-id="d473c-102">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="d473c-103">Essa instrução passo a passo mostra como selecionar os tipos de controle do WPF (Windows Presentation Foundation) que você deseja exibir em seu formulário.</span><span class="sxs-lookup"><span data-stu-id="d473c-103">This walkthrough show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="d473c-104">Você pode selecionar qualquer tipo de controle WPF incluído no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="d473c-104">You can select any WPF control types which are included in your project.</span></span>  
  
 <span data-ttu-id="d473c-105">Nesta instrução passo a passo, as seguintes tarefas serão executadas:</span><span class="sxs-lookup"><span data-stu-id="d473c-105">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="d473c-106">Crie o projeto.</span><span class="sxs-lookup"><span data-stu-id="d473c-106">Create the project.</span></span>  
  
-   <span data-ttu-id="d473c-107">Crie os tipos de controle WPF.</span><span class="sxs-lookup"><span data-stu-id="d473c-107">Create the WPF control types.</span></span>  
  
-   <span data-ttu-id="d473c-108">Selecione os controles de WPF.</span><span class="sxs-lookup"><span data-stu-id="d473c-108">Select WPF controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d473c-109">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="d473c-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d473c-110">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="d473c-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d473c-111">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d473c-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d473c-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d473c-112">Prerequisites</span></span>  
 <span data-ttu-id="d473c-113">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="d473c-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="d473c-114">.</span><span class="sxs-lookup"><span data-stu-id="d473c-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="d473c-115">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="d473c-115">Creating the Project</span></span>  
 <span data-ttu-id="d473c-116">A primeira etapa é criar o projeto dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d473c-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d473c-117">Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d473c-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="d473c-118">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="d473c-118">To create the project</span></span>  
  
-   <span data-ttu-id="d473c-119">Crie um novo projeto de Aplicativo dos Windows Forms no Visual Basic ou Visual C# chamado `SelectingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="d473c-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="d473c-120">Criando tipos de controle WPF</span><span class="sxs-lookup"><span data-stu-id="d473c-120">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="d473c-121">Depois de adicionar tipos de controle WPF ao projeto, você pode hospedá-los em diferentes <xref:System.Windows.Forms.Integration.ElementHost> controles.</span><span class="sxs-lookup"><span data-stu-id="d473c-121">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="d473c-122">Criar tipos de controle WPF</span><span class="sxs-lookup"><span data-stu-id="d473c-122">To create WPF control types</span></span>  
  
1.  <span data-ttu-id="d473c-123">Adicione um novo WPF <xref:System.Windows.Controls.UserControl> projeto à solução.</span><span class="sxs-lookup"><span data-stu-id="d473c-123">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="d473c-124">Use o nome padrão do tipo de controle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="d473c-124">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="d473c-125">Para obter mais informações, consulte [Instruções passo a passo: como criar novo conteúdo WPF nos Windows Forms em tempo de design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="d473c-125">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="d473c-126">No modo de exibição de Design, verifique se `UserControl1` está selecionado.</span><span class="sxs-lookup"><span data-stu-id="d473c-126">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="d473c-127">Para obter mais informações, consulte [Como Selecionar e Mover Elementos na Superfície de Design](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="d473c-127">For more information, see [How to: Select and Move Elements on the Design Surface](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="d473c-128">No **propriedades** janela, defina o valor da <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades a serem `200`.</span><span class="sxs-lookup"><span data-stu-id="d473c-128">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="d473c-129">Adicionar um <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> o controle para o <xref:System.Windows.Controls.UserControl> e defina o valor da <xref:System.Windows.Controls.TextBox.Text%2A> propriedade **conteúdo hospedado**.</span><span class="sxs-lookup"><span data-stu-id="d473c-129">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>  
  
5.  <span data-ttu-id="d473c-130">Adicione um segundo WPF <xref:System.Windows.Controls.UserControl> ao projeto.</span><span class="sxs-lookup"><span data-stu-id="d473c-130">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="d473c-131">Use o nome padrão do tipo de controle, `UserControl2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="d473c-131">Use the default name for the control type, `UserControl2.xaml`.</span></span>  
  
6.  <span data-ttu-id="d473c-132">No **propriedades** janela, defina o valor da <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades a serem `200`.</span><span class="sxs-lookup"><span data-stu-id="d473c-132">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
7.  <span data-ttu-id="d473c-133">Adicionar um <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> o controle para o <xref:System.Windows.Controls.UserControl> e defina o valor da <xref:System.Windows.Controls.TextBox.Text%2A> propriedade **conteúdo hospedado 2**.</span><span class="sxs-lookup"><span data-stu-id="d473c-133">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>  
  
 <span data-ttu-id="d473c-134">**Observação** Em geral, é recomendável hospedar conteúdos WPF mais sofisticados.</span><span class="sxs-lookup"><span data-stu-id="d473c-134">**Note** In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="d473c-135">O <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> controle é usado aqui apenas para fins ilustrativos.</span><span class="sxs-lookup"><span data-stu-id="d473c-135">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>  
  
1.  <span data-ttu-id="d473c-136">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="d473c-136">Build the project.</span></span>  
  
## <a name="selecting-wpf-controls"></a><span data-ttu-id="d473c-137">Selecionando controles de WPF</span><span class="sxs-lookup"><span data-stu-id="d473c-137">Selecting WPF Controls</span></span>  
 <span data-ttu-id="d473c-138">Você pode atribuir diferentes conteúdos WPF a um <xref:System.Windows.Forms.Integration.ElementHost> controle, que já está hospedando o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="d473c-138">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>  
  
#### <a name="to-select-wpf-controls"></a><span data-ttu-id="d473c-139">Selecionar controles de WPF</span><span class="sxs-lookup"><span data-stu-id="d473c-139">To select WPF controls</span></span>  
  
1.  <span data-ttu-id="d473c-140">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="d473c-140">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="d473c-141">Na **Caixa de ferramentas**, clique duas vezes em `UserControl1` para criar uma instância de `UserControl1` no formulário.</span><span class="sxs-lookup"><span data-stu-id="d473c-141">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="d473c-142">Uma instância do `UserControl1` é hospedado em uma nova <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="d473c-142">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="d473c-143">No painel de smart tag para `elementHost1`, abra a lista suspensa **Selecionar conteúdo hospedado**.</span><span class="sxs-lookup"><span data-stu-id="d473c-143">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>  
  
4.  <span data-ttu-id="d473c-144">Selecione **UserControl2** na caixa de listagem suspensa.</span><span class="sxs-lookup"><span data-stu-id="d473c-144">Select **UserControl2** from the drop-down list box.</span></span>  
  
     <span data-ttu-id="d473c-145">O controle `elementHost1` agora hospeda uma instância do tipo `UserControl2`.</span><span class="sxs-lookup"><span data-stu-id="d473c-145">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>  
  
5.  <span data-ttu-id="d473c-146">No **propriedades** janela, confirme se o <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> estiver definida como **UserControl2**.</span><span class="sxs-lookup"><span data-stu-id="d473c-146">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>  
  
6.  <span data-ttu-id="d473c-147">Dos **caixa de ferramentas**, no **interoperabilidade do WPF** de grupo, arraste um <xref:System.Windows.Forms.Integration.ElementHost> controle para o formulário.</span><span class="sxs-lookup"><span data-stu-id="d473c-147">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>  
  
     <span data-ttu-id="d473c-148">O nome padrão do novo controle é `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="d473c-148">The default name for the new control is `elementHost2`.</span></span>  
  
7.  <span data-ttu-id="d473c-149">No painel de smart tag para `elementHost2`, abra a lista suspensa **Selecionar conteúdo hospedado**.</span><span class="sxs-lookup"><span data-stu-id="d473c-149">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>  
  
8.  <span data-ttu-id="d473c-150">Selecione **UserControl1** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="d473c-150">Select **UserControl1** from the drop-down list.</span></span>  
  
9. <span data-ttu-id="d473c-151">O controle `elementHost2` agora hospeda uma instância do tipo `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="d473c-151">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d473c-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d473c-152">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="d473c-153">Migração e interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="d473c-153">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="d473c-154">Usando Controles do WPF</span><span class="sxs-lookup"><span data-stu-id="d473c-154">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="d473c-155">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d473c-155">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
