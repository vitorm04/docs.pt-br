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
ms.openlocfilehash: 49f5ed8b24d81ba8f32a9fe0ad7488693718bde9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468553"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="51adc-102">Método ICorDebugArrayValue::HasBaseIndicies</span><span class="sxs-lookup"><span data-stu-id="51adc-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="51adc-103">Obtém um valor que indica se todas as dimensões desta matriz tem um índice de base de diferente de zero.</span><span class="sxs-lookup"><span data-stu-id="51adc-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51adc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51adc-104">Syntax</span></span>  
  
```  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51adc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="51adc-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="51adc-106">[out] Um ponteiro para um valor booliano que será `true` se um ou mais dimensões dessa `ICorDebugArrayValue` objeto tem um índice de base de diferente de zero; caso contrário, o valor booliano é `false`.</span><span class="sxs-lookup"><span data-stu-id="51adc-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51adc-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="51adc-107">Requirements</span></span>  
 <span data-ttu-id="51adc-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51adc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51adc-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51adc-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51adc-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51adc-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51adc-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51adc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
