---
title: Método ICorDebugType::GetFirstTypeParameter
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetFirstTypeParameter
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type:
- apiref
ms.openlocfilehash: 4dbc042143e68dc962eb21b2bf741cbaefc1977e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122351"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="3e14d-102">Método ICorDebugType::GetFirstTypeParameter</span><span class="sxs-lookup"><span data-stu-id="3e14d-102">ICorDebugType::GetFirstTypeParameter Method</span></span>
<span data-ttu-id="3e14d-103">Obtém um ponteiro de interface para um ICorDebugType que representa o primeiro parâmetro <xref:System.Type> do tipo representado por esse `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="3e14d-103">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e14d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e14d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e14d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3e14d-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="3e14d-106">fora Um ponteiro para o endereço de um objeto de `ICorDebugType` que representa o primeiro parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3e14d-106">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e14d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e14d-107">Remarks</span></span>  
 <span data-ttu-id="3e14d-108">`GetFirstTypeParameter` pode ser chamado em casos em que as informações adicionais sobre o tipo envolvam, no máximo, um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="3e14d-108">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="3e14d-109">Em particular, ele pode ser usado se o tipo for um ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ou ELEMENT_TYPE_PTR, conforme indicado pelo método [ICorDebugType:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3e14d-109">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e14d-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3e14d-110">Requirements</span></span>  
 <span data-ttu-id="3e14d-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e14d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e14d-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e14d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e14d-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e14d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e14d-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e14d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
