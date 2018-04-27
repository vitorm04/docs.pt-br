---
title: Arquitetura de fluxo de trabalho do Windows
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a3a59369738ada0c6b770d272afa9c6c79c2ce01
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="windows-workflow-architecture"></a><span data-ttu-id="b83b0-102">Arquitetura de fluxo de trabalho do Windows</span><span class="sxs-lookup"><span data-stu-id="b83b0-102">Windows Workflow Architecture</span></span>
<span data-ttu-id="b83b0-103">Windows Workflow Foundation (WF) aumenta o nível de abstração para o desenvolvimento de aplicativos interativos de longa execução.</span><span class="sxs-lookup"><span data-stu-id="b83b0-103">Windows Workflow Foundation (WF) raises the abstraction level for developing interactive long-running applications.</span></span> <span data-ttu-id="b83b0-104">As unidades de trabalho são encapsuladas como atividades.</span><span class="sxs-lookup"><span data-stu-id="b83b0-104">Units of work are encapsulated as activities.</span></span> <span data-ttu-id="b83b0-105">As atividades executam em um ambiente que fornece recursos para o controle de fluxo, manipulação de exceção, a propagação de falha, persistência de dados do estado, ao carregamento e descarregamento de fluxos de trabalho em andamento de memória, de rastreamento, e de fluxo de transação.</span><span class="sxs-lookup"><span data-stu-id="b83b0-105">Activities run in an environment that provides facilities for flow control, exception handling, fault propagation, persistence of state data, loading and unloading of in-progress workflows from memory, tracking, and transaction flow.</span></span>  
  
## <a name="activity-architecture"></a><span data-ttu-id="b83b0-106">Arquitetura de atividades</span><span class="sxs-lookup"><span data-stu-id="b83b0-106">Activity Architecture</span></span>  
 <span data-ttu-id="b83b0-107">As atividades são desenvolvidas como os tipos de CLR que derivam de <xref:System.Activities.Activity>, de <xref:System.Activities.CodeActivity>, de <xref:System.Activities.AsyncCodeActivity>, ou de <xref:System.Activities.NativeActivity>, ou as suas variantes que retornam um valor, <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601>, ou <xref:System.Activities.NativeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="b83b0-107">Activities are developed as CLR types that derive from either <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>, or their variants that return a value, <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601>, or <xref:System.Activities.NativeActivity%601>.</span></span> <span data-ttu-id="b83b0-108">Desenvolver as atividades que derivam de <xref:System.Activities.Activity> permite que o usuário reúne atividades pré-compilação existentes para criar rapidamente as unidades de trabalho que executam no ambiente de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b83b0-108">Developing activities that derive from <xref:System.Activities.Activity> allows the user to assemble pre-existing activities to quickly create units of work that execute in the workflow environment.</span></span> <span data-ttu-id="b83b0-109"><xref:System.Activities.CodeActivity>, por outro lado, permite a lógica de execução a ser criado em código gerenciado usando <xref:System.Activities.CodeActivityContext> principalmente para acesso aos argumentos de atividade.</span><span class="sxs-lookup"><span data-stu-id="b83b0-109"><xref:System.Activities.CodeActivity>, on the other hand, enables execution logic to be authored in managed code using <xref:System.Activities.CodeActivityContext> primarily for access to activity arguments.</span></span> <span data-ttu-id="b83b0-110"><xref:System.Activities.AsyncCodeActivity> é semelhante a <xref:System.Activities.CodeActivity> exceto que pode ser usado para implementar tarefas assíncronas.</span><span class="sxs-lookup"><span data-stu-id="b83b0-110"><xref:System.Activities.AsyncCodeActivity> is similar to <xref:System.Activities.CodeActivity> except that it can be used to implement asynchronous tasks.</span></span> <span data-ttu-id="b83b0-111">Desenvolver as atividades que derivam de <xref:System.Activities.NativeActivity> permite que os usuários acessem o tempo de execução com <xref:System.Activities.NativeActivityContext> para a funcionalidade como filhos de programação, criando indexadores, invocando o trabalho assíncrona, registrando transações, e mais.</span><span class="sxs-lookup"><span data-stu-id="b83b0-111">Developing activities that derive from <xref:System.Activities.NativeActivity> allows users to access the runtime through the <xref:System.Activities.NativeActivityContext> for functionality like scheduling children, creating bookmarks, invoking asynchronous work, registering transactions, and more.</span></span>  
  
 <span data-ttu-id="b83b0-112">As atividades de design que derivam de <xref:System.Activities.Activity> são declarativas e essas atividades podem ser criadas em XAML.</span><span class="sxs-lookup"><span data-stu-id="b83b0-112">Authoring activities that derive from <xref:System.Activities.Activity> is declarative and these activities can be authored in XAML.</span></span> <span data-ttu-id="b83b0-113">No exemplo a seguir, uma atividade chamada `Prompt` é criada usando outras atividades para o corpo de execução.</span><span class="sxs-lookup"><span data-stu-id="b83b0-113">In the following example, an activity called `Prompt` is created using other activities for the execution body.</span></span>  
  
