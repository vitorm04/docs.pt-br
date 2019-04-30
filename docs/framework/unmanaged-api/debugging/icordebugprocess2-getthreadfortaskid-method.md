---
title: Método ICorDebugProcess2::GetThreadForTaskID
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetThreadForTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetThreadForTaskID
helpviewer_keywords:
- ICorDebugProcess2::GetThreadForTaskId method [.NET Framework debugging]
- GetThreadForTaskID method [.NET Framework debugging]
ms.assetid: 32d54a5b-8ad3-405b-a1b9-0936a3b49d1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa1f6852544dddcdf514b14710ade3949818c93e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948858"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="ad9e2-102">Método ICorDebugProcess2::GetThreadForTaskID</span><span class="sxs-lookup"><span data-stu-id="ad9e2-102">ICorDebugProcess2::GetThreadForTaskID Method</span></span>
<span data-ttu-id="ad9e2-103">Obtém o thread no qual a tarefa com o identificador especificado está em execução.</span><span class="sxs-lookup"><span data-stu-id="ad9e2-103">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad9e2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad9e2-104">Syntax</span></span>  
  
```  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad9e2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ad9e2-105">Parameters</span></span>  
 `taskid`  
 <span data-ttu-id="ad9e2-106">[in] O identificador da tarefa.</span><span class="sxs-lookup"><span data-stu-id="ad9e2-106">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="ad9e2-107">[out] Um ponteiro para o endereço de um objeto de ICorDebugThread2 que representa o thread a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="ad9e2-107">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad9e2-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="ad9e2-108">Remarks</span></span>  
 <span data-ttu-id="ad9e2-109">O host pode definir o identificador de tarefa usando o [iclrtask:: Settaskidentifier](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="ad9e2-109">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad9e2-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad9e2-110">Requirements</span></span>  
 <span data-ttu-id="ad9e2-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad9e2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad9e2-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad9e2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad9e2-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad9e2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad9e2-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad9e2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
