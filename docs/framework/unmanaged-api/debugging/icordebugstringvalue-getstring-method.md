---
title: Método ICorDebugStringValue::GetString
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetString
helpviewer_keywords:
- ICorDebugStringValue::GetString method [.NET Framework debugging]
- GetString method, ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: 2b94bda7-09ee-435d-91b9-c4e31af1896c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bf62d8855b3f9de5629b9cfc6e0bcd0878a0d17
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489911"
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="be75e-102">Método ICorDebugStringValue::GetString</span><span class="sxs-lookup"><span data-stu-id="be75e-102">ICorDebugStringValue::GetString Method</span></span>
<span data-ttu-id="be75e-103">Obtém a cadeia de caracteres referenciada por este ICorDebugStringValue.</span><span class="sxs-lookup"><span data-stu-id="be75e-103">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be75e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be75e-104">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]   
        WCHAR       szString[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be75e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="be75e-105">Parameters</span></span>  
 `cchString`  
 <span data-ttu-id="be75e-106">[in] O tamanho do `szString` matriz.</span><span class="sxs-lookup"><span data-stu-id="be75e-106">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="be75e-107">[out] Um ponteiro para o número de caracteres retornados no `szString` matriz.</span><span class="sxs-lookup"><span data-stu-id="be75e-107">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="be75e-108">[out] Uma matriz que armazena a cadeia de caracteres recuperada.</span><span class="sxs-lookup"><span data-stu-id="be75e-108">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be75e-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="be75e-109">Requirements</span></span>  
 <span data-ttu-id="be75e-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be75e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be75e-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be75e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be75e-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be75e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be75e-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be75e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
