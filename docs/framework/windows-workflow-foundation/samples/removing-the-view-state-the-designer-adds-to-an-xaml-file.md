---
title: "Removendo o estado de exibição o designer adiciona a um Arquivo XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d9f153d212e1180e5de92a6299d2fbb2d6864c42
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a><span data-ttu-id="e3783-102">Removendo o estado de exibição o designer adiciona a um Arquivo XAML</span><span class="sxs-lookup"><span data-stu-id="e3783-102">Removing the View State the Designer Adds to an XAML File</span></span>
<span data-ttu-id="e3783-103">Este exemplo demonstra como criar uma classe que deriva de <xref:System.Windows.Markup.XamlWriter> e se remova o modo estado de um arquivo XAML.</span><span class="sxs-lookup"><span data-stu-id="e3783-103">This sample demonstrates how to create a class that derives from <xref:System.Windows.Markup.XamlWriter> and removes view state from a XAML file.</span></span> [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)]<span data-ttu-id="e3783-104"> grava informações no documento XAML, que é conhecido como o estado de exibição.</span><span class="sxs-lookup"><span data-stu-id="e3783-104"> writes information into the XAML document, which is known as view state.</span></span> <span data-ttu-id="e3783-105">O estado de exibição se refere à informação que é necessária em tempo de design, como o posicionamento de layout, que não é necessário em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e3783-105">View state refers to the information that is required at design time, such as layout positioning, that is not required at runtime.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]<span data-ttu-id="e3783-106"> insere essas informações no documento XAML que é editado.</span><span class="sxs-lookup"><span data-stu-id="e3783-106"> inserts this information into the XAML document as it is edited.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]<span data-ttu-id="e3783-107"> grava o estado de exibição no arquivo XAML com o atributo de `mc:Ignorable` , o que essa informação não é carregada quando o tempo de execução carrega o arquivo XAML.</span><span class="sxs-lookup"><span data-stu-id="e3783-107"> writes the view state into the XAML file with the `mc:Ignorable` attribute, so this information is not loaded when the runtime loads the XAML file.</span></span> <span data-ttu-id="e3783-108">Este exemplo demonstra como criar uma classe que remove essas informações de estado de exibição ao processar nós XAML.</span><span class="sxs-lookup"><span data-stu-id="e3783-108">This sample demonstrates how to create a class that removes that view state information while processing XAML nodes.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="e3783-109">Discussão</span><span class="sxs-lookup"><span data-stu-id="e3783-109">Discussion</span></span>  
 <span data-ttu-id="e3783-110">Este exemplo demonstra como criar um text writer personalizado.</span><span class="sxs-lookup"><span data-stu-id="e3783-110">This sample demonstrates how to create a custom writer.</span></span>  
  
 <span data-ttu-id="e3783-111">Para criar um text writer personalizado XAML, crie uma classe que herda de <xref:System.Windows.Markup.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="e3783-111">To build a custom XAML writer, create a class that inherits from <xref:System.Windows.Markup.XamlWriter>.</span></span> <span data-ttu-id="e3783-112">Conforme os gravadores XAML são geralmente aninhados, é comum para controlar um gravador XAML "interno".</span><span class="sxs-lookup"><span data-stu-id="e3783-112">As XAML writers are often nested, it is typical to keep track of an "inner" XAML writer.</span></span> <span data-ttu-id="e3783-113">Esses "interna ' gravadores podem ser pensados como referência para a pilha restante de gravadores XAML, permitindo que você tenha vários pontos de entrada para trabalhar e, então, delegar o processamento para o restante da pilha.</span><span class="sxs-lookup"><span data-stu-id="e3783-113">These "inner’ writers can be thought of as the reference to the remaining stack of XAML writers, allowing you to have multiple entry points to do work and then delegate processing to the remainder of the stack.</span></span>  
  
 <span data-ttu-id="e3783-114">Nesse exemplo, há alguns itens de interesse.</span><span class="sxs-lookup"><span data-stu-id="e3783-114">In this sample, there are a few items of interest.</span></span> <span data-ttu-id="e3783-115">Um é a verifique se o item que está sendo gravada for um namespace de designer.</span><span class="sxs-lookup"><span data-stu-id="e3783-115">One is the check to see whether the item being written is from a designer namespace.</span></span> <span data-ttu-id="e3783-116">Observe que isso também tira para fora o uso de outros tipos de namespace de designer em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e3783-116">Note that this also strips out the use of other types from the designer namespace in a workflow.</span></span>  
  
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
  
 <span data-ttu-id="e3783-117">Isso também cria uma pilha de membros XAML que são usados para atravessar o fluxo de nó.</span><span class="sxs-lookup"><span data-stu-id="e3783-117">This also creates a stack of XAML members that are used while traversing the node stream.</span></span> <span data-ttu-id="e3783-118">Basicamente, o trabalho restante deste exemplo está contido no <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` método.</span><span class="sxs-lookup"><span data-stu-id="e3783-118">The remaining work of this sample is largely contained in the <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` method.</span></span>  
  
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
  
 <span data-ttu-id="e3783-119">Os métodos subsequentes verifique para ver se ainda estão contidos em um recipiente de estado de exibição, e em caso afirmativo, retorno, e não passam o nó abaixo da pilha o gravador.</span><span class="sxs-lookup"><span data-stu-id="e3783-119">Subsequent methods then check to see whether they are still contained in a view state container, and if so, return, and do not pass the node down the writer stack.</span></span>  
  
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
  
 <span data-ttu-id="e3783-120">Para usar um text writer personalizado XAML, você deve encadear-la juntos em uma pilha de criadores de XAML.</span><span class="sxs-lookup"><span data-stu-id="e3783-120">To use a custom XAML writer, you must chain it together in a stack of XAML writers.</span></span> <span data-ttu-id="e3783-121">O código a seguir mostra como esse pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="e3783-121">The following code shows how this can be used.</span></span>  
  
