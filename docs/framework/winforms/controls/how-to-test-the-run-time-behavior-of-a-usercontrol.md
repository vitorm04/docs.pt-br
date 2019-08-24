---
title: 'Como: Testar o comportamento de tempo de execução de um UserControl'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1be79d52be3b5b84938d8548a8f101e965fa9dbb
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015774"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="d0200-102">Como: Testar o comportamento de tempo de execução de um UserControl</span><span class="sxs-lookup"><span data-stu-id="d0200-102">How to: Test the run-time behavior of a UserControl</span></span>

<span data-ttu-id="d0200-103">Ao desenvolver um <xref:System.Windows.Forms.UserControl>, você precisa testar seu comportamento de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d0200-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="d0200-104">É possível criar um projeto de aplicativo separado do Windows e colocar o controle em um formulário de teste, porém esse procedimento é inconveniente.</span><span class="sxs-lookup"><span data-stu-id="d0200-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="d0200-105">Uma maneira mais rápida e fácil é usar o **Contêiner de teste de UserControl** fornecido pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d0200-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="d0200-106">Esse contêiner de teste é iniciado diretamente do seu projeto de biblioteca de controles do Windows.</span><span class="sxs-lookup"><span data-stu-id="d0200-106">This test container starts directly from your Windows control library project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d0200-107">Para que o contêiner de teste carregue <xref:System.Windows.Forms.UserControl>seu, o controle deve ter pelo menos um construtor público.</span><span class="sxs-lookup"><span data-stu-id="d0200-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="d0200-108">Não é possível testar um controle do Visual C++ usando o **Contêiner de teste de UserControl**.</span><span class="sxs-lookup"><span data-stu-id="d0200-108">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="d0200-109">Testar o comportamento de tempo de execução de um UserControl</span><span class="sxs-lookup"><span data-stu-id="d0200-109">Test the run-time behavior of a UserControl</span></span>

1. <span data-ttu-id="d0200-110">No Visual Studio, crie um projeto de biblioteca de controle do Windows e nomeie-o **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="d0200-110">In Visual Studio, create a Windows control library project, and name it **TestContainerExample**.</span></span>

2. <span data-ttu-id="d0200-111">Na **Designer de formulários do Windows**, arraste um <xref:System.Windows.Forms.Label> controle da caixa de **ferramentas** para a superfície de design do controle.</span><span class="sxs-lookup"><span data-stu-id="d0200-111">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="d0200-112">Pressione **F5** para compilar o projeto e executar o **contêiner de teste do UserControl**.</span><span class="sxs-lookup"><span data-stu-id="d0200-112">Press **F5** to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="d0200-113">O contêiner de teste é exibido <xref:System.Windows.Forms.UserControl> com seu no painel de **Visualização** .</span><span class="sxs-lookup"><span data-stu-id="d0200-113">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="d0200-114">Selecione a <xref:System.Windows.Forms.Control.BackColor%2A> propriedade exibida <xref:System.Windows.Forms.PropertyGrid> no controle à direita do painel de **Visualização** .</span><span class="sxs-lookup"><span data-stu-id="d0200-114">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="d0200-115">Altere seu valor para **ControlDark**.</span><span class="sxs-lookup"><span data-stu-id="d0200-115">Change its value to **ControlDark**.</span></span> <span data-ttu-id="d0200-116">Observe que o controle é alterado para uma cor mais escura.</span><span class="sxs-lookup"><span data-stu-id="d0200-116">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="d0200-117">Tente alterar outros valores de propriedade e observar o efeito em seu controle.</span><span class="sxs-lookup"><span data-stu-id="d0200-117">Try changing other property values and observe the effect on your control.</span></span>

5. <span data-ttu-id="d0200-118">Clique na caixa de seleção **Controle de usuário Dock Fill** abaixo do painel **Visualização**.</span><span class="sxs-lookup"><span data-stu-id="d0200-118">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="d0200-119">Observe que o controle é redimensionado para preencher o painel.</span><span class="sxs-lookup"><span data-stu-id="d0200-119">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="d0200-120">Redimensione o contêiner de teste e observe como o controle é redimensionado com o painel.</span><span class="sxs-lookup"><span data-stu-id="d0200-120">Resize the test container and observe that the control is resized with the pane.</span></span>

