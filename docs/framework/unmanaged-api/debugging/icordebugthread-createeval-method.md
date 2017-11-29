---
title: "Método ICorDebugThread::CreateEval"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.CreateEval
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aebabf12e6dcf12f0e1e1f24ec2ad69ea55ec86c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="8acc8-102">Método ICorDebugThread::CreateEval</span><span class="sxs-lookup"><span data-stu-id="8acc8-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="8acc8-103">Cria um objeto ICorDebugEval que coleta e expõe a funcionalidade deste ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="8acc8-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8acc8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8acc8-104">Syntax</span></span>  
  
```  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8acc8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8acc8-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="8acc8-106">[out] Um ponteiro para o endereço de uma `ICorDebugEval` objeto que coleta e expõe a funcionalidade deste thread.</span><span class="sxs-lookup"><span data-stu-id="8acc8-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8acc8-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8acc8-107">Remarks</span></span>  
 <span data-ttu-id="8acc8-108">O objeto de avaliação enviará por push uma nova cadeia no thread antes de fazer sua computação.</span><span class="sxs-lookup"><span data-stu-id="8acc8-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="8acc8-109">Isso interrompe a computação atualmente sendo executada no thread de até que a avaliação seja concluída.</span><span class="sxs-lookup"><span data-stu-id="8acc8-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8acc8-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8acc8-110">Requirements</span></span>  
 <span data-ttu-id="8acc8-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8acc8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8acc8-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8acc8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8acc8-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8acc8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8acc8-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8acc8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
