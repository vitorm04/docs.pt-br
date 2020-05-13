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
ms.openlocfilehash: 89be29c770098d92ce3c47f7c45b1bb8580f2edb
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213511"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="aa06a-102">Método ICorDebugProcess2::GetThreadForTaskID</span><span class="sxs-lookup"><span data-stu-id="aa06a-102">ICorDebugProcess2::GetThreadForTaskID Method</span></span>
<span data-ttu-id="aa06a-103">Obtém o thread no qual a tarefa com o identificador especificado está em execução.</span><span class="sxs-lookup"><span data-stu-id="aa06a-103">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa06a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa06a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa06a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa06a-105">Parameters</span></span>  
 `taskid`  
 <span data-ttu-id="aa06a-106">no O identificador da tarefa.</span><span class="sxs-lookup"><span data-stu-id="aa06a-106">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="aa06a-107">fora Um ponteiro para o endereço de um objeto ICorDebugThread2 que representa o thread a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="aa06a-107">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa06a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa06a-108">Remarks</span></span>  
 <span data-ttu-id="aa06a-109">O host pode definir o identificador de tarefa usando o método [ICLRTask:: SetTaskIdentifier](../hosting/iclrtask-settaskidentifier-method.md) .</span><span class="sxs-lookup"><span data-stu-id="aa06a-109">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa06a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa06a-110">Requirements</span></span>  
 <span data-ttu-id="aa06a-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa06a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa06a-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa06a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa06a-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa06a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa06a-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa06a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
