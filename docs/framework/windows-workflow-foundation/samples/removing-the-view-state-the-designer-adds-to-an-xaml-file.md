---
title: Removendo o estado de exibição que o designer adiciona a um arquivo XAML – WF
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: f431275140e821aa5ec4d2235322f06be87d5ee2
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715618"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a><span data-ttu-id="c4a20-102">Removendo o estado de exibição que o designer adiciona a um arquivo XAML</span><span class="sxs-lookup"><span data-stu-id="c4a20-102">Removing the view state the designer adds to an XAML file</span></span>

<span data-ttu-id="c4a20-103">Este exemplo demonstra como criar uma classe que deriva de <xref:System.Xaml.XamlWriter> e se remova o modo estado de um arquivo XAML.</span><span class="sxs-lookup"><span data-stu-id="c4a20-103">This sample demonstrates how to create a class that derives from <xref:System.Xaml.XamlWriter> and removes view state from a XAML file.</span></span> <span data-ttu-id="c4a20-104">O Windows Designer de Fluxo de Trabalho grava informações no documento XAML, que é conhecido como estado de exibição.</span><span class="sxs-lookup"><span data-stu-id="c4a20-104">Windows Workflow Designer writes information into the XAML document, which is known as view state.</span></span> <span data-ttu-id="c4a20-105">O estado de exibição se refere à informação que é necessária em tempo de design, como o posicionamento de layout, que não é necessário em runtime.</span><span class="sxs-lookup"><span data-stu-id="c4a20-105">View state refers to the information that is required at design time, such as layout positioning, that is not required at runtime.</span></span> <span data-ttu-id="c4a20-106">Designer de Fluxo de Trabalho insere essas informações no documento XAML conforme ele é editado.</span><span class="sxs-lookup"><span data-stu-id="c4a20-106">Workflow Designer inserts this information into the XAML document as it is edited.</span></span> <span data-ttu-id="c4a20-107">Designer de Fluxo de Trabalho grava o estado de exibição no arquivo XAML com o atributo `mc:Ignorable`, portanto, essas informações não são carregadas quando o tempo de execução carrega o arquivo XAML.</span><span class="sxs-lookup"><span data-stu-id="c4a20-107">Workflow Designer writes the view state into the XAML file with the `mc:Ignorable` attribute, so this information is not loaded when the runtime loads the XAML file.</span></span> <span data-ttu-id="c4a20-108">Este exemplo demonstra como criar uma classe que remove essas informações de estado de exibição ao processar nós XAML.</span><span class="sxs-lookup"><span data-stu-id="c4a20-108">This sample demonstrates how to create a class that removes that view state information while processing XAML nodes.</span></span>

## <a name="discussion"></a><span data-ttu-id="c4a20-109">Discussão</span><span class="sxs-lookup"><span data-stu-id="c4a20-109">Discussion</span></span>

<span data-ttu-id="c4a20-110">Este exemplo demonstra como criar um text writer personalizado.</span><span class="sxs-lookup"><span data-stu-id="c4a20-110">This sample demonstrates how to create a custom writer.</span></span>

<span data-ttu-id="c4a20-111">Para criar um text writer personalizado XAML, crie uma classe que herda de <xref:System.Xaml.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="c4a20-111">To build a custom XAML writer, create a class that inherits from <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="c4a20-112">Como os gravadores XAML geralmente são aninhados, é comum manter o controle de um gravador XAML "interno".</span><span class="sxs-lookup"><span data-stu-id="c4a20-112">As XAML writers are often nested, it is typical to keep track of an "inner" XAML writer.</span></span> <span data-ttu-id="c4a20-113">Esses gravadores "internos" podem ser considerados como referência à pilha restante de gravadores XAML, permitindo que você tenha vários pontos de entrada para realizar o trabalho e, em seguida, delegue o processamento para o restante da pilha.</span><span class="sxs-lookup"><span data-stu-id="c4a20-113">These "inner’ writers can be thought of as the reference to the remaining stack of XAML writers, allowing you to have multiple entry points to do work and then delegate processing to the remainder of the stack.</span></span>

<span data-ttu-id="c4a20-114">Nesse exemplo, há alguns itens de interesse.</span><span class="sxs-lookup"><span data-stu-id="c4a20-114">In this sample, there are a few items of interest.</span></span> <span data-ttu-id="c4a20-115">Um é a verifique se o item que está sendo gravada for um namespace de designer.</span><span class="sxs-lookup"><span data-stu-id="c4a20-115">One is the check to see whether the item being written is from a designer namespace.</span></span> <span data-ttu-id="c4a20-116">Observe que isso também tira para fora o uso de outros tipos de namespace de designer em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c4a20-116">Note that this also strips out the use of other types from the designer namespace in a workflow.</span></span>

```csharp
static Boolean IsDesignerAttachedProperty(XamlMember xamlMember)
{
    return xamlMember.IsAttachable &&
        xamlMember.PreferredXamlNamespace.Equals(c_sapNamespaceURI, StringComparison.OrdinalIgnoreCase);
}

const String c_sapNamespaceURI = "http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation";

// The next item of interest is the constructor, where the utilization of the inner XAML writer is seen.
public ViewStateCleaningWriter(XamlWriter innerWriter)
{
    this.InnerWriter = innerWriter;
    this.MemberStack = new Stack<XamlMember>();
}

XamlWriter InnerWriter {get; set; }
Stack<XamlMember> MemberStack {get; set; }
```

