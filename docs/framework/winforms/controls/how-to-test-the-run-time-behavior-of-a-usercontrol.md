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
ms.openlocfilehash: 110036e5031a2956375b1edf0689237661522d39
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180203"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="6cdef-102">Como: Testar o comportamento de tempo de execução de um UserControl</span><span class="sxs-lookup"><span data-stu-id="6cdef-102">How to: Test the run-time behavior of a UserControl</span></span>

<span data-ttu-id="6cdef-103">Ao desenvolver um <xref:System.Windows.Forms.UserControl>, você precisa testar seu comportamento de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6cdef-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="6cdef-104">É possível criar um projeto de aplicativo separado do Windows e colocar o controle em um formulário de teste, porém esse procedimento é inconveniente.</span><span class="sxs-lookup"><span data-stu-id="6cdef-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="6cdef-105">Uma maneira mais rápida e fácil é usar o **Contêiner de teste de UserControl** fornecido pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6cdef-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="6cdef-106">Esse contêiner de teste é iniciado diretamente do seu projeto de biblioteca de controles do Windows.</span><span class="sxs-lookup"><span data-stu-id="6cdef-106">This test container starts directly from your Windows control library project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6cdef-107">Para que o contêiner de teste carregue seu <xref:System.Windows.Forms.UserControl>, o controle deve ter pelo menos um construtor público.</span><span class="sxs-lookup"><span data-stu-id="6cdef-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="6cdef-108">Não é possível testar um controle do Visual C++ usando o **Contêiner de teste de UserControl**.</span><span class="sxs-lookup"><span data-stu-id="6cdef-108">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="6cdef-109">Testar o comportamento de tempo de execução de um UserControl</span><span class="sxs-lookup"><span data-stu-id="6cdef-109">Test the run-time behavior of a UserControl</span></span>

1. <span data-ttu-id="6cdef-110">No Visual Studio, crie um projeto de biblioteca de controle do Windows e nomeie-o **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="6cdef-110">In Visual Studio, create a Windows control library project, and name it **TestContainerExample**.</span></span>

2. <span data-ttu-id="6cdef-111">Na **Designer de formulários do Windows**, arraste um controle <xref:System.Windows.Forms.Label> da caixa de **ferramentas** para a superfície de design do controle.</span><span class="sxs-lookup"><span data-stu-id="6cdef-111">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="6cdef-112">Pressione <kbd>F5</kbd> para compilar o projeto e executar o **contêiner de teste do UserControl**.</span><span class="sxs-lookup"><span data-stu-id="6cdef-112">Press <kbd>F5</kbd> to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="6cdef-113">O contêiner de teste é exibido com seu <xref:System.Windows.Forms.UserControl> no painel de **Visualização** .</span><span class="sxs-lookup"><span data-stu-id="6cdef-113">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="6cdef-114">Selecione a propriedade <xref:System.Windows.Forms.Control.BackColor%2A> exibida no controle <xref:System.Windows.Forms.PropertyGrid> à direita do painel de **Visualização** .</span><span class="sxs-lookup"><span data-stu-id="6cdef-114">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="6cdef-115">Altere seu valor para **ControlDark**.</span><span class="sxs-lookup"><span data-stu-id="6cdef-115">Change its value to **ControlDark**.</span></span> <span data-ttu-id="6cdef-116">Observe que o controle é alterado para uma cor mais escura.</span><span class="sxs-lookup"><span data-stu-id="6cdef-116">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="6cdef-117">Tente alterar outros valores de propriedade e observar o efeito em seu controle.</span><span class="sxs-lookup"><span data-stu-id="6cdef-117">Try changing other property values and observe the effect on your control.</span></span>

5. <span data-ttu-id="6cdef-118">Clique na caixa de seleção **Controle de usuário Dock Fill** abaixo do painel **Visualização**.</span><span class="sxs-lookup"><span data-stu-id="6cdef-118">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="6cdef-119">Observe que o controle é redimensionado para preencher o painel.</span><span class="sxs-lookup"><span data-stu-id="6cdef-119">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="6cdef-120">Redimensione o contêiner de teste e observe como o controle é redimensionado com o painel.</span><span class="sxs-lookup"><span data-stu-id="6cdef-120">Resize the test container and observe that the control is resized with the pane.</span></span>

6. <span data-ttu-id="6cdef-121">Feche o contêiner de teste.</span><span class="sxs-lookup"><span data-stu-id="6cdef-121">Close the test container.</span></span>

