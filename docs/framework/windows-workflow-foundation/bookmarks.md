---
title: Bookmarks1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f570db1e677445239cec537f66bdf66fad66b37d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="bookmarks"></a><span data-ttu-id="3390b-102">Indicadores</span><span class="sxs-lookup"><span data-stu-id="3390b-102">Bookmarks</span></span>
<span data-ttu-id="3390b-103">Indexadores são o mecanismo que permite uma atividade para esperar passiva entrada sem conter um segmento de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3390b-103">Bookmarks are the mechanism that enables an activity to passively wait for input without holding onto a workflow thread.</span></span> <span data-ttu-id="3390b-104">Quando uma atividade sinaliza que está esperando estímulo, pode criar um indexador.</span><span class="sxs-lookup"><span data-stu-id="3390b-104">When an activity signals that it is waiting for stimulus, it can create a bookmark.</span></span> <span data-ttu-id="3390b-105">Isso indica o tempo de execução que a execução da atividade não deve ser considerada completo mesmo quando o método atualmente em execução (que criou <xref:System.Activities.Bookmark>) retorna.</span><span class="sxs-lookup"><span data-stu-id="3390b-105">This indicates to the runtime that the activity’s execution should not be considered complete even when the currently executing method (which created the <xref:System.Activities.Bookmark>) returns.</span></span>  
  
## <a name="bookmark-basics"></a><span data-ttu-id="3390b-106">Noções básicas do indexador</span><span class="sxs-lookup"><span data-stu-id="3390b-106">Bookmark Basics</span></span>  
 <span data-ttu-id="3390b-107"><xref:System.Activities.Bookmark> representa um ponto em que a execução pode ser continuada (e através de entrada que pode ser entregada) em uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3390b-107">A <xref:System.Activities.Bookmark> represents a point at which execution can be resumed (and through which input can be delivered) within a workflow instance.</span></span> <span data-ttu-id="3390b-108">Normalmente, <xref:System.Activities.Bookmark> é dado um nome e host (ou extensão) o código externo é responsável para continuar o indexador com dados relevantes.</span><span class="sxs-lookup"><span data-stu-id="3390b-108">Typically, a <xref:System.Activities.Bookmark> is given a name and external (host or extension) code is responsible for resuming the bookmark with relevant data.</span></span> <span data-ttu-id="3390b-109">Quando <xref:System.Activities.Bookmark> é que, o tempo de execução de fluxo de trabalho agenda o representante de <xref:System.Activities.BookmarkCallback> que foi associado com esse <xref:System.Activities.Bookmark> na altura do projeto.</span><span class="sxs-lookup"><span data-stu-id="3390b-109">When a <xref:System.Activities.Bookmark> is resumed, the workflow runtime schedules the <xref:System.Activities.BookmarkCallback> delegate that was associated with that <xref:System.Activities.Bookmark> at the time of its creation.</span></span>  
  
## <a name="bookmark-options"></a><span data-ttu-id="3390b-110">Opções do indexador</span><span class="sxs-lookup"><span data-stu-id="3390b-110">Bookmark Options</span></span>  
 <span data-ttu-id="3390b-111">A classe de <xref:System.Activities.BookmarkOptions> especifica o tipo de <xref:System.Activities.Bookmark> que está sendo criado.</span><span class="sxs-lookup"><span data-stu-id="3390b-111">The <xref:System.Activities.BookmarkOptions> class specifies the type of <xref:System.Activities.Bookmark> being created.</span></span> <span data-ttu-id="3390b-112">Os valores não mutuamente exclusivos possíveis são <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, e <xref:System.Activities.BookmarkOptions.NonBlocking>.</span><span class="sxs-lookup"><span data-stu-id="3390b-112">The possible non mutually-exclusive values are <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, and <xref:System.Activities.BookmarkOptions.NonBlocking>.</span></span> <span data-ttu-id="3390b-113">Use <xref:System.Activities.BookmarkOptions.None>, a opção, ao criar <xref:System.Activities.Bookmark> que seja continuada exatamente uma vez.</span><span class="sxs-lookup"><span data-stu-id="3390b-113">Use <xref:System.Activities.BookmarkOptions.None>, the default, when creating a <xref:System.Activities.Bookmark> that is expected to be resumed exactly once.</span></span> <span data-ttu-id="3390b-114">Use <xref:System.Activities.BookmarkOptions.MultipleResume> ao criar <xref:System.Activities.Bookmark> que pode ser que várias vezes.</span><span class="sxs-lookup"><span data-stu-id="3390b-114">Use <xref:System.Activities.BookmarkOptions.MultipleResume> when creating a <xref:System.Activities.Bookmark> that can be resumed multiple times.</span></span> <span data-ttu-id="3390b-115">Use <xref:System.Activities.BookmarkOptions.NonBlocking> ao criar <xref:System.Activities.Bookmark> que pode ser que nunca.</span><span class="sxs-lookup"><span data-stu-id="3390b-115">Use <xref:System.Activities.BookmarkOptions.NonBlocking> when creating a <xref:System.Activities.Bookmark> that might never be resumed.</span></span> <span data-ttu-id="3390b-116">Ao contrário dos indicadores criados usando <xref:System.Activities.BookmarkOptions>padrão, os indicadores de <xref:System.Activities.BookmarkOptions.NonBlocking> não impede que uma atividade terminar.</span><span class="sxs-lookup"><span data-stu-id="3390b-116">Unlike bookmarks created using the default <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> bookmarks do not prevent an activity from completing.</span></span>  
  
