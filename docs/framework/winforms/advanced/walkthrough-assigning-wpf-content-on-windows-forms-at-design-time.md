---
title: 'Passo a passo: atribuir conteúdo WPF no Windows Forms na hora do design'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
ms.openlocfilehash: 09427bfc836f40ca9c7aa76f4904bfe7083bf8dc
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211231"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="7df2a-102">Passo a passo: Atribuir o conteúdo do WPF nos Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="7df2a-102">Walkthrough: Assign WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="7df2a-103">Essa instrução passo a passo mostra como selecionar os tipos de controle do WPF (Windows Presentation Foundation) que você deseja exibir em seu formulário.</span><span class="sxs-lookup"><span data-stu-id="7df2a-103">This walkthrough show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="7df2a-104">Você pode selecionar qualquer tipo de controle WPF incluído no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="7df2a-104">You can select any WPF control types which are included in your project.</span></span>

<span data-ttu-id="7df2a-105">Nesta instrução passo a passo, as seguintes tarefas serão executadas:</span><span class="sxs-lookup"><span data-stu-id="7df2a-105">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="7df2a-106">Crie o projeto.</span><span class="sxs-lookup"><span data-stu-id="7df2a-106">Create the project.</span></span>

- <span data-ttu-id="7df2a-107">Crie os tipos de controle WPF.</span><span class="sxs-lookup"><span data-stu-id="7df2a-107">Create the WPF control types.</span></span>

- <span data-ttu-id="7df2a-108">Selecione os controles de WPF.</span><span class="sxs-lookup"><span data-stu-id="7df2a-108">Select WPF controls.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7df2a-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7df2a-109">Prerequisites</span></span>

<span data-ttu-id="7df2a-110">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="7df2a-110">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="7df2a-111">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="7df2a-111">Create the project</span></span>

<span data-ttu-id="7df2a-112">Abra o Visual Studio e crie um novo projeto de aplicativo do Windows Forms no Visual Basic ou Visual C# nomeado `SelectingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="7df2a-112">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="7df2a-113">Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7df2a-113">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="7df2a-114">Criar os tipos de controle do WPF</span><span class="sxs-lookup"><span data-stu-id="7df2a-114">Create the WPF control types</span></span>

<span data-ttu-id="7df2a-115">Depois de adicionar tipos de controle WPF ao projeto, você pode hospedá-los em diferentes <xref:System.Windows.Forms.Integration.ElementHost> controles.</span><span class="sxs-lookup"><span data-stu-id="7df2a-115">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>

## <a name="create-wpf-control-types"></a><span data-ttu-id="7df2a-116">Criar tipos de controle WPF</span><span class="sxs-lookup"><span data-stu-id="7df2a-116">Create WPF control types</span></span>

