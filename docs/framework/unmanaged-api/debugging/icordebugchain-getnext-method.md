---
title: "Método ICorDebugChain::GetNext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetNext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetNext
helpviewer_keywords:
- GetNext method [.NET Framework debugging]
- ICorDebugChain::GetNext method [.NET Framework debugging]
ms.assetid: 8d9744a5-e08b-4ab2-9855-5c22711cc1e6
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd01e13c49ef2aa0f55b18e40c1763f61be09a57
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetnext-method"></a><span data-ttu-id="ee772-102">Método ICorDebugChain::GetNext</span><span class="sxs-lookup"><span data-stu-id="ee772-102">ICorDebugChain::GetNext Method</span></span>
<span data-ttu-id="ee772-103">Obtém a próxima cadeia de quadros do thread.</span><span class="sxs-lookup"><span data-stu-id="ee772-103">Gets the next chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee772-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ee772-104">Syntax</span></span>  
  
```  
HRESULT GetNext (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee772-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee772-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="ee772-106">[out] Um ponteiro para o endereço de um objeto ICorDebugChain que representa a próxima cadeia de quadros para o segmento.</span><span class="sxs-lookup"><span data-stu-id="ee772-106">[out] A pointer to the address of an ICorDebugChain object that represents the next chain of frames for the thread.</span></span> <span data-ttu-id="ee772-107">Se essa cadeia é a cadeia de última `ppChain` é nulo.</span><span class="sxs-lookup"><span data-stu-id="ee772-107">If this chain is the last chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee772-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ee772-108">Requirements</span></span>  
 <span data-ttu-id="ee772-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee772-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee772-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee772-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee772-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee772-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee772-112">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee772-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
