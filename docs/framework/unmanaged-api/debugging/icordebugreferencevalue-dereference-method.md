---
title: Método ICorDebugReferenceValue::Dereference
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a0fd1981e7da5af19cf3a422c6008d373e9ac92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="a0ab9-102">Método ICorDebugReferenceValue::Dereference</span><span class="sxs-lookup"><span data-stu-id="a0ab9-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="a0ab9-103">Obtém o objeto referenciado.</span><span class="sxs-lookup"><span data-stu-id="a0ab9-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0ab9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0ab9-104">Syntax</span></span>  
  
```  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0ab9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a0ab9-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="a0ab9-106">[out] Um ponteiro para o endereço de um ICorDebugValue que representa o objeto para o qual este objeto ICorDebugReferenceValue aponta.</span><span class="sxs-lookup"><span data-stu-id="a0ab9-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0ab9-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a0ab9-107">Remarks</span></span>  
 <span data-ttu-id="a0ab9-108">O `ICorDebugValue` objeto é válido apenas enquanto sua referência ainda não foram desabilitada.</span><span class="sxs-lookup"><span data-stu-id="a0ab9-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0ab9-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a0ab9-109">Requirements</span></span>  
 <span data-ttu-id="a0ab9-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0ab9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0ab9-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0ab9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0ab9-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0ab9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0ab9-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0ab9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
