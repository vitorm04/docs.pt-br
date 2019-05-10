---
title: 'Tarefa 1: Criar um aplicativo do Windows Presentation Foundation do Windows'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 44152f0af73b134218cd975d93e186166b1e57ae
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665315"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="2753e-102">Tarefa 1: Criar um aplicativo do Windows Presentation Foundation do Windows</span><span class="sxs-lookup"><span data-stu-id="2753e-102">Task 1: Create a New Windows Presentation Foundation Application</span></span>
<span data-ttu-id="2753e-103">Nesta tarefa, você criará um aplicativo vazio do Windows Presentation Foundation (WPF) usando o modelo de aplicativo WPF Visual Studio e adicionar referências a apropriado [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] assemblies de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2753e-103">In this task, you will create an empty Windows Presentation Foundation (WPF) application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
### <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="2753e-104">Para criar o projeto de aplicativo de WPF</span><span class="sxs-lookup"><span data-stu-id="2753e-104">To create the WPF Application project</span></span>  
  
1. <span data-ttu-id="2753e-105">Abra o Visual Studio e, na **arquivo** , aponte para **New**e, em seguida, clique em **projeto**.</span><span class="sxs-lookup"><span data-stu-id="2753e-105">Open Visual Studio and on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="2753e-106">No **novo projeto** diálogo caixa, selecione **Visual C#**  ou **Visual Basic** do **modelos instalados** painel à esquerda lado da caixa.</span><span class="sxs-lookup"><span data-stu-id="2753e-106">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="2753e-107">Se o idioma de sua escolha não aparecer, procure **outras linguagens**.</span><span class="sxs-lookup"><span data-stu-id="2753e-107">If the language of your choice does not appear, look under **Other Languages**.</span></span>  
  
3. <span data-ttu-id="2753e-108">Selecione **Windows** na **modelos instalados** painel.</span><span class="sxs-lookup"><span data-stu-id="2753e-108">Select **Windows** in the **Installed Templates** pane.</span></span>  
  
4. <span data-ttu-id="2753e-109">No painel superior, confirme se (o valor padrão) **.NET Framework 4** tiver sido selecionado na caixa de listagem suspensa e, em seguida, selecione **aplicativo WPF**.</span><span class="sxs-lookup"><span data-stu-id="2753e-109">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>  
  
5. <span data-ttu-id="2753e-110">Defina o nome do projeto para **HostingApplication** na parte inferior da janela.</span><span class="sxs-lookup"><span data-stu-id="2753e-110">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>  
  
6. <span data-ttu-id="2753e-111">Defina o nome da solução **RehostingTheDesigner**.</span><span class="sxs-lookup"><span data-stu-id="2753e-111">Set the solution name to **RehostingTheDesigner**.</span></span>  
  
7. <span data-ttu-id="2753e-112">Clique em **Okey** para criar o projeto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2753e-112">Click **OK** to create the application project.</span></span> <span data-ttu-id="2753e-113">Visual Studio cria uma UI WPF básica para seu aplicativo e inclui o XAML apropriado e arquivos code-behind.</span><span class="sxs-lookup"><span data-stu-id="2753e-113">Visual Studio creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>  
  
8. <span data-ttu-id="2753e-114">Adicione referências aos **WorkflowModel** assemblies.</span><span class="sxs-lookup"><span data-stu-id="2753e-114">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="2753e-115">Para fazer isso, em **Gerenciador de soluções**, clique com botão direito do **HostingApplication** do projeto e selecione **adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="2753e-115">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>  
  
9. <span data-ttu-id="2753e-116">No **adicionar referência** caixa de diálogo, clique o **.NET** guia, mantenha pressionada a tecla CTRL, selecione os seguintes assemblies e, em seguida, clique em **Okey**:</span><span class="sxs-lookup"><span data-stu-id="2753e-116">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>  
  
    - <span data-ttu-id="2753e-117">System.Activities</span><span class="sxs-lookup"><span data-stu-id="2753e-117">System.Activities</span></span>  
  
    - <span data-ttu-id="2753e-118">System.Activities.Presentation</span><span class="sxs-lookup"><span data-stu-id="2753e-118">System.Activities.Presentation</span></span>  
  
    - <span data-ttu-id="2753e-119">System.Activities.Core.Presentation</span><span class="sxs-lookup"><span data-stu-id="2753e-119">System.Activities.Core.Presentation</span></span>  
  
10. <span data-ttu-id="2753e-120">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="2753e-120">Click **OK**.</span></span>  
  
11. <span data-ttu-id="2753e-121">Consulte [tarefa 2: Hospedar o Designer de fluxo de trabalho](task-2-host-the-workflow-designer.md) para aprender a hospedar a tela de design do designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2753e-121">See [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2753e-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2753e-122">See also</span></span>

- [<span data-ttu-id="2753e-123">Hospedando novamente o Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="2753e-123">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="2753e-124">Tarefa 2: Hospedar o Designer de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="2753e-124">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
