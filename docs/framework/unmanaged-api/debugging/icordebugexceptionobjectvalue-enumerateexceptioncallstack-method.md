---
title: "Método ICorDebugExceptionObjectValue::EnumerateExceptionCallStack"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7453c6cc46ecbb063c7c3f99fc2aef85d1fdcba2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="30e77-102">Método ICorDebugExceptionObjectValue::EnumerateExceptionCallStack</span><span class="sxs-lookup"><span data-stu-id="30e77-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="30e77-103">Obtém um enumerador para a pilha de chamadas incorporada em um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="30e77-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30e77-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30e77-104">Syntax</span></span>  
  
```  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30e77-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="30e77-105">Parameters</span></span>  
 <span data-ttu-id="30e77-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="30e77-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="30e77-107">[out] Um ponteiro para o endereço de um [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) objeto de interface que é um enumerador de rastreamento de pilha para um objeto de exceção gerenciada.</span><span class="sxs-lookup"><span data-stu-id="30e77-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30e77-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="30e77-108">Remarks</span></span>  
 <span data-ttu-id="30e77-109">Se nenhuma informação de pilha de chamada estiver disponível, o método retorna `S_OK`, e [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) é um enumerador válido com um comprimento de 0.</span><span class="sxs-lookup"><span data-stu-id="30e77-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="30e77-110">Se o método for não é possível recuperar informações de rastreamento de pilha, o valor de retorno é `E_FAIL` e nenhum enumerador é retornado.</span><span class="sxs-lookup"><span data-stu-id="30e77-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="30e77-111">O [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) objeto será responsável pela decodificação de dados de rastreamento de pilha do `_stackTrace` campo do objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="30e77-111">The [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30e77-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30e77-112">Requirements</span></span>  
 <span data-ttu-id="30e77-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30e77-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30e77-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30e77-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30e77-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30e77-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30e77-116">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30e77-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30e77-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30e77-117">See Also</span></span>  
 [<span data-ttu-id="30e77-118">Interface ICorDebugExceptionObjectValue</span><span class="sxs-lookup"><span data-stu-id="30e77-118">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 [<span data-ttu-id="30e77-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="30e77-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
