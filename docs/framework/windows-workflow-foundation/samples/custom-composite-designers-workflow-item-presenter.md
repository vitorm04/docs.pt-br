---
title: Designer de compostos personalizados - apresentador de item de fluxo de trabalho
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bba89e9da78fd96d0cd7d61e825e4792729bae5b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="custom-composite-designers---workflow-item-presenter"></a><span data-ttu-id="56e5c-102">Designer de compostos personalizados - apresentador de item de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="56e5c-102">Custom Composite Designers - Workflow Item Presenter</span></span>
<span data-ttu-id="56e5c-103">O <xref:System.Activities.Presentation.WorkflowItemPresenter> é um tipo de chave no WF designer modelo de programação que permite a criação de uma "zona para soltar" onde uma atividade arbitrária pode ser colocada.</span><span class="sxs-lookup"><span data-stu-id="56e5c-103">The <xref:System.Activities.Presentation.WorkflowItemPresenter> is a key type in the WF designer programming model that allows for the creation of a "drop zone" where an arbitrary activity can be placed.</span></span> <span data-ttu-id="56e5c-104">Este exemplo mostra como criar um designer de atividade que superfícies tal uma "zona de descarte."</span><span class="sxs-lookup"><span data-stu-id="56e5c-104">This sample shows how to build an activity designer that surfaces such a "drop zone."</span></span>  
  
 <span data-ttu-id="56e5c-105">Este exemplo demonstra:</span><span class="sxs-lookup"><span data-stu-id="56e5c-105">This sample demonstrates:</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="56e5c-106">Demonstra</span><span class="sxs-lookup"><span data-stu-id="56e5c-106">Demonstrates</span></span>  
  
-   <span data-ttu-id="56e5c-107">Criando um designer personalizado de atividade com <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="56e5c-107">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>  
  
-   <span data-ttu-id="56e5c-108">Registrando o designer personalizado que usa o armazenamento de metadados.</span><span class="sxs-lookup"><span data-stu-id="56e5c-108">Registering the custom designer using the metadata store.</span></span>  
  
-   <span data-ttu-id="56e5c-109">Programando a caixa de ferramentas rehosted declarativamente e imperativa.</span><span class="sxs-lookup"><span data-stu-id="56e5c-109">Programming the rehosted toolbox declaratively and imperatively.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="56e5c-110">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="56e5c-110">Sample Details</span></span>  
 <span data-ttu-id="56e5c-111">O código para esse exemplo mostra:</span><span class="sxs-lookup"><span data-stu-id="56e5c-111">The code for this sample shows:</span></span>  
  
-   <span data-ttu-id="56e5c-112">O designer personalizado de atividade é compilado para a classe de `SimpleNativeActivity` .</span><span class="sxs-lookup"><span data-stu-id="56e5c-112">The custom activity designer is built for the `SimpleNativeActivity` class.</span></span>  
  
-   <span data-ttu-id="56e5c-113">A criação de um designer personalizado de atividade com <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="56e5c-113">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>  
  
```xaml  
<sap:ActivityDesigner x:Class="Microsoft.Samples.UsingWorkflowItemPresenter.SimpleNativeDesigner"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"  
    xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">  
    <sap:ActivityDesigner.Resources>  
        <DataTemplate x:Key="Collapsed">  
            <StackPanel>  
                <TextBlock>This is the collapsed view</TextBlock>  
            </StackPanel>  
        </DataTemplate>  
        <DataTemplate x:Key="Expanded">  
            <StackPanel>  
                <TextBlock>Custom Text</TextBlock>  
                <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
                                        HintText="Please drop an activity here" />  
            </StackPanel>  
        </DataTemplate>  
        <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">  
            <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>  
            <Style.Triggers>  
                <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">  
                    <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>  
                </DataTrigger>  
            </Style.Triggers>  
        </Style>  
    </sap:ActivityDesigner.Resources>  
    <Grid>  
        <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />  
    </Grid>  
</sap:ActivityDesigner>  
```  
  
 <span data-ttu-id="56e5c-114">Observe o uso de associação de dados de WPF associar a `ModelItem.Body`.</span><span class="sxs-lookup"><span data-stu-id="56e5c-114">Note the use of WPF data binding to bind to `ModelItem.Body`.</span></span> <span data-ttu-id="56e5c-115">`ModelItem`é a propriedade em <xref:System.Activities.Presentation.ActivityDesigner> que se refere ao objeto subjacente, o designer está sendo usado, nesse caso, **SimpleNativeActivity**.</span><span class="sxs-lookup"><span data-stu-id="56e5c-115">`ModelItem` is the property on <xref:System.Activities.Presentation.ActivityDesigner> that refers to the underlying object the designer is being used for, in this case, **SimpleNativeActivity**.</span></span>  
  
#### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="56e5c-116">A configuração, compilação, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="56e5c-116">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="56e5c-117">Abra a solução em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56e5c-117">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="56e5c-118">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="56e5c-118">Press F5 to compile and run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="56e5c-119">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="56e5c-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="56e5c-120">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="56e5c-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="56e5c-121">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="56e5c-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="56e5c-122">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="56e5c-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a><span data-ttu-id="56e5c-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56e5c-123">See Also</span></span>  
 <xref:System.Activities.Presentation.WorkflowItemPresenter>  
 [<span data-ttu-id="56e5c-124">Desenvolvendo aplicativos com o Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="56e5c-124">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
