---
title: Método ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
ms.date: 03/30/2017
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
ms.openlocfilehash: 57eb284bfe39ce92b2d6c03a2aeb4ae84d6aba91
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788674"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="ec7b8-102">Método ICorDebugExceptionObjectValue::EnumerateExceptionCallStack</span><span class="sxs-lookup"><span data-stu-id="ec7b8-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="ec7b8-103">Obtém um enumerador para a pilha de chamadas inserido em um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="ec7b8-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec7b8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec7b8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec7b8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ec7b8-105">Parameters</span></span>  
 <span data-ttu-id="ec7b8-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="ec7b8-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="ec7b8-107">fora Um ponteiro para o endereço de um objeto de interface [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) que é um enumerador de rastreamento de pilha para um objeto de exceção gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ec7b8-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec7b8-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec7b8-108">Remarks</span></span>  
 <span data-ttu-id="ec7b8-109">Se nenhuma informação da pilha de chamadas estiver disponível, o método retornará `S_OK`e [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) será um enumerador válido com um comprimento de 0.</span><span class="sxs-lookup"><span data-stu-id="ec7b8-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="ec7b8-110">Se o método não puder recuperar informações de rastreamento de pilha, o valor de retorno será `E_FAIL` e nenhum enumerador será retornado.</span><span class="sxs-lookup"><span data-stu-id="ec7b8-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="ec7b8-111">O objeto [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) é responsável por decodificar os dados de rastreamento de pilha do campo `_stackTrace` do objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="ec7b8-111">The [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec7b8-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="ec7b8-112">Requirements</span></span>  
 <span data-ttu-id="ec7b8-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec7b8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec7b8-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec7b8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec7b8-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec7b8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec7b8-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec7b8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec7b8-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="ec7b8-117">See also</span></span>

- [<span data-ttu-id="ec7b8-118">Interface ICorDebugExceptionObjectValue</span><span class="sxs-lookup"><span data-stu-id="ec7b8-118">ICorDebugExceptionObjectValue Interface</span></span>](icordebugexceptionobjectvalue-interface.md)
- [<span data-ttu-id="ec7b8-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ec7b8-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
