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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0915027ce6a3768ff854eafc5496c5057081cc4d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499531"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="f3563-102">Método ICorDebugType::GetClass</span><span class="sxs-lookup"><span data-stu-id="f3563-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="f3563-103">Obtém um ponteiro de interface para um ICorDebugClass que representa o tipo genérico não instanciado.</span><span class="sxs-lookup"><span data-stu-id="f3563-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3563-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3563-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3563-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f3563-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="f3563-106">[out] Um ponteiro para o endereço de um `ICorDebugClass` interface que representa o tipo genérico não instanciado.</span><span class="sxs-lookup"><span data-stu-id="f3563-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3563-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f3563-107">Remarks</span></span>  
 <span data-ttu-id="f3563-108">`GetClass` pode ser chamado apenas sob determinadas condições.</span><span class="sxs-lookup"><span data-stu-id="f3563-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="f3563-109">Chame [icordebugtype:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) antes de chamar `GetClass`.</span><span class="sxs-lookup"><span data-stu-id="f3563-109">Call [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="f3563-110">Se `ICorDebugType::GetType` retorna um valor de CorElementType ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, `GetClass` pode ser chamado para obter o tipo não instanciado para um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="f3563-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3563-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f3563-111">Requirements</span></span>  
 <span data-ttu-id="f3563-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3563-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3563-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3563-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3563-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3563-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3563-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3563-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
