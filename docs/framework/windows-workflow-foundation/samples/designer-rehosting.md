---
title: Designer ReHosting
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: f8dbe89ec605f3e957b5178eafd2e034e8159dc3
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028908"
---
# <a name="designer-rehosting"></a><span data-ttu-id="1acbe-102">Designer Rehosting</span><span class="sxs-lookup"><span data-stu-id="1acbe-102">Designer Rehosting</span></span>
<span data-ttu-id="1acbe-103">O designer que rehosting é um cenário comum que se refere hospedar a tela de design de fluxo de trabalho em um aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="1acbe-103">Designer rehosting is a common scenario that refers to hosting the workflow design canvas inside of a custom application.</span></span> <span data-ttu-id="1acbe-104">O aplicativo que hospedando a maioria de pessoas estão familiarizados com é Visual Studio entanto, há um número de cenários onde mostrar o designer de fluxo de trabalho em um aplicativo pode ser útil:</span><span class="sxs-lookup"><span data-stu-id="1acbe-104">The hosting application most people are familiar with is Visual Studio, however there are a number of scenarios where showing the workflow designer in an application may be useful:</span></span>  
  
-   <span data-ttu-id="1acbe-105">Monitorando aplicativos (que permitem que um usuário final visualizem o processo, bem como os dados em tempo de execução sobre o processo como o estado atualmente ativa, os dados agregados de tempo de execução, ou outras informações sobre uma instância de fluxo de trabalho).</span><span class="sxs-lookup"><span data-stu-id="1acbe-105">Monitoring applications (allowing an end user to visualize the process, as well as runtime data about the process such as the currently active state, aggregate execution time data, or other information about an instance of the workflow).</span></span>  
  
-   <span data-ttu-id="1acbe-106">Aplicativos que permitem que um usuário personalizar o processo com um conjunto limitado de atividades.</span><span class="sxs-lookup"><span data-stu-id="1acbe-106">Applications that allow a user to customize the process with a limited set of activities.</span></span>  
  
 <span data-ttu-id="1acbe-107">Para oferecer suporte a esses tipos de aplicativos, os vem do designer de fluxo de trabalho dentro do .NET Framework, e podem ser hospedados em um aplicativo de WPF, ou em um aplicativo de WinForms com WPF apropriado que hospeda o código.</span><span class="sxs-lookup"><span data-stu-id="1acbe-107">To support these types of applications, the workflow designer ships inside the .NET Framework, and can be hosted inside a WPF application, or in a WinForms application with the appropriate WPF hosting code.</span></span> <span data-ttu-id="1acbe-108">Este exemplo demonstra:</span><span class="sxs-lookup"><span data-stu-id="1acbe-108">This sample demonstrates:</span></span>  
  
-   <span data-ttu-id="1acbe-109">Rehosting o designer de WF.</span><span class="sxs-lookup"><span data-stu-id="1acbe-109">Rehosting the WF designer.</span></span>  
  
-   <span data-ttu-id="1acbe-110">Usando a caixa de ferramentas e a grade rehosted de propriedade também.</span><span class="sxs-lookup"><span data-stu-id="1acbe-110">Using the rehosted toolbox and property grid as well.</span></span>  
  
## <a name="rehosting-the-designer"></a><span data-ttu-id="1acbe-111">Rehosting o designer</span><span class="sxs-lookup"><span data-stu-id="1acbe-111">Rehosting the designer</span></span>  
 <span data-ttu-id="1acbe-112">Este exemplo mostra como criar o layout de WPF para conter o designer, mostrado no seguinte layout de grade (código da caixa de ferramentas omitido para interesses de espaço).</span><span class="sxs-lookup"><span data-stu-id="1acbe-112">This sample shows how to create the WPF layout to contain the designer, seen in the following grid layout (Toolbox code omitted for space concerns).</span></span> <span data-ttu-id="1acbe-113">Observe a nomeação das bordas que contêm o designer e a grade de propriedade.</span><span class="sxs-lookup"><span data-stu-id="1acbe-113">Note the naming of the borders which contain the designer and property grid.</span></span>  
  
