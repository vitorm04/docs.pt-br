---
title: 'Como: Crie um modelo personalizado de atividades'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: f910d1367c941dbc319421d402cae8f4194872e5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715247"
---
# <a name="how-to-create-a-custom-activity-template"></a><span data-ttu-id="b7187-102">Como: Crie um modelo personalizado de atividades</span><span class="sxs-lookup"><span data-stu-id="b7187-102">How to: Create a Custom Activity Template</span></span>

<span data-ttu-id="b7187-103">Modelos personalizados de atividade são usados para personalizar a configuração de atividades, incluindo atividades compostas personalizados, para que os usuários não tem que criar cada atividade individualmente e configurar suas propriedades e outras configurações manualmente.</span><span class="sxs-lookup"><span data-stu-id="b7187-103">Custom activity templates are used to customize the configuration of activities, including custom composite activities, so that users do not have to create each activity individually and configure their properties and other settings manually.</span></span> <span data-ttu-id="b7187-104">Esses modelos personalizados podem ser disponibilizados na **caixa de ferramentas** do Windows designer de fluxo de trabalho ou em um designer rehospedado, do qual os usuários podem arrastá-los para a superfície de design pré-configurada.</span><span class="sxs-lookup"><span data-stu-id="b7187-104">These custom templates can be made available in the **Toolbox** on the Windows Workflow Designer or from a rehosted designer, from which users can drag them onto the preconfigured design surface.</span></span> <span data-ttu-id="b7187-105">Designer de Fluxo de Trabalho vem com bons exemplos de modelos: o [Designer de modelos SendAndReceiveReply](/visualstudio/workflow-designer/sendandreceivereply-template-designer) e o [Designer de modelos ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer) na categoria [designers de atividade de mensagens](/visualstudio/workflow-designer/messaging-activity-designers) .</span><span class="sxs-lookup"><span data-stu-id="b7187-105">Workflow Designer ships with good examples of such templates: the [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) and the [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) in the [Messaging Activity Designers](/visualstudio/workflow-designer/messaging-activity-designers) category.</span></span>

 <span data-ttu-id="b7187-106">O primeiro procedimento neste tópico descreve como criar um modelo de atividade personalizada para uma atividade de **atraso** e o segundo procedimento descreve brevemente como disponibilizá-lo em um designer de fluxo de trabalho para verificar se o modelo personalizado funciona.</span><span class="sxs-lookup"><span data-stu-id="b7187-106">The first procedure in this topic describes how to create a custom activity template for a **Delay** activity and the second procedure describes briefly how to make it available in a Workflow Designer to verify that the custom template works.</span></span>

 <span data-ttu-id="b7187-107">Modelos personalizados de atividade devem implementar <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span><span class="sxs-lookup"><span data-stu-id="b7187-107">Custom activity templates must implement the <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span></span> <span data-ttu-id="b7187-108">A interface possui um único método de <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> com que você pode criar e configurar as instâncias da atividade usadas no modelo.</span><span class="sxs-lookup"><span data-stu-id="b7187-108">The interface has a single <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> method with which you can create and configure the activity instances used in the template.</span></span>

## <a name="to-create-a-template-for-the-delay-activity"></a><span data-ttu-id="b7187-109">Para criar um modelo para atividades de atraso</span><span class="sxs-lookup"><span data-stu-id="b7187-109">To create a template for the Delay activity</span></span>

1. <span data-ttu-id="b7187-110">Inicie o Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="b7187-110">Start Visual Studio 2010.</span></span>

2. <span data-ttu-id="b7187-111">No menu **Arquivo**, aponte para **Novo** e selecione **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="b7187-111">On the **File** menu, point to **New**, and then select **Project**.</span></span>

     <span data-ttu-id="b7187-112">A caixa de diálogo **Novo Projeto** é aberta.</span><span class="sxs-lookup"><span data-stu-id="b7187-112">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="b7187-113">No painel **tipos de projeto** , selecione **fluxo de trabalho** nos **projetos C# visuais** ou **Visual Basic** agrupamentos, dependendo da sua preferência de idioma.</span><span class="sxs-lookup"><span data-stu-id="b7187-113">In the **Project Types** pane, select **Workflow** from either the **Visual C#** projects or **Visual Basic** groupings depending on your language preference.</span></span>

