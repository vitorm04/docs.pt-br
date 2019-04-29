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
ms.openlocfilehash: b436fa14322d444a6c8b515ba8e50698eecb95ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783013"
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="4252f-102">Método ICorDebugReferenceValue::Dereference</span><span class="sxs-lookup"><span data-stu-id="4252f-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="4252f-103">Obtém o objeto referenciado.</span><span class="sxs-lookup"><span data-stu-id="4252f-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4252f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4252f-104">Syntax</span></span>  
  
```  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4252f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4252f-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="4252f-106">[out] Um ponteiro para o endereço de um ICorDebugValue que representa o objeto para o qual este objeto ICorDebugReferenceValue aponta.</span><span class="sxs-lookup"><span data-stu-id="4252f-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4252f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4252f-107">Remarks</span></span>  
 <span data-ttu-id="4252f-108">O `ICorDebugValue` objeto é válido somente enquanto sua referência ainda não tiver sido desabilitada.</span><span class="sxs-lookup"><span data-stu-id="4252f-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4252f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4252f-109">Requirements</span></span>  
 <span data-ttu-id="4252f-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4252f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4252f-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4252f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4252f-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4252f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4252f-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4252f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
