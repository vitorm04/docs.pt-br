---
title: "Método ICorDebugThread::CreateEval"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugThread.CreateEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 766677d9eef60c811c8537bc60bb8db29dd988c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="5490a-102">Método ICorDebugThread::CreateEval</span><span class="sxs-lookup"><span data-stu-id="5490a-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="5490a-103">Cria um objeto ICorDebugEval que coleta e expõe a funcionalidade deste ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="5490a-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5490a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5490a-104">Syntax</span></span>  
  
```  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5490a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5490a-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="5490a-106">[out] Um ponteiro para o endereço de uma `ICorDebugEval` objeto que coleta e expõe a funcionalidade deste thread.</span><span class="sxs-lookup"><span data-stu-id="5490a-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5490a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="5490a-107">Remarks</span></span>  
 <span data-ttu-id="5490a-108">O objeto de avaliação enviará por push uma nova cadeia no thread antes de fazer sua computação.</span><span class="sxs-lookup"><span data-stu-id="5490a-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="5490a-109">Isso interrompe a computação atualmente sendo executada no thread de até que a avaliação seja concluída.</span><span class="sxs-lookup"><span data-stu-id="5490a-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5490a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5490a-110">Requirements</span></span>  
 <span data-ttu-id="5490a-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5490a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5490a-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5490a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5490a-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5490a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5490a-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5490a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
