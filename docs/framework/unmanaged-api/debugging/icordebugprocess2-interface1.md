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
ms.openlocfilehash: 1ef6af11851acbe0f7e9469c9432ff09f9228608
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792502"
---
# <a name="icordebugprocess2-interface"></a><span data-ttu-id="119da-102">Interface ICorDebugProcess2</span><span class="sxs-lookup"><span data-stu-id="119da-102">ICorDebugProcess2 Interface</span></span>
<span data-ttu-id="119da-103">Uma extensão lógica da interface ICorDebugProcess, que representa um processo que executa código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="119da-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="119da-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="119da-104">Methods</span></span>  
  
|<span data-ttu-id="119da-105">Método</span><span class="sxs-lookup"><span data-stu-id="119da-105">Method</span></span>|<span data-ttu-id="119da-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="119da-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="119da-107">Método ClearUnmanagedBreakpoint</span><span class="sxs-lookup"><span data-stu-id="119da-107">ClearUnmanagedBreakpoint Method</span></span>](icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="119da-108">Remove um ponto de interrupção no deslocamento especificado que foi definido por uma chamada anterior para `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="119da-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="119da-109">Método GetDesiredNGENCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="119da-109">GetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="119da-110">Obtém os sinalizadores que devem ser definidos para o Common Language Runtime (CLR) para carregar a imagem no processo referenciado por este `ICorDebugProcess2`.</span><span class="sxs-lookup"><span data-stu-id="119da-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="119da-111">Método GetReferenceValueFromGCHandle</span><span class="sxs-lookup"><span data-stu-id="119da-111">GetReferenceValueFromGCHandle Method</span></span>](icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="119da-112">Obtém um ponteiro de referência para o objeto gerenciado especificado que tem um identificador de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="119da-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="119da-113">Método GetThreadForTaskID</span><span class="sxs-lookup"><span data-stu-id="119da-113">GetThreadForTaskID Method</span></span>](icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="119da-114">Obtém o thread no qual a tarefa com o identificador especificado está em execução.</span><span class="sxs-lookup"><span data-stu-id="119da-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="119da-115">Método GetVersion</span><span class="sxs-lookup"><span data-stu-id="119da-115">GetVersion Method</span></span>](icordebugprocess2-getversion-method.md)|<span data-ttu-id="119da-116">Obtém a versão do CLR no qual o processo que está sendo depurado está em execução.</span><span class="sxs-lookup"><span data-stu-id="119da-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="119da-117">Método SetDesiredNGENCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="119da-117">SetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="119da-118">Define os sinalizadores que são necessários para o compilador JIT (just-in-time) carregar uma imagem no processo que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="119da-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="119da-119">Método SetUnmanagedBreakpoint</span><span class="sxs-lookup"><span data-stu-id="119da-119">SetUnmanagedBreakpoint Method</span></span>](icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="119da-120">Define um ponto de interrupção não gerenciado no deslocamento da imagem nativa especificada.</span><span class="sxs-lookup"><span data-stu-id="119da-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="119da-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="119da-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="119da-122">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="119da-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="119da-123">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="119da-123">Requirements</span></span>  
 <span data-ttu-id="119da-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="119da-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="119da-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="119da-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="119da-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="119da-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="119da-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="119da-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="119da-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="119da-128">See also</span></span>

- [<span data-ttu-id="119da-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="119da-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
