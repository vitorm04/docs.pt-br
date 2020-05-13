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
ms.openlocfilehash: 878a57514af34730049864f17f4853c1237904c2
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379967"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="2fa1f-102">Método ICorDebugType::GetClass</span><span class="sxs-lookup"><span data-stu-id="2fa1f-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="2fa1f-103">Obtém um ponteiro de interface para um ICorDebugClass que representa o tipo genérico não instanciado.</span><span class="sxs-lookup"><span data-stu-id="2fa1f-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fa1f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2fa1f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fa1f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2fa1f-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="2fa1f-106">fora Um ponteiro para o endereço de uma `ICorDebugClass` interface que representa o tipo genérico não instanciado.</span><span class="sxs-lookup"><span data-stu-id="2fa1f-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fa1f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2fa1f-107">Remarks</span></span>  
 <span data-ttu-id="2fa1f-108">`GetClass`pode ser chamado somente sob determinadas condições.</span><span class="sxs-lookup"><span data-stu-id="2fa1f-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="2fa1f-109">Chame [ICorDebugType:: GetType](icordebugtype-gettype-method.md) antes de chamar `GetClass` .</span><span class="sxs-lookup"><span data-stu-id="2fa1f-109">Call [ICorDebugType::GetType](icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="2fa1f-110">Se `ICorDebugType::GetType` retorna um valor de CorElementType que é ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, `GetClass` pode ser chamado para obter o tipo não instanciado para um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="2fa1f-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fa1f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2fa1f-111">Requirements</span></span>  
 <span data-ttu-id="2fa1f-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fa1f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fa1f-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fa1f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fa1f-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fa1f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fa1f-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fa1f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
