---
title: Método ICorDebugReferenceValue::SetValue
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::SetValue
helpviewer_keywords:
- SetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::SetValue method [.NET Framework debugging]
ms.assetid: 3d3f6eec-d772-401f-a028-1a2ecdc31e95
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 804aa4a6508713b2d6f2d154fc47e09638994468
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747368"
---
# <a name="icordebugreferencevaluesetvalue-method"></a><span data-ttu-id="c2df4-102">Método ICorDebugReferenceValue::SetValue</span><span class="sxs-lookup"><span data-stu-id="c2df4-102">ICorDebugReferenceValue::SetValue Method</span></span>
<span data-ttu-id="c2df4-103">Define o endereço de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="c2df4-103">Sets the specified memory address.</span></span> <span data-ttu-id="c2df4-104">Ou seja, esse método define esse ICorDebugReferenceValue para apontar para um objeto.</span><span class="sxs-lookup"><span data-stu-id="c2df4-104">That is, this method sets this ICorDebugReferenceValue to point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2df4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2df4-105">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2df4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2df4-106">Parameters</span></span>  
 `value`  
 <span data-ttu-id="c2df4-107">[in] Um `CORDB_ADDRESS` valor que especifica o endereço do objeto ao qual este `ICorDebugReferenceValue` pontos.</span><span class="sxs-lookup"><span data-stu-id="c2df4-107">[in] A `CORDB_ADDRESS` value that specifies the address of the object to which this `ICorDebugReferenceValue` points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2df4-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2df4-108">Requirements</span></span>  
 <span data-ttu-id="c2df4-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2df4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2df4-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2df4-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2df4-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2df4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2df4-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2df4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
