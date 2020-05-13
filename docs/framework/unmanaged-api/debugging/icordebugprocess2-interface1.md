---
title: Interface ICorDebugProcess2
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
ms.openlocfilehash: 1a57b7ceb6da961fba1f0d6e8e0ba1aa88ca0541
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213485"
---
# <a name="icordebugprocess2-interface"></a><span data-ttu-id="8d6fd-102">Interface ICorDebugProcess2</span><span class="sxs-lookup"><span data-stu-id="8d6fd-102">ICorDebugProcess2 Interface</span></span>
<span data-ttu-id="8d6fd-103">Uma extensão lógica da interface ICorDebugProcess, que representa um processo que executa código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8d6fd-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8d6fd-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="8d6fd-104">Methods</span></span>  
  
|<span data-ttu-id="8d6fd-105">Método</span><span class="sxs-lookup"><span data-stu-id="8d6fd-105">Method</span></span>|<span data-ttu-id="8d6fd-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d6fd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8d6fd-107">Método ClearUnmanagedBreakpoint</span><span class="sxs-lookup"><span data-stu-id="8d6fd-107">ClearUnmanagedBreakpoint Method</span></span>](icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="8d6fd-108">Remove um ponto de interrupção no deslocamento especificado que foi definido por uma chamada anterior para `ICorDebugProcess2::SetUnmanagedBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="8d6fd-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="8d6fd-109">Método GetDesiredNGENCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="8d6fd-109">GetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="8d6fd-110">Obtém os sinalizadores que devem ser definidos para o Common Language Runtime (CLR) para carregar a imagem no processo referenciado por isso `ICorDebugProcess2` .</span><span class="sxs-lookup"><span data-stu-id="8d6fd-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="8d6fd-111">Método GetReferenceValueFromGCHandle</span><span class="sxs-lookup"><span data-stu-id="8d6fd-111">GetReferenceValueFromGCHandle Method</span></span>](icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="8d6fd-112">Obtém um ponteiro de referência para o objeto gerenciado especificado que tem um identificador de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8d6fd-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="8d6fd-113">Método GetThreadForTaskID</span><span class="sxs-lookup"><span data-stu-id="8d6fd-113">GetThreadForTaskID Method</span></span>](icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="8d6fd-114">Obtém o thread no qual a tarefa com o identificador especificado está em execução.</span><span class="sxs-lookup"><span data-stu-id="8d6fd-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="8d6fd-115">Método GetVersion</span><span class="sxs-lookup"><span data-stu-id="8d6fd-115">GetVersion Method</span></span>](icordebugprocess2-getversion-method.md)|<span data-ttu-id="8d6fd-116">Obtém a versão do CLR no qual o processo que está sendo depurado está em execução.</span><span class="sxs-lookup"><span data-stu-id="8d6fd-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="8d6fd-117">Método SetDesiredNGENCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="8d6fd-117">SetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="8d6fd-118">Define os sinalizadores que são necessários para o compilador JIT (just-in-time) carregar uma imagem no processo que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="8d6fd-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="8d6fd-119">Método SetUnmanagedBreakpoint</span><span class="sxs-lookup"><span data-stu-id="8d6fd-119">SetUnmanagedBreakpoint Method</span></span>](icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="8d6fd-120">Define um ponto de interrupção não gerenciado no deslocamento da imagem nativa especificada.</span><span class="sxs-lookup"><span data-stu-id="8d6fd-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d6fd-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d6fd-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d6fd-122">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="8d6fd-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d6fd-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8d6fd-123">Requirements</span></span>  
 <span data-ttu-id="8d6fd-124">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d6fd-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d6fd-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d6fd-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d6fd-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d6fd-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d6fd-127">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d6fd-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d6fd-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="8d6fd-128">See also</span></span>

- [<span data-ttu-id="8d6fd-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8d6fd-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
