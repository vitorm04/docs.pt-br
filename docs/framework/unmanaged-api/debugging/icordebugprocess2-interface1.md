---
title: Interface1 ICorDebugProcess2
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a1588a37891d6a73c49cb1b9ccbc81d9dcdb7e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420411"
---
# <a name="icordebugprocess2-interface1"></a><span data-ttu-id="7334a-102">Interface1 ICorDebugProcess2</span><span class="sxs-lookup"><span data-stu-id="7334a-102">ICorDebugProcess2 Interface1</span></span>
<span data-ttu-id="7334a-103">Uma extensão lógica da interface ICorDebugProcess, que representa um código gerenciado em execução do processo.</span><span class="sxs-lookup"><span data-stu-id="7334a-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7334a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="7334a-104">Methods</span></span>  
  
|<span data-ttu-id="7334a-105">Método</span><span class="sxs-lookup"><span data-stu-id="7334a-105">Method</span></span>|<span data-ttu-id="7334a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7334a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7334a-107">Método ClearUnmanagedBreakpoint</span><span class="sxs-lookup"><span data-stu-id="7334a-107">ClearUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="7334a-108">Remove um ponto de interrupção no deslocamento especificado que foi definido por uma chamada anterior para `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="7334a-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="7334a-109">Método GetDesiredNGENCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="7334a-109">GetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="7334a-110">Obtém os sinalizadores que devem ser definidos para o common language runtime (CLR) para carregar a imagem no processo referenciado por este `ICorDebugProcess2`.</span><span class="sxs-lookup"><span data-stu-id="7334a-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="7334a-111">Método GetReferenceValueFromGCHandle</span><span class="sxs-lookup"><span data-stu-id="7334a-111">GetReferenceValueFromGCHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="7334a-112">Obtém um ponteiro de referência para o objeto especificado gerenciado que possua uma coleta de lixo a alça.</span><span class="sxs-lookup"><span data-stu-id="7334a-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="7334a-113">Método GetThreadForTaskID</span><span class="sxs-lookup"><span data-stu-id="7334a-113">GetThreadForTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="7334a-114">Obtém o thread em que a tarefa com o identificador especificado está em execução.</span><span class="sxs-lookup"><span data-stu-id="7334a-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="7334a-115">Método GetVersion</span><span class="sxs-lookup"><span data-stu-id="7334a-115">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|<span data-ttu-id="7334a-116">Obtém a versão do CLR no qual o processo está sendo depurado está em execução.</span><span class="sxs-lookup"><span data-stu-id="7334a-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="7334a-117">Método SetDesiredNGENCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="7334a-117">SetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="7334a-118">Define os sinalizadores que são necessários para o compilador just-in-time (JIT) carregar uma imagem no processo sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="7334a-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="7334a-119">Método SetUnmanagedBreakpoint</span><span class="sxs-lookup"><span data-stu-id="7334a-119">SetUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="7334a-120">Define um ponto de interrupção não gerenciado no deslocamento especificado de imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="7334a-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7334a-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="7334a-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7334a-122">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="7334a-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7334a-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7334a-123">Requirements</span></span>  
 <span data-ttu-id="7334a-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7334a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7334a-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7334a-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7334a-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7334a-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7334a-127">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7334a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7334a-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7334a-128">See Also</span></span>  
 [<span data-ttu-id="7334a-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="7334a-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
