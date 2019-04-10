---
title: 'Passo a passo: Preencher de forma automática a caixa de ferramentas com componentes personalizados'
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: 6ecf69350b8337dc6049b73251809192b47dc2fb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338092"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a><span data-ttu-id="a89dc-102">Passo a passo: Preencher de forma automática a caixa de ferramentas com componentes personalizados</span><span class="sxs-lookup"><span data-stu-id="a89dc-102">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>
<span data-ttu-id="a89dc-103">Se seus componentes forem definidos por um projeto na solução aberta no momento, eles aparecerão automaticamente na **Caixa de Ferramentas** sem exigir que você execute nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="a89dc-103">If your components are defined by a project in the currently open solution, they will automatically appear in the **Toolbox**, with no action required by you.</span></span> <span data-ttu-id="a89dc-104">Você também pode preencher manualmente a **Caixa de Ferramentas** com seus componentes personalizados usando a [Caixa de Diálogo Escolher Itens da Caixa de Ferramentas (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100)), mas a **Caixa de Ferramentas** leva em conta itens nas saídas de build da sua solução com todas as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="a89dc-104">You can also manually populate the **Toolbox** with your custom components by using the [Choose Toolbox Items Dialog Box (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100)), but the **Toolbox** takes account of items in your solution's build outputs with all the following characteristics:</span></span>  
  
-   <span data-ttu-id="a89dc-105">Implementa <xref:System.ComponentModel.IComponent>;</span><span class="sxs-lookup"><span data-stu-id="a89dc-105">Implements <xref:System.ComponentModel.IComponent>;</span></span>  
  
-   <span data-ttu-id="a89dc-106">Não tem <xref:System.ComponentModel.ToolboxItemAttribute> definido como `false`;</span><span class="sxs-lookup"><span data-stu-id="a89dc-106">Does not have <xref:System.ComponentModel.ToolboxItemAttribute> set to `false`;</span></span>  
  
-   <span data-ttu-id="a89dc-107">Não tem <xref:System.ComponentModel.DesignTimeVisibleAttribute> definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="a89dc-107">Does not have <xref:System.ComponentModel.DesignTimeVisibleAttribute> set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a89dc-108">A **Caixa de Ferramentas** não segue cadeias de referência, portanto, não exibirá itens que não sejam criados por um projeto em sua solução.</span><span class="sxs-lookup"><span data-stu-id="a89dc-108">The **Toolbox** does not follow reference chains, so it will not display items that are not built by a project in your solution.</span></span>  
  
 <span data-ttu-id="a89dc-109">Este passo a passo demonstra como um componente personalizado aparece automaticamente na **Caixa de Ferramentas** depois que o componente é criado.</span><span class="sxs-lookup"><span data-stu-id="a89dc-109">This walkthrough demonstrates how a custom component automatically appears in the **Toolbox** once the component is built.</span></span> <span data-ttu-id="a89dc-110">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="a89dc-110">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="a89dc-111">Criando um projeto dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a89dc-111">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="a89dc-112">Criando um componente personalizado.</span><span class="sxs-lookup"><span data-stu-id="a89dc-112">Creating a custom component.</span></span>  
  
-   <span data-ttu-id="a89dc-113">Criando uma instância de um componente personalizado.</span><span class="sxs-lookup"><span data-stu-id="a89dc-113">Creating an instance of a custom component.</span></span>  
  
-   <span data-ttu-id="a89dc-114">Descarregando e recarregando um componente personalizado.</span><span class="sxs-lookup"><span data-stu-id="a89dc-114">Unloading and reloading a custom component.</span></span>  
  
 <span data-ttu-id="a89dc-115">Quando tiver terminado, verá que a **Caixa de Ferramentas** é preenchida com um componente que você criou.</span><span class="sxs-lookup"><span data-stu-id="a89dc-115">When you are finished, you will see that the **Toolbox** is populated with a component that you have created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a89dc-116">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="a89dc-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a89dc-117">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="a89dc-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a89dc-118">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="a89dc-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="a89dc-119">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="a89dc-119">Creating the Project</span></span>  
 <span data-ttu-id="a89dc-120">A primeira etapa é criar o projeto e configurar o formulário.</span><span class="sxs-lookup"><span data-stu-id="a89dc-120">The first step is to create the project and to set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="a89dc-121">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="a89dc-121">To create the project</span></span>  
  
