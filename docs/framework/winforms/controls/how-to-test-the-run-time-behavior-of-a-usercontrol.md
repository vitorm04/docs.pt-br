---
title: "Como testar o comportamento de tempo de execução de um UserControl"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 48b7c47a14f27439c60280a5c4202e9f4af76397
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="4854d-102">Como testar o comportamento de tempo de execução de um UserControl</span><span class="sxs-lookup"><span data-stu-id="4854d-102">How to: Test the Run-Time Behavior of a UserControl</span></span>
<span data-ttu-id="4854d-103">Ao desenvolver um <xref:System.Windows.Forms.UserControl>, você precisará testar seu comportamento de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4854d-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="4854d-104">É possível criar um projeto de aplicativo separado do Windows e colocar o controle em um formulário de teste, porém esse procedimento é inconveniente.</span><span class="sxs-lookup"><span data-stu-id="4854d-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="4854d-105">Uma maneira mais rápida e fácil é usar o **Contêiner de teste de UserControl** fornecido pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4854d-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="4854d-106">Esse contêiner de teste é iniciado diretamente do seu projeto de biblioteca de controles do Windows.</span><span class="sxs-lookup"><span data-stu-id="4854d-106">This test container starts directly from your Windows control library project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4854d-107">Para o contêiner de teste carregar seu <xref:System.Windows.Forms.UserControl>, o controle deve ter pelo menos um construtor público.</span><span class="sxs-lookup"><span data-stu-id="4854d-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4854d-108">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="4854d-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="4854d-109">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="4854d-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="4854d-110">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="4854d-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4854d-111">Não é possível testar um controle do Visual C++ usando o **Contêiner de teste de UserControl**.</span><span class="sxs-lookup"><span data-stu-id="4854d-111">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="4854d-112">Testar o comportamento de tempo de execução de um UserControl</span><span class="sxs-lookup"><span data-stu-id="4854d-112">To test the run-time behavior of a UserControl</span></span>  
  
