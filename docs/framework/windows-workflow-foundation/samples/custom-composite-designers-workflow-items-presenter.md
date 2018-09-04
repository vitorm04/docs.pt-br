---
title: Designer de compostos personalizados - apresentador de itens de fluxo de trabalho
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
ms.openlocfilehash: 708b62290900db3e668de81c31f3a1dc85eb6d19
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528930"
---
# <a name="custom-composite-designers---workflow-items-presenter"></a><span data-ttu-id="56e6b-102">Designer de compostos personalizados - apresentador de itens de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="56e6b-102">Custom Composite Designers - Workflow Items Presenter</span></span>
<span data-ttu-id="56e6b-103"><xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> é um principal no modelo de programação do designer de WF que permite a edição de uma coleção de elementos contidos.</span><span class="sxs-lookup"><span data-stu-id="56e6b-103">The <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> is a key type in the WF designer programming model that allows for the editing of a collection of contained elements.</span></span> <span data-ttu-id="56e6b-104">Este exemplo mostra como criar um designer de atividade que surija uma coleção tão editável.</span><span class="sxs-lookup"><span data-stu-id="56e6b-104">This sample shows how to build an activity designer that surfaces such an editable collection.</span></span>  
  
 <span data-ttu-id="56e6b-105">Este exemplo demonstra:</span><span class="sxs-lookup"><span data-stu-id="56e6b-105">This sample demonstrates:</span></span>  
  
-   <span data-ttu-id="56e6b-106">Criando um designer personalizado de atividade com <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="56e6b-106">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="56e6b-107">Criando um designer de atividade com um modo de exibição "recolheu" e "expandiu".</span><span class="sxs-lookup"><span data-stu-id="56e6b-107">Creating an activity designer with a "collapsed" and "expanded" view.</span></span>  
  
-   <span data-ttu-id="56e6b-108">Substituindo um designer padrão em um aplicativo rehosted.</span><span class="sxs-lookup"><span data-stu-id="56e6b-108">Overriding a default designer in a rehosted application.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="56e6b-109">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="56e6b-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="56e6b-110">Abra o **Usingworkflowitemspresenter** solução de exemplo para c# ou VB no [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56e6b-110">Open the **UsingWorkflowItemsPresenter.sln** sample solution for C# or for VB in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="56e6b-111">Criar e executar a solução.</span><span class="sxs-lookup"><span data-stu-id="56e6b-111">Build and run the solution.</span></span> <span data-ttu-id="56e6b-112">Um aplicativo rehosted de designer de fluxo de trabalho deve abrir, e você pode arrastar atividades na tela.</span><span class="sxs-lookup"><span data-stu-id="56e6b-112">A rehosted workflow designer application should open, and you can drag activities onto the canvas.</span></span>  
  
## <a name="sample-highlights"></a><span data-ttu-id="56e6b-113">Realces de exemplo</span><span class="sxs-lookup"><span data-stu-id="56e6b-113">Sample Highlights</span></span>  
 <span data-ttu-id="56e6b-114">O código para esse exemplo mostra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="56e6b-114">The code for this sample shows the following:</span></span>  
  
-   <span data-ttu-id="56e6b-115">A atividade um designer é compilada para:  `Parallel`</span><span class="sxs-lookup"><span data-stu-id="56e6b-115">The activity a designer is built for:  `Parallel`</span></span>  
  
-   <span data-ttu-id="56e6b-116">A criação de um designer personalizado de atividade com <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="56e6b-116">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span> <span data-ttu-id="56e6b-117">Algumas coisas para indicar:</span><span class="sxs-lookup"><span data-stu-id="56e6b-117">A few things to point out:</span></span>  
  
    -   <span data-ttu-id="56e6b-118">Observe o uso de associação de dados de WPF associar a `ModelItem.Branches`.</span><span class="sxs-lookup"><span data-stu-id="56e6b-118">Note the use of WPF data binding to bind to `ModelItem.Branches`.</span></span> <span data-ttu-id="56e6b-119">`ModelItem` é a propriedade em `WorkflowElementDesigner` que refere-se ao objeto subjacente que o designer está sendo usado para, nesse caso, nosso `Parallel`.</span><span class="sxs-lookup"><span data-stu-id="56e6b-119">`ModelItem` is the property on `WorkflowElementDesigner` that refers to the underlying object the designer is being used for, in this case, our `Parallel`.</span></span>  
  
    -   <span data-ttu-id="56e6b-120"><xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> pode ser usado para colocar um visual para exibir entre os itens individuais na coleção.</span><span class="sxs-lookup"><span data-stu-id="56e6b-120">The <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> can be used to put a visual to display between the individual items in the collection.</span></span>  
  
    -   <span data-ttu-id="56e6b-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> é um modelo que pode ser fornecido para determinar o layout dos itens na coleção.</span><span class="sxs-lookup"><span data-stu-id="56e6b-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> is a template that can be provided to determine the layout of the items in the collection.</span></span> <span data-ttu-id="56e6b-122">Nesse caso, um painel horizontal de pilha é usado.</span><span class="sxs-lookup"><span data-stu-id="56e6b-122">In this case, a horizontal stack panel is used.</span></span>  
  
 <span data-ttu-id="56e6b-123">Esse código de exemplo a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="56e6b-123">This following example code shows this.</span></span>  
  
