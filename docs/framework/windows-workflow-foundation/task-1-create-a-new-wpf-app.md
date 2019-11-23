---
title: 'Tarefa 1: Crie um aplicativo do windows presentation foundation do windows'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 3205840da575041b449eb841fc8084e89937fca7
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031889"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="4566b-102">Tarefa 1: Crie um aplicativo do windows presentation foundation do windows</span><span class="sxs-lookup"><span data-stu-id="4566b-102">Task 1: Create a New Windows Presentation Foundation Application</span></span>

<span data-ttu-id="4566b-103">Nesta tarefa, você criará um aplicativo Windows Presentation Foundation (WPF) vazio usando o modelo do Visual Studio de aplicativo WPF e adicionará referências aos assemblies de fluxo de trabalho de [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] apropriados.</span><span class="sxs-lookup"><span data-stu-id="4566b-103">In this task, you will create an empty Windows Presentation Foundation (WPF) application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
## <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="4566b-104">Para criar o projeto de aplicativo de WPF</span><span class="sxs-lookup"><span data-stu-id="4566b-104">To create the WPF Application project</span></span>

1. <span data-ttu-id="4566b-105">Abra o Visual Studio e, no menu **arquivo** , aponte para **novo**e clique em **projeto**.</span><span class="sxs-lookup"><span data-stu-id="4566b-105">Open Visual Studio and on the **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="4566b-106">Na caixa de diálogo **novo projeto** , selecione **Visual C#**  ou **Visual Basic** no painel **modelos instalados** no lado esquerdo da caixa.</span><span class="sxs-lookup"><span data-stu-id="4566b-106">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="4566b-107">Se o idioma de sua escolha não aparecer, procure em **outros idiomas**.</span><span class="sxs-lookup"><span data-stu-id="4566b-107">If the language of your choice does not appear, look under **Other Languages**.</span></span>

3. <span data-ttu-id="4566b-108">Selecione **Windows** no painel **modelos instalados** .</span><span class="sxs-lookup"><span data-stu-id="4566b-108">Select **Windows** in the **Installed Templates** pane.</span></span>

4. <span data-ttu-id="4566b-109">No painel superior, confirme que (o valor padrão) **.NET Framework 4** foi selecionado na caixa de listagem suspensa e, em seguida, selecione **aplicativo WPF**.</span><span class="sxs-lookup"><span data-stu-id="4566b-109">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>

5. <span data-ttu-id="4566b-110">Defina o nome do projeto como **HostingApplication** na parte inferior da janela.</span><span class="sxs-lookup"><span data-stu-id="4566b-110">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>

6. <span data-ttu-id="4566b-111">Defina o nome da solução como **RehostingTheDesigner**.</span><span class="sxs-lookup"><span data-stu-id="4566b-111">Set the solution name to **RehostingTheDesigner**.</span></span>

7. <span data-ttu-id="4566b-112">Clique em **OK** para criar o projeto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4566b-112">Click **OK** to create the application project.</span></span> <span data-ttu-id="4566b-113">O Visual Studio cria uma interface do usuário básica do WPF para seu aplicativo e inclui os arquivos XAML e code-behind apropriados.</span><span class="sxs-lookup"><span data-stu-id="4566b-113">Visual Studio creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>

8. <span data-ttu-id="4566b-114">Adicione referências a assemblies **WorkflowModel** .</span><span class="sxs-lookup"><span data-stu-id="4566b-114">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="4566b-115">Para fazer isso, em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **HostingApplication** e selecione **Adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="4566b-115">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>

9. <span data-ttu-id="4566b-116">Na caixa de diálogo **Adicionar referência** , clique na guia **.net** , mantenha pressionada a tecla CTRL, selecione os seguintes assemblies e clique em **OK**:</span><span class="sxs-lookup"><span data-stu-id="4566b-116">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>

    - <span data-ttu-id="4566b-117">System.Activities</span><span class="sxs-lookup"><span data-stu-id="4566b-117">System.Activities</span></span>
    - <span data-ttu-id="4566b-118">System.Activities.Presentation</span><span class="sxs-lookup"><span data-stu-id="4566b-118">System.Activities.Presentation</span></span>
    - <span data-ttu-id="4566b-119">System.Activities.Core.Presentation</span><span class="sxs-lookup"><span data-stu-id="4566b-119">System.Activities.Core.Presentation</span></span>

10. <span data-ttu-id="4566b-120">Consulte [tarefa 2: hospedar o designer de fluxo de trabalho](task-2-host-the-workflow-designer.md) para saber como hospedar a tela de design do designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4566b-120">See [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>

## <a name="see-also"></a><span data-ttu-id="4566b-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4566b-121">See also</span></span>

- [<span data-ttu-id="4566b-122">Hospedando novamente o Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="4566b-122">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="4566b-123">Tarefa 2: Hospedar o Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="4566b-123">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
