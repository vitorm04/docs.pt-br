---
title: "Método ICorDebugChain::GetCallee"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetCallee
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3b584929d99e641e361de916c402a0d5723e53c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="73302-102">Método ICorDebugChain::GetCallee</span><span class="sxs-lookup"><span data-stu-id="73302-102">ICorDebugChain::GetCallee Method</span></span>
<span data-ttu-id="73302-103">Obtém a cadeia que foi chamada por essa cadeia.</span><span class="sxs-lookup"><span data-stu-id="73302-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73302-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73302-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73302-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="73302-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="73302-106">[out] Um ponteiro para o endereço de um objeto ICorDebugChain que representa a cadeia de chamada.</span><span class="sxs-lookup"><span data-stu-id="73302-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="73302-107">Se esta cadeia está em execução (ou seja, se essa cadeia não estiver esperando por uma cadeia de chamada retornar), `ppChain` será nulo.</span><span class="sxs-lookup"><span data-stu-id="73302-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73302-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="73302-108">Remarks</span></span>  
 <span data-ttu-id="73302-109">Esta cadeia de espera para a cadeia de chamada retornar antes de retomar a execução.</span><span class="sxs-lookup"><span data-stu-id="73302-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="73302-110">A cadeia de chamada pode ser em outro thread no caso de chamadas empacotadas entre threads.</span><span class="sxs-lookup"><span data-stu-id="73302-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73302-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="73302-111">Requirements</span></span>  
 <span data-ttu-id="73302-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73302-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73302-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73302-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73302-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73302-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73302-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73302-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