```xml  
<Activity x:Class='Prompt'  
  xmlns:x='http://schemas.microsoft.com/winfx/2006/xaml'  
    xmlns:z='http://schemas.microsoft.com/netfx/2008/xaml/schema'  
xmlns:my='clr-namespace:XAMLActivityDefinition;assembly=XAMLActivityDefinition'  
xmlns:s="clr-namespace:System;assembly=mscorlib"  
xmlns="http://schemas.microsoft.com/2009/workflow">  
<z:SchemaType.Members>  
    <z:SchemaType.SchemaProperty Name='Text' Type=' InArgument(s:String)' />  
  <z:SchemaType.SchemaProperty Name='Response' Type='OutArgument(s:String)' />  
</z:SchemaType.Members>  
  <Sequence>  
    <my:WriteLine Text='[Text]' />  
    <my:ReadLine BookmarkName='r1' Result='[Response]' />  
  </Sequence>  
</Activity>  
```  
  
## <a name="activity-context"></a><span data-ttu-id="b83b0-114">Contexto de atividades</span><span class="sxs-lookup"><span data-stu-id="b83b0-114">Activity Context</span></span>  
 <span data-ttu-id="b83b0-115"><xref:System.Activities.ActivityContext> é a interface de autor de atividade do tempo de execução de fluxo de trabalho e fornece acesso a riqueza de tempo de execução dos recursos.</span><span class="sxs-lookup"><span data-stu-id="b83b0-115">The <xref:System.Activities.ActivityContext> is the activity author's interface to the workflow runtime and provides access to the runtime's wealth of features.</span></span> <span data-ttu-id="b83b0-116">No exemplo a seguir, uma atividade é definida que usa o contexto de execução para criar um marcador (o mecanismo que permite uma atividade registra um ponto de continuação de linha em sua execução que pode ser continuada por um host que passa dados na atividade).</span><span class="sxs-lookup"><span data-stu-id="b83b0-116">In the following example, an activity is defined that uses the execution context to create a bookmark (the mechanism that allows an activity to register a continuation point in its execution that can be resumed by a host passing data into the activity).</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## <a name="activity-life-cycle"></a><span data-ttu-id="b83b0-117">Ciclo de vida de atividades</span><span class="sxs-lookup"><span data-stu-id="b83b0-117">Activity Life Cycle</span></span>  
 <span data-ttu-id="b83b0-118">Uma instância de uma atividade começa em estado de <xref:System.Activities.ActivityInstanceState.Executing> .</span><span class="sxs-lookup"><span data-stu-id="b83b0-118">An instance of an activity starts out in the <xref:System.Activities.ActivityInstanceState.Executing> state.</span></span> <span data-ttu-id="b83b0-119">A menos que as exceções são localizadas, permanece nesse estado até que todas as atividades filho sejam executar completo e qualquer outro trabalho pendente (<xref:System.Activities.Bookmark> objetos, por exemplo) está concluído, ao ponto que ele faz a transição de estado de <xref:System.Activities.ActivityInstanceState.Closed> .</span><span class="sxs-lookup"><span data-stu-id="b83b0-119">Unless exceptions are encountered, it remains in this state until all child activities are finished executing and any other pending work (<xref:System.Activities.Bookmark> objects, for instance) is completed, at which point it transitions to the <xref:System.Activities.ActivityInstanceState.Closed> state.</span></span> <span data-ttu-id="b83b0-120">O pai de uma instância da atividade pode solicitar um filho; cancelar se o filho pode ser cancelado termina em estado de <xref:System.Activities.ActivityInstanceState.Canceled> .</span><span class="sxs-lookup"><span data-stu-id="b83b0-120">The parent of an activity instance can request a child to cancel; if the child is able to be canceled it completes in the <xref:System.Activities.ActivityInstanceState.Canceled> state.</span></span> <span data-ttu-id="b83b0-121">Se uma exceção é lançada durante a execução, o tempo de execução coloca a atividade no estado de <xref:System.Activities.ActivityInstanceState.Faulted> e propaga a exceção acima da cadeia pai de atividades.</span><span class="sxs-lookup"><span data-stu-id="b83b0-121">If an exception is thrown during execution, the runtime puts the activity into the <xref:System.Activities.ActivityInstanceState.Faulted> state and propagates the exception up the parent chain of activities.</span></span> <span data-ttu-id="b83b0-122">A seguir estão os três estados de conclusão de uma atividade:</span><span class="sxs-lookup"><span data-stu-id="b83b0-122">Following are the three completion states of an activity:</span></span>  
  
-   <span data-ttu-id="b83b0-123">**Fechados:** a atividade foi concluída seu trabalho e foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="b83b0-123">**Closed:** The activity has completed its work and exited.</span></span>  
  
-   <span data-ttu-id="b83b0-124">**Cancelada:** a atividade normalmente tem abandonou seu trabalho e foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="b83b0-124">**Canceled:** The activity has gracefully abandoned its work and exited.</span></span> <span data-ttu-id="b83b0-125">O trabalho não será revertido explicitamente quando esse estado está conectado.</span><span class="sxs-lookup"><span data-stu-id="b83b0-125">Work is not explicitly rolled back when this state is entered.</span></span>  
  
-   <span data-ttu-id="b83b0-126">**Falha:** a atividade encontrou um erro e foi encerrado sem concluir seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="b83b0-126">**Faulted:** The activity has encountered an error and has exited without completing its work.</span></span>  
  
 <span data-ttu-id="b83b0-127">As atividades permanecem no estado de <xref:System.Activities.ActivityInstanceState.Executing> quando são persistentes ou descarregadas.</span><span class="sxs-lookup"><span data-stu-id="b83b0-127">Activities remain in the <xref:System.Activities.ActivityInstanceState.Executing> state when they are persisted or unloaded.</span></span>
