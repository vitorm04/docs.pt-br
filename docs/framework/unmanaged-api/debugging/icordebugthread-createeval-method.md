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
ms.openlocfilehash: 0c622e0eba27f501446d2b7d9d264ee0834e869c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133614"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="29958-102">Método ICorDebugThread::CreateEval</span><span class="sxs-lookup"><span data-stu-id="29958-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="29958-103">Cria um objeto ICorDebugEval que coleta e expõe a funcionalidade desse ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="29958-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29958-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29958-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29958-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="29958-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="29958-106">fora Um ponteiro para o endereço de um objeto `ICorDebugEval` que coleta e expõe a funcionalidade desse thread.</span><span class="sxs-lookup"><span data-stu-id="29958-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29958-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="29958-107">Remarks</span></span>  
 <span data-ttu-id="29958-108">O objeto de avaliação enviará por push uma nova cadeia no thread antes de fazer seu cálculo.</span><span class="sxs-lookup"><span data-stu-id="29958-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="29958-109">Isso interrompe a computação que está sendo executada atualmente no thread até que a avaliação seja concluída.</span><span class="sxs-lookup"><span data-stu-id="29958-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29958-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29958-110">Requirements</span></span>  
 <span data-ttu-id="29958-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29958-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29958-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29958-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29958-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29958-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29958-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29958-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