4. <span data-ttu-id="b7187-114">No painel **modelos** , selecione **biblioteca de atividades**.</span><span class="sxs-lookup"><span data-stu-id="b7187-114">In the **Templates** pane, select **Activity Library**.</span></span>

5. <span data-ttu-id="b7187-115">Na caixa **nome** , digite `DelayActivityTemplate`.</span><span class="sxs-lookup"><span data-stu-id="b7187-115">In the **Name** box, enter `DelayActivityTemplate`.</span></span>

6. <span data-ttu-id="b7187-116">Aceite os padrões nas caixas de texto **nome da solução** e **local** e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="b7187-116">Accept the defaults in the **Location** and **Solution name** text boxes, and then click **OK**.</span></span>

7. <span data-ttu-id="b7187-117">Clique com o botão direito do mouse no diretório References do projeto DelayActivityTemplate em **Gerenciador de soluções** e escolha **Adicionar referência** para abrir a caixa de diálogo **Adicionar referência** .</span><span class="sxs-lookup"><span data-stu-id="b7187-117">Right-click the References directory of the DelayActivityTemplate project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

8. <span data-ttu-id="b7187-118">Vá para a guia **.net** e selecione **PresentationFramework** na coluna **nome do componente** à esquerda e clique em **OK** para adicionar uma referência ao arquivo PresentationFramework. dll.</span><span class="sxs-lookup"><span data-stu-id="b7187-118">Go to the **.NET** tab and select **PresentationFramework** from the **Component Name** column on the left and click **OK** to add a reference to the PresentationFramework.dll file.</span></span>

9. <span data-ttu-id="b7187-119">Repita este procedimento para adicionar referências para System.Activities.Presentation.dll e arquivos de WindowsBase.dll.</span><span class="sxs-lookup"><span data-stu-id="b7187-119">Repeat this procedure to add references to the System.Activities.Presentation.dll and the WindowsBase.dll files.</span></span>

10. <span data-ttu-id="b7187-120">Clique com o botão direito do mouse no projeto DelayActivityTemplate no **Gerenciador de soluções** e escolha **Adicionar** e **novo item** para abrir a caixa de diálogo **Adicionar novo item** .</span><span class="sxs-lookup"><span data-stu-id="b7187-120">Right-click the DelayActivityTemplate project in **Solution Explorer** and choose **Add** and then **New Item** to open the **Add New Item** dialog box.</span></span>

11. <span data-ttu-id="b7187-121">Selecione o modelo de **classe** , nomeie-o mydelaytemplate e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="b7187-121">Select the **Class** template, name it MyDelayTemplate, and then click **OK**.</span></span>