7. <span data-ttu-id="6cdef-122">Adicione outro controle de usuário ao projeto **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="6cdef-122">Add another user control to the **TestContainerExample** project.</span></span>

8. <span data-ttu-id="6cdef-123">Na **Designer de formulários do Windows**, arraste um controle <xref:System.Windows.Forms.Button> da caixa de **ferramentas** para a superfície de design do controle.</span><span class="sxs-lookup"><span data-stu-id="6cdef-123">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>

9. <span data-ttu-id="6cdef-124">Pressione <kbd>F5</kbd> para compilar o projeto e executar o contêiner de teste.</span><span class="sxs-lookup"><span data-stu-id="6cdef-124">Press <kbd>F5</kbd> to build the project and run the test container.</span></span>

10. <span data-ttu-id="6cdef-125">Clique em **selecionar controle de usuário** <xref:System.Windows.Forms.ComboBox> para alternar entre os dois controles de usuário.</span><span class="sxs-lookup"><span data-stu-id="6cdef-125">Click the **Select User Control** <xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>

## <a name="test-user-controls-from-another-project"></a><span data-ttu-id="6cdef-126">Testar controles de usuário de outro projeto</span><span class="sxs-lookup"><span data-stu-id="6cdef-126">Test user controls from another project</span></span>

<span data-ttu-id="6cdef-127">É possível testar os controles de usuário de outros projetos no contêiner de teste do seu projeto atual.</span><span class="sxs-lookup"><span data-stu-id="6cdef-127">You can test user controls from other projects in your current project's test container.</span></span>

1. <span data-ttu-id="6cdef-128">No Visual Studio, crie um projeto de biblioteca de controle do Windows e nomeie-o **TestContainerExample2**.</span><span class="sxs-lookup"><span data-stu-id="6cdef-128">In Visual Studio, create a Windows control library project, and name it **TestContainerExample2**.</span></span>

2. <span data-ttu-id="6cdef-129">Na **Designer de formulários do Windows**, arraste um controle <xref:System.Windows.Forms.RadioButton> da caixa de **ferramentas** para a superfície de design do controle.</span><span class="sxs-lookup"><span data-stu-id="6cdef-129">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="6cdef-130">Pressione <kbd>F5</kbd> para compilar o projeto e executar o contêiner de teste.</span><span class="sxs-lookup"><span data-stu-id="6cdef-130">Press <kbd>F5</kbd> to build the project and run the test container.</span></span> <span data-ttu-id="6cdef-131">O contêiner de teste é exibido com seu <xref:System.Windows.Forms.UserControl> no painel de **Visualização** .</span><span class="sxs-lookup"><span data-stu-id="6cdef-131">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="6cdef-132">Clique no botão **Carregar**.</span><span class="sxs-lookup"><span data-stu-id="6cdef-132">Click the **Load** button.</span></span>

5. <span data-ttu-id="6cdef-133">Na caixa de diálogo **abrir** , navegue até *TestContainerExample. dll*, que você criou no procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="6cdef-133">In the **Open** dialog box, navigate to *TestContainerExample.dll*, which you built in the previous procedure.</span></span> <span data-ttu-id="6cdef-134">Selecione *TestContainerExample. dll* e clique no botão **abrir** para carregar os controles de usuário.</span><span class="sxs-lookup"><span data-stu-id="6cdef-134">Select *TestContainerExample.dll* and click the **Open** button to load the user controls.</span></span>

6. <span data-ttu-id="6cdef-135">Use o @no__t de **controle Selecionar usuário** -1 para alternar entre os dois controles de usuário do projeto **TestContainerExample** .</span><span class="sxs-lookup"><span data-stu-id="6cdef-135">Use the **Select User Control** <xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>

## <a name="see-also"></a><span data-ttu-id="6cdef-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6cdef-136">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <span data-ttu-id="6cdef-137">[Como: Criar controles de composição @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="6cdef-137">[How to: Author Composite Controls](how-to-author-composite-controls.md)</span></span>
- <span data-ttu-id="6cdef-138">[Passo a passo: Criando um controle composto @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="6cdef-138">[Walkthrough: Authoring a Composite Control](walkthrough-authoring-a-composite-control-with-visual-csharp.md)</span></span>
- <span data-ttu-id="6cdef-139">[Designer de Controle de Usuário](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6cdef-139">[User Control Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span></span>
