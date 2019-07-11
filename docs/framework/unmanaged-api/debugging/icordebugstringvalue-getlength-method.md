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
ms.openlocfilehash: b13fe65f892a222abb126aa9237b802507738b7f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771612"
---
# <a name="icordebugstringvaluegetlength-method"></a><span data-ttu-id="c4ebb-102">Método ICorDebugStringValue::GetLength</span><span class="sxs-lookup"><span data-stu-id="c4ebb-102">ICorDebugStringValue::GetLength Method</span></span>
<span data-ttu-id="c4ebb-103">Obtém o número de caracteres na cadeia de caracteres referenciada por este ICorDebugStringValue.</span><span class="sxs-lookup"><span data-stu-id="c4ebb-103">Gets the number of characters in the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4ebb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4ebb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4ebb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c4ebb-105">Parameters</span></span>  
 `pcchString`  
 <span data-ttu-id="c4ebb-106">[out] Um ponteiro para um valor que especifica o comprimento da cadeia de caracteres referenciada por este `ICorDebugStringValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="c4ebb-106">[out] A pointer to a value that specifies the length of the string referenced by this `ICorDebugStringValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4ebb-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c4ebb-107">Requirements</span></span>  
 <span data-ttu-id="c4ebb-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4ebb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4ebb-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4ebb-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4ebb-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4ebb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4ebb-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4ebb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
