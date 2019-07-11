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
ms.openlocfilehash: 54981be7104eb04ac6347ad13b61a69f40d4377c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770615"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="6158a-102">Método ICorDebugThread::GetHandle</span><span class="sxs-lookup"><span data-stu-id="6158a-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="6158a-103">Obtém o identificador atual para a parte ativa deste ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="6158a-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6158a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6158a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6158a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6158a-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="6158a-106">[out] Um ponteiro para um HTHREAD que é o identificador de parte ativa desse thread.</span><span class="sxs-lookup"><span data-stu-id="6158a-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6158a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="6158a-107">Remarks</span></span>  
 <span data-ttu-id="6158a-108">O identificador pode mudar, pois o processo é executado e pode ser diferente para diferentes partes do thread.</span><span class="sxs-lookup"><span data-stu-id="6158a-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="6158a-109">Esse identificador pertence a API de depuração.</span><span class="sxs-lookup"><span data-stu-id="6158a-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="6158a-110">O depurador deve duplicá-lo antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="6158a-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6158a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6158a-111">Requirements</span></span>  
 <span data-ttu-id="6158a-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6158a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6158a-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6158a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6158a-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6158a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6158a-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6158a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
