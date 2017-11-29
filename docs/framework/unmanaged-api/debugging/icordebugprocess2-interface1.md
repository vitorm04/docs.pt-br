---
title: Interface1 ICorDebugProcess2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2
helpviewer_keywords: ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca1a73874f6ca2f839639cbaf731a59721b2aede
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2-interface1"></a><span data-ttu-id="c289d-102">Interface1 ICorDebugProcess2</span><span class="sxs-lookup"><span data-stu-id="c289d-102">ICorDebugProcess2 Interface1</span></span>
<span data-ttu-id="c289d-103">Uma extensão lógica da interface ICorDebugProcess, que representa um código gerenciado em execução do processo.</span><span class="sxs-lookup"><span data-stu-id="c289d-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c289d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c289d-104">Methods</span></span>  
  
|<span data-ttu-id="c289d-105">Método</span><span class="sxs-lookup"><span data-stu-id="c289d-105">Method</span></span>|<span data-ttu-id="c289d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c289d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c289d-107">Método ClearUnmanagedBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c289d-107">ClearUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="c289d-108">Remove um ponto de interrupção no deslocamento especificado que foi definido por uma chamada anterior para `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="c289d-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="c289d-109">Método GetDesiredNGENCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="c289d-109">GetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="c289d-110">Obtém os sinalizadores que devem ser definidos para o common language runtime (CLR) para carregar a imagem no processo referenciado por este `ICorDebugProcess2`.</span><span class="sxs-lookup"><span data-stu-id="c289d-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="c289d-111">Método GetReferenceValueFromGCHandle</span><span class="sxs-lookup"><span data-stu-id="c289d-111">GetReferenceValueFromGCHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="c289d-112">Obtém um ponteiro de referência para o objeto especificado gerenciado que possua uma coleta de lixo a alça.</span><span class="sxs-lookup"><span data-stu-id="c289d-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="c289d-113">Método GetThreadForTaskID</span><span class="sxs-lookup"><span data-stu-id="c289d-113">GetThreadForTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="c289d-114">Obtém o thread em que a tarefa com o identificador especificado está em execução.</span><span class="sxs-lookup"><span data-stu-id="c289d-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="c289d-115">Método GetVersion</span><span class="sxs-lookup"><span data-stu-id="c289d-115">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|<span data-ttu-id="c289d-116">Obtém a versão do CLR no qual o processo está sendo depurado está em execução.</span><span class="sxs-lookup"><span data-stu-id="c289d-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="c289d-117">Método SetDesiredNGENCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="c289d-117">SetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="c289d-118">Define os sinalizadores que são necessários para o compilador just-in-time (JIT) carregar uma imagem no processo sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="c289d-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="c289d-119">Método SetUnmanagedBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c289d-119">SetUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="c289d-120">Define um ponto de interrupção não gerenciado no deslocamento especificado de imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="c289d-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c289d-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="c289d-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c289d-122">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="c289d-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c289d-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c289d-123">Requirements</span></span>  
 <span data-ttu-id="c289d-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c289d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c289d-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c289d-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c289d-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c289d-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c289d-127">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c289d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c289d-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c289d-128">See Also</span></span>  
 [<span data-ttu-id="c289d-129">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="c289d-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
