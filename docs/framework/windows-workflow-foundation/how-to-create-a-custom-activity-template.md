---
title: 'Como: Criar um modelo de atividade personalizada'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: c90721676fc5b77704ee86bcd5e98c99e3af6683
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512704"
---
# <a name="how-to-create-a-custom-activity-template"></a><span data-ttu-id="ec1ad-102">Como: Criar um modelo de atividade personalizada</span><span class="sxs-lookup"><span data-stu-id="ec1ad-102">How to: Create a Custom Activity Template</span></span>

<span data-ttu-id="ec1ad-103">Modelos personalizados de atividade são usados para personalizar a configuração de atividades, incluindo atividades compostas personalizados, para que os usuários não tem que criar cada atividade individualmente e configurar suas propriedades e outras configurações manualmente.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-103">Custom activity templates are used to customize the configuration of activities, including custom composite activities, so that users do not have to create each activity individually and configure their properties and other settings manually.</span></span> <span data-ttu-id="ec1ad-104">Esses modelos personalizados podem ser disponibilizados na **caixa de ferramentas** no [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] ou um designer rehosted, do qual os usuários podem o arrastar para a superfície de design pré-configurado.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-104">These custom templates can be made available in the **Toolbox** on the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] or from a rehosted designer, from which users can drag them onto the preconfigured design surface.</span></span> [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] <span data-ttu-id="ec1ad-105">é fornecido com bons exemplos desses modelos: o [Designer de modelo de SendAndReceiveReply](/visualstudio/workflow-designer/sendandreceivereply-template-designer) e o [Designer de modelo de ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer) no [Designersdeatividadedemensagens](/visualstudio/workflow-designer/messaging-activity-designers) categoria.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-105">ships with good examples of such templates: the [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) and the [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) in the [Messaging Activity Designers](/visualstudio/workflow-designer/messaging-activity-designers) category.</span></span>

 <span data-ttu-id="ec1ad-106">O primeiro procedimento neste tópico descreve como criar um modelo de atividade personalizada para um **atraso** atividade e o segundo procedimento rapidamente descreve como disponibilizá-lo em um [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] para verificar se o modelo personalizado funciona.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-106">The first procedure in this topic describes how to create a custom activity template for a **Delay** activity and the second procedure describes briefly how to make it available in a [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] to verify that the custom template works.</span></span>

 <span data-ttu-id="ec1ad-107">Modelos personalizados de atividade devem implementar <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-107">Custom activity templates must implement the <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span></span> <span data-ttu-id="ec1ad-108">A interface possui um único método de <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> com que você pode criar e configurar as instâncias da atividade usadas no modelo.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-108">The interface has a single <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> method with which you can create and configure the activity instances used in the template.</span></span>

## <a name="to-create-a-template-for-the-delay-activity"></a><span data-ttu-id="ec1ad-109">Para criar um modelo para atividades de atraso</span><span class="sxs-lookup"><span data-stu-id="ec1ad-109">To create a template for the Delay activity</span></span>

1.  <span data-ttu-id="ec1ad-110">Inicie o Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-110">Start Visual Studio 2010.</span></span>

2.  <span data-ttu-id="ec1ad-111">No menu **Arquivo**, aponte para **Novo** e selecione **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-111">On the **File** menu, point to **New**, and then select **Project**.</span></span>

     <span data-ttu-id="ec1ad-112">A caixa de diálogo **Novo Projeto** é aberta.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-112">The **New Project** dialog box opens.</span></span>

3.  <span data-ttu-id="ec1ad-113">No **tipos de projeto** painel, selecione **fluxo de trabalho** de qualquer um os **Visual c#** projetos ou **Visual Basic** agrupamentos dependendo da sua preferência de idioma.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-113">In the **Project Types** pane, select **Workflow** from either the **Visual C#** projects or **Visual Basic** groupings depending on your language preference.</span></span>

4.  <span data-ttu-id="ec1ad-114">No **modelos** painel, selecione **biblioteca de atividades**.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-114">In the **Templates** pane, select **Activity Library**.</span></span>

5.  <span data-ttu-id="ec1ad-115">No **nome** , digite `DelayActivityTemplate`.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-115">In the **Name** box, enter `DelayActivityTemplate`.</span></span>

6.  <span data-ttu-id="ec1ad-116">Aceite os padrões de **local** e **nome da solução** caixas de texto e clique **Okey**.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-116">Accept the defaults in the **Location** and **Solution name** text boxes, and then click **OK**.</span></span>

7.  <span data-ttu-id="ec1ad-117">Clique com botão direito no diretório de referências do projeto de DelayActivityTemplate em **Gerenciador de soluções** e escolha **adicionar referência** para abrir o **Add Reference** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-117">Right-click the References directory of the DelayActivityTemplate project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

8.  <span data-ttu-id="ec1ad-118">Vá para o **.NET** e selecione **PresentationFramework** do **nome do componente** coluna à esquerda e clique em **Okey** para adicionar uma referência para o arquivo de PresentationFramework. dll.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-118">Go to the **.NET** tab and select **PresentationFramework** from the **Component Name** column on the left and click **OK** to add a reference to the PresentationFramework.dll file.</span></span>

9. <span data-ttu-id="ec1ad-119">Repita este procedimento para adicionar referências para System.Activities.Presentation.dll e arquivos de WindowsBase.dll.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-119">Repeat this procedure to add references to the System.Activities.Presentation.dll and the WindowsBase.dll files.</span></span>

