---
title: "Método ICorDebugExceptionObjectValue::EnumerateExceptionCallStack"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 861d2ad5f9ce0fcc11ea7b1743cd369235cbd878
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="89d6d-102">Método ICorDebugExceptionObjectValue::EnumerateExceptionCallStack</span><span class="sxs-lookup"><span data-stu-id="89d6d-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="89d6d-103">Obtém um enumerador para a pilha de chamadas incorporada em um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="89d6d-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89d6d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89d6d-104">Syntax</span></span>  
  
```  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89d6d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="89d6d-105">Parameters</span></span>  
 <span data-ttu-id="89d6d-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="89d6d-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="89d6d-107">[out] Um ponteiro para o endereço de um [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) objeto de interface que é um enumerador de rastreamento de pilha para um objeto de exceção gerenciada.</span><span class="sxs-lookup"><span data-stu-id="89d6d-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89d6d-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="89d6d-108">Remarks</span></span>  
 <span data-ttu-id="89d6d-109">Se nenhuma informação de pilha de chamada estiver disponível, o método retorna `S_OK`, e [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) é um enumerador válido com um comprimento de 0.</span><span class="sxs-lookup"><span data-stu-id="89d6d-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="89d6d-110">Se o método for não é possível recuperar informações de rastreamento de pilha, o valor de retorno é `E_FAIL` e nenhum enumerador é retornado.</span><span class="sxs-lookup"><span data-stu-id="89d6d-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="89d6d-111">O [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) objeto será responsável pela decodificação de dados de rastreamento de pilha do `_stackTrace` campo do objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="89d6d-111">The [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89d6d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="89d6d-112">Requirements</span></span>  
 <span data-ttu-id="89d6d-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89d6d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89d6d-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89d6d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89d6d-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89d6d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89d6d-116">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89d6d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89d6d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89d6d-117">See Also</span></span>  
 [<span data-ttu-id="89d6d-118">Interface ICorDebugExceptionObjectValue</span><span class="sxs-lookup"><span data-stu-id="89d6d-118">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 [<span data-ttu-id="89d6d-119">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="89d6d-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
