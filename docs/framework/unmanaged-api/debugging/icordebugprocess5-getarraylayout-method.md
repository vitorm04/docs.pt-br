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
ms.openlocfilehash: 332de11790e78b712a429365bd89cc9e41539edc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948753"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="079c2-102">Método ICorDebugProcess5::GetArrayLayout</span><span class="sxs-lookup"><span data-stu-id="079c2-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="079c2-103">Fornece informações sobre o layout dos tipos de matriz.</span><span class="sxs-lookup"><span data-stu-id="079c2-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="079c2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="079c2-104">Syntax</span></span>  
  
```  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="079c2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="079c2-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="079c2-106">[in] Um [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token que especifica a matriz cujo layout é desejado.</span><span class="sxs-lookup"><span data-stu-id="079c2-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="079c2-107">[out] Um ponteiro para um [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) estrutura que contém informações sobre o layout da matriz na memória.</span><span class="sxs-lookup"><span data-stu-id="079c2-107">[out] A pointer to a [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="079c2-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="079c2-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="079c2-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="079c2-109">Requirements</span></span>  
 <span data-ttu-id="079c2-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="079c2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="079c2-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="079c2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="079c2-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="079c2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="079c2-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="079c2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="079c2-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="079c2-114">See also</span></span>

- [<span data-ttu-id="079c2-115">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="079c2-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="079c2-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="079c2-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
