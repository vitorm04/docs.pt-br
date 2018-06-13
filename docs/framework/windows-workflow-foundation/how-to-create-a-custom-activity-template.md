---
title: 'Como: Crie um modelo personalizado de atividades'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: b455f8a763859d31405380e25cd7516856e8da2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517843"
---
# <a name="how-to-create-a-custom-activity-template"></a><span data-ttu-id="9c05f-102">Como: Crie um modelo personalizado de atividades</span><span class="sxs-lookup"><span data-stu-id="9c05f-102">How to: Create a Custom Activity Template</span></span>
<span data-ttu-id="9c05f-103">Modelos personalizados de atividade são usados para personalizar a configuração de atividades, incluindo atividades compostas personalizados, para que os usuários não tem que criar cada atividade individualmente e configurar suas propriedades e outras configurações manualmente.</span><span class="sxs-lookup"><span data-stu-id="9c05f-103">Custom activity templates are used to customize the configuration of activities, including custom composite activities, so that users do not have to create each activity individually and configure their properties and other settings manually.</span></span> <span data-ttu-id="9c05f-104">Esses modelos personalizados podem ser disponibilizados no **caixa de ferramentas** no [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] ou de um designer de rehosted, do qual os usuários podem arrastá-los na superfície de design pré-configurado.</span><span class="sxs-lookup"><span data-stu-id="9c05f-104">These custom templates can be made available in the **Toolbox** on the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] or from a rehosted designer, from which users can drag them onto the preconfigured design surface.</span></span> [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]<span data-ttu-id="9c05f-105"> acompanha Bons exemplos de tais modelos: o [Designer de modelo de SendAndReceiveReply](/visualstudio/workflow-designer/sendandreceivereply-template-designer) e [Designer de modelo de ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer) no [Designersdeatividadedemensagens](/visualstudio/workflow-designer/messaging-activity-designers) categoria.</span><span class="sxs-lookup"><span data-stu-id="9c05f-105"> ships with good examples of such templates: the [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) and the [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) in the [Messaging Activity Designers](/visualstudio/workflow-designer/messaging-activity-designers) category.</span></span>  
  
 <span data-ttu-id="9c05f-106">O primeiro procedimento neste tópico descreve como criar um modelo de atividade personalizada para um **atraso** atividade e o segundo procedimento descreve brevemente como disponibilizá-lo em um [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] para verificar se o modelo personalizado funciona.</span><span class="sxs-lookup"><span data-stu-id="9c05f-106">The first procedure in this topic describes how to create a custom activity template for a **Delay** activity and the second procedure describes briefly how to make it available in a [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] to verify that the custom template works.</span></span>  
  
 <span data-ttu-id="9c05f-107">Modelos personalizados de atividade devem implementar <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span><span class="sxs-lookup"><span data-stu-id="9c05f-107">Custom activity templates must implement the <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span></span> <span data-ttu-id="9c05f-108">A interface possui um único método de <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> com que você pode criar e configurar as instâncias da atividade usadas no modelo.</span><span class="sxs-lookup"><span data-stu-id="9c05f-108">The interface has a single <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> method with which you can create and configure the activity instances used in the template.</span></span>  
  
### <a name="to-create-a-template-for-the-delay-activity"></a><span data-ttu-id="9c05f-109">Para criar um modelo para atividades de atraso</span><span class="sxs-lookup"><span data-stu-id="9c05f-109">To create a template for the Delay activity</span></span>  
  
