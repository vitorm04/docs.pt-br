---
title: Interface ICorDebugRegisterSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet
helpviewer_keywords: ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ccff205758dee2ffc6a6432ab20b3310147eb06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="48b2c-102">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="48b2c-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="48b2c-103">Representa o conjunto de registros disponíveis no computador que está executando o código.</span><span class="sxs-lookup"><span data-stu-id="48b2c-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="48b2c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="48b2c-104">Methods</span></span>  
  
|<span data-ttu-id="48b2c-105">Método</span><span class="sxs-lookup"><span data-stu-id="48b2c-105">Method</span></span>|<span data-ttu-id="48b2c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="48b2c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="48b2c-107">Método GetRegisters</span><span class="sxs-lookup"><span data-stu-id="48b2c-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|<span data-ttu-id="48b2c-108">Obtém o valor de cada registro (no computador que está executando código) que é especificado pela máscara de bits.</span><span class="sxs-lookup"><span data-stu-id="48b2c-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="48b2c-109">Método GetRegistersAvailable</span><span class="sxs-lookup"><span data-stu-id="48b2c-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="48b2c-110">Obtém um pouco máscara indicando que registra neste `ICorDebugRegisterSet` estão disponíveis no momento.</span><span class="sxs-lookup"><span data-stu-id="48b2c-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="48b2c-111">Método GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="48b2c-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="48b2c-112">Obtém o contexto do thread atual.</span><span class="sxs-lookup"><span data-stu-id="48b2c-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="48b2c-113">Método SetRegisters</span><span class="sxs-lookup"><span data-stu-id="48b2c-113">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|<span data-ttu-id="48b2c-114">Não implementado para o .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="48b2c-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="48b2c-115">Método SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="48b2c-115">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="48b2c-116">Não implementado para o .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="48b2c-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48b2c-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="48b2c-117">Remarks</span></span>  
 <span data-ttu-id="48b2c-118">O `ICorDebugRegisterSet` interface oferece suporte a registros somente 32 bits.</span><span class="sxs-lookup"><span data-stu-id="48b2c-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="48b2c-119">Use o [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface em plataformas, como IA-64 que exigem registros adicionais.</span><span class="sxs-lookup"><span data-stu-id="48b2c-119">Use the [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48b2c-120">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="48b2c-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48b2c-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48b2c-121">Requirements</span></span>  
 <span data-ttu-id="48b2c-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48b2c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48b2c-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48b2c-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48b2c-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48b2c-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48b2c-125">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48b2c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48b2c-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48b2c-126">See Also</span></span>  
 [<span data-ttu-id="48b2c-127">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="48b2c-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="48b2c-128">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="48b2c-128">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
