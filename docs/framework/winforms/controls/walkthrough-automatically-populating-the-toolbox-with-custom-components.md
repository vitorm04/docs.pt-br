---
title: "Instruções passo a passo: preenchendo de forma automática a caixa de ferramentas com componentes personalizados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b60d4ee7908a5ed9dcb3393132ba7d0bd0a6cb5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a><span data-ttu-id="14a24-102">Instruções passo a passo: preenchendo de forma automática a caixa de ferramentas com componentes personalizados</span><span class="sxs-lookup"><span data-stu-id="14a24-102">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>
<span data-ttu-id="14a24-103">Se seus componentes forem definidos por um projeto na solução aberta no momento, eles aparecerão automaticamente na **Caixa de Ferramentas** sem exigir que você execute nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="14a24-103">If your components are defined by a project in the currently open solution, they will automatically appear in the **Toolbox**, with no action required by you.</span></span> <span data-ttu-id="14a24-104">Você também pode preencher manualmente a **Caixa de Ferramentas** com seus componentes personalizados usando a [Caixa de Diálogo Escolher Itens da Caixa de Ferramentas (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), mas a **Caixa de Ferramentas** leva em conta itens nas saídas de build da sua solução com todas as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="14a24-104">You can also manually populate the **Toolbox** with your custom components by using the [Choose Toolbox Items Dialog Box (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), but the **Toolbox** takes account of items in your solution's build outputs with all the following characteristics:</span></span>  
  
-   <span data-ttu-id="14a24-105">Implementa <xref:System.ComponentModel.IComponent>;</span><span class="sxs-lookup"><span data-stu-id="14a24-105">Implements <xref:System.ComponentModel.IComponent>;</span></span>  
  
-   <span data-ttu-id="14a24-106">Não tem <xref:System.ComponentModel.ToolboxItemAttribute> definida como `false`;</span><span class="sxs-lookup"><span data-stu-id="14a24-106">Does not have <xref:System.ComponentModel.ToolboxItemAttribute> set to `false`;</span></span>  
  
-   <span data-ttu-id="14a24-107">Não tem <xref:System.ComponentModel.DesignTimeVisibleAttribute> definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="14a24-107">Does not have <xref:System.ComponentModel.DesignTimeVisibleAttribute> set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14a24-108">A **Caixa de Ferramentas** não segue cadeias de referência, portanto, não exibirá itens que não sejam criados por um projeto em sua solução.</span><span class="sxs-lookup"><span data-stu-id="14a24-108">The **Toolbox** does not follow reference chains, so it will not display items that are not built by a project in your solution.</span></span>  
  
 <span data-ttu-id="14a24-109">Este passo a passo demonstra como um componente personalizado aparece automaticamente na **Caixa de Ferramentas** depois que o componente é criado.</span><span class="sxs-lookup"><span data-stu-id="14a24-109">This walkthrough demonstrates how a custom component automatically appears in the **Toolbox** once the component is built.</span></span> <span data-ttu-id="14a24-110">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="14a24-110">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="14a24-111">Criando um projeto dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="14a24-111">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="14a24-112">Criando um componente personalizado.</span><span class="sxs-lookup"><span data-stu-id="14a24-112">Creating a custom component.</span></span>  
  
-   <span data-ttu-id="14a24-113">Criando uma instância de um componente personalizado.</span><span class="sxs-lookup"><span data-stu-id="14a24-113">Creating an instance of a custom component.</span></span>  
  
-   <span data-ttu-id="14a24-114">Descarregando e recarregando um componente personalizado.</span><span class="sxs-lookup"><span data-stu-id="14a24-114">Unloading and reloading a custom component.</span></span>  
  
 <span data-ttu-id="14a24-115">Quando tiver terminado, verá que a **Caixa de Ferramentas** é preenchida com um componente que você criou.</span><span class="sxs-lookup"><span data-stu-id="14a24-115">When you are finished, you will see that the **Toolbox** is populated with a component that you have created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14a24-116">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="14a24-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="14a24-117">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="14a24-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="14a24-118">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="14a24-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="14a24-119">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="14a24-119">Creating the Project</span></span>  
 <span data-ttu-id="14a24-120">A primeira etapa é criar o projeto e configurar o formulário.</span><span class="sxs-lookup"><span data-stu-id="14a24-120">The first step is to create the project and to set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="14a24-121">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="14a24-121">To create the project</span></span>  
  
1.  <span data-ttu-id="14a24-122">Crie um projeto de aplicativos do baseado em Windows chamado `ToolboxExample`.</span><span class="sxs-lookup"><span data-stu-id="14a24-122">Create a Windows-based application project called `ToolboxExample`.</span></span>  
  
     <span data-ttu-id="14a24-123">Para obter mais informações, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="14a24-123">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="14a24-124">Adicione um novo componente ao projeto.</span><span class="sxs-lookup"><span data-stu-id="14a24-124">Add a new component to the project.</span></span> <span data-ttu-id="14a24-125">Chame `DemoComponent`.</span><span class="sxs-lookup"><span data-stu-id="14a24-125">Call it `DemoComponent`.</span></span>  
  
     <span data-ttu-id="14a24-126">Para obter mais informações, consulte [NIB: como adicionar novos itens do projeto](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span><span class="sxs-lookup"><span data-stu-id="14a24-126">For more information, see [NIB:How to: Add New Project Items](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span>  
  
3.  <span data-ttu-id="14a24-127">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="14a24-127">Build the project.</span></span>  
  
4.  <span data-ttu-id="14a24-128">No menu **Ferramentas**, clique no item **Opções**.</span><span class="sxs-lookup"><span data-stu-id="14a24-128">From the **Tools** menu, click the **Options** item.</span></span> <span data-ttu-id="14a24-129">Clique em **Geral** no item **Designer de Formulários do Windows** e certifique-se de que a opção **AutoToolboxPopulate** esteja definida como **True**.</span><span class="sxs-lookup"><span data-stu-id="14a24-129">Click **General** under the **Windows Forms Designer** item and ensure that the **AutoToolboxPopulate** option is set to **True**.</span></span>  
  
## <a name="creating-an-instance-of-a-custom-component"></a><span data-ttu-id="14a24-130">Criando uma instância de um componente personalizado</span><span class="sxs-lookup"><span data-stu-id="14a24-130">Creating an Instance of a Custom Component</span></span>  
 <span data-ttu-id="14a24-131">A próxima etapa é criar uma instância do componente personalizado no formulário.</span><span class="sxs-lookup"><span data-stu-id="14a24-131">The next step is to create an instance of the custom component on the form.</span></span> <span data-ttu-id="14a24-132">Uma vez que a **Caixa de Ferramentas** automaticamente conta para o novo componente, isso é tão fácil quanto criar qualquer outro componente ou controle.</span><span class="sxs-lookup"><span data-stu-id="14a24-132">Because the **Toolbox** automatically accounts for the new component, this is as easy as creating any other component or control.</span></span>  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a><span data-ttu-id="14a24-133">Para criar uma instância de um componente personalizado</span><span class="sxs-lookup"><span data-stu-id="14a24-133">To create an instance of a custom component</span></span>  
  
1.  <span data-ttu-id="14a24-134">Abra o formulário do projeto no **Designer de Formulários**.</span><span class="sxs-lookup"><span data-stu-id="14a24-134">Open the project's form in the **Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="14a24-135">Na **Caixa de Ferramentas**, clique na nova guia chamada **Componentes de ToolboxExample**.</span><span class="sxs-lookup"><span data-stu-id="14a24-135">In the **Toolbox**, click the new tab called **ToolboxExample Components**.</span></span>  
  
     <span data-ttu-id="14a24-136">Ao clicar na guia, você verá **DemoComponent**.</span><span class="sxs-lookup"><span data-stu-id="14a24-136">Once you click the tab, you will see **DemoComponent**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="14a24-137">Por motivos de desempenho, componentes na área preenchida automaticamente do **caixa de ferramentas** não exibir bitmaps personalizados e o <xref:System.Drawing.ToolboxBitmapAttribute> não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="14a24-137">For performance reasons, components in the auto-populated area of the **Toolbox** do not display custom bitmaps, and the <xref:System.Drawing.ToolboxBitmapAttribute> is not supported.</span></span> <span data-ttu-id="14a24-138">Para exibir um ícone para um componente personalizado na **Caixa de Ferramentas**, use a caixa de diálogo **Escolher Itens da Caixa de Ferramentas** para carregar seu componente.</span><span class="sxs-lookup"><span data-stu-id="14a24-138">To display an icon for a custom component in the **Toolbox**, use the **Choose Toolbox Items** dialog box to load your component.</span></span>  
  
3.  <span data-ttu-id="14a24-139">Arraste o componente para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="14a24-139">Drag your component onto your form.</span></span>  
  
     <span data-ttu-id="14a24-140">Uma instância do componente é criada e adicionada à **Bandeja de Componentes**.</span><span class="sxs-lookup"><span data-stu-id="14a24-140">An instance of the component is created and added to the **Component Tray**.</span></span>  
  
## <a name="unloading-and-reloading-a-custom-component"></a><span data-ttu-id="14a24-141">Descarregando e recarregando um componente personalizado</span><span class="sxs-lookup"><span data-stu-id="14a24-141">Unloading and Reloading a Custom Component</span></span>  
 <span data-ttu-id="14a24-142">A **Caixa de Ferramentas** considera os componentes em cada projeto carregado e, quando um projeto é descarregado, ela remove referências aos componentes do projeto.</span><span class="sxs-lookup"><span data-stu-id="14a24-142">The **Toolbox** takes account of the components in each loaded project, and when a project is unloaded, it removes references to the project's components.</span></span>  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a><span data-ttu-id="14a24-143">Para experimentar o efeito que descarregar e recarregar componentes tem sobre a Caixa de Ferramentas</span><span class="sxs-lookup"><span data-stu-id="14a24-143">To experiment with the effect on the Toolbox of unloading and reloading components</span></span>  
  
1.  <span data-ttu-id="14a24-144">Descarregue o projeto da solução.</span><span class="sxs-lookup"><span data-stu-id="14a24-144">Unload the project from the solution.</span></span>  
  
     <span data-ttu-id="14a24-145">Para obter mais informações sobre descarregar projetos, consulte [NIB: Como descarregar e recarregar projetos](http://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b).</span><span class="sxs-lookup"><span data-stu-id="14a24-145">For more information about unloading projects, see [NIB:How to: Unload and Reload Projects](http://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b).</span></span> <span data-ttu-id="14a24-146">Se você for solicitado a salvar, escolha **Sim**.</span><span class="sxs-lookup"><span data-stu-id="14a24-146">If you are prompted to save, choose **Yes**.</span></span>  
  
2.  <span data-ttu-id="14a24-147">Adicione um novo projeto de **Aplicativos do Windows** à solução.</span><span class="sxs-lookup"><span data-stu-id="14a24-147">Add a new **Windows Application** project to the solution.</span></span> <span data-ttu-id="14a24-148">Abra o formulário no **Designer**.</span><span class="sxs-lookup"><span data-stu-id="14a24-148">Open the form in the **Designer**.</span></span>  
  
     <span data-ttu-id="14a24-149">A guia **Componentes de ToolboxExample** do projeto anterior agora está ausente.</span><span class="sxs-lookup"><span data-stu-id="14a24-149">The **ToolboxExample Components** tab from the previous project is now gone.</span></span>  
  
3.  <span data-ttu-id="14a24-150">Recarregue o projeto `ToolboxExample`.</span><span class="sxs-lookup"><span data-stu-id="14a24-150">Reload the `ToolboxExample` project.</span></span>  
  
     <span data-ttu-id="14a24-151">A guia **Componentes de ToolboxExample** agora será exibida novamente.</span><span class="sxs-lookup"><span data-stu-id="14a24-151">The **ToolboxExample Components** tab now reappears.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="14a24-152">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="14a24-152">Next Steps</span></span>  
 <span data-ttu-id="14a24-153">Este passo a passo demonstra que a **Caixa de Ferramentas** leva em conta componentes do projeto, mas a **Caixa de Ferramentas** também leva em os controles.</span><span class="sxs-lookup"><span data-stu-id="14a24-153">This walkthrough demonstrates that the **Toolbox** takes account of a project's components, but the **Toolbox** is also takes account of controls.</span></span> <span data-ttu-id="14a24-154">Experimente seus próprios controles personalizados adicionando e removendo projetos de controle de sua solução.</span><span class="sxs-lookup"><span data-stu-id="14a24-154">Experiment with your own custom controls by adding and removing control projects from your solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14a24-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14a24-155">See Also</span></span>  
 [<span data-ttu-id="14a24-156">Geral, Designer de formulários do Windows, a caixa de diálogo Opções</span><span class="sxs-lookup"><span data-stu-id="14a24-156">General, Windows Forms Designer, Options Dialog Box</span></span>](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)  
 [<span data-ttu-id="14a24-157">Como manipular guias da caixa de ferramentas</span><span class="sxs-lookup"><span data-stu-id="14a24-157">How to: Manipulate Toolbox Tabs</span></span>](http://msdn.microsoft.com/library/21285050-cadd-455a-b1f5-a2289a89c4db)  
 [<span data-ttu-id="14a24-158">Caixa de diálogo Escolher Itens da Caixa de Ferramentas (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="14a24-158">Choose Toolbox Items Dialog Box (Visual Studio)</span></span>](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [<span data-ttu-id="14a24-159">Colocando controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="14a24-159">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)
