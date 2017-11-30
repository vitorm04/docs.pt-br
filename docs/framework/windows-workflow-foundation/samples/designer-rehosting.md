---
title: Designer ReHosting
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 888282d10be9840817274e0fed36b3cb1cf6da32
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="designer-rehosting"></a>Designer ReHosting
O designer que rehosting é um cenário comum que se refere hospedar a tela de design de fluxo de trabalho em um aplicativo personalizado. O aplicativo que hospedando a maioria de pessoas estão familiarizados com é Visual Studio entanto, há um número de cenários onde mostrar o designer de fluxo de trabalho em um aplicativo pode ser útil:  
  
-   Monitorando aplicativos (que permitem que um usuário final visualizem o processo, bem como os dados em tempo de execução sobre o processo como o estado atualmente ativa, os dados agregados de tempo de execução, ou outras informações sobre uma instância de fluxo de trabalho).  
  
-   Aplicativos que permitem que um usuário personalizar o processo com um conjunto limitado de atividades.  
  
 Para oferecer suporte a esses tipos de aplicativos, os vem do designer de fluxo de trabalho dentro do .NET Framework, e podem ser hospedados em um aplicativo de WPF, ou em um aplicativo de WinForms com WPF apropriado que hospeda o código. Este exemplo demonstra:  
  
-   Rehosting o designer de WF.  
  
-   Usando a caixa de ferramentas e a grade rehosted de propriedade também.  
  
## <a name="rehosting-the-designer"></a>Rehosting o designer  
 Este exemplo mostra como criar o layout de WPF para conter o designer, mostrado no seguinte layout de grade (código da caixa de ferramentas omitido para interesses de espaço). Observe a nomeação das bordas que contêm o designer e a grade de propriedade.  
  
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
  
 Em seguida o exemplo cria o designer, e associa os <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> e <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> principais com o recipiente apropriado na interface do usuário. Há algumas linhas de código adicionais no exemplo a seguir merecem que alguma explicação. A chamada de <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> é necessário associar os designers padrão de atividade para as atividades enviados com [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. <xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> é chamado para passar no item de WF a ser editado. Finalmente, <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (canvas primária) e <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (grade de propriedade) são colocados na superfície de interface do usuário.  
  
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
  
## <a name="using-the-rehosted-toolbox"></a>Usando a caixa de ferramentas rehosted  
 Este exemplo usa o controle rehosted da caixa de ferramentas declarativamente em XAML. Observe que no código, um pode passar um tipo para o construtor de <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> .  
  
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
  
#### <a name="using-the-sample"></a>Usando o exemplo  
  
1.  Abra a solução de DesignerRehosting.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Pressione F5 para compilar e executar o aplicativo.  
  
3.  Inicia de um aplicativo de WPF com um designer rehosted.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`  
  
## <a name="see-also"></a>Consulte também
