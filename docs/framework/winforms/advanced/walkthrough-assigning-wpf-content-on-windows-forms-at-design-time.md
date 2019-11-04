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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0c1e0c91b7ab8bded677a86b597b02b9cb442d98
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460664"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="a1378-102">Walkthrough: atribuir conteúdo do WPF em Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="a1378-102">Walkthrough: Assign WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="a1378-103">Este artigo mostra como selecionar os tipos de controle Windows Presentation Foundation (WPF) que você deseja exibir no formulário.</span><span class="sxs-lookup"><span data-stu-id="a1378-103">This article show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="a1378-104">Você pode selecionar qualquer tipo de controle WPF incluído no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a1378-104">You can select any WPF control types which are included in your project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a1378-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="a1378-105">Prerequisites</span></span>

<span data-ttu-id="a1378-106">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="a1378-106">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="a1378-107">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="a1378-107">Create the project</span></span>

<span data-ttu-id="a1378-108">Abra o Visual Studio e crie um novo projeto de aplicativo Windows Forms em Visual Basic C# ou Visual chamado `SelectingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="a1378-108">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="a1378-109">Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a1378-109">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="a1378-110">Criar os tipos de controle do WPF</span><span class="sxs-lookup"><span data-stu-id="a1378-110">Create the WPF control types</span></span>

<span data-ttu-id="a1378-111">Depois de adicionar tipos de controle do WPF ao projeto, você pode hospedá-los em diferentes controles de <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="a1378-111">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>

1. <span data-ttu-id="a1378-112">Adicione um novo projeto <xref:System.Windows.Controls.UserControl> do WPF à solução.</span><span class="sxs-lookup"><span data-stu-id="a1378-112">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="a1378-113">Use o nome padrão do tipo de controle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="a1378-113">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="a1378-114">Para obter mais informações, consulte [Instruções passo a passo: como criar novo conteúdo WPF nos Windows Forms em tempo de design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="a1378-114">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="a1378-115">No modo de exibição de Design, verifique se `UserControl1` está selecionado.</span><span class="sxs-lookup"><span data-stu-id="a1378-115">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="a1378-116">Na janela **Propriedades** , defina o valor das propriedades <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> como **200**.</span><span class="sxs-lookup"><span data-stu-id="a1378-116">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="a1378-117">Adicione um controle de <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> à <xref:System.Windows.Controls.UserControl> e defina o valor da propriedade <xref:System.Windows.Controls.TextBox.Text%2A> como **conteúdo hospedado**.</span><span class="sxs-lookup"><span data-stu-id="a1378-117">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

5. <span data-ttu-id="a1378-118">Adicione um segundo <xref:System.Windows.Controls.UserControl> do WPF ao projeto.</span><span class="sxs-lookup"><span data-stu-id="a1378-118">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="a1378-119">Use o nome padrão do tipo de controle, `UserControl2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="a1378-119">Use the default name for the control type, `UserControl2.xaml`.</span></span>

6. <span data-ttu-id="a1378-120">Na janela **Propriedades** , defina o valor das propriedades <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> como **200**.</span><span class="sxs-lookup"><span data-stu-id="a1378-120">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

7. <span data-ttu-id="a1378-121">Adicione um controle de <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> à <xref:System.Windows.Controls.UserControl> e defina o valor da propriedade <xref:System.Windows.Controls.TextBox.Text%2A> como o **conteúdo hospedado 2**.</span><span class="sxs-lookup"><span data-stu-id="a1378-121">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="a1378-122">No geral, é necessário hospedar conteúdos do WPF mais sofisticados.</span><span class="sxs-lookup"><span data-stu-id="a1378-122">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="a1378-123">O controle de <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> é usado aqui apenas para fins ilustrativos.</span><span class="sxs-lookup"><span data-stu-id="a1378-123">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

8. <span data-ttu-id="a1378-124">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="a1378-124">Build the project.</span></span>

## <a name="select-wpf-controls"></a><span data-ttu-id="a1378-125">Selecionar controles WPF</span><span class="sxs-lookup"><span data-stu-id="a1378-125">Select WPF controls</span></span>

<span data-ttu-id="a1378-126">Você pode atribuir conteúdo diferente do WPF a um controle <xref:System.Windows.Forms.Integration.ElementHost>, que já está hospedando o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="a1378-126">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>

1. <span data-ttu-id="a1378-127">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="a1378-127">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="a1378-128">Na **Caixa de ferramentas**, clique duas vezes em `UserControl1` para criar uma instância de `UserControl1` no formulário.</span><span class="sxs-lookup"><span data-stu-id="a1378-128">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

   <span data-ttu-id="a1378-129">Uma instância de `UserControl1` é hospedada em um novo controle de <xref:System.Windows.Forms.Integration.ElementHost> chamado `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="a1378-129">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

3. <span data-ttu-id="a1378-130">No painel de smart tag para `elementHost1`, abra a lista suspensa **Selecionar conteúdo hospedado**.</span><span class="sxs-lookup"><span data-stu-id="a1378-130">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>

4. <span data-ttu-id="a1378-131">Selecione **UserControl2** na caixa de listagem suspensa.</span><span class="sxs-lookup"><span data-stu-id="a1378-131">Select **UserControl2** from the drop-down list box.</span></span>

   <span data-ttu-id="a1378-132">O controle `elementHost1` agora hospeda uma instância do tipo `UserControl2`.</span><span class="sxs-lookup"><span data-stu-id="a1378-132">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>

5. <span data-ttu-id="a1378-133">Na janela **Propriedades** , confirme se a propriedade <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> está definida como **UserControl2**.</span><span class="sxs-lookup"><span data-stu-id="a1378-133">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>

6. <span data-ttu-id="a1378-134">Na **caixa de ferramentas**, no grupo de **interoperabilidade do WPF** , arraste um controle de <xref:System.Windows.Forms.Integration.ElementHost> para o formulário.</span><span class="sxs-lookup"><span data-stu-id="a1378-134">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>

   <span data-ttu-id="a1378-135">O nome padrão do novo controle é `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="a1378-135">The default name for the new control is `elementHost2`.</span></span>

7. <span data-ttu-id="a1378-136">No painel de smart tag para `elementHost2`, abra a lista suspensa **Selecionar conteúdo hospedado**.</span><span class="sxs-lookup"><span data-stu-id="a1378-136">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>

8. <span data-ttu-id="a1378-137">Selecione **UserControl1** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="a1378-137">Select **UserControl1** from the drop-down list.</span></span>

9. <span data-ttu-id="a1378-138">O controle `elementHost2` agora hospeda uma instância do tipo `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="a1378-138">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1378-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1378-139">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="a1378-140">Migração e Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="a1378-140">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="a1378-141">Usando Controles do WPF</span><span class="sxs-lookup"><span data-stu-id="a1378-141">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="a1378-142">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a1378-142">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
