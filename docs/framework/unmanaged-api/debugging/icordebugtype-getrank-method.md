---
title: "Método ICorDebugType::GetRank"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetRank
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetRank
helpviewer_keywords:
- GetRank method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetRank method [.NET Framework debugging]
ms.assetid: 72d3d927-f590-4f2d-8f60-448f3dfb96af
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af481f01202d8a864c5258720f06e67d0bbd1e2b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetrank-method"></a><span data-ttu-id="6fbd1-102">Método ICorDebugType::GetRank</span><span class="sxs-lookup"><span data-stu-id="6fbd1-102">ICorDebugType::GetRank Method</span></span>
<span data-ttu-id="6fbd1-103">Obtém o número de dimensões em um tipo de matriz.</span><span class="sxs-lookup"><span data-stu-id="6fbd1-103">Gets the number of dimensions in an array type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fbd1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6fbd1-104">Syntax</span></span>  
  
```  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6fbd1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6fbd1-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="6fbd1-106">[out] Um ponteiro para o número de dimensões.</span><span class="sxs-lookup"><span data-stu-id="6fbd1-106">[out] A pointer to the number of dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fbd1-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6fbd1-107">Requirements</span></span>  
 <span data-ttu-id="6fbd1-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fbd1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fbd1-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6fbd1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fbd1-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fbd1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fbd1-111">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fbd1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
