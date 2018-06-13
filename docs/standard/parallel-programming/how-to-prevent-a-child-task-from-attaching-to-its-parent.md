---
title: 'Como: Evitar que uma tarefa filho se anexe ao seu pai'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ea0254add0592c0c79c03f4e94f02526f9fe689
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580764"
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a><span data-ttu-id="a9db8-102">Como: Evitar que uma tarefa filho se anexe ao seu pai</span><span class="sxs-lookup"><span data-stu-id="a9db8-102">How to: Prevent a Child Task from Attaching to its Parent</span></span>
<span data-ttu-id="a9db8-103">Este documento demonstra como evitar que uma tarefa filho se anexe à tarefa principal.</span><span class="sxs-lookup"><span data-stu-id="a9db8-103">This document demonstrates how to prevent a child task from attaching to the parent task.</span></span> <span data-ttu-id="a9db8-104">Impedir que uma tarefa filho seja anexada à tarefa pai é útil quando você chama um componente que é gravado por um terceiro e que também usa tarefas.</span><span class="sxs-lookup"><span data-stu-id="a9db8-104">Preventing a child task from attaching to its parent is useful when you call a component that is written by a third party and that also uses tasks.</span></span> <span data-ttu-id="a9db8-105">Por exemplo, um componente de terceiros que usa a opção <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> para criar um objeto <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> pode causar problemas em seu código se ele for de longa duração ou lançar uma exceção não controlada.</span><span class="sxs-lookup"><span data-stu-id="a9db8-105">For example, a third-party component that uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> option to create a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object can cause problems in your code if it is long-running or throws an unhandled exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9db8-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a9db8-106">Example</span></span>  
 <span data-ttu-id="a9db8-107">O exemplo a seguir compara os efeitos de usar as opções padrão com os efeitos de impedir que uma tarefa filho seja anexada ao pai.</span><span class="sxs-lookup"><span data-stu-id="a9db8-107">The following example compares the effects of using the default options to the effects of preventing a child task from attaching to the parent.</span></span> <span data-ttu-id="a9db8-108">O exemplo cria um objeto <xref:System.Threading.Tasks.Task> que chama para uma biblioteca de terceiros que também usa um objeto <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="a9db8-108">The example creates a <xref:System.Threading.Tasks.Task> object that calls into a third-party library that also uses a <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="a9db8-109">A biblioteca de terceiros usa a opção <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> para criar o objeto <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="a9db8-109">The third-party library uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> option to create the <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="a9db8-110">O aplicativo usa a opção <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> para criar a tarefa pai.</span><span class="sxs-lookup"><span data-stu-id="a9db8-110">The application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option to create the parent task.</span></span> <span data-ttu-id="a9db8-111">Essa opção instrui o tempo de execução para remover a especificação <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> em tarefas filho.</span><span class="sxs-lookup"><span data-stu-id="a9db8-111">This option instructs the runtime to remove the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specification in child tasks.</span></span>  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 <span data-ttu-id="a9db8-112">Como a tarefa pai não termina até que todas as tarefas filho sejam concluídas, uma tarefa filho de longa duração pode fazer com que o aplicativo geral tenha um baixo desempenho.</span><span class="sxs-lookup"><span data-stu-id="a9db8-112">Because a parent task does not finish until all child tasks finish, a long-running child task can cause the overall application to perform poorly.</span></span> <span data-ttu-id="a9db8-113">Neste exemplo, quando o aplicativo usa as opções padrão para criar a tarefa pai, a tarefa filho deve terminar antes da conclusão da tarefa pai.</span><span class="sxs-lookup"><span data-stu-id="a9db8-113">In this example, when the application uses the default options to create the parent task, the child task must finish before the parent task finishes.</span></span> <span data-ttu-id="a9db8-114">Quando o aplicativo usa a opção <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>, a tarefa filho não está anexada à tarefa pai.</span><span class="sxs-lookup"><span data-stu-id="a9db8-114">When the application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option, the child is not attached to the parent.</span></span> <span data-ttu-id="a9db8-115">Portanto, o aplicativo pode executar trabalhos adicionais após a conclusão da tarefa pai e antes de aguardar a conclusão da tarefa filho.</span><span class="sxs-lookup"><span data-stu-id="a9db8-115">Therefore, the application can perform additional work after the parent task finishes and before it must wait for the child task to finish.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a9db8-116">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a9db8-116">Compiling the Code</span></span>  
 <span data-ttu-id="a9db8-117">Copie o código de exemplo e cole-o em um projeto do Visual Studio, ou cole-o em um arquivo chamado `DenyChildAttach.cs` (`DenyChildAttach.vb` para Visual Basic) e, em seguida, execute o seguinte comando em uma janela do prompt de comando do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9db8-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DenyChildAttach.cs` (`DenyChildAttach.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="a9db8-118">Visual C#</span><span class="sxs-lookup"><span data-stu-id="a9db8-118">Visual C#</span></span>  
  
 <span data-ttu-id="a9db8-119">**csc.exe DenyChildAttach.cs**</span><span class="sxs-lookup"><span data-stu-id="a9db8-119">**csc.exe DenyChildAttach.cs**</span></span>  
  
 <span data-ttu-id="a9db8-120">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a9db8-120">Visual Basic</span></span>  
  
 <span data-ttu-id="a9db8-121">**vbc.exe DenyChildAttach.vb**</span><span class="sxs-lookup"><span data-stu-id="a9db8-121">**vbc.exe DenyChildAttach.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a9db8-122">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="a9db8-122">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9db8-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9db8-123">See Also</span></span>  
 [<span data-ttu-id="a9db8-124">Programação assíncrona baseada em tarefa</span><span class="sxs-lookup"><span data-stu-id="a9db8-124">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
