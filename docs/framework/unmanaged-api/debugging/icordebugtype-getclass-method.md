---
title: Método ICorDebugType::GetClass
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
ms.openlocfilehash: 3a895f432ed640cc35a492df0c91cece34893062
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122362"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="0c7b7-102">Método ICorDebugType::GetClass</span><span class="sxs-lookup"><span data-stu-id="0c7b7-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="0c7b7-103">Obtém um ponteiro de interface para um ICorDebugClass que representa o tipo genérico não instanciado.</span><span class="sxs-lookup"><span data-stu-id="0c7b7-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c7b7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c7b7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c7b7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0c7b7-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="0c7b7-106">fora Um ponteiro para o endereço de uma interface de `ICorDebugClass` que representa o tipo genérico não instanciado.</span><span class="sxs-lookup"><span data-stu-id="0c7b7-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c7b7-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="0c7b7-107">Remarks</span></span>  
 <span data-ttu-id="0c7b7-108">`GetClass` pode ser chamado somente sob determinadas condições.</span><span class="sxs-lookup"><span data-stu-id="0c7b7-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="0c7b7-109">Chame [ICorDebugType:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) antes de chamar `GetClass`.</span><span class="sxs-lookup"><span data-stu-id="0c7b7-109">Call [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="0c7b7-110">Se `ICorDebugType::GetType` retornar um valor de CorElementType que seja ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, `GetClass` poderá ser chamado para obter o tipo não instanciado para um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="0c7b7-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c7b7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0c7b7-111">Requirements</span></span>  
 <span data-ttu-id="0c7b7-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c7b7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c7b7-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c7b7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c7b7-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c7b7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c7b7-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c7b7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
