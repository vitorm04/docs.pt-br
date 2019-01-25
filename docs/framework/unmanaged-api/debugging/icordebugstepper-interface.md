---
title: ICorDebugStepper Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1f796e665a4e403d2d2b5a15837dd8bb8bf47ed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631341"
---
# <a name="icordebugstepper-interface1"></a><span data-ttu-id="97180-102">ICorDebugStepper Interface1</span><span class="sxs-lookup"><span data-stu-id="97180-102">ICorDebugStepper Interface1</span></span>
<span data-ttu-id="97180-103">Representa uma etapa na execução do código que é realizada por um depurador, serve como um identificador entre a emissão e a conclusão de um comando e fornece uma maneira de cancelar uma etapa.</span><span class="sxs-lookup"><span data-stu-id="97180-103">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97180-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="97180-104">Methods</span></span>  
  
|<span data-ttu-id="97180-105">Método</span><span class="sxs-lookup"><span data-stu-id="97180-105">Method</span></span>|<span data-ttu-id="97180-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="97180-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97180-107">Método Deactivate</span><span class="sxs-lookup"><span data-stu-id="97180-107">Deactivate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|<span data-ttu-id="97180-108">Faz com que essa `ICorDebugStepper` para cancelar o último comando etapa recebido.</span><span class="sxs-lookup"><span data-stu-id="97180-108">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="97180-109">Método IsActive</span><span class="sxs-lookup"><span data-stu-id="97180-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|<span data-ttu-id="97180-110">Obtém um valor que indica se este `ICorDebugStepper` está executando uma etapa.</span><span class="sxs-lookup"><span data-stu-id="97180-110">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="97180-111">Método SetInterceptMask</span><span class="sxs-lookup"><span data-stu-id="97180-111">SetInterceptMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="97180-112">Define um valor de CorDebugIntercept que especifica os tipos de código são entrados.</span><span class="sxs-lookup"><span data-stu-id="97180-112">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="97180-113">Método SetRangeIL</span><span class="sxs-lookup"><span data-stu-id="97180-113">SetRangeIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|<span data-ttu-id="97180-114">Define um valor que indica se chamadas para [ICorDebugStepper:: Steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) passar valores de argumento em relação ao código nativo ou ao código do Microsoft intermediate language (MSIL) do método que está sendo percorrido.</span><span class="sxs-lookup"><span data-stu-id="97180-114">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="97180-115">Método SetUnmappedStopMask</span><span class="sxs-lookup"><span data-stu-id="97180-115">SetUnmappedStopMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="97180-116">Define um valor de CorDebugUnmappedStop que especifica o tipo de código não mapeado no qual a execução será interrompida.</span><span class="sxs-lookup"><span data-stu-id="97180-116">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="97180-117">Método Step</span><span class="sxs-lookup"><span data-stu-id="97180-117">Step Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|<span data-ttu-id="97180-118">Faz com que essa `ICorDebugStepper` a etapa única por meio de seu recipiente thread e, opcionalmente, para continuar a depuração de único por meio de funções que são chamadas de dentro do thread.</span><span class="sxs-lookup"><span data-stu-id="97180-118">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="97180-119">Método StepOut</span><span class="sxs-lookup"><span data-stu-id="97180-119">StepOut Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|<span data-ttu-id="97180-120">Faz com que essa `ICorDebugStepper` único-percorra seu recipiente thread e concluído quando o quadro atual retorna o controle para o quadro de chamada.</span><span class="sxs-lookup"><span data-stu-id="97180-120">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="97180-121">Método StepRange</span><span class="sxs-lookup"><span data-stu-id="97180-121">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|<span data-ttu-id="97180-122">Faz com que essa `ICorDebugStepper` a etapa única por meio de seu recipiente thread e para retornar quando ele atinge o código além do último dos intervalos especificados.</span><span class="sxs-lookup"><span data-stu-id="97180-122">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97180-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="97180-123">Remarks</span></span>  
 <span data-ttu-id="97180-124">O `ICorDebugStepper` interface tem as seguintes finalidades:</span><span class="sxs-lookup"><span data-stu-id="97180-124">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
-   <span data-ttu-id="97180-125">Ele atua como um identificador entre um comando de depuração é emitido e a conclusão desse comando.</span><span class="sxs-lookup"><span data-stu-id="97180-125">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
-   <span data-ttu-id="97180-126">Ele fornece uma interface central para encapsular todo o passo a passo que pode ser executada.</span><span class="sxs-lookup"><span data-stu-id="97180-126">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
-   <span data-ttu-id="97180-127">Ele fornece uma maneira de cancelar prematuramente uma operação de passo a passo.</span><span class="sxs-lookup"><span data-stu-id="97180-127">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="97180-128">Pode haver mais de um seletor por thread.</span><span class="sxs-lookup"><span data-stu-id="97180-128">There can be more than one stepper per thread.</span></span> <span data-ttu-id="97180-129">Por exemplo, um ponto de interrupção pode ser obtido ao passar sobre uma função, e o usuário deseja iniciar uma nova operação de deslocamento dentro dessa função.</span><span class="sxs-lookup"><span data-stu-id="97180-129">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="97180-130">É responsabilidade do depurador para determinar como lidar com essa situação.</span><span class="sxs-lookup"><span data-stu-id="97180-130">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="97180-131">O depurador poderá cancelar a operação de passo a passo original ou aninhar as duas operações.</span><span class="sxs-lookup"><span data-stu-id="97180-131">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="97180-132">O `ICorDebugStepper` interface dá suporte a ambas as opções.</span><span class="sxs-lookup"><span data-stu-id="97180-132">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="97180-133">Um seletor pode migrar entre threads, se o common language runtime (CLR) faz uma chamada de thread cruzado, com marshaling.</span><span class="sxs-lookup"><span data-stu-id="97180-133">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97180-134">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="97180-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97180-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="97180-135">Requirements</span></span>  
 <span data-ttu-id="97180-136">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97180-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97180-137">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97180-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97180-138">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97180-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97180-139">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97180-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97180-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97180-140">See also</span></span>
- [<span data-ttu-id="97180-141">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="97180-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
