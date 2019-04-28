---
title: Método ICorDebugProcess::GetHandle
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5d81564a34ed8e7ef75840e3a174661c36f5411
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994482"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="70cf3-102">Método ICorDebugProcess::GetHandle</span><span class="sxs-lookup"><span data-stu-id="70cf3-102">ICorDebugProcess::GetHandle Method</span></span>
<span data-ttu-id="70cf3-103">Obtém um identificador para o processo.</span><span class="sxs-lookup"><span data-stu-id="70cf3-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70cf3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70cf3-104">Syntax</span></span>  
  
```  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70cf3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="70cf3-105">Parameters</span></span>  
 `phProcessHandle`  
 <span data-ttu-id="70cf3-106">[out] Um ponteiro para um `HPROCESS` que é o identificador para o processo.</span><span class="sxs-lookup"><span data-stu-id="70cf3-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70cf3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="70cf3-107">Remarks</span></span>  
 <span data-ttu-id="70cf3-108">O identificador recuperado pertence a interface de depuração.</span><span class="sxs-lookup"><span data-stu-id="70cf3-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="70cf3-109">O depurador deve duplicar o identificador antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="70cf3-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70cf3-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="70cf3-110">Requirements</span></span>  
 <span data-ttu-id="70cf3-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70cf3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70cf3-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70cf3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70cf3-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70cf3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70cf3-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70cf3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