## <a name="bookmark-resumption"></a><span data-ttu-id="3390b-117">Ressunção do indexador</span><span class="sxs-lookup"><span data-stu-id="3390b-117">Bookmark Resumption</span></span>  
 <span data-ttu-id="3390b-118">Indexadores podem ser continuados pelo código fora de um fluxo de trabalho usando uma das sobrecargas de <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> .</span><span class="sxs-lookup"><span data-stu-id="3390b-118">Bookmarks can be resumed by code outside of a workflow using one of the <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> overloads.</span></span> <span data-ttu-id="3390b-119">Nesse exemplo, uma atividade de `ReadLine` é criada.</span><span class="sxs-lookup"><span data-stu-id="3390b-119">In this example, a `ReadLine` activity is created.</span></span> <span data-ttu-id="3390b-120">Quando executada, a atividade de `ReadLine` cria <xref:System.Activities.Bookmark>, registra um retorno de chamada, e espera em <xref:System.Activities.Bookmark> a ser continuado.</span><span class="sxs-lookup"><span data-stu-id="3390b-120">When executed, the `ReadLine` activity creates a <xref:System.Activities.Bookmark>, registers a callback, and then waits for the <xref:System.Activities.Bookmark> to be resumed.</span></span> <span data-ttu-id="3390b-121">Quando é continuada, a atividade de `ReadLine` atribui os dados que foram passados com <xref:System.Activities.Bookmark> ao seu argumento de <xref:System.Activities.Activity%601.Result%2A> .</span><span class="sxs-lookup"><span data-stu-id="3390b-121">When it is resumed, the `ReadLine` activity assigns the data that was passed with the <xref:System.Activities.Bookmark> to its <xref:System.Activities.Activity%601.Result%2A> argument.</span></span>  
  
```csharp  
public sealed class ReadLine : NativeActivity<string>  
{  
    [RequiredArgument]  
    public  InArgument<string> BookmarkName { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        // Create a Bookmark and wait for it to be resumed.  
        context.CreateBookmark(BookmarkName.Get(context),   
            new BookmarkCallback(OnResumeBookmark));  
    }  
  
    // NativeActivity derived activities that do asynchronous operations by calling   
    // one of the CreateBookmark overloads defined on System.Activities.NativeActivityContext   
    // must override the CanInduceIdle property and return true.  
    protected override bool CanInduceIdle  
    {  
        get { return true; }  
    }  
  
    public void OnResumeBookmark(NativeActivityContext context, Bookmark bookmark, object obj)  
    {  
        // When the Bookmark is resumed, assign its value to  
        // the Result argument.  
        Result.Set(context, (string)obj);  
    }  
}  
```  
  
 <span data-ttu-id="3390b-122">Nesse exemplo, um fluxo de trabalho é criado que usa a atividade de `ReadLine` para coletar o nome de usuário e para o exibir a janela do console.</span><span class="sxs-lookup"><span data-stu-id="3390b-122">In this example, a workflow is created that uses the `ReadLine` activity to gather the user’s name and display it to the console window.</span></span> <span data-ttu-id="3390b-123">O aplicativo host executa o trabalho real de coletar entrada e passá-lo para o fluxo de trabalho continuando <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="3390b-123">The host application performs the actual work of gathering the input and passes it to the workflow by resuming the <xref:System.Activities.Bookmark>.</span></span>  
  