```xaml  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="2*"/>  
        <ColumnDefinition Width="7*"/>  
        <ColumnDefinition Width="3*"/>  
    </Grid.ColumnDefinitions>  
    <Border Grid.Column="0">  
        <sapt:ToolboxControl>...</sapt:ToolboxControl>  
    </Border>  
    <Border Grid.Column="1" Name="DesignerBorder"/>  
    <Border Grid.Column="2" Name="PropertyBorder"/>  
</Grid>  
```  
  
 <span data-ttu-id="1acbe-114">Em seguida o exemplo cria o designer, e associa os <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> e <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> principais com o recipiente apropriado na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="1acbe-114">Next the sample creates the designer, and associates its primary <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> with the appropriate container in the user interface.</span></span> <span data-ttu-id="1acbe-115">Há algumas linhas de código adicionais no exemplo a seguir merecem que alguma explicação.</span><span class="sxs-lookup"><span data-stu-id="1acbe-115">There are a few additional lines of code in the following example that merit some explanation.</span></span> <span data-ttu-id="1acbe-116">A chamada de <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> é necessário associar os designers padrão de atividade para as atividades enviados com [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1acbe-116">The <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> call is required to associate the default activity designers for the activities shipped with [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="1acbe-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> é chamado para passar no item de WF a ser editado.</span><span class="sxs-lookup"><span data-stu-id="1acbe-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> is called to pass in the WF item to be edited.</span></span> <span data-ttu-id="1acbe-118">Finalmente, <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (canvas primária) e <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (grade de propriedade) são colocados na superfície de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="1acbe-118">Finally, the <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primary canvas) and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (property grid) are placed onto the user interface surface.</span></span>  
  
```csharp  
protected override void OnInitialized(EventArgs e)  
{  
   base.OnInitialized(e);  
   // register metadata  
   (new DesignerMetadata()).Register();  
  
   // create the workflow designer  
   WorkflowDesigner wd = new WorkflowDesigner();  
   wd.Load(new Sequence());  
   DesignerBorder.Child = wd.View;  
   PropertyBorder.Child = wd.PropertyInspectorView;  
}  
```  
  
## <a name="using-the-rehosted-toolbox"></a><span data-ttu-id="1acbe-119">Usando a caixa de ferramentas rehosted</span><span class="sxs-lookup"><span data-stu-id="1acbe-119">Using the rehosted toolbox</span></span>  
 <span data-ttu-id="1acbe-120">Este exemplo usa o controle rehosted da caixa de ferramentas declarativamente em XAML.</span><span class="sxs-lookup"><span data-stu-id="1acbe-120">This sample uses the rehosted toolbox control declaratively in XAML.</span></span> <span data-ttu-id="1acbe-121">Observe que no código, um pode passar um tipo para o construtor de <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> .</span><span class="sxs-lookup"><span data-stu-id="1acbe-121">Note that in code, one can pass a type to the <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> constructor.</span></span>  
  
```xaml  
<!-- Copyright (c) Microsoft Corporation. All rights reserved-->  
<Window x:Class="Microsoft.Samples.DesignerRehosting.RehostingWfDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"  
        xmlns:sys="clr-namespace:System;assembly=mscorlib"  
        Title="Window1" Height="600" Width="900">  
    <Window.Resources>  
        <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>  
    </Window.Resources>  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="2*"/>  
            <ColumnDefinition Width="7*"/>  
            <ColumnDefinition Width="3*"/>  
        </Grid.ColumnDefinitions>  
        <Border Grid.Column="0">  
            <sapt:ToolboxControl>  
                <sapt:ToolboxCategory CategoryName="Basic">  
                    <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.Sequence  
                        </sapt:ToolboxItemWrapper.ToolName>  
                       </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.WriteLine  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.If  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.While  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                </sapt:ToolboxCategory>  
            </sapt:ToolboxControl>  
        </Border>  
        <Border Grid.Column="1" Name="DesignerBorder"/>  
        <Border Grid.Column="2" Name="PropertyBorder"/>  
    </Grid>  
</Window>  
```  
  
#### <a name="using-the-sample"></a><span data-ttu-id="1acbe-122">Usando o exemplo</span><span class="sxs-lookup"><span data-stu-id="1acbe-122">Using the sample</span></span>  
  
1.  <span data-ttu-id="1acbe-123">Abra a solução de DesignerRehosting.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1acbe-123">Open the DesignerRehosting.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="1acbe-124">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1acbe-124">Press F5 to compile and run the application.</span></span>  
  
3.  <span data-ttu-id="1acbe-125">Inicia de um aplicativo de WPF com um designer rehosted.</span><span class="sxs-lookup"><span data-stu-id="1acbe-125">A WPF application starts with a rehosted designer.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1acbe-126">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="1acbe-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1acbe-127">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="1acbe-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1acbe-128">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="1acbe-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1acbe-129">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="1acbe-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`