<span data-ttu-id="c4a20-117">Isso também cria uma pilha de membros XAML que são usados para atravessar o fluxo de nó.</span><span class="sxs-lookup"><span data-stu-id="c4a20-117">This also creates a stack of XAML members that are used while traversing the node stream.</span></span> <span data-ttu-id="c4a20-118">O trabalho restante deste exemplo é contido amplamente no método de `WriteStartMember` .</span><span class="sxs-lookup"><span data-stu-id="c4a20-118">The remaining work of this sample is largely contained in the `WriteStartMember` method.</span></span>

```csharp
public override void WriteStartMember(XamlMember xamlMember)
{
    MemberStack.Push(xamlMember);

    if (IsDesignerAttachedProperty(xamlMember))
    {
        m_attachedPropertyDepth++;
    }

    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteStartMember(xamlMember);
}
```

<span data-ttu-id="c4a20-119">Os métodos subsequentes verifique para ver se ainda estão contidos em um recipiente de estado de exibição, e em caso afirmativo, retorno, e não passam o nó abaixo da pilha o gravador.</span><span class="sxs-lookup"><span data-stu-id="c4a20-119">Subsequent methods then check to see whether they are still contained in a view state container, and if so, return, and do not pass the node down the writer stack.</span></span>

```csharp
public override void WriteValue(Object value)
{
    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteValue(value);
}
```

<span data-ttu-id="c4a20-120">Para usar um text writer personalizado XAML, você deve encadear-la juntos em uma pilha de criadores de XAML.</span><span class="sxs-lookup"><span data-stu-id="c4a20-120">To use a custom XAML writer, you must chain it together in a stack of XAML writers.</span></span> <span data-ttu-id="c4a20-121">O código a seguir mostra como esse pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="c4a20-121">The following code shows how this can be used.</span></span>

```csharp
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);
```

## <a name="to-use-this-sample"></a><span data-ttu-id="c4a20-122">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="c4a20-122">To use this sample</span></span>

1. <span data-ttu-id="c4a20-123">Usando o Visual Studio 2010, abra o arquivo de solução ViewStateCleaningWriter. sln.</span><span class="sxs-lookup"><span data-stu-id="c4a20-123">Using Visual Studio 2010, open the ViewStateCleaningWriter.sln solution file.</span></span>

2. <span data-ttu-id="c4a20-124">Abra um prompt de comando e navegue para o diretório onde o ViewStageCleaningWriter.exe é criado.</span><span class="sxs-lookup"><span data-stu-id="c4a20-124">Open a command prompt and navigate to the directory where the ViewStageCleaningWriter.exe is built.</span></span>

3. <span data-ttu-id="c4a20-125">Executar ViewStateCleaningWriter.exe no arquivo de Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="c4a20-125">Run ViewStateCleaningWriter.exe on the Workflow1.xaml file.</span></span>

   <span data-ttu-id="c4a20-126">A sintaxe para o arquivo executável é mostrada no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c4a20-126">The syntax for the executable is shown in the following example.</span></span>

   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```

   <span data-ttu-id="c4a20-127">Isso gera um arquivo XAML para \[outfile], que tem todas as informações de estado de exibição removidas.</span><span class="sxs-lookup"><span data-stu-id="c4a20-127">This outputs a XAML file to \[outfile], which has all its view state information removed.</span></span>

> [!NOTE]
> <span data-ttu-id="c4a20-128">Para um fluxo de trabalho <xref:System.Activities.Statements.Sequence> , um número de dicas de virtualização são removidos.</span><span class="sxs-lookup"><span data-stu-id="c4a20-128">For a <xref:System.Activities.Statements.Sequence> workflow, a number of virtualization hints are removed.</span></span> <span data-ttu-id="c4a20-129">Isso faz com que o designer recalcule o layout na próxima vez que é carregado.</span><span class="sxs-lookup"><span data-stu-id="c4a20-129">This causes the designer to recalculate layout the next time it is loaded.</span></span> <span data-ttu-id="c4a20-130">Quando você usa este exemplo para <xref:System.Activities.Statements.Flowchart>, qualquer posicionamento e linha informações de roteamento são removidos e a carga subsequente no designer, todas as atividades são empilhadas no lado esquerdo da tela.</span><span class="sxs-lookup"><span data-stu-id="c4a20-130">When you use this sample for a <xref:System.Activities.Statements.Flowchart>, all positioning and line routing information are removed and on subsequent loading into the designer, all activities are stacked on the left side of the screen.</span></span>

## <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a><span data-ttu-id="c4a20-131">Para criar um arquivo XAML exemplo para uso com esse exemplo</span><span class="sxs-lookup"><span data-stu-id="c4a20-131">To create a sample XAML file for use with this sample</span></span>

1. <span data-ttu-id="c4a20-132">Abra o Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="c4a20-132">Open Visual Studio 2010.</span></span>

2. <span data-ttu-id="c4a20-133">Criar um novo aplicativo de console do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c4a20-133">Create a new Workflow Console Application.</span></span>

3. <span data-ttu-id="c4a20-134">Arrastar e soltar quaisquer atividades na tela</span><span class="sxs-lookup"><span data-stu-id="c4a20-134">Drag and drop a few activities onto the canvas</span></span>

4. <span data-ttu-id="c4a20-135">Salve o arquivo de fluxo de trabalho XAML.</span><span class="sxs-lookup"><span data-stu-id="c4a20-135">Save the workflow XAML file.</span></span>

5. <span data-ttu-id="c4a20-136">Inspecione o arquivo XAML para ver as propriedades anexadas do estado de exibição.</span><span class="sxs-lookup"><span data-stu-id="c4a20-136">Inspect the XAML file to see the view state attached properties.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c4a20-137">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="c4a20-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c4a20-138">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="c4a20-138">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="c4a20-139">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="c4a20-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c4a20-140">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="c4a20-140">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
