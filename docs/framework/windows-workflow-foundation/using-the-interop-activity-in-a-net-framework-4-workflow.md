---
title: Usando a atividade de Interoperabilidade em um fluxo de trabalho do .NET Framework 4
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9bb747f0-eb33-4f70-84cd-317382372dcd
caps.latest.revision: "20"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c485a1c2c69169812e69c3bc1ea9969d12467d53
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-interop-activity-in-a-net-framework-4-workflow"></a><span data-ttu-id="e4799-102">Usando a atividade de Interoperabilidade em um fluxo de trabalho do .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="e4799-102">Using the Interop Activity in a .NET Framework 4 Workflow</span></span>
<span data-ttu-id="e4799-103">As atividades criada usando [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] ou [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] pode ser usado em um fluxo de trabalho [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] usando a atividade de <xref:System.Activities.Statements.Interop> .</span><span class="sxs-lookup"><span data-stu-id="e4799-103">Activities created using [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] or [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] can be used in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow by using the <xref:System.Activities.Statements.Interop> activity.</span></span> <span data-ttu-id="e4799-104">Este tópico fornece uma visão geral de usar a atividade de <xref:System.Activities.Statements.Interop> .</span><span class="sxs-lookup"><span data-stu-id="e4799-104">This topic provides an overview of using the <xref:System.Activities.Statements.Interop> activity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4799-105">O <xref:System.Activities.Statements.Interop> não aparecerá na caixa de ferramentas de designer da fluxo de trabalho, a menos que o projeto do fluxo de trabalho tem seu **Framework de destino** configuração definida como **.Net Framework 4** ou posterior.</span><span class="sxs-lookup"><span data-stu-id="e4799-105">The <xref:System.Activities.Statements.Interop> activity does not appear in the workflow designer toolbox unless the workflow's project has its **Target Framework** setting set to **.Net Framework 4** or later.</span></span>  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a><span data-ttu-id="e4799-106">Usando a atividade de Interoperabilidade em fluxos de trabalho do .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="e4799-106">Using the Interop Activity in .NET Framework 4.5 Workflows</span></span>  
 <span data-ttu-id="e4799-107">Neste tópico, uma biblioteca de atividade de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] é criada que contém uma atividade de `DiscountCalculator` .</span><span class="sxs-lookup"><span data-stu-id="e4799-107">In this topic, a [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity library is created that contains a `DiscountCalculator` activity.</span></span> <span data-ttu-id="e4799-108">`DiscountCalculator` calcula desconto com base em uma quantidade de compra e consiste em <xref:System.Workflow.Activities.SequenceActivity> que contém <xref:System.Workflow.Activities.PolicyActivity>.</span><span class="sxs-lookup"><span data-stu-id="e4799-108">The `DiscountCalculator` calculates a discount based on a purchase amount and consists of a <xref:System.Workflow.Activities.SequenceActivity> that contains a <xref:System.Workflow.Activities.PolicyActivity>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4799-109">A atividade de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] criada neste tópico usa <xref:System.Workflow.Activities.PolicyActivity> para implementar a lógica de atividade.</span><span class="sxs-lookup"><span data-stu-id="e4799-109">The [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity created in this topic uses a <xref:System.Workflow.Activities.PolicyActivity> to implement the logic of the activity.</span></span> <span data-ttu-id="e4799-110">Não é necessário para usar uma atividade personalizado de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] ou a atividade de <xref:System.Activities.Statements.Interop> para usar regras em um fluxo de trabalho [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e4799-110">It is not required to use a custom [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity or the <xref:System.Activities.Statements.Interop> activity in order to use rules in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow.</span></span> <span data-ttu-id="e4799-111">Para obter um exemplo do uso de regras em um [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] fluxo de trabalho sem usar o <xref:System.Activities.Statements.Interop> atividade, consulte o [atividade de política no .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="e4799-111">For an example of using rules in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow without using the <xref:System.Activities.Statements.Interop> activity, see the [Policy Activity in .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) sample.</span></span>  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a><span data-ttu-id="e4799-112">Para criar o projeto de biblioteca de atividade do .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="e4799-112">To create the .NET Framework 3.5 activity library project</span></span>  
  
1.  <span data-ttu-id="e4799-113">Abra [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] e selecione **novo** e **projeto...**</span><span class="sxs-lookup"><span data-stu-id="e4799-113">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and select **New** and then **Project…**</span></span> <span data-ttu-id="e4799-114">do **arquivo** menu.</span><span class="sxs-lookup"><span data-stu-id="e4799-114">from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="e4799-115">Expanda o **outros tipos de projetos** nó o **modelos instalados** painel e selecione **soluções do Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="e4799-115">Expand the **Other Project Types** node in the **Installed Templates** pane and select **Visual Studio Solutions**.</span></span>  
  
3.  <span data-ttu-id="e4799-116">Selecione **solução em branco** do **soluções do Visual Studio** lista.</span><span class="sxs-lookup"><span data-stu-id="e4799-116">Select **Blank Solution** from the **Visual Studio Solutions** list.</span></span> <span data-ttu-id="e4799-117">Tipo `PolicyInteropDemo` no **nome** caixa e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="e4799-117">Type `PolicyInteropDemo` in the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="e4799-118">Clique com botão direito **PolicyInteropDemo** na **Solution Explorer** e selecione **adicionar** e, em seguida, **novo projeto...** .</span><span class="sxs-lookup"><span data-stu-id="e4799-118">Right-click **PolicyInteropDemo** in **Solution Explorer** and select **Add** and then **New Project…**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="e4799-119">Se o **Solution Explorer** janela não estiver visível, selecione **Solution Explorer** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="e4799-119">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="e4799-120">No **modelos instalados** lista, selecione **Visual C#** e **fluxo de trabalho**.</span><span class="sxs-lookup"><span data-stu-id="e4799-120">In the **Installed Templates** list, select **Visual C#** and then **Workflow**.</span></span> <span data-ttu-id="e4799-121">Selecione **.NET Framework 3.5** na lista de lista suspensa de versão do .NET Framework e, em seguida, selecione **biblioteca de atividades de fluxo de trabalho** do **modelos** lista.</span><span class="sxs-lookup"><span data-stu-id="e4799-121">Select **.NET Framework 3.5** from the .NET Framework version drop-down list, and then select **Workflow Activity Library** from the **Templates** list.</span></span>  
  
6.  <span data-ttu-id="e4799-122">Tipo `PolicyActivityLibrary` no **nome** caixa e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="e4799-122">Type `PolicyActivityLibrary` in the **Name** box and click **OK**.</span></span>  
  
7.  <span data-ttu-id="e4799-123">Clique com botão direito **Activity1.cs** na **Solution Explorer** e selecione **excluir**.</span><span class="sxs-lookup"><span data-stu-id="e4799-123">Right-click **Activity1.cs** in **Solution Explorer** and select **Delete**.</span></span> <span data-ttu-id="e4799-124">Clique em **Okey** para confirmar.</span><span class="sxs-lookup"><span data-stu-id="e4799-124">Click **OK** to confirm.</span></span>  
  
#### <a name="to-create-the-discountcalculator-activity"></a><span data-ttu-id="e4799-125">Para criar a atividade de DiscountCalculator</span><span class="sxs-lookup"><span data-stu-id="e4799-125">To create the DiscountCalculator activity</span></span>  
  
1.  <span data-ttu-id="e4799-126">Clique com botão direito **PolicyActivityLibrary** na **Solution Explorer** e selecione **adicionar** e, em seguida, **atividade...** .</span><span class="sxs-lookup"><span data-stu-id="e4799-126">Right-click **PolicyActivityLibrary** in **Solution Explorer** and select **Add** and then **Activity…**.</span></span>  
  
2.  <span data-ttu-id="e4799-127">Selecione **atividade (com separação de código)** do **itens do Visual C#** lista.</span><span class="sxs-lookup"><span data-stu-id="e4799-127">Select **Activity (with code separation)** from the **Visual C# Items** list.</span></span> <span data-ttu-id="e4799-128">Tipo `DiscountCalculator` no **nome** caixa e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="e4799-128">Type `DiscountCalculator` in the **Name** box and click **OK**.</span></span>  
  
3.  <span data-ttu-id="e4799-129">Clique com botão direito **DiscountCalculator.xoml** na **Solution Explorer** e selecione **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="e4799-129">Right-click **DiscountCalculator.xoml** in **Solution Explorer** and select **View Code**.</span></span>  
  
4.  <span data-ttu-id="e4799-130">Adicione as seguintes três propriedades para a classe de `DiscountCalculator` .</span><span class="sxs-lookup"><span data-stu-id="e4799-130">Add the following three properties to the `DiscountCalculator` class.</span></span>  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  <span data-ttu-id="e4799-131">Clique com botão direito **DiscountCalculator.xoml** na **Solution Explorer** e selecione **Designer de exibição**.</span><span class="sxs-lookup"><span data-stu-id="e4799-131">Right-click **DiscountCalculator.xoml** in **Solution Explorer** and select **View Designer**.</span></span>  
  
6.  <span data-ttu-id="e4799-132">Arraste um **política** atividade do **v 3.0 do fluxo de trabalho do Windows** seção o **caixa de ferramentas** e solte-o no **DiscountCalculator** atividade .</span><span class="sxs-lookup"><span data-stu-id="e4799-132">Drag a **Policy** activity from the **Windows Workflow v3.0** section of the **Toolbox** and drop it in the **DiscountCalculator** activity.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="e4799-133">Se o **caixa de ferramentas** janela não estiver visível, selecione **caixa de ferramentas** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="e4799-133">If the **Toolbox** window is not visible, select **Toolbox** from the **View** menu.</span></span>  
  
#### <a name="to-configure-the-rules"></a><span data-ttu-id="e4799-134">Para configurar as regras</span><span class="sxs-lookup"><span data-stu-id="e4799-134">To configure the rules</span></span>  
  
1.  <span data-ttu-id="e4799-135">Clique em recém-adicionado **política** atividade para selecioná-la, se não ainda estiver selecionada.</span><span class="sxs-lookup"><span data-stu-id="e4799-135">Click the newly added **Policy** activity to select it, if it is not already selected.</span></span>  
  
2.  <span data-ttu-id="e4799-136">Clique o **RuleSetReference** propriedade o **propriedades** janela para selecioná-la e clique no botão de reticências à direita da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e4799-136">Click the **RuleSetReference** property in the **Properties** window to select it, and click the ellipsis button to the right of the property.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="e4799-137">Se o **propriedades** janela não estiver visível, escolha **janela propriedades** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="e4799-137">If the **Properties** window is not visible, choose **Properties Window** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="e4799-138">Selecione **clique em novo...** .</span><span class="sxs-lookup"><span data-stu-id="e4799-138">Select **Click New…**.</span></span>  
  
4.  <span data-ttu-id="e4799-139">Clique em **Adicionar regra**.</span><span class="sxs-lookup"><span data-stu-id="e4799-139">Click **Add Rule**.</span></span>  
  
5.  <span data-ttu-id="e4799-140">Digite a seguinte expressão para o **condição** caixa.</span><span class="sxs-lookup"><span data-stu-id="e4799-140">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.Subtotal >= 50 && this.Subtotal < 100  
    ```  
  
6.  <span data-ttu-id="e4799-141">Digite a seguinte expressão para o **ações, em seguida,** caixa.</span><span class="sxs-lookup"><span data-stu-id="e4799-141">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.DiscountPercent = 0.075  
    ```  
  
7.  <span data-ttu-id="e4799-142">Clique em **Adicionar regra**.</span><span class="sxs-lookup"><span data-stu-id="e4799-142">Click **Add Rule**.</span></span>  
  
8.  <span data-ttu-id="e4799-143">Digite a seguinte expressão para o **condição** caixa.</span><span class="sxs-lookup"><span data-stu-id="e4799-143">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.Subtotal >= 100  
    ```  
  
9. <span data-ttu-id="e4799-144">Digite a seguinte expressão para o **ações, em seguida,** caixa.</span><span class="sxs-lookup"><span data-stu-id="e4799-144">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.DiscountPercent = 0.15  
    ```  
  
10. <span data-ttu-id="e4799-145">Clique em **Adicionar regra**.</span><span class="sxs-lookup"><span data-stu-id="e4799-145">Click **Add Rule**.</span></span>  
  
11. <span data-ttu-id="e4799-146">Digite a seguinte expressão para o **condição** caixa.</span><span class="sxs-lookup"><span data-stu-id="e4799-146">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.DiscountPercent > 0  
    ```  
  
12. <span data-ttu-id="e4799-147">Digite a seguinte expressão para o **ações, em seguida,** caixa.</span><span class="sxs-lookup"><span data-stu-id="e4799-147">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent  
    ```  
  
13. <span data-ttu-id="e4799-148">Digite a seguinte expressão para o **ações Else** caixa.</span><span class="sxs-lookup"><span data-stu-id="e4799-148">Type the following expression into the **Else Actions** box.</span></span>  
  
    ```  
    this.Total = this.Subtotal  
    ```  
  
14. <span data-ttu-id="e4799-149">Clique em **Okey** para fechar o **Editor de conjunto de regra** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="e4799-149">Click **OK** to close the **Rule Set Editor** dialog box.</span></span>  
  
15. <span data-ttu-id="e4799-150">Certifique-se de que o recém-criado <xref:System.Workflow.Activities.Rules.RuleSet> está selecionado no **nome** lista e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="e4799-150">Ensure that the newly-created <xref:System.Workflow.Activities.Rules.RuleSet> is selected in the **Name** list, and click **OK**.</span></span>  
  
16. <span data-ttu-id="e4799-151">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="e4799-151">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
 <span data-ttu-id="e4799-152">As regras adicionadas à atividade de `DiscountCalculator` neste procedimento são mostradas no exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="e4799-152">The rules added to the `DiscountCalculator` activity in this procedure are shown in the following code example.</span></span>  
  
```  
Rule1: IF this.Subtotal >= 50 && this.Subtotal < 100   
       THEN this.DiscountPercent = 0.075   
  
Rule2: IF this. Subtotal >= 100   
       THEN this.DiscountPercent = 0.15   
  
Rule3: IF this.DiscountPercent > 0   
       THEN this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent   
       ELSE this.Total = this.Subtotal  
```  
  
 <span data-ttu-id="e4799-153">Quando <xref:System.Workflow.Activities.PolicyActivity> executa, essas três regras valor e alteram `Subtotal`, `DiscountPercent`, e valores de propriedade de `Total` de atividade de `DiscountCalculator` para calcular o desconto desejado.</span><span class="sxs-lookup"><span data-stu-id="e4799-153">When the <xref:System.Workflow.Activities.PolicyActivity> executes, these three rules evaluate and modify the `Subtotal`, `DiscountPercent`, and `Total` property values of the `DiscountCalculator` activity to calculate the desired discount.</span></span>  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a><span data-ttu-id="e4799-154">Usando a atividade de DiscountCalculator com a atividade de Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="e4799-154">Using the DiscountCalculator Activity with the Interop Activity</span></span>  
 <span data-ttu-id="e4799-155">Para usar a atividade de `DiscountCalculator` em um fluxo de trabalho [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] , a atividade de <xref:System.Activities.Statements.Interop> é usada.</span><span class="sxs-lookup"><span data-stu-id="e4799-155">To use the `DiscountCalculator` activity inside a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow, the <xref:System.Activities.Statements.Interop> activity is used.</span></span> <span data-ttu-id="e4799-156">Em fluxos de trabalho desta seção dois são criados, um código e um uso de utilizando o designer de fluxo de trabalho, que mostram como usar a atividade de <xref:System.Activities.Statements.Interop> com a atividade de `DiscountCalculator` .</span><span class="sxs-lookup"><span data-stu-id="e4799-156">In this section two workflows are created, one using code and one using the workflow designer, which show how to use the <xref:System.Activities.Statements.Interop> activity with the `DiscountCalculator` activity.</span></span> <span data-ttu-id="e4799-157">O mesmo aplicativo host é usado para ambos os fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e4799-157">The same host application is used for both workflows.</span></span>  
  
#### <a name="to-create-the-host-application"></a><span data-ttu-id="e4799-158">Para criar o aplicativo host</span><span class="sxs-lookup"><span data-stu-id="e4799-158">To create the host application</span></span>  
  
1.  <span data-ttu-id="e4799-159">Clique com botão direito **PolicyInteropDemo** na **Solution Explorer** e selecione **adicionar**e, em seguida, **novo projeto...** .</span><span class="sxs-lookup"><span data-stu-id="e4799-159">Right-click **PolicyInteropDemo** in **Solution Explorer** and select **Add**, and then **New Project…**.</span></span>  
  
2.  <span data-ttu-id="e4799-160">Certifique-se de que **.NET Framework 4.5** está selecionado na lista suspensa de versão do .NET Framework e selecione **aplicativo de Console do fluxo de trabalho** do **itens do Visual C#** lista.</span><span class="sxs-lookup"><span data-stu-id="e4799-160">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list, and select  **Workflow Console Application** from the **Visual C# Items** list.</span></span>  
  
3.  <span data-ttu-id="e4799-161">Tipo `PolicyInteropHost` para o **nome** caixa e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="e4799-161">Type `PolicyInteropHost` into the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="e4799-162">Clique com botão direito **PolicyInteropHost** na **Solution Explorer** e selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="e4799-162">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="e4799-163">No **framework de destino** suspensa lista, altere a seleção de **.NET Framework 4 Client Profile** para **.NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="e4799-163">In the **Target framework** drop-down list, change the selection from **.NET Framework 4 Client Profile** to **.NET Framework 4.5**.</span></span> <span data-ttu-id="e4799-164">Clique em **Sim** para confirmar.</span><span class="sxs-lookup"><span data-stu-id="e4799-164">Click **Yes** to confirm.</span></span>  
  
6.  <span data-ttu-id="e4799-165">Clique com botão direito **PolicyInteropHost** na **Solution Explorer** e selecione **adicionar referência...** .</span><span class="sxs-lookup"><span data-stu-id="e4799-165">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add Reference…**.</span></span>  
  
7.  <span data-ttu-id="e4799-166">Selecione **PolicyActivityLibrary** do **projetos** guia e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="e4799-166">Select **PolicyActivityLibrary** from the **Projects** tab and click **OK**.</span></span>  
  
8.  <span data-ttu-id="e4799-167">Clique com botão direito **PolicyInteropHost** na **Solution Explorer** e selecione **adicionar referência...** .</span><span class="sxs-lookup"><span data-stu-id="e4799-167">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add Reference…**.</span></span>  
  
9. <span data-ttu-id="e4799-168">Selecione **System.Workflow.Activities**, **System.Workflow.ComponentModel**e, em seguida, **System.Workflow.Runtime** do **.NET**guia e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="e4799-168">Select **System.Workflow.Activities**, **System.Workflow.ComponentModel**, and then **System.Workflow.Runtime** from the **.NET** tab and click **OK**.</span></span>  
  
10. <span data-ttu-id="e4799-169">Clique com botão direito **PolicyInteropHost** na **Solution Explorer** e selecione **definir como projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="e4799-169">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>  
  
11. <span data-ttu-id="e4799-170">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="e4799-170">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
### <a name="using-the-interop-activity-in-code"></a><span data-ttu-id="e4799-171">Usando a atividade de Interoperabilidade no código</span><span class="sxs-lookup"><span data-stu-id="e4799-171">Using the Interop Activity in Code</span></span>  
 <span data-ttu-id="e4799-172">Nesse exemplo, uma definição de fluxo de trabalho é criada usando o código que contém a atividade de <xref:System.Activities.Statements.Interop> e a atividade de `DiscountCalculator` .</span><span class="sxs-lookup"><span data-stu-id="e4799-172">In this example, a workflow definition is created using code that contains the <xref:System.Activities.Statements.Interop> activity and the `DiscountCalculator` activity.</span></span> <span data-ttu-id="e4799-173">Este fluxo de trabalho é chamado usando <xref:System.Activities.WorkflowInvoker> e os resultados de avaliação de regras são gravados no console usando uma atividade de <xref:System.Activities.Statements.WriteLine> .</span><span class="sxs-lookup"><span data-stu-id="e4799-173">This workflow is invoked using <xref:System.Activities.WorkflowInvoker> and the results of the rule evaluation are written to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
##### <a name="to-use-the-interop-activity-in-code"></a><span data-ttu-id="e4799-174">Para usar a atividade de Interoperabilidade no código</span><span class="sxs-lookup"><span data-stu-id="e4799-174">To use the Interop activity in code</span></span>  
  
1.  <span data-ttu-id="e4799-175">Clique com botão direito **Program.cs** na **Solution Explorer** e selecione **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="e4799-175">Right-click **Program.cs** in **Solution Explorer** and select **View Code**.</span></span>  
  
2.  <span data-ttu-id="e4799-176">Adicione a seguinte declaração de `using` na parte superior do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e4799-176">Add the following `using` statement at the top of the file.</span></span>  
  
    ```csharp  
    using PolicyActivityLibrary;  
    ```  
  
3.  <span data-ttu-id="e4799-177">Remova o conteúdo do método de `Main` e substituí-los com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e4799-177">Remove the contents of the `Main` method and replace with the following code.</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
4.  <span data-ttu-id="e4799-178">Crie um novo método na classe de `Program` chamada `CalculateDiscountUsingCodeWorkflow` que contém o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e4799-178">Create a new method in the `Program` class called `CalculateDiscountUsingCodeWorkflow` that contains the following code.</span></span>  
  
    ```csharp  
    static void CalculateDiscountUsingCodeWorkflow()  
    {  
        Variable<double> Subtotal = new Variable<double>  
        {  
            Default = 75.99,  
            Name = "Subtotal"  
        };  
  
        Variable<double> DiscountPercent = new Variable<double>  
        {  
            Name = "DiscountPercent"  
        };  
  
        Variable<double> Total = new Variable<double>  
        {  
            Name = "Total"  
        };  
  
        Activity wf = new Sequence  
        {  
            Variables = { Subtotal, DiscountPercent, Total },  
            Activities =   
            {  
                new Interop  
                {  
                    ActivityType = typeof(DiscountCalculator),  
                    ActivityProperties =   
                    {  
                        { "Subtotal", new InArgument<double>(Subtotal) },  
                        { "DiscountPercentOut", new OutArgument<double>(DiscountPercent) },  
                        { "TotalOut", new OutArgument<double>(Total) }  
                    }  
                },  
                new WriteLine  
                {  
                    Text =  new InArgument<string>(env =>   
                        string.Format("Subtotal: {0:C}, Discount {1}%, Total {2:C}",   
                        Subtotal.Get(env), DiscountPercent.Get(env) * 100, Total.Get(env)))  
                }  
            }  
        };  
  
        WorkflowInvoker.Invoke(wf);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e4799-179">`Subtotal`, `DiscountPercent`, e as propriedades de `Total` de atividade de `DiscountCalculator` são surgidos como argumentos de atividade de <xref:System.Activities.Statements.Interop> , e limite a variáveis locais de fluxo de trabalho na coleção de <xref:System.Activities.Statements.Interop> de atividade de <xref:System.Activities.Statements.Interop.ActivityProperties%2A> .</span><span class="sxs-lookup"><span data-stu-id="e4799-179">The `Subtotal`, `DiscountPercent`, and `Total` properties of the `DiscountCalculator` activity are surfaced as arguments of the <xref:System.Activities.Statements.Interop> activity, and bound to local workflow variables in the <xref:System.Activities.Statements.Interop> activity’s <xref:System.Activities.Statements.Interop.ActivityProperties%2A> collection.</span></span> <span data-ttu-id="e4799-180">`Subtotal` é adicionado como um argumento de <xref:System.Activities.ArgumentDirection.In> porque os fluxos de dados de `Subtotal` na atividade de <xref:System.Activities.Statements.Interop> , e `DiscountPercent` e `Total` são adicionados como argumentos de <xref:System.Activities.ArgumentDirection.Out> porque os fluxos de dados fora de atividade de <xref:System.Activities.Statements.Interop> .</span><span class="sxs-lookup"><span data-stu-id="e4799-180">`Subtotal` is added as an <xref:System.Activities.ArgumentDirection.In> argument because the `Subtotal` data flows into the <xref:System.Activities.Statements.Interop> activity, and `DiscountPercent` and `Total` are added as <xref:System.Activities.ArgumentDirection.Out> arguments because their data flows out of the <xref:System.Activities.Statements.Interop> activity.</span></span> <span data-ttu-id="e4799-181">Observe que os dois argumentos de <xref:System.Activities.ArgumentDirection.Out> são acrescentados com os nomes `DiscountPercentOut` e `TotalOut` para indicar que representam argumentos de <xref:System.Activities.ArgumentDirection.Out> .</span><span class="sxs-lookup"><span data-stu-id="e4799-181">Note that the two <xref:System.Activities.ArgumentDirection.Out> arguments are added with the names `DiscountPercentOut` and `TotalOut` to indicate that they represent <xref:System.Activities.ArgumentDirection.Out> arguments.</span></span> <span data-ttu-id="e4799-182">O tipo de `DiscountCalculator` é especificado como <xref:System.Activities.Statements.Interop>de atividade de <xref:System.Activities.Statements.Interop.ActivityType%2A> .</span><span class="sxs-lookup"><span data-stu-id="e4799-182">The `DiscountCalculator` type is specified as the <xref:System.Activities.Statements.Interop> activity’s <xref:System.Activities.Statements.Interop.ActivityType%2A>.</span></span>  
  
5.  <span data-ttu-id="e4799-183">Pressione CTRL+F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4799-183">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="e4799-184">Substitua valores diferentes para o valor de `Subtotal` para testar para fora os diferentes níveis de desconto fornecidos pela atividade de `DiscountCalculator` .</span><span class="sxs-lookup"><span data-stu-id="e4799-184">Substitute different values for the `Subtotal` value to test out the different discount levels provided by the `DiscountCalculator` activity.</span></span>  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a><span data-ttu-id="e4799-185">Usando a atividade de Interoperabilidade em Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="e4799-185">Using the Interop Activity in the Workflow Designer</span></span>  
 <span data-ttu-id="e4799-186">Nesse exemplo, um trabalho são criados usando o designer de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e4799-186">In this example, a workflow is created using the workflow designer.</span></span> <span data-ttu-id="e4799-187">Este fluxo de trabalho tem a mesma funcionalidade que o exemplo anterior, a não ser que o que em vez de usar uma atividade de <xref:System.Activities.Statements.WriteLine> para exibir o desconto, o aplicativo host recupere e exibe informações de desconto quando o fluxo de trabalho completa.</span><span class="sxs-lookup"><span data-stu-id="e4799-187">This workflow has the same functionality as the previous example, except than instead of using a <xref:System.Activities.Statements.WriteLine> activity to display the discount, the host application retrieves and displays the discount information when the workflow completes.</span></span> <span data-ttu-id="e4799-188">Além disso, em vez de usar variáveis locais de fluxo de trabalho para conter os dados, os argumentos são criados no designer de fluxo de trabalho e os valores são passados host quando o fluxo de trabalho é chamado.</span><span class="sxs-lookup"><span data-stu-id="e4799-188">Also, instead of using local workflow variables to contain the data, arguments are created in the workflow designer and the values are passed in from the host when the workflow is invoked.</span></span>  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a><span data-ttu-id="e4799-189">Para hospedar o PolicyActivity que usa um trabalho Designer- criou trabalho</span><span class="sxs-lookup"><span data-stu-id="e4799-189">To host the PolicyActivity using a Workflow Designer-created workflow</span></span>  
  
1.  <span data-ttu-id="e4799-190">Clique com botão direito **Workflow1.xaml** na **Solution Explorer** e selecione **excluir**.</span><span class="sxs-lookup"><span data-stu-id="e4799-190">Right-click **Workflow1.xaml** in **Solution Explorer** and select **Delete**.</span></span> <span data-ttu-id="e4799-191">Clique em **Okey** para confirmar.</span><span class="sxs-lookup"><span data-stu-id="e4799-191">Click **OK** to confirm.</span></span>  
  
2.  <span data-ttu-id="e4799-192">Clique com botão direito **PolicyInteropHost** na **Solution Explorer** e selecione **adicionar**, **Novo Item...** .</span><span class="sxs-lookup"><span data-stu-id="e4799-192">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add**, **New Item…**.</span></span>  
  
3.  <span data-ttu-id="e4799-193">Expanda o **itens do Visual C#** nó e selecione **fluxo de trabalho**.</span><span class="sxs-lookup"><span data-stu-id="e4799-193">Expand the **Visual C# Items** node and select **Workflow**.</span></span> <span data-ttu-id="e4799-194">Selecione **atividade** do **itens do Visual C#** lista.</span><span class="sxs-lookup"><span data-stu-id="e4799-194">Select **Activity** from the **Visual C# Items** list.</span></span>  
  
4.  <span data-ttu-id="e4799-195">Tipo `DiscountWorkflow` para o **nome** caixa e clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="e4799-195">Type `DiscountWorkflow` into the **Name** box and click **Add**.</span></span>  
  
5.  <span data-ttu-id="e4799-196">Clique o **argumentos** botão no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **argumentos** painel.</span><span class="sxs-lookup"><span data-stu-id="e4799-196">Click the **Arguments** button on the lower left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
6.  <span data-ttu-id="e4799-197">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="e4799-197">Click **Create Argument**.</span></span>  
  
7.  <span data-ttu-id="e4799-198">Tipo `Subtotal` no **nome** caixa, selecione **na** do **direção** lista suspensa, selecione **duplo** da **Tipo de argumento** lista suspensa e, em seguida, pressione ENTER para salvar o argumento.</span><span class="sxs-lookup"><span data-stu-id="e4799-198">Type `Subtotal` into the **Name** box, select **In** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e4799-199">Se **duplo** não está no **tipo de argumento** lista suspensa, selecione **procurar tipos...** , tipo `System.Double` no **nome do tipo** caixa e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="e4799-199">If **Double** is not in the **Argument type** drop-down list, select **Browse for Types …**, type `System.Double` in the **Type Name** box, and click **OK**.</span></span>  
  
8.  <span data-ttu-id="e4799-200">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="e4799-200">Click **Create Argument**.</span></span>  
  
9. <span data-ttu-id="e4799-201">Tipo `DiscountPercent` no **nome** caixa, selecione **Out** do **direção** lista suspensa, selecione **duplo** da **Tipo de argumento** lista suspensa e, em seguida, pressione ENTER para salvar o argumento.</span><span class="sxs-lookup"><span data-stu-id="e4799-201">Type `DiscountPercent` into the **Name** box, select **Out** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
10. <span data-ttu-id="e4799-202">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="e4799-202">Click **Create Argument**.</span></span>  
  
11. <span data-ttu-id="e4799-203">Tipo `Total` no **nome** caixa, selecione **Out** do **direção** lista suspensa, selecione **duplo** da **Tipo de argumento** lista suspensa e, em seguida, pressione ENTER para salvar o argumento.</span><span class="sxs-lookup"><span data-stu-id="e4799-203">Type `Total` into the **Name** box, select **Out** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
12. <span data-ttu-id="e4799-204">Clique o **argumentos** botão no lado inferior esquerdo do designer de fluxo de trabalho para fechar o **argumentos** painel.</span><span class="sxs-lookup"><span data-stu-id="e4799-204">Click the **Arguments** button on the lower left side of the workflow designer to close the **Arguments** pane.</span></span>  
  
13. <span data-ttu-id="e4799-205">Arraste um **sequência** atividade do **fluxo de controle** seção o **caixa de ferramentas** e solte-o para a superfície de designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e4799-205">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the workflow designer surface.</span></span>  
  
14. <span data-ttu-id="e4799-206">Arraste um **Interop** atividade do **migração** seção o **caixa de ferramentas** e solte-o no **sequência** atividade.</span><span class="sxs-lookup"><span data-stu-id="e4799-206">Drag an **Interop** activity from the **Migration** section of the **Toolbox** and drop it in the **Sequence** activity.</span></span>  
  
15. <span data-ttu-id="e4799-207">Clique o **Interop** atividade no **clique para procurar...**</span><span class="sxs-lookup"><span data-stu-id="e4799-207">Click the **Interop** activity on the **Click to browse…**</span></span> <span data-ttu-id="e4799-208">rótulo, digite **DiscountCalculator** no **nome do tipo** caixa e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="e4799-208">label, type **DiscountCalculator** in the **Type Name** box, and click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e4799-209">Quando a atividade de <xref:System.Activities.Statements.Interop> é adicionada ao fluxo de trabalho e o tipo de `DiscountCalculator` é especificado como seu <xref:System.Activities.Statements.Interop.ActivityType%2A>, a atividade de <xref:System.Activities.Statements.Interop> expõe três argumentos de <xref:System.Activities.ArgumentDirection.In> e três argumentos de <xref:System.Activities.ArgumentDirection.Out> que representam as três propriedades públicas de atividade de `DiscountCalculator` .</span><span class="sxs-lookup"><span data-stu-id="e4799-209">When the <xref:System.Activities.Statements.Interop> activity is added to the workflow and the `DiscountCalculator` type is specified as its <xref:System.Activities.Statements.Interop.ActivityType%2A>, the <xref:System.Activities.Statements.Interop> activity exposes three <xref:System.Activities.ArgumentDirection.In> arguments and three <xref:System.Activities.ArgumentDirection.Out> arguments that represent the three public properties of the `DiscountCalculator` activity.</span></span> <span data-ttu-id="e4799-210">O <xref:System.Activities.ArgumentDirection.In> argumentos têm o mesmo nome que as três propriedades públicas e os três <xref:System.Activities.ArgumentDirection.Out> argumentos têm os mesmos nomes com **Out** acrescentado ao nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e4799-210">The <xref:System.Activities.ArgumentDirection.In> arguments have the same name as the three public properties, and the three <xref:System.Activities.ArgumentDirection.Out> arguments have the same names with **Out** appended to the property name.</span></span> <span data-ttu-id="e4799-211">As seguintes etapas, os argumentos de fluxo de trabalho criados nas etapas anteriores são associados aos argumentos de atividade de <xref:System.Activities.Statements.Interop> .</span><span class="sxs-lookup"><span data-stu-id="e4799-211">In the following steps, the workflow arguments created in the previous steps are bound to the <xref:System.Activities.Statements.Interop> activity’s arguments.</span></span>  
  
16. <span data-ttu-id="e4799-212">Tipo `DiscountPercent` para o **insira uma expressão VB** caixa à direita do **DiscountPercentOut** propriedade e pressione TAB.</span><span class="sxs-lookup"><span data-stu-id="e4799-212">Type `DiscountPercent` into the **Enter a VB expression** box to the right of the **DiscountPercentOut** property and press TAB.</span></span>  
  
17. <span data-ttu-id="e4799-213">Tipo `Subtotal` para o **insira uma expressão VB** caixa à direita do **Subtotal** propriedade e pressione TAB.</span><span class="sxs-lookup"><span data-stu-id="e4799-213">Type `Subtotal` into the **Enter a VB expression** box to the right of the **Subtotal** property and press TAB.</span></span>  
  
18. <span data-ttu-id="e4799-214">Tipo `Total` para o **insira uma expressão VB** caixa à direita do **TotalOut** propriedade e pressione TAB.</span><span class="sxs-lookup"><span data-stu-id="e4799-214">Type `Total` into the **Enter a VB expression** box to the right of the **TotalOut** property and press TAB.</span></span>  
  
19. <span data-ttu-id="e4799-215">Clique com botão direito **Program.cs** na **Solution Explorer** e selecione **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="e4799-215">Right-click **Program.cs** in **Solution Explorer** and select **View Code**.</span></span>  
  
20. <span data-ttu-id="e4799-216">Adicione a seguinte declaração de `using` na parte superior do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e4799-216">Add the following `using` statement at the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
21. <span data-ttu-id="e4799-217">Comente a chamada ao método de `CalculateDiscountInCode` no método de `Main` e adicione o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="e4799-217">Comment out the call to the `CalculateDiscountInCode` method in the `Main` method and add the following code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e4799-218">Se você não tiver usado o procedimento anterior e o código de `Main` de opção estiver presente, substitua o conteúdo de `Main` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e4799-218">If you did not follow the previous procedure and the default `Main` code is present, replace the contents of `Main` with the following code.</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingDesignerWorkflow();  
        //CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
22. <span data-ttu-id="e4799-219">Crie um novo método na classe de `Program` chamada `CalculateDiscountUsingDesignerWorkflow` que contém o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e4799-219">Create a new method in the `Program` class called `CalculateDiscountUsingDesignerWorkflow` that contains the following code.</span></span>  
  
    ```csharp  
    static void CalculateDiscountUsingDesignerWorkflow()  
    {  
        double SubtotalValue = 125.99;  
        Dictionary<string, object> wfargs = new Dictionary<string, object>  
        {  
            {"Subtotal", SubtotalValue}  
        };  
  
        Activity wf = new DiscountWorkflow();  
  
        IDictionary<string, object> outputs =  
            WorkflowInvoker.Invoke(wf, wfargs);  
  
        Console.WriteLine("Subtotal: {0:C}, Discount {1}%, Total {2:C}",  
            SubtotalValue, (double)outputs["DiscountPercent"] * 100,  
            outputs["Total"]);  
    }  
    ```  
  
23. <span data-ttu-id="e4799-220">Pressione CTRL+F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4799-220">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="e4799-221">Para especificar um valor diferente de `Subtotal` , altere o valor de `SubtotalValue` no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e4799-221">To specify a different `Subtotal` amount, change the value of `SubtotalValue` in the following code.</span></span>  
  
    ```csharp  
    double SubtotalValue = 125.99; // Change this value.  
    ```  
  
## <a name="rules-features-overview"></a><span data-ttu-id="e4799-222">Visão geral dos recursos de regras</span><span class="sxs-lookup"><span data-stu-id="e4799-222">Rules Features Overview</span></span>  
 <span data-ttu-id="e4799-223">O mecanismo de regras de [!INCLUDE[wf1](../../../includes/wf1-md.md)] fornece suporte para processar regras de uma maneira prioridade- base com suporte para encadear frente.</span><span class="sxs-lookup"><span data-stu-id="e4799-223">The [!INCLUDE[wf1](../../../includes/wf1-md.md)] rules engine provides support for processing rules in a priority-based manner with support for forward chaining.</span></span> <span data-ttu-id="e4799-224">As regras podem ser avaliadas para um único item ou para itens em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="e4799-224">Rules can be evaluated for a single item or for items in a collection.</span></span> <span data-ttu-id="e4799-225">Para uma visão geral das regras e de informações na funcionalidade das regras de específico, por favor consulte a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="e4799-225">For an overview of rules and information on specific rules functionality, please refer to the following table.</span></span>  
  
|<span data-ttu-id="e4799-226">Recurso de regras</span><span class="sxs-lookup"><span data-stu-id="e4799-226">Rules Feature</span></span>|<span data-ttu-id="e4799-227">Documentação</span><span class="sxs-lookup"><span data-stu-id="e4799-227">Documentation</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="e4799-228">Visão geral das regras</span><span class="sxs-lookup"><span data-stu-id="e4799-228">Rules Overview</span></span>|[<span data-ttu-id="e4799-229">Introdução ao mecanismo de regras do Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="e4799-229">Introduction to the Windows Workflow Foundation Rules Engine</span></span>](http://go.microsoft.com/fwlink/?LinkID=152836)|  
|<span data-ttu-id="e4799-230">RuleSet</span><span class="sxs-lookup"><span data-stu-id="e4799-230">RuleSet</span></span>|<span data-ttu-id="e4799-231">[Usando conjuntos de regras em fluxos de trabalho](http://go.microsoft.com/fwlink/?LinkId=178516) e<xref:System.Workflow.Activities.Rules.RuleSet></span><span class="sxs-lookup"><span data-stu-id="e4799-231">[Using RuleSets in Workflows](http://go.microsoft.com/fwlink/?LinkId=178516) and <xref:System.Workflow.Activities.Rules.RuleSet></span></span>|  
|<span data-ttu-id="e4799-232">Avaliação das regras</span><span class="sxs-lookup"><span data-stu-id="e4799-232">Evaluation of Rules</span></span>|[<span data-ttu-id="e4799-233">Avaliação de regras no conjunto de regras</span><span class="sxs-lookup"><span data-stu-id="e4799-233">Rules Evaluation in RuleSets</span></span>](http://go.microsoft.com/fwlink/?LinkId=178517)|  
|<span data-ttu-id="e4799-234">Encadeamento das regras</span><span class="sxs-lookup"><span data-stu-id="e4799-234">Rules Chaining</span></span>|<span data-ttu-id="e4799-235">[Controle o encadeamento de encaminhamento](http://go.microsoft.com/fwlink/?LinkId=178518) e [encadeamento de regras de encaminhamento](http://go.microsoft.com/fwlink/?LinkId=178519)</span><span class="sxs-lookup"><span data-stu-id="e4799-235">[Forward Chaining Control](http://go.microsoft.com/fwlink/?LinkId=178518) and [Forward Chaining of Rules](http://go.microsoft.com/fwlink/?LinkId=178519)</span></span>|  
|<span data-ttu-id="e4799-236">Coleções de processamento nas regras</span><span class="sxs-lookup"><span data-stu-id="e4799-236">Processing Collections in Rules</span></span>|[<span data-ttu-id="e4799-237">Coleções de regras de processamento</span><span class="sxs-lookup"><span data-stu-id="e4799-237">Processing Collections in Rules</span></span>](http://go.microsoft.com/fwlink/?LinkId=178520)|  
|<span data-ttu-id="e4799-238">Usando o PolicyActivity</span><span class="sxs-lookup"><span data-stu-id="e4799-238">Using the PolicyActivity</span></span>|<span data-ttu-id="e4799-239">[Usando a atividade de PolicyActivity](http://go.microsoft.com/fwlink/?LinkId=178521) e<xref:System.Workflow.Activities.PolicyActivity></span><span class="sxs-lookup"><span data-stu-id="e4799-239">[Using the PolicyActivity Activity](http://go.microsoft.com/fwlink/?LinkId=178521) and <xref:System.Workflow.Activities.PolicyActivity></span></span>|  
  
 <span data-ttu-id="e4799-240">Fluxos de trabalho criados em [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] não usam todos os recursos de regras fornecidos por [!INCLUDE[wf1](../../../includes/wf1-md.md)], como condições declarativas de atividade e atividades condicionais como <xref:System.Workflow.Activities.ConditionedActivityGroup> e <xref:System.Workflow.Activities.ReplicatorActivity>.</span><span class="sxs-lookup"><span data-stu-id="e4799-240">Workflows created in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] do not use all of the rules features provided by [!INCLUDE[wf1](../../../includes/wf1-md.md)], such as declarative activity conditions and conditional activities such as the <xref:System.Workflow.Activities.ConditionedActivityGroup> and <xref:System.Workflow.Activities.ReplicatorActivity>.</span></span> <span data-ttu-id="e4799-241">Se necessário, essa funcionalidade está disponível para os fluxos de trabalho criados usando [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] e [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e4799-241">If required, this functionality is available for workflows created using [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="e4799-242">[Orientação de migração](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).</span><span class="sxs-lookup"><span data-stu-id="e4799-242"> [Migration Guidance](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).</span></span>
