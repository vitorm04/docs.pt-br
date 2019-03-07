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
ms.openlocfilehash: ed5a7657affde335acf79952d77bbdb7ac42c7a0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490457"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="5f219-102">Método ICorDebugChain::GetCallee</span><span class="sxs-lookup"><span data-stu-id="5f219-102">ICorDebugChain::GetCallee Method</span></span>
<span data-ttu-id="5f219-103">Obtém a cadeia que foi chamada por essa cadeia.</span><span class="sxs-lookup"><span data-stu-id="5f219-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f219-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f219-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f219-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5f219-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="5f219-106">[out] Um ponteiro para o endereço de um objeto de ICorDebugChain que representa a cadeia de chamada.</span><span class="sxs-lookup"><span data-stu-id="5f219-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="5f219-107">Se esta cadeia está sendo executado (ou seja, se essa cadeia não está aguardando uma cadeia de chamada retornar), `ppChain` será nulo.</span><span class="sxs-lookup"><span data-stu-id="5f219-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f219-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="5f219-108">Remarks</span></span>  
 <span data-ttu-id="5f219-109">Esta cadeia aguardará para a cadeia de chamada retornar antes de retomar a execução.</span><span class="sxs-lookup"><span data-stu-id="5f219-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="5f219-110">A cadeia de chamada pode ser em outro thread no caso de chamadas de com marshaling entre threads.</span><span class="sxs-lookup"><span data-stu-id="5f219-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f219-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5f219-111">Requirements</span></span>  
 <span data-ttu-id="5f219-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f219-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f219-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f219-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f219-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f219-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f219-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f219-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
