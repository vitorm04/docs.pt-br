---
title: Árvore modelo de programação de item
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: f2d89cb2a3b0f6167f043148ea793ec1c264a556
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038181"
---
# <a name="programming-model-item-tree"></a><span data-ttu-id="6eed3-102">Árvore modelo de programação de item</span><span class="sxs-lookup"><span data-stu-id="6eed3-102">Programming Model Item Tree</span></span>
<span data-ttu-id="6eed3-103">Este exemplo demonstra como navegar na <xref:System.Activities.Presentation.Model.ModelItem> árvore usando a associação de dados declarativa da exibição de árvore Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="6eed3-103">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the Windows Presentation Foundation (WPF) Tree View.</span></span>

## <a name="sample-details"></a><span data-ttu-id="6eed3-104">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="6eed3-104">Sample Details</span></span>
 <span data-ttu-id="6eed3-105">A árvore de <xref:System.Activities.Presentation.Model.ModelItem> é a abstração que é usada pela infraestrutura de [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] para expor os dados sobre a instância subjacente que está sendo editada.</span><span class="sxs-lookup"><span data-stu-id="6eed3-105">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="6eed3-106">A ilustração a seguir é uma descrição das várias camadas de infraestrutura dentro de [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6eed3-106">The following illustration is a depiction of the various layers of infrastructure within the [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span>

 ![Diagrama que mostra a arquitetura de Designer de Fluxo de Trabalho.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <span data-ttu-id="6eed3-108"><xref:System.Activities.Presentation.Model.ModelItem> consiste em um ponteiro para o valor subjacente, bem como uma coleção de objetos <xref:System.Activities.Presentation.Model.ModelProperty> .</span><span class="sxs-lookup"><span data-stu-id="6eed3-108">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="6eed3-109">Um objeto de <xref:System.Activities.Presentation.Model.ModelProperty> por sua vez, consiste dados como nome e tipo da propriedade e então um ponteiro para o valor que, por sua vez, é outro <xref:System.Activities.Presentation.Model.ModelItem>.</span><span class="sxs-lookup"><span data-stu-id="6eed3-109">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="6eed3-110">Um conversor de valor é usado para manipular qualquer um de <xref:System.Activities.Presentation.Model.ModelItem>s retornado de <xref:System.Activities.Presentation.Model.ModelProperty> para fazê-lo aparecer corretamente no modo de exibição de árvore.</span><span class="sxs-lookup"><span data-stu-id="6eed3-110">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="6eed3-111">O exemplo demonstra como programar em imperativa contra a árvore de <xref:System.Activities.Presentation.Model.ModelItem> usando a sintaxe imperativa, como visto no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6eed3-111">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="6eed3-112">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="6eed3-112">To use this sample</span></span>

1. <span data-ttu-id="6eed3-113">Abra a solução ProgrammingModelItemTree. sln no Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="6eed3-113">Open the ProgrammingModelItemTree.sln solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="6eed3-114">Crie a solução selecionando **Compilar solução** no menu **Compilar** .</span><span class="sxs-lookup"><span data-stu-id="6eed3-114">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>

3. <span data-ttu-id="6eed3-115">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6eed3-115">Press F5 to run the application.</span></span> <span data-ttu-id="6eed3-116">Em seguida, o formulário do WPF é exibido.</span><span class="sxs-lookup"><span data-stu-id="6eed3-116">The WPF form is then displayed.</span></span>

4. <span data-ttu-id="6eed3-117">Clique no botão **carregar o WF** para carregar <xref:System.Activities.Presentation.Model.ModelItem> o e associá-lo ao modo de exibição de árvore.</span><span class="sxs-lookup"><span data-stu-id="6eed3-117">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>

5. <span data-ttu-id="6eed3-118">Clicar no botão **alterar árvore do item do modelo** executa o código anterior para adicionar um item à árvore e definir uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="6eed3-118">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6eed3-119">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="6eed3-119">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6eed3-120">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="6eed3-120">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="6eed3-121">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="6eed3-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6eed3-122">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="6eed3-122">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="6eed3-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6eed3-123">See also</span></span>

- <xref:System.Windows.Data.IValueConverter>
