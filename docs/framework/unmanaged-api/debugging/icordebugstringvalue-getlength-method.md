---
title: Método ICorDebugStringValue::GetLength
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetLength
helpviewer_keywords:
- ICorDebugStringValue::GetLength method [.NET Framework debugging]
- GetLength method [.NET Framework debugging]
ms.assetid: a1ebfc69-46a6-4225-8788-b7cfb2f15e1d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b168673e76beddd8ae0479b8daae009c5f057b2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494656"
---
# <a name="icordebugstringvaluegetlength-method"></a><span data-ttu-id="12046-102">Método ICorDebugStringValue::GetLength</span><span class="sxs-lookup"><span data-stu-id="12046-102">ICorDebugStringValue::GetLength Method</span></span>
<span data-ttu-id="12046-103">Obtém o número de caracteres na cadeia de caracteres referenciada por este ICorDebugStringValue.</span><span class="sxs-lookup"><span data-stu-id="12046-103">Gets the number of characters in the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12046-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12046-104">Syntax</span></span>  
  
```  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12046-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="12046-105">Parameters</span></span>  
 `pcchString`  
 <span data-ttu-id="12046-106">[out] Um ponteiro para um valor que especifica o comprimento da cadeia de caracteres referenciada por este `ICorDebugStringValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="12046-106">[out] A pointer to a value that specifies the length of the string referenced by this `ICorDebugStringValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12046-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="12046-107">Requirements</span></span>  
 <span data-ttu-id="12046-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12046-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12046-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12046-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12046-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12046-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12046-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12046-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
