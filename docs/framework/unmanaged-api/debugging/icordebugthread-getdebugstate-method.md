---
title: "Método ICorDebugThread::GetDebugState"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetDebugState
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4e66cc976be59c519e48d7ef9285963e5109d848
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="4475e-102">Método ICorDebugThread::GetDebugState</span><span class="sxs-lookup"><span data-stu-id="4475e-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="4475e-103">Obtém o estado de depuração atual deste objeto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="4475e-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4475e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4475e-104">Syntax</span></span>  
  
```  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4475e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4475e-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="4475e-106">[out] Um ponteiro para uma combinação bit a bit dos valores de enumeração CorDebugThreadState que descreve o estado de depuração atual deste thread.</span><span class="sxs-lookup"><span data-stu-id="4475e-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4475e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4475e-107">Remarks</span></span>  
 <span data-ttu-id="4475e-108">Se o processo está parado no momento, `pState` representa o estado de depuração que deve existir para esse thread se o processo continuar, não o estado real atual deste thread.</span><span class="sxs-lookup"><span data-stu-id="4475e-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4475e-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4475e-109">Requirements</span></span>  
 <span data-ttu-id="4475e-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4475e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4475e-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4475e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4475e-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4475e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4475e-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4475e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
