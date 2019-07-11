---
title: Método ICorDebugChain::GetCallee
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79743b78ea3d19bab4756b580d2feddd07e0a23b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745014"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="da333-102">Método ICorDebugChain::GetCallee</span><span class="sxs-lookup"><span data-stu-id="da333-102">ICorDebugChain::GetCallee Method</span></span>
<span data-ttu-id="da333-103">Obtém a cadeia que foi chamada por essa cadeia.</span><span class="sxs-lookup"><span data-stu-id="da333-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da333-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da333-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da333-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="da333-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="da333-106">[out] Um ponteiro para o endereço de um objeto de ICorDebugChain que representa a cadeia de chamada.</span><span class="sxs-lookup"><span data-stu-id="da333-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="da333-107">Se esta cadeia está sendo executado (ou seja, se essa cadeia não está aguardando uma cadeia de chamada retornar), `ppChain` será nulo.</span><span class="sxs-lookup"><span data-stu-id="da333-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da333-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="da333-108">Remarks</span></span>  
 <span data-ttu-id="da333-109">Esta cadeia aguardará para a cadeia de chamada retornar antes de retomar a execução.</span><span class="sxs-lookup"><span data-stu-id="da333-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="da333-110">A cadeia de chamada pode ser em outro thread no caso de chamadas de com marshaling entre threads.</span><span class="sxs-lookup"><span data-stu-id="da333-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da333-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da333-111">Requirements</span></span>  
 <span data-ttu-id="da333-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da333-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da333-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da333-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da333-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da333-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da333-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da333-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
