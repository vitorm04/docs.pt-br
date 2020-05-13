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
ms.openlocfilehash: 7c64823e1a5c519eb74b508af093afeb1132e608
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210079"
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="02b48-102">Método ICorDebugReferenceValue::Dereference</span><span class="sxs-lookup"><span data-stu-id="02b48-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="02b48-103">Obtém o objeto que é referenciado.</span><span class="sxs-lookup"><span data-stu-id="02b48-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02b48-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02b48-104">Syntax</span></span>  
  
```cpp  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02b48-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="02b48-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="02b48-106">fora Um ponteiro para o endereço de um ICorDebugValue que representa o objeto ao qual esse objeto ICorDebugReferenceValue aponta.</span><span class="sxs-lookup"><span data-stu-id="02b48-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02b48-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="02b48-107">Remarks</span></span>  
 <span data-ttu-id="02b48-108">O `ICorDebugValue` objeto é válido somente enquanto sua referência ainda não foi desabilitada.</span><span class="sxs-lookup"><span data-stu-id="02b48-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02b48-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="02b48-109">Requirements</span></span>  
 <span data-ttu-id="02b48-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02b48-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02b48-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02b48-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02b48-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02b48-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02b48-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02b48-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
