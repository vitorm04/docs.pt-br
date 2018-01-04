---
title: Associando uma propriedade personalizada de atividade a um controle de designer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e8061ea-10f5-407c-a31f-d0d74ce12f27
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79ceeb7406fdae9b4044053e12bec2aad926f26e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a><span data-ttu-id="cc201-102">Associando uma propriedade personalizada de atividade a um controle de designer</span><span class="sxs-lookup"><span data-stu-id="cc201-102">Binding a custom activity property to a designer control</span></span>
<span data-ttu-id="cc201-103">Associar um controle de designer caixa de texto para um argumento de atividade é relativamente simples; associar um controle complexo do designer (como uma caixa combo) para um argumento de atividade pode apresentar desafios, no entanto.</span><span class="sxs-lookup"><span data-stu-id="cc201-103">Binding a text box designer control to an activity argument is fairly straightforward; binding a complex designer control (such as a combo box) to an activity argument may present challenges, however.</span></span> <span data-ttu-id="cc201-104">Este tópico discute como associar um argumento de atividade a um controle caixa de combinação em um designer personalizado de atividade.</span><span class="sxs-lookup"><span data-stu-id="cc201-104">This topic discusses how to bind an activity argument to a combo box control on a custom activity designer.</span></span>  
  
#### <a name="creating-the-combo-box-item-converter"></a><span data-ttu-id="cc201-105">Criando o conversor de item da caixa de combinação</span><span class="sxs-lookup"><span data-stu-id="cc201-105">Creating the combo box item converter</span></span>  
  
1.  <span data-ttu-id="cc201-106">Crie uma nova solução vazia no Visual Studio chama CustomProperty.</span><span class="sxs-lookup"><span data-stu-id="cc201-106">Create a new empty solution in Visual Studio called CustomProperty.</span></span>  
  
2.  <span data-ttu-id="cc201-107">Crie uma nova classe chamada ComboBoxItemConverter.</span><span class="sxs-lookup"><span data-stu-id="cc201-107">Create a new class called ComboBoxItemConverter.</span></span> <span data-ttu-id="cc201-108">Adicione uma referência a System.Windows.Data, e tem a classe derivar de <xref:System.Windows.Data.IValueConverter>.</span><span class="sxs-lookup"><span data-stu-id="cc201-108">Add a reference to System.Windows.Data, and have the class derive from <xref:System.Windows.Data.IValueConverter>.</span></span> <span data-ttu-id="cc201-109">Tenha o Visual Studio fornecedores da interface para gerar stub para `Convert` e `ConvertBack`.</span><span class="sxs-lookup"><span data-stu-id="cc201-109">Have Visual Studio implement the interface to generate stubs for `Convert` and `ConvertBack`.</span></span>  
  
3.  <span data-ttu-id="cc201-110">Adicione o seguinte código ao método de `Convert` .</span><span class="sxs-lookup"><span data-stu-id="cc201-110">Add the following code to the `Convert` method.</span></span> <span data-ttu-id="cc201-111">Este código a seguir converte <xref:System.Activities.InArgument%601> de atividade do tipo <xref:System.String> para o valor a ser colocado no designer.</span><span class="sxs-lookup"><span data-stu-id="cc201-111">This code converts the activity's <xref:System.Activities.InArgument%601> of type <xref:System.String> to the value to be placed in the designer.</span></span>  
  
    ```  
    ModelItem modelItem = value as ModelItem;  
    if (value != null)  
    {  
        InArgument<string> inArgument = modelItem.GetCurrentValue() as InArgument<string>;  
  
        if (inArgument != null)  
        {  
            Activity<string> expression = inArgument.Expression;  
            VisualBasicValue<string> vbexpression = expression as VisualBasicValue<string>;  
            Literal<string> literal = expression as Literal<string>;  
  
            if (literal != null)  
            {  
                return "\"" + literal.Value + "\"";  
            }  
            else if (vbexpression != null)  
            {  
                return vbexpression.ExpressionText;  
            }  
        }  
    }  
    return null;  
    ```  
  
     <span data-ttu-id="cc201-112">A expressão no trecho de código anterior também pode ser criada usando <xref:Microsoft.CSharp.Activities.CSharpValue%601> em vez de <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span><span class="sxs-lookup"><span data-stu-id="cc201-112">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>  
  
    ```  
    ModelItem modelItem = value as ModelItem;  
    if (value != null)  
    {  
        InArgument<string> inArgument = modelItem.GetCurrentValue() as InArgument<string>;  
  
        if (inArgument != null)  
        {  
            Activity<string> expression = inArgument.Expression;  
            CSharpValue<string> csexpression = expression as CSharpValue<string>;  
            Literal<string> literal = expression as Literal<string>;  
  
            if (literal != null)  
            {  
                return "\"" + literal.Value + "\"";  
            }  
            else if (csexpression != null)  
            {  
                return csexpression.ExpressionText;  
            }  
        }  
    }  
    return null;  
    ```  
  
4.  <span data-ttu-id="cc201-113">Adicione o seguinte código ao método de `ConvertBack` .</span><span class="sxs-lookup"><span data-stu-id="cc201-113">Add the following code to the `ConvertBack` method.</span></span> <span data-ttu-id="cc201-114">Este código a seguir converte o item de entrada da caixa de combinação de volta a <xref:System.Activities.InArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="cc201-114">This code converts the incoming combo box item back to an <xref:System.Activities.InArgument%601>.</span></span>  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(vbArgument);  
                return inArgument;  
    ```  
  
     <span data-ttu-id="cc201-115">A expressão no trecho de código anterior também pode ser criada usando <xref:Microsoft.CSharp.Activities.CSharpValue%601> em vez de <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span><span class="sxs-lookup"><span data-stu-id="cc201-115">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(csArgument);  
                return inArgument;  
    ```  
  
