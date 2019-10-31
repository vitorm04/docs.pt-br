---
title: Método ICorDebugReferenceValue::IsNull
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.IsNull
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type:
- apiref
ms.openlocfilehash: 9d5047b1d44f836d10b659f18cf885eba3b0e973
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139824"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="2cded-102">Método ICorDebugReferenceValue::IsNull</span><span class="sxs-lookup"><span data-stu-id="2cded-102">ICorDebugReferenceValue::IsNull Method</span></span>
<span data-ttu-id="2cded-103">Obtém um valor que indica se este ICorDebugReferenceValue é um valor nulo; nesse caso, o `ICorDebugReferenceValue` não aponta para um objeto.</span><span class="sxs-lookup"><span data-stu-id="2cded-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cded-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2cded-104">Syntax</span></span>  
  
```cpp  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cded-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2cded-105">Parameters</span></span>  
 `pbNull`  
 <span data-ttu-id="2cded-106">fora Um ponteiro para um valor booliano `true` se esse objeto `ICorDebugReferenceValue` for nulo; caso contrário, `pbNull` será `false`.</span><span class="sxs-lookup"><span data-stu-id="2cded-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cded-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2cded-107">Requirements</span></span>  
 <span data-ttu-id="2cded-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cded-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cded-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2cded-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2cded-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2cded-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cded-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cded-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