```xaml  
<sad:WorkflowItemsPresenter HintText="Drop Activities Here"  
                              Items="{Binding Path=ModelItem.Branches}">  
    <sad:WorkflowItemsPresenter.SpacerTemplate>  
      <DataTemplate>  
        <Ellipse Width="10" Height="10" Fill="Black"/>  
      </DataTemplate>  
    </sad:WorkflowItemsPresenter.SpacerTemplate>  
    <sad:WorkflowItemsPresenter.ItemsPanel>  
      <ItemsPanelTemplate>  
        <StackPanel Orientation="Horizontal"/>  
      </ItemsPanelTemplate>  
    </sad:WorkflowItemsPresenter.ItemsPanel>  
  </sad:WorkflowItemsPresenter>  
```  
  
-   <span data-ttu-id="56e6b-124">Executar uma associação de `DesignerAttribute` para o tipo de `Parallel` e então saída que atributos relataram.</span><span class="sxs-lookup"><span data-stu-id="56e6b-124">Perform an association of the `DesignerAttribute` to the `Parallel` type and then output the attributes reported.</span></span>  
  
    -   <span data-ttu-id="56e6b-125">Primeiro, para todos os designers padrão.</span><span class="sxs-lookup"><span data-stu-id="56e6b-125">First, register all of the default designers.</span></span>  
  
 <span data-ttu-id="56e6b-126">A seguir está o exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="56e6b-126">The following is the code example.</span></span>  
  
```csharp  
// register metadata  
(new DesignerMetadata()).Register();  
RegisterCustomMetadata();  
```  
  
```vb  
' register metadata  
Dim metadata = New DesignerMetadata()  
metadata.Register()  
' register custom metadata  
RegisterCustomMetadata()  
```  
  
    -   <span data-ttu-id="56e6b-127">Em seguida, substituir a paralela no método de `RegisterCustomMetadata` .</span><span class="sxs-lookup"><span data-stu-id="56e6b-127">Then, override the parallel in `RegisterCustomMetadata` method.</span></span>  
  
 <span data-ttu-id="56e6b-128">O código a seguir mostra esse em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="56e6b-128">The following code shows this in C# and Visual Basic.</span></span>  
 
```csharp  
void RegisterCustomMetadata()  
{  
      AttributeTableBuilder builder = new AttributeTableBuilder();  
      builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));  
      MetadataStore.AddAttributeTable(builder.CreateTable());  
}  
```  
  
```vb  
Sub RegisterCustomMetadata()  
   Dim builder As New AttributeTableBuilder()  
   builder.AddCustomAttributes(GetType(Parallel), New DesignerAttribute(GetType(CustomParallelDesigner)))  
   MetadataStore.AddAttributeTable(builder.CreateTable())  
End Sub  
```  
  
-   <span data-ttu-id="56e6b-129">Finalmente, observe o uso de modelos e disparadores de diferentes de dados selecione o modelo apropriado com base na propriedade de `IsRootDesigner` .</span><span class="sxs-lookup"><span data-stu-id="56e6b-129">Finally, note the use of differing data templates and triggers to select the appropriate template based on the `IsRootDesigner` property.</span></span>  
  
 <span data-ttu-id="56e6b-130">A seguir está o exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="56e6b-130">The following is the code example.</span></span>  
  
```xaml  
<sad:ActivityDesigner x:Class="Microsoft.Samples.CustomParallelDesigner"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:sad="clr-namespace:System.Activities.Design;assembly=System.Activities.Design"  
    xmlns:sadv="clr-namespace:System.Activities.Design.View;assembly=System.Activities.Design">  
  <sad:ActivityDesigner.Resources>  
    <DataTemplate x:Key="Expanded">  
      <StackPanel>  
        <TextBlock>This is the Expanded View</TextBlock>  
        <sad:WorkflowItemsPresenter HintText="Drop Activities Here"  
                                    Items="{Binding Path=ModelItem.Branches}">  
          <sad:WorkflowItemsPresenter.SpacerTemplate>  
            <DataTemplate>  
              <Ellipse Width="10" Height="10" Fill="Black"/>  
            </DataTemplate>  
          </sad:WorkflowItemsPresenter.SpacerTemplate>  
          <sad:WorkflowItemsPresenter.ItemsPanel>  
            <ItemsPanelTemplate>  
              <StackPanel Orientation="Horizontal"/>  
            </ItemsPanelTemplate>  
          </sad:WorkflowItemsPresenter.ItemsPanel>  
        </sad:WorkflowItemsPresenter>  
      </StackPanel>  
    </DataTemplate>  
    <DataTemplate x:Key="Collapsed">  
      <TextBlock>This is the Collapsed View</TextBlock>  
    </DataTemplate>  
    <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">  
      <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>  
      <Style.Triggers>  
        <DataTrigger Binding="{Binding Path=IsRootDesigner}" Value="true">  
          <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>  
        </DataTrigger>  
      </Style.Triggers>  
    </Style>  
  </sad: ActivityDesigner.Resources>  
  <Grid>  
    <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>  
  </Grid>  
</sad: ActivityDesigner>  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="56e6b-131">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="56e6b-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="56e6b-132">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="56e6b-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="56e6b-133">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="56e6b-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="56e6b-134">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="56e6b-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`  
  
## <a name="see-also"></a><span data-ttu-id="56e6b-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56e6b-135">See Also</span></span>  
 <xref:System.Activities.Presentation.WorkflowItemsPresenter>  
 [<span data-ttu-id="56e6b-136">Desenvolvendo aplicativos com o Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="56e6b-136">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
