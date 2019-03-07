---
title: Método ICorDebugThread2::GetTaskID
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 417f99c2b9fa7e77f8696c27cb3929c92956c08c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494643"
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="8794c-102">Método ICorDebugThread2::GetTaskID</span><span class="sxs-lookup"><span data-stu-id="8794c-102">ICorDebugThread2::GetTaskID Method</span></span>
<span data-ttu-id="8794c-103">Obtém o identificador da tarefa em execução nesse thread.</span><span class="sxs-lookup"><span data-stu-id="8794c-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8794c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8794c-104">Syntax</span></span>  
  
```  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8794c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8794c-105">Parameters</span></span>  
 `pTaskId`  
 <span data-ttu-id="8794c-106">[out] Um ponteiro para o identificador da tarefa em execução no thread representado por esse objeto ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="8794c-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8794c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8794c-107">Remarks</span></span>  
 <span data-ttu-id="8794c-108">Uma tarefa só pode ser executado no thread, se o thread estiver associado uma conexão.</span><span class="sxs-lookup"><span data-stu-id="8794c-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="8794c-109">`GetTaskID` Retorna zero `pTaskId` se o thread não está associado uma conexão.</span><span class="sxs-lookup"><span data-stu-id="8794c-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8794c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8794c-110">Requirements</span></span>  
 <span data-ttu-id="8794c-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8794c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8794c-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8794c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8794c-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8794c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8794c-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8794c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
