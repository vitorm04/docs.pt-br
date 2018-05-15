---
title: Método ICorDebugThread::GetID
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52962ea7d2cf3dd1822b1a36cc6cfcb56bc427f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="c4b52-102">Método ICorDebugThread::GetID</span><span class="sxs-lookup"><span data-stu-id="c4b52-102">ICorDebugThread::GetID Method</span></span>
<span data-ttu-id="c4b52-103">Obtém o identificador de sistema operacional atual da parte ativa deste ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="c4b52-103">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4b52-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4b52-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4b52-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c4b52-105">Parameters</span></span>  
 `pdwThreadId`  
 <span data-ttu-id="c4b52-106">[out] O identificador do segmento.</span><span class="sxs-lookup"><span data-stu-id="c4b52-106">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4b52-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c4b52-107">Remarks</span></span>  
 <span data-ttu-id="c4b52-108">O identificador de sistema operacional podendo ser alterado durante a execução de um processo e pode ser um valor diferente para partes diferentes do thread.</span><span class="sxs-lookup"><span data-stu-id="c4b52-108">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4b52-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c4b52-109">Requirements</span></span>  
 <span data-ttu-id="c4b52-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4b52-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4b52-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4b52-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4b52-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4b52-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4b52-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4b52-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
