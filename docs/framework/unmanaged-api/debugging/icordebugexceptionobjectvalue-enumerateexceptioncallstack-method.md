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
ms.openlocfilehash: e45b180ac6d943d89740ad7ae10500ea4ad1aa9c
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975960"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="fd64e-102">Método ICorDebugExceptionObjectValue::EnumerateExceptionCallStack</span><span class="sxs-lookup"><span data-stu-id="fd64e-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="fd64e-103">Obtém um enumerador para a pilha de chamadas inserido em um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="fd64e-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd64e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fd64e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd64e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fd64e-105">Parameters</span></span>  
 <span data-ttu-id="fd64e-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="fd64e-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="fd64e-107">fora Um ponteiro para o endereço de um objeto de interface [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) que é um enumerador de rastreamento de pilha para um objeto de exceção gerenciado.</span><span class="sxs-lookup"><span data-stu-id="fd64e-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd64e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="fd64e-108">Remarks</span></span>  
 <span data-ttu-id="fd64e-109">Se nenhuma informação da pilha de chamadas estiver disponível, o `S_OK`método retornará e [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) será um enumerador válido com um comprimento de 0.</span><span class="sxs-lookup"><span data-stu-id="fd64e-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="fd64e-110">Se o método não puder recuperar informações de rastreamento de pilha, o valor de `E_FAIL` retorno será e nenhum enumerador será retornado.</span><span class="sxs-lookup"><span data-stu-id="fd64e-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="fd64e-111">O objeto [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) é responsável por decodificar os dados de rastreamento de pilha `_stackTrace` do campo do objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="fd64e-111">The [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd64e-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fd64e-112">Requirements</span></span>  
 <span data-ttu-id="fd64e-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd64e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd64e-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd64e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd64e-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd64e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd64e-116">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd64e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd64e-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd64e-117">See also</span></span>

- [<span data-ttu-id="fd64e-118">Interface ICorDebugExceptionObjectValue</span><span class="sxs-lookup"><span data-stu-id="fd64e-118">ICorDebugExceptionObjectValue Interface</span></span>](icordebugexceptionobjectvalue-interface.md)
- [<span data-ttu-id="fd64e-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fd64e-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