#### <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a><span data-ttu-id="cc201-116">Adicionando o ComboBoxItemConverter o designer personalizado de uma atividade</span><span class="sxs-lookup"><span data-stu-id="cc201-116">Adding the ComboBoxItemConverter to the custom designer of an activity</span></span>  
  
1.  <span data-ttu-id="cc201-117">Adicionar um novo item ao projeto.</span><span class="sxs-lookup"><span data-stu-id="cc201-117">Add a new item to the project.</span></span> <span data-ttu-id="cc201-118">Na caixa de diálogo add new item, selecione o nó de fluxo de trabalho e selecione o designer de atividade como o tipo do novo item.</span><span class="sxs-lookup"><span data-stu-id="cc201-118">In the New Item dialog, select the Workflow node and select Activity Designer as the type of the new item.</span></span> <span data-ttu-id="cc201-119">Nomeie o item CustomPropertyDesigner.</span><span class="sxs-lookup"><span data-stu-id="cc201-119">Name the item CustomPropertyDesigner.</span></span>  
  
2.  <span data-ttu-id="cc201-120">Adicione uma caixa de combinação para o novo designer.</span><span class="sxs-lookup"><span data-stu-id="cc201-120">Add a Combo Box to the new designer.</span></span> <span data-ttu-id="cc201-121">A propriedade itens, adicione um par itens à caixa de combinação, com valores de conteúdo de “Item1” e “de” Item2.</span><span class="sxs-lookup"><span data-stu-id="cc201-121">In the Items property, add a couple of items to the combo box, with Content values of "Item1" and 'Item2".</span></span>  
  
3.  <span data-ttu-id="cc201-122">Modifique o XAML caixa de combinação para adicionar o novo conversor de item como o conversor de item a ser usado para a caixa de combinação.</span><span class="sxs-lookup"><span data-stu-id="cc201-122">Modify the XAML of the combo box to add the new item converter as the item converter to be used for the combo box.</span></span> <span data-ttu-id="cc201-123">O conversor é adicionado como um recurso no segmento de ActivityDesigner.Resources, e especifica o conversor no atributo de conversor para <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="cc201-123">The converter is added as a resource in the ActivityDesigner.Resources segment, and specifies the converter in the Converter attribute for the <xref:System.Windows.Controls.ComboBox>.</span></span> <span data-ttu-id="cc201-124">Observe que o namespace do projeto está especificada em atributos namespaces para o designer de atividade; se o designer deve ser usada em um projeto diferente, esse namespace deverá ser alterada.</span><span class="sxs-lookup"><span data-stu-id="cc201-124">Note that the namespace of the project is specified in the namespaces attributes for the activity designer; if the designer is to be used in a different project, this namespace will need to be changed.</span></span>  
  
    ```  
    <sap:ActivityDesigner x:Class="CustomProperty.CustomPropertyDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:c="clr-namespace:CustomProperty"  
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"  
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">  
  
        <sap:ActivityDesigner.Resources>  
            <ResourceDictionary>  
                <c:ComboBoxItemConverter x:Key="comboBoxItemConverter"/>  
            </ResourceDictionary>  
        </sap:ActivityDesigner.Resources>  
        <Grid>  
            <ComboBox SelectedValue="{Binding Path=ModelItem.Text, Mode=TwoWay, Converter={StaticResource comboBoxItemConverter}}"  Height="23" HorizontalAlignment="Left" Margin="132,5,0,0" Name="comboBox1" VerticalAlignment="Top" Width="120" ItemsSource="{Binding}">  
                <ComboBoxItem>item1</ComboBoxItem>  
                <ComboBoxItem>item2</ComboBoxItem>  
            </ComboBox>  
        </Grid>  
    </sap:ActivityDesigner>  
    ```  
  
4.  <span data-ttu-id="cc201-125">Crie um novo item do tipo <xref:System.Activities.CodeActivity>.</span><span class="sxs-lookup"><span data-stu-id="cc201-125">Create a new item of type <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="cc201-126">O código padrão criado pelo IDE para atividades será suficiente para esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="cc201-126">The default code created by the IDE for the activity will be sufficient for this example.</span></span>  
  
5.  <span data-ttu-id="cc201-127">Adicione o atributo a seguir para a definição de classe:</span><span class="sxs-lookup"><span data-stu-id="cc201-127">Add the following attribute to the class definition:</span></span>  
  
    ```  
    [Designer(typeof(CustomPropertyDesigner))]  
    ```  
  
     <span data-ttu-id="cc201-128">Esta linha associa o novo designer com a nova classe.</span><span class="sxs-lookup"><span data-stu-id="cc201-128">This line associates the new designer with the new class.</span></span>  
  
 <span data-ttu-id="cc201-129">A nova atividade agora deve ser associada com o designer.</span><span class="sxs-lookup"><span data-stu-id="cc201-129">The new activity should now be associated with the designer.</span></span> <span data-ttu-id="cc201-130">Para testar a nova atividade, adicioná-lo a um fluxo de trabalho, e defina a caixa de combinação para dois valores.</span><span class="sxs-lookup"><span data-stu-id="cc201-130">To test the new activity, add it to a workflow, and set the combo box to the two values.</span></span> <span data-ttu-id="cc201-131">A janela propriedades deve atualizar para refletir o valor de caixa combo.</span><span class="sxs-lookup"><span data-stu-id="cc201-131">The properties window should update to reflect the combo box value.</span></span>