10. <span data-ttu-id="ec1ad-120">Clique com botão direito no projeto de DelayActivityTemplate em **Gerenciador de soluções** e escolha **Add** e, em seguida, **Novo Item** para abrir o **Add New Item**caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-120">Right-click the DelayActivityTemplate project in **Solution Explorer** and choose **Add** and then **New Item** to open the **Add New Item** dialog box.</span></span>

11. <span data-ttu-id="ec1ad-121">Selecione o **classe** modelo, nomeie-o MyDelayTemplate e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-121">Select the **Class** template, name it MyDelayTemplate, and then click **OK**.</span></span>

12. <span data-ttu-id="ec1ad-122">Abra o arquivo de MyDelayTemplate.cs e adicione as instruções a seguir.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-122">Open the MyDelayTemplate.cs file and add the following statements.</span></span>

    ```
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. <span data-ttu-id="ec1ad-123">Implementar <xref:System.Activities.Presentation.IActivityTemplateFactory> com a classe de `MyDelayActivity` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-123">Implement the <xref:System.Activities.Presentation.IActivityTemplateFactory> with the `MyDelayActivity` class with the following code.</span></span> <span data-ttu-id="ec1ad-124">Isso configura o atraso para ter uma duração de 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-124">This configures the delay to have a duration of 10 seconds.</span></span>

    ```
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

14. <span data-ttu-id="ec1ad-125">Selecione **compilar solução** da **Build** menu para gerar o arquivo de Delayactivitytemplate.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-125">Select **Build Solution** from the **Build** menu to generate the DelayActivityTemplate.dll file.</span></span>

### <a name="to-make-the-template-available-in-a-workflow-designer"></a><span data-ttu-id="ec1ad-126">Para fazer o modelo disponível em Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="ec1ad-126">To make the template available in a Workflow Designer</span></span>

1.  <span data-ttu-id="ec1ad-127">Clique com botão direito na solução de DelayActivityTemplate em **Gerenciador de soluções** e escolha **Add** e, em seguida, **novo projeto** para abrir o **adicionar novo projeto** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-127">Right-click the DelayActivityTemplate solution in **Solution Explorer** and choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>

2.  <span data-ttu-id="ec1ad-128">Selecione o **aplicativo de Console do fluxo de trabalho** modelo, nomeie- `CustomActivityTemplateApp`e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-128">Select the **Workflow Console Application** template, name it `CustomActivityTemplateApp`, and then click **OK**.</span></span>

3.  <span data-ttu-id="ec1ad-129">Clique com botão direito no diretório de referências de projeto de CustomActivityTemplateApp em **Gerenciador de soluções** e escolha **adicionar referência** para abrir o **Add Reference** caixa de diálogo caixa.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-129">Right-click the References directory of the CustomActivityTemplateApp project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

4.  <span data-ttu-id="ec1ad-130">Vá para o **projetos** e selecione **DelayActivityTemplate** do **nome do projeto** coluna à esquerda e clique em **Okey** para adicionar um referência para o arquivo de Delayactivitytemplate que você criou no primeiro procedimento.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-130">Go to the **Projects** tab and select **DelayActivityTemplate** from the **Project Name** column on the left and click **OK** to add a reference to the DelayActivityTemplate.dll file that you created in the first procedure.</span></span>

5.  <span data-ttu-id="ec1ad-131">Clique com botão direito no projeto de CustomActivityTemplateApp em **Gerenciador de soluções** e escolha **Build** para compilar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-131">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Build** to compile the application.</span></span>

6.  <span data-ttu-id="ec1ad-132">Clique com botão direito no projeto de CustomActivityTemplateApp em **Gerenciador de soluções** e escolha **definir como projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-132">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Set as Startup Project**.</span></span>

7.  <span data-ttu-id="ec1ad-133">Selecione **Start Without Debugging** da **depurar** menu e pressione qualquer tecla para continuar quando solicitado da janela cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-133">Select **Start Without Debugging** from the **Debug** menu and press any key to continue when prompted from the cmd.exe window.</span></span>

8.  <span data-ttu-id="ec1ad-134">Abra o arquivo de Workflow1.xaml e abra o **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-134">Open the Workflow1.xaml file and open the **Toolbox**.</span></span>

9. <span data-ttu-id="ec1ad-135">Localize o **MyDelayActivity** modelo na **DelayActivityTemplate** categoria.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-135">Locate the **MyDelayActivity** template in the **DelayActivityTemplate** category.</span></span> <span data-ttu-id="ec1ad-136">Arraste-o para a superfície de design.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-136">Drag it onto the design surface.</span></span> <span data-ttu-id="ec1ad-137">Confirmar a **propriedades** janela que o `Duration` propriedade foi definida como 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-137">Confirm in the **Properties** window that the `Duration` property has been set to 10 seconds.</span></span>

## <a name="example"></a><span data-ttu-id="ec1ad-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ec1ad-138">Example</span></span>
 <span data-ttu-id="ec1ad-139">O arquivo de MyDelayActivity.cs deve conter o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ec1ad-139">The MyDelayActivity.cs file should contain the following code.</span></span>

```
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

## <a name="see-also"></a><span data-ttu-id="ec1ad-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec1ad-140">See also</span></span>

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [<span data-ttu-id="ec1ad-141">Personalizando a experiência de design de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="ec1ad-141">Customizing the Workflow Design Experience</span></span>](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)