---
title: Método ICorDebugProcess5::GetArrayLayout
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetArrayLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5cff3f3f577a0c7ef04a226ec70a2722c89b5c8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496879"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="51194-102">Método ICorDebugProcess5::GetArrayLayout</span><span class="sxs-lookup"><span data-stu-id="51194-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="51194-103">Fornece informações sobre o layout dos tipos de matriz.</span><span class="sxs-lookup"><span data-stu-id="51194-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51194-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51194-104">Syntax</span></span>  
  
```  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51194-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="51194-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="51194-106">[in] Um [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token que especifica a matriz cujo layout é desejado.</span><span class="sxs-lookup"><span data-stu-id="51194-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="51194-107">[out] Um ponteiro para um [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) estrutura que contém informações sobre o layout da matriz na memória.</span><span class="sxs-lookup"><span data-stu-id="51194-107">[out] A pointer to a [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51194-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="51194-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51194-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="51194-109">Requirements</span></span>  
 <span data-ttu-id="51194-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51194-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51194-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51194-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51194-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51194-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51194-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51194-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51194-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51194-114">See also</span></span>
- [<span data-ttu-id="51194-115">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="51194-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="51194-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="51194-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
