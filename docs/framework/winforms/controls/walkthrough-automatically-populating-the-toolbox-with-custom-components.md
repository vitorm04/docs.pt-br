---
title: 'Passo a passo: Preencher de forma automática a caixa de ferramentas com componentes personalizados'
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: 876de650f9c182c0f82a02d1c5b356faa4f7f118
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211156"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a><span data-ttu-id="83c31-102">Passo a passo: Preencher de forma automática a caixa de ferramentas com componentes personalizados</span><span class="sxs-lookup"><span data-stu-id="83c31-102">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>

<span data-ttu-id="83c31-103">Se seus componentes forem definidos por um projeto na solução aberta no momento, eles aparecerão automaticamente na **Caixa de Ferramentas** sem exigir que você execute nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="83c31-103">If your components are defined by a project in the currently open solution, they will automatically appear in the **Toolbox**, with no action required by you.</span></span> <span data-ttu-id="83c31-104">Você também pode preencher manualmente a **Caixa de Ferramentas** com seus componentes personalizados usando a [Caixa de Diálogo Escolher Itens da Caixa de Ferramentas (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100)), mas a **Caixa de Ferramentas** leva em conta itens nas saídas de build da sua solução com todas as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="83c31-104">You can also manually populate the **Toolbox** with your custom components by using the [Choose Toolbox Items Dialog Box (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100)), but the **Toolbox** takes account of items in your solution's build outputs with all the following characteristics:</span></span>

- <span data-ttu-id="83c31-105">Implementa <xref:System.ComponentModel.IComponent>;</span><span class="sxs-lookup"><span data-stu-id="83c31-105">Implements <xref:System.ComponentModel.IComponent>;</span></span>

- <span data-ttu-id="83c31-106">Não tem <xref:System.ComponentModel.ToolboxItemAttribute> definido como `false`;</span><span class="sxs-lookup"><span data-stu-id="83c31-106">Does not have <xref:System.ComponentModel.ToolboxItemAttribute> set to `false`;</span></span>

- <span data-ttu-id="83c31-107">Não tem <xref:System.ComponentModel.DesignTimeVisibleAttribute> definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="83c31-107">Does not have <xref:System.ComponentModel.DesignTimeVisibleAttribute> set to `false`.</span></span>

> [!NOTE]
> <span data-ttu-id="83c31-108">O **caixa de ferramentas** não segue cadeias de referência, portanto, ele não exibirá itens que não são criados por um projeto em sua solução.</span><span class="sxs-lookup"><span data-stu-id="83c31-108">The **Toolbox** does not follow reference chains, so it won't display items that are not built by a project in your solution.</span></span>

<span data-ttu-id="83c31-109">Este passo a passo demonstra como um componente personalizado aparece automaticamente na **Caixa de Ferramentas** depois que o componente é criado.</span><span class="sxs-lookup"><span data-stu-id="83c31-109">This walkthrough demonstrates how a custom component automatically appears in the **Toolbox** once the component is built.</span></span> <span data-ttu-id="83c31-110">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="83c31-110">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="83c31-111">Criando um projeto dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="83c31-111">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="83c31-112">Criando um componente personalizado.</span><span class="sxs-lookup"><span data-stu-id="83c31-112">Creating a custom component.</span></span>

- <span data-ttu-id="83c31-113">Criando uma instância de um componente personalizado.</span><span class="sxs-lookup"><span data-stu-id="83c31-113">Creating an instance of a custom component.</span></span>

- <span data-ttu-id="83c31-114">Descarregando e recarregando um componente personalizado.</span><span class="sxs-lookup"><span data-stu-id="83c31-114">Unloading and reloading a custom component.</span></span>

<span data-ttu-id="83c31-115">Quando tiver terminado, verá que a **Caixa de Ferramentas** é preenchida com um componente que você criou.</span><span class="sxs-lookup"><span data-stu-id="83c31-115">When you are finished, you will see that the **Toolbox** is populated with a component that you have created.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="83c31-116">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="83c31-116">Create the project</span></span>

