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
ms.openlocfilehash: 63d3df561a3b48a4b26426235455ef1a074512f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417954"
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="278fd-102">Método ICorDebugStringValue::GetString</span><span class="sxs-lookup"><span data-stu-id="278fd-102">ICorDebugStringValue::GetString Method</span></span>
<span data-ttu-id="278fd-103">Obtém a cadeia de caracteres referenciada por este ICorDebugStringValue.</span><span class="sxs-lookup"><span data-stu-id="278fd-103">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="278fd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="278fd-104">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]   
        WCHAR       szString[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="278fd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="278fd-105">Parameters</span></span>  
 `cchString`  
 <span data-ttu-id="278fd-106">[in] O tamanho do `szString` matriz.</span><span class="sxs-lookup"><span data-stu-id="278fd-106">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="278fd-107">[out] Um ponteiro para o número de caracteres retornados na `szString` matriz.</span><span class="sxs-lookup"><span data-stu-id="278fd-107">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="278fd-108">[out] Uma matriz que armazena a cadeia de caracteres recuperada.</span><span class="sxs-lookup"><span data-stu-id="278fd-108">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="278fd-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="278fd-109">Requirements</span></span>  
 <span data-ttu-id="278fd-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="278fd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="278fd-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="278fd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="278fd-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="278fd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="278fd-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="278fd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
