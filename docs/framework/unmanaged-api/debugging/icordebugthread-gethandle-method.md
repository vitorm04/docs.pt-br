---
title: Método ICorDebugThread::GetHandle
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 900fece1dd29f73f77b85ff08e4deff1396f8aaf
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484505"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="212eb-102">Método ICorDebugThread::GetHandle</span><span class="sxs-lookup"><span data-stu-id="212eb-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="212eb-103">Obtém o identificador atual para a parte ativa deste ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="212eb-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="212eb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="212eb-104">Syntax</span></span>  
  
```  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="212eb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="212eb-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="212eb-106">[out] Um ponteiro para um HTHREAD que é o identificador de parte ativa desse thread.</span><span class="sxs-lookup"><span data-stu-id="212eb-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="212eb-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="212eb-107">Remarks</span></span>  
 <span data-ttu-id="212eb-108">O identificador pode mudar, pois o processo é executado e pode ser diferente para diferentes partes do thread.</span><span class="sxs-lookup"><span data-stu-id="212eb-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="212eb-109">Esse identificador pertence a API de depuração.</span><span class="sxs-lookup"><span data-stu-id="212eb-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="212eb-110">O depurador deve duplicá-lo antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="212eb-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="212eb-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="212eb-111">Requirements</span></span>  
 <span data-ttu-id="212eb-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="212eb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="212eb-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="212eb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="212eb-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="212eb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="212eb-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="212eb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
