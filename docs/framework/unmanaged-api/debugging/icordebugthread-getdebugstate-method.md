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
ms.openlocfilehash: 68df19120f2e0b45e73f9d5e137afc8a5e7ac513
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489885"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="f4308-102">Método ICorDebugThread::GetDebugState</span><span class="sxs-lookup"><span data-stu-id="f4308-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="f4308-103">Obtém o estado de depuração atual deste objeto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="f4308-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4308-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f4308-104">Syntax</span></span>  
  
```  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4308-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4308-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="f4308-106">[out] Um ponteiro para uma combinação bit a bit dos valores de enumeração CorDebugThreadState que descreve o estado de depuração atual deste thread.</span><span class="sxs-lookup"><span data-stu-id="f4308-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4308-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f4308-107">Remarks</span></span>  
 <span data-ttu-id="f4308-108">Se o processo for interrompido no momento, `pState` representa o estado de depuração que deve existir para esse thread se o processo de ser continuada, não o estado atual real desse thread.</span><span class="sxs-lookup"><span data-stu-id="f4308-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4308-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4308-109">Requirements</span></span>  
 <span data-ttu-id="f4308-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4308-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4308-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4308-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4308-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4308-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4308-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4308-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