6. <span data-ttu-id="d0200-121">Feche o contêiner de teste.</span><span class="sxs-lookup"><span data-stu-id="d0200-121">Close the test container.</span></span>

7. <span data-ttu-id="d0200-122">Adicione outro controle de usuário ao projeto **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="d0200-122">Add another user control to the **TestContainerExample** project.</span></span>

8. <span data-ttu-id="d0200-123">Na **Designer de formulários do Windows**, arraste um <xref:System.Windows.Forms.Button> controle da caixa de **ferramentas** para a superfície de design do controle.</span><span class="sxs-lookup"><span data-stu-id="d0200-123">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>

9. <span data-ttu-id="d0200-124">Pressione **F5** para compilar o projeto e executar o contêiner de teste.</span><span class="sxs-lookup"><span data-stu-id="d0200-124">Press **F5** to build the project and run the test container.</span></span>

10. <span data-ttu-id="d0200-125">Clique<xref:System.Windows.Forms.ComboBox> no **controle Selecionar usuário** para alternar entre os dois controles de usuário.</span><span class="sxs-lookup"><span data-stu-id="d0200-125">Click the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>

## <a name="test-user-controls-from-another-project"></a><span data-ttu-id="d0200-126">Testar controles de usuário de outro projeto</span><span class="sxs-lookup"><span data-stu-id="d0200-126">Test user controls from another project</span></span>

<span data-ttu-id="d0200-127">É possível testar os controles de usuário de outros projetos no contêiner de teste do seu projeto atual.</span><span class="sxs-lookup"><span data-stu-id="d0200-127">You can test user controls from other projects in your current project's test container.</span></span>

1. <span data-ttu-id="d0200-128">No Visual Studio, crie um projeto de biblioteca de controle do Windows e nomeie-o **TestContainerExample2**.</span><span class="sxs-lookup"><span data-stu-id="d0200-128">In Visual Studio, create a Windows control library project, and name it **TestContainerExample2**.</span></span>

2. <span data-ttu-id="d0200-129">Na **Designer de formulários do Windows**, arraste um <xref:System.Windows.Forms.RadioButton> controle da caixa de **ferramentas** para a superfície de design do controle.</span><span class="sxs-lookup"><span data-stu-id="d0200-129">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="d0200-130">Pressione **F5** para compilar o projeto e executar o contêiner de teste.</span><span class="sxs-lookup"><span data-stu-id="d0200-130">Press **F5** to build the project and run the test container.</span></span> <span data-ttu-id="d0200-131">O contêiner de teste é exibido <xref:System.Windows.Forms.UserControl> com seu no painel de **Visualização** .</span><span class="sxs-lookup"><span data-stu-id="d0200-131">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="d0200-132">Clique no botão **Carregar**.</span><span class="sxs-lookup"><span data-stu-id="d0200-132">Click the **Load** button.</span></span>

5. <span data-ttu-id="d0200-133">Na caixa de diálogo **Abrir**, navegue até **TestContainerExample**.dll que você criou no procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="d0200-133">In the **Open** dialog box, navigate to **TestContainerExample**.dll, which you built in the previous procedure.</span></span> <span data-ttu-id="d0200-134">Selecione **TestContainerExample**.dll e clique no botão **Abrir** para carregar os controles de usuário</span><span class="sxs-lookup"><span data-stu-id="d0200-134">Select **TestContainerExample**.dll and click the **Open** button to load the user controls</span></span>

6. <span data-ttu-id="d0200-135">Use<xref:System.Windows.Forms.ComboBox> o **controle Selecionar usuário** para alternar entre os dois controles de usuário do projeto **TestContainerExample** .</span><span class="sxs-lookup"><span data-stu-id="d0200-135">Use the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0200-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0200-136">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="d0200-137">Como: Controles de composição de autor</span><span class="sxs-lookup"><span data-stu-id="d0200-137">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="d0200-138">Passo a passo: Criando um controle composto</span><span class="sxs-lookup"><span data-stu-id="d0200-138">Walkthrough: Authoring a Composite Control</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- <span data-ttu-id="d0200-139">[Designer de Controle de Usuário](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d0200-139">[User Control Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span></span>
