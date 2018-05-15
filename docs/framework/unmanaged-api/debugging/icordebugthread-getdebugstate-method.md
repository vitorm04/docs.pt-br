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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95d9696e29bc1b460c94d7f4d8afd3de82653333
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="702b2-102">Método ICorDebugThread::GetDebugState</span><span class="sxs-lookup"><span data-stu-id="702b2-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="702b2-103">Obtém o estado de depuração atual deste objeto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="702b2-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="702b2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="702b2-104">Syntax</span></span>  
  
```  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="702b2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="702b2-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="702b2-106">[out] Um ponteiro para uma combinação bit a bit dos valores de enumeração CorDebugThreadState que descreve o estado de depuração atual deste thread.</span><span class="sxs-lookup"><span data-stu-id="702b2-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="702b2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="702b2-107">Remarks</span></span>  
 <span data-ttu-id="702b2-108">Se o processo está parado no momento, `pState` representa o estado de depuração que deve existir para esse thread se o processo continuar, não o estado real atual deste thread.</span><span class="sxs-lookup"><span data-stu-id="702b2-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="702b2-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="702b2-109">Requirements</span></span>  
 <span data-ttu-id="702b2-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="702b2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="702b2-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="702b2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="702b2-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="702b2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="702b2-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="702b2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