1.  <span data-ttu-id="9c05f-110">Inicie o [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9c05f-110">Start [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="9c05f-111">No menu **Arquivo**, aponte para **Novo** e selecione **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="9c05f-111">On the **File** menu, point to **New**, and then select **Project**.</span></span>  
  
     <span data-ttu-id="9c05f-112">A caixa de diálogo **Novo Projeto** é aberta.</span><span class="sxs-lookup"><span data-stu-id="9c05f-112">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="9c05f-113">No **tipos de projeto** painel, selecione **fluxo de trabalho** do **Visual C#** projetos ou **Visual Basic** agrupamentos dependendo de sua preferência de idioma.</span><span class="sxs-lookup"><span data-stu-id="9c05f-113">In the **Project Types** pane, select **Workflow** from either the **Visual C#** projects or **Visual Basic** groupings depending on your language preference.</span></span>  
  
4.  <span data-ttu-id="9c05f-114">No **modelos** painel, selecione **biblioteca de atividades**.</span><span class="sxs-lookup"><span data-stu-id="9c05f-114">In the **Templates** pane, select **Activity Library**.</span></span>  
  
5.  <span data-ttu-id="9c05f-115">No **nome** , digite `DelayActivityTemplate`.</span><span class="sxs-lookup"><span data-stu-id="9c05f-115">In the **Name** box, enter `DelayActivityTemplate`.</span></span>  
  
6.  <span data-ttu-id="9c05f-116">Aceite os padrões no **local** e **nome da solução** caixas de texto e clique **Okey**.</span><span class="sxs-lookup"><span data-stu-id="9c05f-116">Accept the defaults in the **Location** and **Solution name** text boxes, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="9c05f-117">Clique o diretório de referências do projeto em DelayActivityTemplate **Solution Explorer** e escolha **adicionar referência** para abrir o **adicionar referência** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="9c05f-117">Right-click the References directory of the DelayActivityTemplate project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>  
  
8.  <span data-ttu-id="9c05f-118">Vá para o **.NET** guia e selecione **PresentationFramework** do **nome do componente** coluna à esquerda e clique em **Okey** para adicionar uma referência para o arquivo PresentationFramework. dll.</span><span class="sxs-lookup"><span data-stu-id="9c05f-118">Go to the **.NET** tab and select **PresentationFramework** from the **Component Name** column on the left and click **OK** to add a reference to the PresentationFramework.dll file.</span></span>  
  
9. <span data-ttu-id="9c05f-119">Repita este procedimento para adicionar referências para System.Activities.Presentation.dll e arquivos de WindowsBase.dll.</span><span class="sxs-lookup"><span data-stu-id="9c05f-119">Repeat this procedure to add references to the System.Activities.Presentation.dll and the WindowsBase.dll files.</span></span>  
  
10. <span data-ttu-id="9c05f-120">Com o botão direito no projeto DelayActivityTemplate no **Solution Explorer** e escolha **adicionar** e **Novo Item** para abrir o **Adicionar Novo Item**caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="9c05f-120">Right-click the DelayActivityTemplate project in **Solution Explorer** and choose **Add** and then **New Item** to open the **Add New Item** dialog box.</span></span>  
  
11. <span data-ttu-id="9c05f-121">Selecione o **classe** modelo, nomeie-o MyDelayTemplate e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="9c05f-121">Select the **Class** template, name it MyDelayTemplate, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="9c05f-122">Abra o arquivo de MyDelayTemplate.cs e adicione as instruções a seguir.</span><span class="sxs-lookup"><span data-stu-id="9c05f-122">Open the MyDelayTemplate.cs file and add the following statements.</span></span>  
  
    ```  
    //Namespaces added  
    using System.Activities;  
    using System.Activities.Statements;  
    using System.Activities.Presentation;  
    using System.Windows;  
    ```  
  
13. <span data-ttu-id="9c05f-123">Implementar <xref:System.Activities.Presentation.IActivityTemplateFactory> com a classe de `MyDelayActivity` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9c05f-123">Implement the <xref:System.Activities.Presentation.IActivityTemplateFactory> with the `MyDelayActivity` class with the following code.</span></span> <span data-ttu-id="9c05f-124">Isso configura o atraso para ter uma duração de 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="9c05f-124">This configures the delay to have a duration of 10 seconds.</span></span>  
  
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
  
14. <span data-ttu-id="9c05f-125">Selecione **compilar solução** do **criar** menu para gerar o arquivo DelayActivityTemplate.dll.</span><span class="sxs-lookup"><span data-stu-id="9c05f-125">Select **Build Solution** from the **Build** menu to generate the DelayActivityTemplate.dll file.</span></span>  
  
### <a name="to-make-the-template-available-in-a-workflow-designer"></a><span data-ttu-id="9c05f-126">Para fazer o modelo disponível em Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="9c05f-126">To make the template available in a Workflow Designer</span></span>  
  
1.  <span data-ttu-id="9c05f-127">Clique com botão direito da solução de DelayActivityTemplate **Gerenciador de soluções** e escolha **adicionar** e, em seguida, **novo projeto** para abrir o **adicionar novo projeto** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="9c05f-127">Right-click the DelayActivityTemplate solution in **Solution Explorer** and choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="9c05f-128">Selecione o **aplicativo de Console do fluxo de trabalho** modelo, nomeie-o `CustomActivityTemplateApp`e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="9c05f-128">Select the **Workflow Console Application** template, name it `CustomActivityTemplateApp`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="9c05f-129">Clique o diretório de referências do projeto em CustomActivityTemplateApp **Solution Explorer** e escolha **adicionar referência** para abrir o **adicionar referência** caixa de diálogo caixa.</span><span class="sxs-lookup"><span data-stu-id="9c05f-129">Right-click the References directory of the CustomActivityTemplateApp project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>  
  
4.  <span data-ttu-id="9c05f-130">Vá para o **projetos** guia e selecione **DelayActivityTemplate** do **nome do projeto** coluna à esquerda e clique em **Okey** para adicionar um fazer referência ao arquivo DelayActivityTemplate.dll que você criou no primeiro procedimento.</span><span class="sxs-lookup"><span data-stu-id="9c05f-130">Go to the **Projects** tab and select **DelayActivityTemplate** from the **Project Name** column on the left and click **OK** to add a reference to the DelayActivityTemplate.dll file that you created in the first procedure.</span></span>  
  
5.  <span data-ttu-id="9c05f-131">Clique com botão direito no projeto CustomActivityTemplateApp no **Solution Explorer** e escolha **Build** para compilar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9c05f-131">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Build** to compile the application.</span></span>  
  
6.  <span data-ttu-id="9c05f-132">Clique com botão direito no projeto CustomActivityTemplateApp no **Solution Explorer** e escolha **definir como projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="9c05f-132">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Set as Startup Project**.</span></span>  
  
7.  <span data-ttu-id="9c05f-133">Selecione **Start Without Debugging** do **depurar** menu e pressione qualquer tecla para continuar quando solicitado na janela de cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="9c05f-133">Select **Start Without Debugging** from the **Debug** menu and press any key to continue when prompted from the cmd.exe window.</span></span>  
  
8.  <span data-ttu-id="9c05f-134">Abra o arquivo Workflow1.xaml e o **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="9c05f-134">Open the Workflow1.xaml file and open the **Toolbox**.</span></span>  
  
9. <span data-ttu-id="9c05f-135">Localize o **MyDelayActivity** modelo o **DelayActivityTemplate** categoria.</span><span class="sxs-lookup"><span data-stu-id="9c05f-135">Locate the **MyDelayActivity** template in the **DelayActivityTemplate** category.</span></span> <span data-ttu-id="9c05f-136">Arraste-o para a superfície de design.</span><span class="sxs-lookup"><span data-stu-id="9c05f-136">Drag it onto the design surface.</span></span> <span data-ttu-id="9c05f-137">Confirme no **propriedades** janela que o `Duration` propriedade foi definida como 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="9c05f-137">Confirm in the **Properties** window that the `Duration` property has been set to 10 seconds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c05f-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c05f-138">Example</span></span>  
 <span data-ttu-id="9c05f-139">O arquivo de MyDelayActivity.cs deve conter o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9c05f-139">The MyDelayActivity.cs file should contain the following code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9c05f-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c05f-140">See Also</span></span>  
 <xref:System.Activities.Presentation.IActivityTemplateFactory>  
 [<span data-ttu-id="9c05f-141">Personalizando a experiência de design de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="9c05f-141">Customizing the Workflow Design Experience</span></span>](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)
