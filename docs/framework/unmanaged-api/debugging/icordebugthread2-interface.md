---
title: Interface ICorDebugThread2
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82648714c375998e9daa1bb59cd9ebd9802b5794
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153927"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="657a4-102">Interface ICorDebugThread2</span><span class="sxs-lookup"><span data-stu-id="657a4-102">ICorDebugThread2 Interface</span></span>
<span data-ttu-id="657a4-103">Serve como uma extensão lógica para a interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="657a4-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="657a4-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="657a4-104">Methods</span></span>  
  
|<span data-ttu-id="657a4-105">Método</span><span class="sxs-lookup"><span data-stu-id="657a4-105">Method</span></span>|<span data-ttu-id="657a4-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="657a4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="657a4-107">Método GetActiveFunctions</span><span class="sxs-lookup"><span data-stu-id="657a4-107">GetActiveFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="657a4-108">Obtém uma matriz de instâncias COR_ACTIVE_FUNCTION que contêm dados sobre as funções do Active Directory em quadros de um thread.</span><span class="sxs-lookup"><span data-stu-id="657a4-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="657a4-109">Método GetConnectionID</span><span class="sxs-lookup"><span data-stu-id="657a4-109">GetConnectionID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="657a4-110">Obtém um identificador de conexão para este `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="657a4-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="657a4-111">Método GetTaskID</span><span class="sxs-lookup"><span data-stu-id="657a4-111">GetTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|<span data-ttu-id="657a4-112">Obtém um identificador de tarefa para este `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="657a4-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="657a4-113">Método GetVolatileOSThreadID</span><span class="sxs-lookup"><span data-stu-id="657a4-113">GetVolatileOSThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="657a4-114">Obtém o identificador de thread do sistema operacional para este `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="657a4-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="657a4-115">Método InterceptCurrentException</span><span class="sxs-lookup"><span data-stu-id="657a4-115">InterceptCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="657a4-116">Permite que um depurador interceptar a exceção atual em um thread.</span><span class="sxs-lookup"><span data-stu-id="657a4-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="657a4-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="657a4-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="657a4-118">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="657a4-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="657a4-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="657a4-119">Requirements</span></span>  
 <span data-ttu-id="657a4-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="657a4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="657a4-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="657a4-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="657a4-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="657a4-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="657a4-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="657a4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="657a4-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="657a4-124">See also</span></span>

- [<span data-ttu-id="657a4-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="657a4-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