```csharp  
Variable<string> name = new Variable<string>  
{  
    Name = "name"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        name  
    },  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "What is your name?"  
        },  
        new ReadLine()  
        {  
            BookmarkName = "UserName",  
            Result = name  
        },  
        new WriteLine()  
        {  
            Text = new InArgument<string>((env) => "Hello, " + name.Get(env))  
        }  
    }  
};  
  
AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
// Create the WorkflowApplication using the desired  
// workflow definition.  
WorkflowApplication wfApp = new WorkflowApplication(wf);  
  
// Handle the desired lifecycle events.  
wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
{  
    // Signal the host that the workflow is complete.  
    syncEvent.Set();  
};  
  
// Start the workflow.  
wfApp.Run();  
  
// Collect the user's name and resume the bookmark.  
// Bookmark resumption only occurs when the workflow  
// is idle. If a call to ResumeBookmark is made and the workflow  
// is not idle, ResumeBookmark blocks until the workflow becomes  
// idle before resuming the bookmark.  
wfApp.ResumeBookmark("UserName", Console.ReadLine());  
  
// Wait for Completed to arrive and signal that  
// the workflow is complete.  
syncEvent.WaitOne();  
```  
  
 <span data-ttu-id="3390b-124">Quando a atividade de `ReadLine` é executada, cria <xref:System.Activities.Bookmark> chamado `UserName` e espera no indexador a ser continuado.</span><span class="sxs-lookup"><span data-stu-id="3390b-124">When the `ReadLine` activity is executed, it creates a <xref:System.Activities.Bookmark> named `UserName` and then waits for the bookmark to be resumed.</span></span> <span data-ttu-id="3390b-125">O host reúne os dados desejados e depois <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="3390b-125">The host collects the desired data and then resumes the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="3390b-126">Retoma de fluxo de trabalho, exibe o nome, e então usa.</span><span class="sxs-lookup"><span data-stu-id="3390b-126">The workflow resumes, displays the name, and then completes.</span></span> <span data-ttu-id="3390b-127">Observe que nenhum código de sincronização é necessário em relação ao indexador continuar.</span><span class="sxs-lookup"><span data-stu-id="3390b-127">Note that no synchronization code is required with regard to resuming the bookmark.</span></span> <span data-ttu-id="3390b-128"><xref:System.Activities.Bookmark> só pode ser que quando o fluxo de trabalho estiver ocioso, e se o fluxo de trabalho não estiver ocioso, a chamada para blocos de <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> até que o fluxo de trabalho se torne ocioso.</span><span class="sxs-lookup"><span data-stu-id="3390b-128">A <xref:System.Activities.Bookmark> can only be resumed when the workflow is idle, and if the workflow is not idle, the call to <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blocks until the workflow becomes idle.</span></span>  
  
## <a name="bookmark-resumption-result"></a><span data-ttu-id="3390b-129">Resultado de ressunção do indexador</span><span class="sxs-lookup"><span data-stu-id="3390b-129">Bookmark Resumption Result</span></span>  
 <span data-ttu-id="3390b-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> retorna um valor de enumeração <xref:System.Activities.BookmarkResumptionResult> para indicar os resultados da solicitação de ressunção do indexador.</span><span class="sxs-lookup"><span data-stu-id="3390b-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> returns a <xref:System.Activities.BookmarkResumptionResult> enumeration value to indicate the results of the bookmark resumption request.</span></span> <span data-ttu-id="3390b-131">Retornar valores possíveis são <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, e <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span><span class="sxs-lookup"><span data-stu-id="3390b-131">The possible return values are <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, and <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span></span> <span data-ttu-id="3390b-132">Hosts e extensões podem usar esse valor para determinar como continuar.</span><span class="sxs-lookup"><span data-stu-id="3390b-132">Hosts and extensions can use this value to determine how to proceed.</span></span>