1. <span data-ttu-id="a89dc-122">Crie um projeto de aplicativo baseado no Windows chamado `ToolboxExample` (**arquivo** > **New** > **projeto**  >  **Visual c#** ou **Visual Basic** > **área de trabalho clássica** > **aplicativo de formulários do Windows**).</span><span class="sxs-lookup"><span data-stu-id="a89dc-122">Create a Windows-based application project called `ToolboxExample` (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2. <span data-ttu-id="a89dc-123">Adicione um novo componente ao projeto.</span><span class="sxs-lookup"><span data-stu-id="a89dc-123">Add a new component to the project.</span></span> <span data-ttu-id="a89dc-124">Chame `DemoComponent`.</span><span class="sxs-lookup"><span data-stu-id="a89dc-124">Call it `DemoComponent`.</span></span>  
  
     <span data-ttu-id="a89dc-125">Para obter mais informações, confira [Como: Adicionar novos itens de projeto](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a89dc-125">For more information, see [How to: Add New Project Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span></span>  
  
3. <span data-ttu-id="a89dc-126">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="a89dc-126">Build the project.</span></span>  
  
4. <span data-ttu-id="a89dc-127">No menu **Ferramentas**, clique no item **Opções**.</span><span class="sxs-lookup"><span data-stu-id="a89dc-127">From the **Tools** menu, click the **Options** item.</span></span> <span data-ttu-id="a89dc-128">Clique em **Geral** no item **Designer de Formulários do Windows** e certifique-se de que a opção **AutoToolboxPopulate** esteja definida como **True**.</span><span class="sxs-lookup"><span data-stu-id="a89dc-128">Click **General** under the **Windows Forms Designer** item and ensure that the **AutoToolboxPopulate** option is set to **True**.</span></span>  
  
## <a name="creating-an-instance-of-a-custom-component"></a><span data-ttu-id="a89dc-129">Criando uma instância de um componente personalizado</span><span class="sxs-lookup"><span data-stu-id="a89dc-129">Creating an Instance of a Custom Component</span></span>  
 <span data-ttu-id="a89dc-130">A próxima etapa é criar uma instância do componente personalizado no formulário.</span><span class="sxs-lookup"><span data-stu-id="a89dc-130">The next step is to create an instance of the custom component on the form.</span></span> <span data-ttu-id="a89dc-131">Uma vez que a **Caixa de Ferramentas** automaticamente conta para o novo componente, isso é tão fácil quanto criar qualquer outro componente ou controle.</span><span class="sxs-lookup"><span data-stu-id="a89dc-131">Because the **Toolbox** automatically accounts for the new component, this is as easy as creating any other component or control.</span></span>  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a><span data-ttu-id="a89dc-132">Para criar uma instância de um componente personalizado</span><span class="sxs-lookup"><span data-stu-id="a89dc-132">To create an instance of a custom component</span></span>  
  
1. <span data-ttu-id="a89dc-133">Abra o formulário do projeto no **Designer de Formulários**.</span><span class="sxs-lookup"><span data-stu-id="a89dc-133">Open the project's form in the **Forms Designer**.</span></span>  
  
2. <span data-ttu-id="a89dc-134">Na **Caixa de Ferramentas**, clique na nova guia chamada **Componentes de ToolboxExample**.</span><span class="sxs-lookup"><span data-stu-id="a89dc-134">In the **Toolbox**, click the new tab called **ToolboxExample Components**.</span></span>  
  
     <span data-ttu-id="a89dc-135">Ao clicar na guia, você verá **DemoComponent**.</span><span class="sxs-lookup"><span data-stu-id="a89dc-135">Once you click the tab, you will see **DemoComponent**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a89dc-136">Por motivos de desempenho de componentes na área preenchida automaticamente dos **caixa de ferramentas** não exibem bitmaps personalizados e o <xref:System.Drawing.ToolboxBitmapAttribute> não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="a89dc-136">For performance reasons, components in the auto-populated area of the **Toolbox** do not display custom bitmaps, and the <xref:System.Drawing.ToolboxBitmapAttribute> is not supported.</span></span> <span data-ttu-id="a89dc-137">Para exibir um ícone para um componente personalizado na **Caixa de Ferramentas**, use a caixa de diálogo **Escolher Itens da Caixa de Ferramentas** para carregar seu componente.</span><span class="sxs-lookup"><span data-stu-id="a89dc-137">To display an icon for a custom component in the **Toolbox**, use the **Choose Toolbox Items** dialog box to load your component.</span></span>  
  
3. <span data-ttu-id="a89dc-138">Arraste o componente para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="a89dc-138">Drag your component onto your form.</span></span>  
  
     <span data-ttu-id="a89dc-139">Uma instância do componente é criada e adicionada à **Bandeja de Componentes**.</span><span class="sxs-lookup"><span data-stu-id="a89dc-139">An instance of the component is created and added to the **Component Tray**.</span></span>  
  
## <a name="unloading-and-reloading-a-custom-component"></a><span data-ttu-id="a89dc-140">Descarregando e recarregando um componente personalizado</span><span class="sxs-lookup"><span data-stu-id="a89dc-140">Unloading and Reloading a Custom Component</span></span>  
 <span data-ttu-id="a89dc-141">A **Caixa de Ferramentas** considera os componentes em cada projeto carregado e, quando um projeto é descarregado, ela remove referências aos componentes do projeto.</span><span class="sxs-lookup"><span data-stu-id="a89dc-141">The **Toolbox** takes account of the components in each loaded project, and when a project is unloaded, it removes references to the project's components.</span></span>  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a><span data-ttu-id="a89dc-142">Para experimentar o efeito que descarregar e recarregar componentes tem sobre a Caixa de Ferramentas</span><span class="sxs-lookup"><span data-stu-id="a89dc-142">To experiment with the effect on the Toolbox of unloading and reloading components</span></span>  
  
1. <span data-ttu-id="a89dc-143">Descarregue o projeto da solução.</span><span class="sxs-lookup"><span data-stu-id="a89dc-143">Unload the project from the solution.</span></span>  
  
     <span data-ttu-id="a89dc-144">Para obter mais informações sobre descarregar projetos, consulte [como: Descarregar e recarregar projetos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a89dc-144">For more information about unloading projects, see [How to: Unload and Reload Projects](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100)).</span></span> <span data-ttu-id="a89dc-145">Se você for solicitado a salvar, escolha **Sim**.</span><span class="sxs-lookup"><span data-stu-id="a89dc-145">If you are prompted to save, choose **Yes**.</span></span>  
  
2. <span data-ttu-id="a89dc-146">Adicione um novo projeto de **Aplicativos do Windows** à solução.</span><span class="sxs-lookup"><span data-stu-id="a89dc-146">Add a new **Windows Application** project to the solution.</span></span> <span data-ttu-id="a89dc-147">Abra o formulário no **Designer**.</span><span class="sxs-lookup"><span data-stu-id="a89dc-147">Open the form in the **Designer**.</span></span>  
  
     <span data-ttu-id="a89dc-148">A guia **Componentes de ToolboxExample** do projeto anterior agora está ausente.</span><span class="sxs-lookup"><span data-stu-id="a89dc-148">The **ToolboxExample Components** tab from the previous project is now gone.</span></span>  
  
3. <span data-ttu-id="a89dc-149">Recarregue o projeto `ToolboxExample`.</span><span class="sxs-lookup"><span data-stu-id="a89dc-149">Reload the `ToolboxExample` project.</span></span>  
  
     <span data-ttu-id="a89dc-150">A guia **Componentes de ToolboxExample** agora será exibida novamente.</span><span class="sxs-lookup"><span data-stu-id="a89dc-150">The **ToolboxExample Components** tab now reappears.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a89dc-151">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="a89dc-151">Next Steps</span></span>  
 <span data-ttu-id="a89dc-152">Este passo a passo demonstra que a **Caixa de Ferramentas** leva em conta componentes do projeto, mas a **Caixa de Ferramentas** também leva em os controles.</span><span class="sxs-lookup"><span data-stu-id="a89dc-152">This walkthrough demonstrates that the **Toolbox** takes account of a project's components, but the **Toolbox** is also takes account of controls.</span></span> <span data-ttu-id="a89dc-153">Experimente seus próprios controles personalizados adicionando e removendo projetos de controle de sua solução.</span><span class="sxs-lookup"><span data-stu-id="a89dc-153">Experiment with your own custom controls by adding and removing control projects from your solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a89dc-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a89dc-154">See also</span></span>

- [<span data-ttu-id="a89dc-155">Geral, Windows Forms Designer, Opções da Caixa de Diálogo</span><span class="sxs-lookup"><span data-stu-id="a89dc-155">General, Windows Forms Designer, Options Dialog Box</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))
- [<span data-ttu-id="a89dc-156">Como: Manipular guias da caixa de ferramentas</span><span class="sxs-lookup"><span data-stu-id="a89dc-156">How to: Manipulate Toolbox Tabs</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100))
- [<span data-ttu-id="a89dc-157">Escolha a caixa de diálogo de itens de caixa de ferramentas (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="a89dc-157">Choose Toolbox Items Dialog Box (Visual Studio)</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))
- [<span data-ttu-id="a89dc-158">Colocando controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a89dc-158">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
