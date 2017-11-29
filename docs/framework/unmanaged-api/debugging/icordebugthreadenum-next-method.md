---
title: "Método ICorDebugThreadEnum::Next"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThreadEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThreadEnum::Next
helpviewer_keywords:
- ICorDebugThreadEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: f967c93d-9a7f-4aaf-99a1-a1317899ff3f
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cb26dd4cd625c025685113611a189b51a4d56a99
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="d44a7-102">Método ICorDebugThreadEnum::Next</span><span class="sxs-lookup"><span data-stu-id="d44a7-102">ICorDebugThreadEnum::Next Method</span></span>
<span data-ttu-id="d44a7-103">Obtém o número de instâncias de ICorDebugThread especificados de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="d44a7-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d44a7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d44a7-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d44a7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d44a7-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d44a7-106">[in] O número de `ICorDebugThread` instâncias a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="d44a7-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="d44a7-107">[out] Uma matriz de ponteiros, cada qual apontando para um `ICorDebugThread` objeto que representa um segmento.</span><span class="sxs-lookup"><span data-stu-id="d44a7-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d44a7-108">[out] Ponteiro para o número de `ICorDebugThread` , na verdade, retornadas de instâncias.</span><span class="sxs-lookup"><span data-stu-id="d44a7-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="d44a7-109">Esse valor pode ser null se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="d44a7-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d44a7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d44a7-110">Requirements</span></span>  
 <span data-ttu-id="d44a7-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d44a7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d44a7-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d44a7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d44a7-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d44a7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d44a7-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d44a7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
