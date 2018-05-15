---
title: Método ICorDebugArrayValue::HasBaseIndicies
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.HasBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::HasBaseIndicies
helpviewer_keywords:
- HasBaseIndicies method [.NET Framework debugging]
- ICorDebugArrayValue::HasBaseIndicies method [.NET Framework debugging]
ms.assetid: aa26df07-e0a6-4608-bdef-d4afafec89aa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 574df434360dfab644a4c937dac46ebc3871a53a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="61ca2-102">Método ICorDebugArrayValue::HasBaseIndicies</span><span class="sxs-lookup"><span data-stu-id="61ca2-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="61ca2-103">Obtém um valor que indica se todas as dimensões dessa matriz tem um índice de base do diferente de zero.</span><span class="sxs-lookup"><span data-stu-id="61ca2-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61ca2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61ca2-104">Syntax</span></span>  
  
```  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61ca2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="61ca2-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="61ca2-106">[out] Um ponteiro para um valor booliano que é `true` se uma ou mais dimensões deste `ICorDebugArrayValue` objeto tem um índice de base não-zero; caso contrário, o valor booliano é `false`.</span><span class="sxs-lookup"><span data-stu-id="61ca2-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61ca2-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61ca2-107">Requirements</span></span>  
 <span data-ttu-id="61ca2-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61ca2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61ca2-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61ca2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61ca2-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61ca2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61ca2-111">**Versões do .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61ca2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
