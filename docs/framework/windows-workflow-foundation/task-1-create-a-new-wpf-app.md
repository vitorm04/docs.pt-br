---
title: 'Tarefa 1: Crie um aplicativo do windows presentation foundation do windows'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a207b09ff7124bb161678627f365a6fa4021a38d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="5d733-102">Tarefa 1: Crie um aplicativo do windows presentation foundation do windows</span><span class="sxs-lookup"><span data-stu-id="5d733-102">Task 1: Create a New Windows Presentation Foundation Application</span></span>
<span data-ttu-id="5d733-103">Nesta tarefa, você criará um aplicativo vazia de [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] usando o modelo do Visual Studio de aplicativo WPF e adicionar referências a assemblies apropriadas de fluxo de trabalho de [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5d733-103">In this task, you will create an empty [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
### <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="5d733-104">Para criar o projeto de aplicativo de WPF</span><span class="sxs-lookup"><span data-stu-id="5d733-104">To create the WPF Application project</span></span>  
  
1.  <span data-ttu-id="5d733-105">Abra [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] e na **arquivo** , aponte para **novo**e, em seguida, clique em **projeto**.</span><span class="sxs-lookup"><span data-stu-id="5d733-105">Open [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] and on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="5d733-106">No **novo projeto** caixa de diálogo, selecione o **Visual C#** ou **Visual Basic** do **modelos instalados** painel no lado esquerdo do a caixa.</span><span class="sxs-lookup"><span data-stu-id="5d733-106">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="5d733-107">Se o idioma de sua escolha não aparecer, procure em **outras linguagens**.</span><span class="sxs-lookup"><span data-stu-id="5d733-107">If the language of your choice does not appear, look under **Other Languages**.</span></span>  
  
3.  <span data-ttu-id="5d733-108">Selecione **Windows** no **modelos instalados** painel.</span><span class="sxs-lookup"><span data-stu-id="5d733-108">Select **Windows** in the **Installed Templates** pane.</span></span>  
  
4.  <span data-ttu-id="5d733-109">No painel superior, confirme se (o valor padrão) **.NET Framework 4** tiver sido selecionado na caixa de listagem suspensa e, em seguida, selecione **aplicativo WPF**.</span><span class="sxs-lookup"><span data-stu-id="5d733-109">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="5d733-110">Defina o nome do projeto para **HostingApplication** na parte inferior da janela.</span><span class="sxs-lookup"><span data-stu-id="5d733-110">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>  
  
6.  <span data-ttu-id="5d733-111">Defina o nome de solução para **RehostingTheDesigner**.</span><span class="sxs-lookup"><span data-stu-id="5d733-111">Set the solution name to **RehostingTheDesigner**.</span></span>  
  
7.  <span data-ttu-id="5d733-112">Clique em **Okey** para criar o projeto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5d733-112">Click **OK** to create the application project.</span></span> [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]<span data-ttu-id="5d733-113"> cria WPF básico interface do usuário para seu aplicativo e inclui o XAML apropriado e arquivos code-behind.</span><span class="sxs-lookup"><span data-stu-id="5d733-113"> creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>  
  
8.  <span data-ttu-id="5d733-114">Adicione referências a **WorkflowModel** assemblies.</span><span class="sxs-lookup"><span data-stu-id="5d733-114">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="5d733-115">Para fazer isso, em **Solution Explorer**, com o botão direito do **HostingApplication** do projeto e selecione **adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="5d733-115">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>  
  
9. <span data-ttu-id="5d733-116">No **adicionar referência** caixa de diálogo, clique o **.NET** guia, mantenha pressionada a tecla CTRL, selecione os seguintes assemblies e, em seguida, clique em **Okey**:</span><span class="sxs-lookup"><span data-stu-id="5d733-116">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>  
  
    -   <span data-ttu-id="5d733-117">System.Activities</span><span class="sxs-lookup"><span data-stu-id="5d733-117">System.Activities</span></span>  
  
    -   <span data-ttu-id="5d733-118">System.Activities.Presentation</span><span class="sxs-lookup"><span data-stu-id="5d733-118">System.Activities.Presentation</span></span>  
  
    -   <span data-ttu-id="5d733-119">System.Activities.Core.Presentation</span><span class="sxs-lookup"><span data-stu-id="5d733-119">System.Activities.Core.Presentation</span></span>  
  
10. <span data-ttu-id="5d733-120">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="5d733-120">Click **OK**.</span></span>  
  
11. <span data-ttu-id="5d733-121">Consulte [tarefa 2: hospedar Designer de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) para aprender a hospedar a tela de design do designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="5d733-121">See [Task 2: Host the Workflow Designer](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d733-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d733-122">See Also</span></span>  
 [<span data-ttu-id="5d733-123">Hospedando novamente o Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="5d733-123">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="5d733-124">Tarefa 2: Hospedar o Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="5d733-124">Task 2: Host the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