```csharp 
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };  
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);  
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());  
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="e3783-122">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="e3783-122">To use this sample</span></span>  
  
1. <span data-ttu-id="e3783-123">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de ViewStateCleaningWriter.sln.</span><span class="sxs-lookup"><span data-stu-id="e3783-123">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ViewStateCleaningWriter.sln solution file.</span></span>  
  
2. <span data-ttu-id="e3783-124">Abra um prompt de comando e navegue para o diretório onde o ViewStageCleaningWriter.exe é criado.</span><span class="sxs-lookup"><span data-stu-id="e3783-124">Open a command prompt and navigate to the directory where the ViewStageCleaningWriter.exe is built.</span></span>  
  
3. <span data-ttu-id="e3783-125">Executar ViewStateCleaningWriter.exe no arquivo de Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="e3783-125">Run ViewStateCleaningWriter.exe on the Workflow1.xaml file.</span></span>  

   <span data-ttu-id="e3783-126">A sintaxe para o arquivo executável é mostrada no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e3783-126">The syntax for the executable is shown in the following example.</span></span>  
  
   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```
   
   <span data-ttu-id="e3783-127">Isso gera um arquivo XAML para \[outfile], que tem todas as suas informações de estado de exibição removidas.</span><span class="sxs-lookup"><span data-stu-id="e3783-127">This outputs a XAML file to \[outfile], which has all its view state information removed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3783-128">Para um fluxo de trabalho <xref:System.Activities.Statements.Sequence> , um número de dicas de virtualização são removidos.</span><span class="sxs-lookup"><span data-stu-id="e3783-128">For a <xref:System.Activities.Statements.Sequence> workflow, a number of virtualization hints are removed.</span></span> <span data-ttu-id="e3783-129">Isso faz com que o designer recalcule o layout na próxima vez que é carregado.</span><span class="sxs-lookup"><span data-stu-id="e3783-129">This causes the designer to recalculate layout the next time it is loaded.</span></span> <span data-ttu-id="e3783-130">Quando você usa este exemplo para <xref:System.Activities.Statements.Flowchart>, qualquer posicionamento e linha informações de roteamento são removidos e a carga subsequente no designer, todas as atividades são empilhadas no lado esquerdo da tela.</span><span class="sxs-lookup"><span data-stu-id="e3783-130">When you use this sample for a <xref:System.Activities.Statements.Flowchart>, all positioning and line routing information are removed and on subsequent loading into the designer, all activities are stacked on the left side of the screen.</span></span>  
  
#### <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a><span data-ttu-id="e3783-131">Para criar um arquivo XAML exemplo para uso com esse exemplo</span><span class="sxs-lookup"><span data-stu-id="e3783-131">To create a sample XAML file for use with this sample</span></span>  
  
1. <span data-ttu-id="e3783-132">Abra [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3783-132">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2. <span data-ttu-id="e3783-133">Criar um novo aplicativo de console do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e3783-133">Create a new Workflow Console Application.</span></span>  
  
3. <span data-ttu-id="e3783-134">Arrastar e soltar quaisquer atividades na tela</span><span class="sxs-lookup"><span data-stu-id="e3783-134">Drag and drop a few activities onto the canvas</span></span>  
  
4. <span data-ttu-id="e3783-135">Salve o arquivo de fluxo de trabalho XAML.</span><span class="sxs-lookup"><span data-stu-id="e3783-135">Save the workflow XAML file.</span></span>  
  
5. <span data-ttu-id="e3783-136">Inspecione o arquivo XAML para ver as propriedades anexadas do estado de exibição.</span><span class="sxs-lookup"><span data-stu-id="e3783-136">Inspect the XAML file to see the view state attached properties.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e3783-137">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e3783-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e3783-138">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e3783-138">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="e3783-139">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="e3783-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e3783-140">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e3783-140">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
