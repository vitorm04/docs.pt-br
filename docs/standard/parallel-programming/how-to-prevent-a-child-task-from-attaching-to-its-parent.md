---
title: 'Como: Evitar que uma tarefa filho se anexe ao seu pai'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4717e3a077648d9db51fe39228209617b384bd0c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a><span data-ttu-id="b8343-102">Como: Evitar que uma tarefa filho se anexe ao seu pai</span><span class="sxs-lookup"><span data-stu-id="b8343-102">How to: Prevent a Child Task from Attaching to its Parent</span></span>
<span data-ttu-id="b8343-103">Este documento demonstra como impedir a anexar à tarefa pai de uma tarefa filho.</span><span class="sxs-lookup"><span data-stu-id="b8343-103">This document demonstrates how to prevent a child task from attaching to the parent task.</span></span> <span data-ttu-id="b8343-104">Impedindo que uma tarefa filho se anexe ao seu pai é útil quando você chama um componente que foi criado por um terceiro e que também usa as tarefas.</span><span class="sxs-lookup"><span data-stu-id="b8343-104">Preventing a child task from attaching to its parent is useful when you call a component that is written by a third party and that also uses tasks.</span></span> <span data-ttu-id="b8343-105">Por exemplo, um componente de terceiros que usa o <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opção para criar um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> objeto pode causar problemas no seu código, se ela for demorada ou gera uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="b8343-105">For example, a third-party component that uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> option to create a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object can cause problems in your code if it is long-running or throws an unhandled exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8343-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8343-106">Example</span></span>  
 <span data-ttu-id="b8343-107">O exemplo a seguir compara os efeitos de usar as opções padrão para os efeitos de impedir que uma tarefa filho anexe ao pai.</span><span class="sxs-lookup"><span data-stu-id="b8343-107">The following example compares the effects of using the default options to the effects of preventing a child task from attaching to the parent.</span></span> <span data-ttu-id="b8343-108">O exemplo cria um <xref:System.Threading.Tasks.Task> objeto que chama em uma biblioteca de terceiros que também usa um <xref:System.Threading.Tasks.Task> objeto.</span><span class="sxs-lookup"><span data-stu-id="b8343-108">The example creates a <xref:System.Threading.Tasks.Task> object that calls into a third-party library that also uses a <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="b8343-109">A biblioteca de terceiros usa a <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> opção para criar o <xref:System.Threading.Tasks.Task> objeto.</span><span class="sxs-lookup"><span data-stu-id="b8343-109">The third-party library uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> option to create the <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="b8343-110">O aplicativo usa o <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opção para criar a tarefa pai.</span><span class="sxs-lookup"><span data-stu-id="b8343-110">The application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option to create the parent task.</span></span> <span data-ttu-id="b8343-111">Essa opção instrui o tempo de execução para remover o <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> especificação de tarefas filho.</span><span class="sxs-lookup"><span data-stu-id="b8343-111">This option instructs the runtime to remove the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specification in child tasks.</span></span>  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 <span data-ttu-id="b8343-112">Como uma tarefa pai não for concluída até o término de todas as tarefas filho, uma tarefa filho de execução longa pode causar o desempenho geral do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b8343-112">Because a parent task does not finish until all child tasks finish, a long-running child task can cause the overall application to perform poorly.</span></span> <span data-ttu-id="b8343-113">Neste exemplo, quando o aplicativo usa as opções padrão para criar a tarefa pai, a tarefa filho deve ser concluído antes de concluir a tarefa pai.</span><span class="sxs-lookup"><span data-stu-id="b8343-113">In this example, when the application uses the default options to create the parent task, the child task must finish before the parent task finishes.</span></span> <span data-ttu-id="b8343-114">Quando o aplicativo usa o <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opção, o filho não está anexada ao pai.</span><span class="sxs-lookup"><span data-stu-id="b8343-114">When the application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option, the child is not attached to the parent.</span></span> <span data-ttu-id="b8343-115">Portanto, o aplicativo pode executar trabalho adicional após a conclusão da tarefa pai e antes que ele deve aguardar a conclusão da tarefa do filho.</span><span class="sxs-lookup"><span data-stu-id="b8343-115">Therefore, the application can perform additional work after the parent task finishes and before it must wait for the child task to finish.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b8343-116">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b8343-116">Compiling the Code</span></span>  
 <span data-ttu-id="b8343-117">Copie o código de exemplo e cole-o em um projeto do Visual Studio ou colá-lo em um arquivo chamado `DenyChildAttach.cs` (`DenyChildAttach.vb` para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), e, em seguida, execute o seguinte comando em uma janela de Prompt de comando do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8343-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DenyChildAttach.cs` (`DenyChildAttach.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="b8343-118">**CSC.exe DenyChildAttach.cs**</span><span class="sxs-lookup"><span data-stu-id="b8343-118">**csc.exe DenyChildAttach.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="b8343-119">**Vbc.exe DenyChildAttach.vb**</span><span class="sxs-lookup"><span data-stu-id="b8343-119">**vbc.exe DenyChildAttach.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b8343-120">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="b8343-120">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8343-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8343-121">See Also</span></span>  
 [<span data-ttu-id="b8343-122">Programação assíncrona baseada em tarefa</span><span class="sxs-lookup"><span data-stu-id="b8343-122">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