1. <span data-ttu-id="7df2a-117">Adicione um novo WPF <xref:System.Windows.Controls.UserControl> projeto à solução.</span><span class="sxs-lookup"><span data-stu-id="7df2a-117">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="7df2a-118">Use o nome padrão do tipo de controle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="7df2a-118">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="7df2a-119">Para obter mais informações, confira [Passo a passo: Criando novo conteúdo WPF nos Windows Forms em tempo de Design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="7df2a-119">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="7df2a-120">No modo de exibição de Design, verifique se `UserControl1` está selecionado.</span><span class="sxs-lookup"><span data-stu-id="7df2a-120">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="7df2a-121">Para obter mais informações, confira [Como: Selecionar e mover elementos na superfície de Design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="7df2a-121">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="7df2a-122">No **propriedades** janela, defina o valor da <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades a serem `200`.</span><span class="sxs-lookup"><span data-stu-id="7df2a-122">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

4. <span data-ttu-id="7df2a-123">Adicionar um <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> o controle para o <xref:System.Windows.Controls.UserControl> e defina o valor da <xref:System.Windows.Controls.TextBox.Text%2A> propriedade **conteúdo hospedado**.</span><span class="sxs-lookup"><span data-stu-id="7df2a-123">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

5. <span data-ttu-id="7df2a-124">Adicione um segundo WPF <xref:System.Windows.Controls.UserControl> ao projeto.</span><span class="sxs-lookup"><span data-stu-id="7df2a-124">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="7df2a-125">Use o nome padrão do tipo de controle, `UserControl2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="7df2a-125">Use the default name for the control type, `UserControl2.xaml`.</span></span>

6. <span data-ttu-id="7df2a-126">No **propriedades** janela, defina o valor da <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades a serem `200`.</span><span class="sxs-lookup"><span data-stu-id="7df2a-126">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

7. <span data-ttu-id="7df2a-127">Adicionar um <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> o controle para o <xref:System.Windows.Controls.UserControl> e defina o valor da <xref:System.Windows.Controls.TextBox.Text%2A> propriedade **conteúdo hospedado 2**.</span><span class="sxs-lookup"><span data-stu-id="7df2a-127">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>

 <span data-ttu-id="7df2a-128">**Observação** Em geral, é recomendável hospedar conteúdos WPF mais sofisticados.</span><span class="sxs-lookup"><span data-stu-id="7df2a-128">**Note** In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="7df2a-129">O <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> controle é usado aqui apenas para fins ilustrativos.</span><span class="sxs-lookup"><span data-stu-id="7df2a-129">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

1. <span data-ttu-id="7df2a-130">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="7df2a-130">Build the project.</span></span>

## <a name="select-wpf-controls"></a><span data-ttu-id="7df2a-131">Selecione controles WPF</span><span class="sxs-lookup"><span data-stu-id="7df2a-131">Select WPF controls</span></span>

<span data-ttu-id="7df2a-132">Você pode atribuir diferentes conteúdos WPF a um <xref:System.Windows.Forms.Integration.ElementHost> controle, que já está hospedando o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="7df2a-132">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>

1. <span data-ttu-id="7df2a-133">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="7df2a-133">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="7df2a-134">Na **Caixa de ferramentas**, clique duas vezes em `UserControl1` para criar uma instância de `UserControl1` no formulário.</span><span class="sxs-lookup"><span data-stu-id="7df2a-134">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

     <span data-ttu-id="7df2a-135">Uma instância do `UserControl1` é hospedado em uma nova <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="7df2a-135">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

3. <span data-ttu-id="7df2a-136">No painel de smart tag para `elementHost1`, abra a lista suspensa **Selecionar conteúdo hospedado**.</span><span class="sxs-lookup"><span data-stu-id="7df2a-136">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>

4. <span data-ttu-id="7df2a-137">Selecione **UserControl2** na caixa de listagem suspensa.</span><span class="sxs-lookup"><span data-stu-id="7df2a-137">Select **UserControl2** from the drop-down list box.</span></span>

     <span data-ttu-id="7df2a-138">O controle `elementHost1` agora hospeda uma instância do tipo `UserControl2`.</span><span class="sxs-lookup"><span data-stu-id="7df2a-138">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>

5. <span data-ttu-id="7df2a-139">No **propriedades** janela, confirme se o <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> estiver definida como **UserControl2**.</span><span class="sxs-lookup"><span data-stu-id="7df2a-139">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>

6. <span data-ttu-id="7df2a-140">Dos **caixa de ferramentas**, no **interoperabilidade do WPF** de grupo, arraste um <xref:System.Windows.Forms.Integration.ElementHost> controle para o formulário.</span><span class="sxs-lookup"><span data-stu-id="7df2a-140">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>

     <span data-ttu-id="7df2a-141">O nome padrão do novo controle é `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="7df2a-141">The default name for the new control is `elementHost2`.</span></span>

7. <span data-ttu-id="7df2a-142">No painel de smart tag para `elementHost2`, abra a lista suspensa **Selecionar conteúdo hospedado**.</span><span class="sxs-lookup"><span data-stu-id="7df2a-142">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>

8. <span data-ttu-id="7df2a-143">Selecione **UserControl1** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="7df2a-143">Select **UserControl1** from the drop-down list.</span></span>

9. <span data-ttu-id="7df2a-144">O controle `elementHost2` agora hospeda uma instância do tipo `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="7df2a-144">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>

## <a name="see-also"></a><span data-ttu-id="7df2a-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7df2a-145">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="7df2a-146">Migração e interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="7df2a-146">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="7df2a-147">Usando Controles do WPF</span><span class="sxs-lookup"><span data-stu-id="7df2a-147">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="7df2a-148">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7df2a-148">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
