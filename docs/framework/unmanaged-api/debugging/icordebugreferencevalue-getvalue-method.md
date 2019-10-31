---
title: Método ICorDebugReferenceValue::GetValue
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::GetValue method [.NET Framework debugging]
ms.assetid: 5da07f99-6c70-46ec-b997-5ab6fb7106cd
topic_type:
- apiref
ms.openlocfilehash: 7a2288eb84bd51795995032954e41525c2ce605a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137722"
---
# <a name="icordebugreferencevaluegetvalue-method"></a><span data-ttu-id="20bca-102">Método ICorDebugReferenceValue::GetValue</span><span class="sxs-lookup"><span data-stu-id="20bca-102">ICorDebugReferenceValue::GetValue Method</span></span>
<span data-ttu-id="20bca-103">Obtém o endereço de memória atual do objeto referenciado.</span><span class="sxs-lookup"><span data-stu-id="20bca-103">Gets the current memory address of the referenced object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20bca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="20bca-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] CORDB_ADDRESS   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20bca-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="20bca-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="20bca-106">fora Um ponteiro para um valor `CORDB_ADDRESS` que especifica o endereço do objeto ao qual esse objeto ICorDebugReferenceValue aponta.</span><span class="sxs-lookup"><span data-stu-id="20bca-106">[out] A pointer to a `CORDB_ADDRESS` value that specifies the address of the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20bca-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="20bca-107">Requirements</span></span>  
 <span data-ttu-id="20bca-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20bca-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20bca-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20bca-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20bca-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20bca-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20bca-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20bca-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