1. <span data-ttu-id="83c31-117">No Visual Studio, crie um projeto de aplicativo baseado no Windows chamado `ToolboxExample` (**arquivo** > **New** > **projeto**  >  **Visual C#**  ou **Visual Basic** > **área de trabalho clássica** > **Windows Forms Aplicativo**).</span><span class="sxs-lookup"><span data-stu-id="83c31-117">In Visual Studio, create a Windows-based application project called `ToolboxExample` (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="83c31-118">Adicione um novo componente ao projeto.</span><span class="sxs-lookup"><span data-stu-id="83c31-118">Add a new component to the project.</span></span> <span data-ttu-id="83c31-119">Chame `DemoComponent`.</span><span class="sxs-lookup"><span data-stu-id="83c31-119">Call it `DemoComponent`.</span></span>

     <span data-ttu-id="83c31-120">Para obter mais informações, confira [Como: Adicionar novos itens de projeto](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="83c31-120">For more information, see [How to: Add New Project Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span></span>

3. <span data-ttu-id="83c31-121">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="83c31-121">Build the project.</span></span>

4. <span data-ttu-id="83c31-122">No menu **Ferramentas**, clique no item **Opções**.</span><span class="sxs-lookup"><span data-stu-id="83c31-122">From the **Tools** menu, click the **Options** item.</span></span> <span data-ttu-id="83c31-123">Clique em **Geral** no item **Designer de Formulários do Windows** e certifique-se de que a opção **AutoToolboxPopulate** esteja definida como **True**.</span><span class="sxs-lookup"><span data-stu-id="83c31-123">Click **General** under the **Windows Forms Designer** item and ensure that the **AutoToolboxPopulate** option is set to **True**.</span></span>

## <a name="create-an-instance-of-a-custom-component"></a><span data-ttu-id="83c31-124">Criar uma instância de um componente personalizado</span><span class="sxs-lookup"><span data-stu-id="83c31-124">Create an instance of a custom component</span></span>

<span data-ttu-id="83c31-125">A próxima etapa é criar uma instância do componente personalizado no formulário.</span><span class="sxs-lookup"><span data-stu-id="83c31-125">The next step is to create an instance of the custom component on the form.</span></span> <span data-ttu-id="83c31-126">Uma vez que a **Caixa de Ferramentas** automaticamente conta para o novo componente, isso é tão fácil quanto criar qualquer outro componente ou controle.</span><span class="sxs-lookup"><span data-stu-id="83c31-126">Because the **Toolbox** automatically accounts for the new component, this is as easy as creating any other component or control.</span></span>

1. <span data-ttu-id="83c31-127">Abra o formulário do projeto no **Designer de Formulários**.</span><span class="sxs-lookup"><span data-stu-id="83c31-127">Open the project's form in the **Forms Designer**.</span></span>

2. <span data-ttu-id="83c31-128">Na **Caixa de Ferramentas**, clique na nova guia chamada **Componentes de ToolboxExample**.</span><span class="sxs-lookup"><span data-stu-id="83c31-128">In the **Toolbox**, click the new tab called **ToolboxExample Components**.</span></span>

     <span data-ttu-id="83c31-129">Ao clicar na guia, você verá **DemoComponent**.</span><span class="sxs-lookup"><span data-stu-id="83c31-129">Once you click the tab, you will see **DemoComponent**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="83c31-130">Por motivos de desempenho de componentes na área preenchida automaticamente dos **caixa de ferramentas** não exibem bitmaps personalizados e o <xref:System.Drawing.ToolboxBitmapAttribute> não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="83c31-130">For performance reasons, components in the auto-populated area of the **Toolbox** do not display custom bitmaps, and the <xref:System.Drawing.ToolboxBitmapAttribute> is not supported.</span></span> <span data-ttu-id="83c31-131">Para exibir um ícone para um componente personalizado na **Caixa de Ferramentas**, use a caixa de diálogo **Escolher Itens da Caixa de Ferramentas** para carregar seu componente.</span><span class="sxs-lookup"><span data-stu-id="83c31-131">To display an icon for a custom component in the **Toolbox**, use the **Choose Toolbox Items** dialog box to load your component.</span></span>

3. <span data-ttu-id="83c31-132">Arraste o componente para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="83c31-132">Drag your component onto your form.</span></span>

     <span data-ttu-id="83c31-133">Uma instância do componente é criada e adicionada à **Bandeja de Componentes**.</span><span class="sxs-lookup"><span data-stu-id="83c31-133">An instance of the component is created and added to the **Component Tray**.</span></span>

## <a name="unload-and-reload-a-custom-component"></a><span data-ttu-id="83c31-134">Descarregar e recarregar um componente personalizado</span><span class="sxs-lookup"><span data-stu-id="83c31-134">Unload and reload a custom component</span></span>

<span data-ttu-id="83c31-135">A **Caixa de Ferramentas** considera os componentes em cada projeto carregado e, quando um projeto é descarregado, ela remove referências aos componentes do projeto.</span><span class="sxs-lookup"><span data-stu-id="83c31-135">The **Toolbox** takes account of the components in each loaded project, and when a project is unloaded, it removes references to the project's components.</span></span>

1. <span data-ttu-id="83c31-136">Descarregue o projeto da solução.</span><span class="sxs-lookup"><span data-stu-id="83c31-136">Unload the project from the solution.</span></span>

     <span data-ttu-id="83c31-137">Para obter mais informações sobre descarregar projetos, consulte [como: Descarregar e recarregar projetos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="83c31-137">For more information about unloading projects, see [How to: Unload and Reload Projects](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100)).</span></span> <span data-ttu-id="83c31-138">Se você for solicitado a salvar, escolha **Sim**.</span><span class="sxs-lookup"><span data-stu-id="83c31-138">If you are prompted to save, choose **Yes**.</span></span>

2. <span data-ttu-id="83c31-139">Adicione um novo projeto de **Aplicativos do Windows** à solução.</span><span class="sxs-lookup"><span data-stu-id="83c31-139">Add a new **Windows Application** project to the solution.</span></span> <span data-ttu-id="83c31-140">Abra o formulário no **Designer**.</span><span class="sxs-lookup"><span data-stu-id="83c31-140">Open the form in the **Designer**.</span></span>

     <span data-ttu-id="83c31-141">A guia **Componentes de ToolboxExample** do projeto anterior agora está ausente.</span><span class="sxs-lookup"><span data-stu-id="83c31-141">The **ToolboxExample Components** tab from the previous project is now gone.</span></span>

3. <span data-ttu-id="83c31-142">Recarregue o projeto `ToolboxExample`.</span><span class="sxs-lookup"><span data-stu-id="83c31-142">Reload the `ToolboxExample` project.</span></span>

     <span data-ttu-id="83c31-143">A guia **Componentes de ToolboxExample** agora será exibida novamente.</span><span class="sxs-lookup"><span data-stu-id="83c31-143">The **ToolboxExample Components** tab now reappears.</span></span>

## <a name="next-steps"></a><span data-ttu-id="83c31-144">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="83c31-144">Next steps</span></span>

<span data-ttu-id="83c31-145">Este passo a passo demonstra que a **Caixa de Ferramentas** leva em conta componentes do projeto, mas a **Caixa de Ferramentas** também leva em os controles.</span><span class="sxs-lookup"><span data-stu-id="83c31-145">This walkthrough demonstrates that the **Toolbox** takes account of a project's components, but the **Toolbox** is also takes account of controls.</span></span> <span data-ttu-id="83c31-146">Experimente seus próprios controles personalizados adicionando e removendo projetos de controle de sua solução.</span><span class="sxs-lookup"><span data-stu-id="83c31-146">Experiment with your own custom controls by adding and removing control projects from your solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="83c31-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83c31-147">See also</span></span>

- <span data-ttu-id="83c31-148">[Geral, Designer de formulários do Windows, caixa de diálogo Opções](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="83c31-148">[General, Windows Forms Designer, Options Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))</span></span>
- <span data-ttu-id="83c31-149">[Como: Manipular guias da caixa de ferramentas](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="83c31-149">[How to: Manipulate Toolbox Tabs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100))</span></span>
- <span data-ttu-id="83c31-150">[Caixa de diálogo Escolher Itens da Caixa de Ferramentas (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="83c31-150">[Choose Toolbox Items Dialog Box (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span></span>
- [<span data-ttu-id="83c31-151">Colocando controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83c31-151">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
