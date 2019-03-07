---
title: Método ICorDebugThread::CreateEval
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2016795e7b2c0588e2bd69e764fb96f7f90b24d0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480657"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="eab65-102">Método ICorDebugThread::CreateEval</span><span class="sxs-lookup"><span data-stu-id="eab65-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="eab65-103">Cria um objeto ICorDebugEval que coleta e expõe a funcionalidade deste ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="eab65-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eab65-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eab65-104">Syntax</span></span>  
  
```  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eab65-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eab65-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="eab65-106">[out] Um ponteiro para o endereço de um `ICorDebugEval` objeto que coleta e expõe a funcionalidade desse thread.</span><span class="sxs-lookup"><span data-stu-id="eab65-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eab65-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="eab65-107">Remarks</span></span>  
 <span data-ttu-id="eab65-108">O objeto de avaliação enviará por push uma nova cadeia no thread antes de fazer sua computação.</span><span class="sxs-lookup"><span data-stu-id="eab65-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="eab65-109">Isso interrompe a computação que está sendo executada atualmente no thread até que a avaliação for concluída.</span><span class="sxs-lookup"><span data-stu-id="eab65-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eab65-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eab65-110">Requirements</span></span>  
 <span data-ttu-id="eab65-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eab65-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eab65-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eab65-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eab65-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eab65-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eab65-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eab65-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