1.  <span data-ttu-id="4854d-113">Crie um projeto de biblioteca de controles do Windows chamado **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="4854d-113">Create a Windows control library project called **TestContainerExample**.</span></span> <span data-ttu-id="4854d-114">Para obter detalhes, consulte [Modelo da Biblioteca de Controles do Windows](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span><span class="sxs-lookup"><span data-stu-id="4854d-114">For details, see [Windows Control Library Template](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span></span>  
  
2.  <span data-ttu-id="4854d-115">No **Windows Forms Designer**, arraste um <xref:System.Windows.Forms.Label> controlar do **caixa de ferramentas** na superfície de design do controle.</span><span class="sxs-lookup"><span data-stu-id="4854d-115">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3.  <span data-ttu-id="4854d-116">Pressione F5 para compilar o projeto e executar o **Contêiner de teste do UserControl**.</span><span class="sxs-lookup"><span data-stu-id="4854d-116">Press F5 to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="4854d-117">O contêiner de teste é exibido com seu <xref:System.Windows.Forms.UserControl> no **visualização** painel.</span><span class="sxs-lookup"><span data-stu-id="4854d-117">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4.  <span data-ttu-id="4854d-118">Selecione o <xref:System.Windows.Forms.Control.BackColor%2A> propriedade exibida no <xref:System.Windows.Forms.PropertyGrid> controle à direita do **visualização** painel.</span><span class="sxs-lookup"><span data-stu-id="4854d-118">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="4854d-119">Altere seu valor para `ControlDark`.</span><span class="sxs-lookup"><span data-stu-id="4854d-119">Change its value to `ControlDark`.</span></span> <span data-ttu-id="4854d-120">Observe que o controle é alterado para uma cor mais escura.</span><span class="sxs-lookup"><span data-stu-id="4854d-120">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="4854d-121">Tente alterar outros valores de propriedade e observar o efeito em seu controle.</span><span class="sxs-lookup"><span data-stu-id="4854d-121">Try changing other property values and observe the effect on your control.</span></span>  
  
5.  <span data-ttu-id="4854d-122">Clique na caixa de seleção **Controle de usuário Dock Fill** abaixo do painel **Visualização**.</span><span class="sxs-lookup"><span data-stu-id="4854d-122">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="4854d-123">Observe que o controle é redimensionado para preencher o painel.</span><span class="sxs-lookup"><span data-stu-id="4854d-123">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="4854d-124">Redimensione o contêiner de teste e observe como o controle é redimensionado com o painel.</span><span class="sxs-lookup"><span data-stu-id="4854d-124">Resize the test container and observe that the control is resized with the pane.</span></span>  
  
6.  <span data-ttu-id="4854d-125">Feche o contêiner de teste.</span><span class="sxs-lookup"><span data-stu-id="4854d-125">Close the test container.</span></span>  
  
7.  <span data-ttu-id="4854d-126">Adicione outro controle de usuário ao projeto **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="4854d-126">Add another user control to the **TestContainerExample** project.</span></span> <span data-ttu-id="4854d-127">Para ver mais detalhes, consulte [NIB: como adicionar itens existentes a um projeto](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span><span class="sxs-lookup"><span data-stu-id="4854d-127">For details, see [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span>  
  
8.  <span data-ttu-id="4854d-128">No **Windows Forms Designer**, arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** na superfície de design do controle.</span><span class="sxs-lookup"><span data-stu-id="4854d-128">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>  
  
9. <span data-ttu-id="4854d-129">Pressione F5 para compilar o projeto e execute o contêiner de teste.</span><span class="sxs-lookup"><span data-stu-id="4854d-129">Press F5 to build the project and run the test container.</span></span>  
  
10. <span data-ttu-id="4854d-130">Clique o **Selecionar controle de usuário** <xref:System.Windows.Forms.ComboBox> para alternar entre os controles de usuário de dois.</span><span class="sxs-lookup"><span data-stu-id="4854d-130">Click the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>  
  
## <a name="testing-user-controls-from-another-project"></a><span data-ttu-id="4854d-131">Testando controles de usuário de outro projeto</span><span class="sxs-lookup"><span data-stu-id="4854d-131">Testing User Controls from Another Project</span></span>  
 <span data-ttu-id="4854d-132">É possível testar os controles de usuário de outros projetos no contêiner de teste do seu projeto atual.</span><span class="sxs-lookup"><span data-stu-id="4854d-132">You can test user controls from other projects in your current project's test container.</span></span>  
  
#### <a name="to-test-user-controls-from-another-project"></a><span data-ttu-id="4854d-133">Testar controles de outro projeto</span><span class="sxs-lookup"><span data-stu-id="4854d-133">To test user controls from another project</span></span>  
  
1.  <span data-ttu-id="4854d-134">Crie um projeto de biblioteca de controles do Windows chamado **TestContainerExample2**.</span><span class="sxs-lookup"><span data-stu-id="4854d-134">Create a Windows control library project called **TestContainerExample2**.</span></span> <span data-ttu-id="4854d-135">Para obter detalhes, consulte [Modelo da Biblioteca de Controles do Windows](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span><span class="sxs-lookup"><span data-stu-id="4854d-135">For details, see [Windows Control Library Template](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span></span>  
  
2.  <span data-ttu-id="4854d-136">No **Windows Forms Designer**, arraste um <xref:System.Windows.Forms.RadioButton> controlar do **caixa de ferramentas** na superfície de design do controle.</span><span class="sxs-lookup"><span data-stu-id="4854d-136">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3.  <span data-ttu-id="4854d-137">Pressione F5 para compilar o projeto e execute o contêiner de teste.</span><span class="sxs-lookup"><span data-stu-id="4854d-137">Press F5 to build the project and run the test container.</span></span> <span data-ttu-id="4854d-138">O contêiner de teste é exibido com seu <xref:System.Windows.Forms.UserControl> no **visualização** painel.</span><span class="sxs-lookup"><span data-stu-id="4854d-138">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4.  <span data-ttu-id="4854d-139">Clique no botão **Carregar**.</span><span class="sxs-lookup"><span data-stu-id="4854d-139">Click the **Load** button.</span></span>  
  
5.  <span data-ttu-id="4854d-140">Na caixa de diálogo **Abrir**, navegue até **TestContainerExample**.dll que você criou no procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="4854d-140">In the **Open** dialog box, navigate to **TestContainerExample**.dll, which you built in the previous procedure.</span></span> <span data-ttu-id="4854d-141">Selecione **TestContainerExample**.dll e clique no botão **Abrir** para carregar os controles de usuário</span><span class="sxs-lookup"><span data-stu-id="4854d-141">Select **TestContainerExample**.dll and click the **Open** button to load the user controls</span></span>  
  
6.  <span data-ttu-id="4854d-142">Use o **Selecionar controle de usuário** <xref:System.Windows.Forms.ComboBox> para alternar entre os controles de usuário de dois do **TestContainerExample** projeto.</span><span class="sxs-lookup"><span data-stu-id="4854d-142">Use the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4854d-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4854d-143">See Also</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 [<span data-ttu-id="4854d-144">Como criar controles de composição</span><span class="sxs-lookup"><span data-stu-id="4854d-144">How to: Author Composite Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 [<span data-ttu-id="4854d-145">Passo a passo: criando um controle de composição com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4854d-145">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [<span data-ttu-id="4854d-146">Passo a passo: criando um controle de composição com o Visual C#</span><span class="sxs-lookup"><span data-stu-id="4854d-146">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [<span data-ttu-id="4854d-147">Designer de Controle de Usuário</span><span class="sxs-lookup"><span data-stu-id="4854d-147">User Control Designer</span></span>](http://msdn.microsoft.com/library/2abb9eec-ba32-45cb-b73d-8b52a8bd6bf1)
