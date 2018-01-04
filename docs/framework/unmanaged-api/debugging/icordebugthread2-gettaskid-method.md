---
title: "Método ICorDebugThread2::GetTaskID"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2.GetTaskID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b94478a0dfb8cc4d90dea611620238024634799
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="914c6-102">Método ICorDebugThread2::GetTaskID</span><span class="sxs-lookup"><span data-stu-id="914c6-102">ICorDebugThread2::GetTaskID Method</span></span>
<span data-ttu-id="914c6-103">Obtém o identificador da tarefa em execução neste thread.</span><span class="sxs-lookup"><span data-stu-id="914c6-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="914c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="914c6-104">Syntax</span></span>  
  
```  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="914c6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="914c6-105">Parameters</span></span>  
 `pTaskId`  
 <span data-ttu-id="914c6-106">[out] Um ponteiro para o identificador da tarefa em execução no thread representado pelo objeto ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="914c6-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="914c6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="914c6-107">Remarks</span></span>  
 <span data-ttu-id="914c6-108">Uma tarefa só pode ser executado no thread se o thread está associado uma conexão.</span><span class="sxs-lookup"><span data-stu-id="914c6-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="914c6-109">`GetTaskID`Retorna zero `pTaskId` se o thread não está associado uma conexão.</span><span class="sxs-lookup"><span data-stu-id="914c6-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="914c6-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="914c6-110">Requirements</span></span>  
 <span data-ttu-id="914c6-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="914c6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="914c6-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="914c6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="914c6-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="914c6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="914c6-114">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="914c6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
