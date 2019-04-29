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
ms.openlocfilehash: 15b37c71e6643b588c0378510965a9a3e7cb56e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672569"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="5e4ae-102">Como: Testar o comportamento de tempo de execução de um UserControl</span><span class="sxs-lookup"><span data-stu-id="5e4ae-102">How to: Test the Run-Time Behavior of a UserControl</span></span>
<span data-ttu-id="5e4ae-103">Quando você desenvolve um <xref:System.Windows.Forms.UserControl>, você precisa testar seu comportamento de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="5e4ae-104">É possível criar um projeto de aplicativo separado do Windows e colocar o controle em um formulário de teste, porém esse procedimento é inconveniente.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="5e4ae-105">Uma maneira mais rápida e fácil é usar o **Contêiner de teste de UserControl** fornecido pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="5e4ae-106">Esse contêiner de teste é iniciado diretamente do seu projeto de biblioteca de controles do Windows.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-106">This test container starts directly from your Windows control library project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5e4ae-107">Para o contêiner de teste carregar seu <xref:System.Windows.Forms.UserControl>, o controle deve ter pelo menos um construtor público.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e4ae-108">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5e4ae-109">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5e4ae-110">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="5e4ae-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e4ae-111">Não é possível testar um controle do Visual C++ usando o **Contêiner de teste de UserControl**.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-111">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="5e4ae-112">Testar o comportamento de tempo de execução de um UserControl</span><span class="sxs-lookup"><span data-stu-id="5e4ae-112">To test the run-time behavior of a UserControl</span></span>  
  
1. <span data-ttu-id="5e4ae-113">Crie um projeto de biblioteca de controles do Windows chamado **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-113">Create a Windows control library project called **TestContainerExample**.</span></span> <span data-ttu-id="5e4ae-114">Para obter detalhes, consulte [Modelo da Biblioteca de Controles do Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="5e4ae-114">For details, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="5e4ae-115">No **Designer de formulários do Windows**, arraste um <xref:System.Windows.Forms.Label> controlar dos **caixa de ferramentas** na superfície de design do controle.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-115">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3. <span data-ttu-id="5e4ae-116">Pressione F5 para compilar o projeto e executar o **Contêiner de teste do UserControl**.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-116">Press F5 to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="5e4ae-117">O contêiner de teste é exibido com seu <xref:System.Windows.Forms.UserControl> no **visualização** painel.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-117">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4. <span data-ttu-id="5e4ae-118">Selecione o <xref:System.Windows.Forms.Control.BackColor%2A> propriedade exibida na <xref:System.Windows.Forms.PropertyGrid> controle à direita do **visualização** painel.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-118">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="5e4ae-119">Altere seu valor para `ControlDark`.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-119">Change its value to `ControlDark`.</span></span> <span data-ttu-id="5e4ae-120">Observe que o controle é alterado para uma cor mais escura.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-120">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="5e4ae-121">Tente alterar outros valores de propriedade e observar o efeito em seu controle.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-121">Try changing other property values and observe the effect on your control.</span></span>  
  
5. <span data-ttu-id="5e4ae-122">Clique na caixa de seleção **Controle de usuário Dock Fill** abaixo do painel **Visualização**.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-122">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="5e4ae-123">Observe que o controle é redimensionado para preencher o painel.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-123">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="5e4ae-124">Redimensione o contêiner de teste e observe como o controle é redimensionado com o painel.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-124">Resize the test container and observe that the control is resized with the pane.</span></span>  
  
6. <span data-ttu-id="5e4ae-125">Feche o contêiner de teste.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-125">Close the test container.</span></span>  
  
7. <span data-ttu-id="5e4ae-126">Adicione outro controle de usuário ao projeto **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-126">Add another user control to the **TestContainerExample** project.</span></span> <span data-ttu-id="5e4ae-127">Para obter detalhes, confira [Como: Adicionar itens existentes a um projeto](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="5e4ae-127">For details, see [How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100)).</span></span>  
  
