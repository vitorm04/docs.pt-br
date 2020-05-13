---
title: Método ICorDebugThread::GetDebugState
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
ms.openlocfilehash: 13125f60f596cb8a80d9c42c51a979f632de494b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379753"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="dd0cc-102">Método ICorDebugThread::GetDebugState</span><span class="sxs-lookup"><span data-stu-id="dd0cc-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="dd0cc-103">Obtém o estado de depuração atual deste objeto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="dd0cc-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd0cc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd0cc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd0cc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dd0cc-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="dd0cc-106">fora Um ponteiro para uma combinação de bits de valor de enumeração CorDebugThreadState que descreve o estado de depuração atual desse thread.</span><span class="sxs-lookup"><span data-stu-id="dd0cc-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd0cc-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd0cc-107">Remarks</span></span>  
 <span data-ttu-id="dd0cc-108">Se o processo estiver parado no momento, `pState` representará o estado de depuração que existiria para esse thread se o processo fosse continuado, não o estado real atual desse thread.</span><span class="sxs-lookup"><span data-stu-id="dd0cc-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd0cc-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dd0cc-109">Requirements</span></span>  
 <span data-ttu-id="dd0cc-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd0cc-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd0cc-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd0cc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd0cc-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd0cc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd0cc-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd0cc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
