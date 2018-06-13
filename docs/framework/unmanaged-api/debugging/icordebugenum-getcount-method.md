---
title: Método ICorDebugEnum::GetCount
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::GetCount
helpviewer_keywords:
- ICorDebugEnum::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: d8a74304-1cb2-4977-a21d-e1af48c563ff
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5eddad89c60f25c957a06822d54cc73501b974ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415623"
---
# <a name="icordebugenumgetcount-method"></a><span data-ttu-id="10402-102">Método ICorDebugEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="10402-102">ICorDebugEnum::GetCount Method</span></span>
<span data-ttu-id="10402-103">Obtém o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="10402-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10402-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10402-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10402-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="10402-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="10402-106">[out] Um ponteiro para o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="10402-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10402-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="10402-107">Requirements</span></span>  
 <span data-ttu-id="10402-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10402-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10402-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10402-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10402-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10402-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10402-111">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10402-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