8. <span data-ttu-id="5e4ae-128">No **Designer de formulários do Windows**, arraste um <xref:System.Windows.Forms.Button> controlar dos **caixa de ferramentas** na superfície de design do controle.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-128">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>  
  
9. <span data-ttu-id="5e4ae-129">Pressione F5 para compilar o projeto e execute o contêiner de teste.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-129">Press F5 to build the project and run the test container.</span></span>  
  
10. <span data-ttu-id="5e4ae-130">Clique o **Selecionar controle de usuário** <xref:System.Windows.Forms.ComboBox> para alternar entre os dois controles de usuário.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-130">Click the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>  
  
## <a name="testing-user-controls-from-another-project"></a><span data-ttu-id="5e4ae-131">Testando controles de usuário de outro projeto</span><span class="sxs-lookup"><span data-stu-id="5e4ae-131">Testing User Controls from Another Project</span></span>  
 <span data-ttu-id="5e4ae-132">É possível testar os controles de usuário de outros projetos no contêiner de teste do seu projeto atual.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-132">You can test user controls from other projects in your current project's test container.</span></span>  
  
#### <a name="to-test-user-controls-from-another-project"></a><span data-ttu-id="5e4ae-133">Testar controles de outro projeto</span><span class="sxs-lookup"><span data-stu-id="5e4ae-133">To test user controls from another project</span></span>  
  
1. <span data-ttu-id="5e4ae-134">Crie um projeto de biblioteca de controles do Windows chamado **TestContainerExample2**.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-134">Create a Windows control library project called **TestContainerExample2**.</span></span> <span data-ttu-id="5e4ae-135">Para obter detalhes, consulte [Modelo da Biblioteca de Controles do Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="5e4ae-135">For details, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="5e4ae-136">No **Designer de formulários do Windows**, arraste um <xref:System.Windows.Forms.RadioButton> controlar dos **caixa de ferramentas** na superfície de design do controle.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-136">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3. <span data-ttu-id="5e4ae-137">Pressione F5 para compilar o projeto e execute o contêiner de teste.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-137">Press F5 to build the project and run the test container.</span></span> <span data-ttu-id="5e4ae-138">O contêiner de teste é exibido com seu <xref:System.Windows.Forms.UserControl> no **visualização** painel.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-138">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4. <span data-ttu-id="5e4ae-139">Clique no botão **Carregar**.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-139">Click the **Load** button.</span></span>  
  
5. <span data-ttu-id="5e4ae-140">Na caixa de diálogo **Abrir**, navegue até **TestContainerExample**.dll que você criou no procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-140">In the **Open** dialog box, navigate to **TestContainerExample**.dll, which you built in the previous procedure.</span></span> <span data-ttu-id="5e4ae-141">Selecione **TestContainerExample**.dll e clique no botão **Abrir** para carregar os controles de usuário</span><span class="sxs-lookup"><span data-stu-id="5e4ae-141">Select **TestContainerExample**.dll and click the **Open** button to load the user controls</span></span>  
  
6. <span data-ttu-id="5e4ae-142">Use o **Selecionar controle de usuário** <xref:System.Windows.Forms.ComboBox> para alternar entre os dois controles de usuário da **TestContainerExample** projeto.</span><span class="sxs-lookup"><span data-stu-id="5e4ae-142">Use the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e4ae-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e4ae-143">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="5e4ae-144">Como: Criar controles compostos</span><span class="sxs-lookup"><span data-stu-id="5e4ae-144">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="5e4ae-145">Passo a passo: Criando um controle composto com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e4ae-145">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="5e4ae-146">Passo a passo: Criando um controle composto com VisualC#</span><span class="sxs-lookup"><span data-stu-id="5e4ae-146">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- <span data-ttu-id="5e4ae-147">[Designer de Controle de Usuário](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5e4ae-147">[User Control Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span></span>