12. <span data-ttu-id="b7187-122">Abra o arquivo de MyDelayTemplate.cs e adicione as instruções a seguir.</span><span class="sxs-lookup"><span data-stu-id="b7187-122">Open the MyDelayTemplate.cs file and add the following statements.</span></span>

    ```csharp
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. <span data-ttu-id="b7187-123">Implementar <xref:System.Activities.Presentation.IActivityTemplateFactory> com a classe de `MyDelayActivity` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b7187-123">Implement the <xref:System.Activities.Presentation.IActivityTemplateFactory> with the `MyDelayActivity` class with the following code.</span></span> <span data-ttu-id="b7187-124">Isso configura o atraso para ter uma duração de 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="b7187-124">This configures the delay to have a duration of 10 seconds.</span></span>

    ```csharp
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
    ```

14. <span data-ttu-id="b7187-125">Selecione **Compilar solução** no menu **Compilar** para gerar o arquivo DelayActivityTemplate. dll.</span><span class="sxs-lookup"><span data-stu-id="b7187-125">Select **Build Solution** from the **Build** menu to generate the DelayActivityTemplate.dll file.</span></span>

### <a name="to-make-the-template-available-in-a-workflow-designer"></a><span data-ttu-id="b7187-126">Para fazer o modelo disponível em Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="b7187-126">To make the template available in a Workflow Designer</span></span>

1. <span data-ttu-id="b7187-127">Clique com o botão direito do mouse na solução DelayActivityTemplate em **Gerenciador de soluções** e escolha **Adicionar** e **novo projeto** para abrir a caixa de diálogo **Adicionar novo projeto** .</span><span class="sxs-lookup"><span data-stu-id="b7187-127">Right-click the DelayActivityTemplate solution in **Solution Explorer** and choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="b7187-128">Selecione o modelo de **aplicativo do console de fluxo de trabalho** , nomeie-o `CustomActivityTemplateApp`e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="b7187-128">Select the **Workflow Console Application** template, name it `CustomActivityTemplateApp`, and then click **OK**.</span></span>

3. <span data-ttu-id="b7187-129">Clique com o botão direito do mouse no diretório References do projeto CustomActivityTemplateApp em **Gerenciador de soluções** e escolha **Adicionar referência** para abrir a caixa de diálogo **Adicionar referência** .</span><span class="sxs-lookup"><span data-stu-id="b7187-129">Right-click the References directory of the CustomActivityTemplateApp project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

4. <span data-ttu-id="b7187-130">Vá para a guia **projetos** e selecione **DelayActivityTemplate** na coluna **nome do projeto** à esquerda e clique em **OK** para adicionar uma referência ao arquivo DelayActivityTemplate. dll que você criou no primeiro procedimento.</span><span class="sxs-lookup"><span data-stu-id="b7187-130">Go to the **Projects** tab and select **DelayActivityTemplate** from the **Project Name** column on the left and click **OK** to add a reference to the DelayActivityTemplate.dll file that you created in the first procedure.</span></span>

5. <span data-ttu-id="b7187-131">Clique com o botão direito do mouse no projeto CustomActivityTemplateApp no **Gerenciador de soluções** e escolha **Compilar** para compilar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b7187-131">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Build** to compile the application.</span></span>

6. <span data-ttu-id="b7187-132">Clique com o botão direito do mouse no projeto CustomActivityTemplateApp em **Gerenciador de soluções** e escolha **definir como projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="b7187-132">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Set as Startup Project**.</span></span>

7. <span data-ttu-id="b7187-133">Selecione **Iniciar sem depuração** no menu **depurar** e pressione qualquer tecla para continuar quando solicitado na janela cmd. exe.</span><span class="sxs-lookup"><span data-stu-id="b7187-133">Select **Start Without Debugging** from the **Debug** menu and press any key to continue when prompted from the cmd.exe window.</span></span>

8. <span data-ttu-id="b7187-134">Abra o arquivo workflow1. XAML e abra a **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="b7187-134">Open the Workflow1.xaml file and open the **Toolbox**.</span></span>

9. <span data-ttu-id="b7187-135">Localize o modelo **MyDelayActivity** na categoria **DelayActivityTemplate** .</span><span class="sxs-lookup"><span data-stu-id="b7187-135">Locate the **MyDelayActivity** template in the **DelayActivityTemplate** category.</span></span> <span data-ttu-id="b7187-136">Arraste-o para a superfície de design.</span><span class="sxs-lookup"><span data-stu-id="b7187-136">Drag it onto the design surface.</span></span> <span data-ttu-id="b7187-137">Confirme na janela **Propriedades** que a propriedade `Duration` foi definida como 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="b7187-137">Confirm in the **Properties** window that the `Duration` property has been set to 10 seconds.</span></span>

## <a name="example"></a><span data-ttu-id="b7187-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7187-138">Example</span></span>
 <span data-ttu-id="b7187-139">O arquivo de MyDelayActivity.cs deve conter o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b7187-139">The MyDelayActivity.cs file should contain the following code.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

//Namespaces added
using System.Activities;
using System.Activities.Statements;
using System.Activities.Presentation;
using System.Windows;

namespace DelayActivityTemplate
{
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="b7187-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7187-140">See also</span></span>

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [<span data-ttu-id="b7187-141">Personalizando a experiência de design de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b7187-141">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
