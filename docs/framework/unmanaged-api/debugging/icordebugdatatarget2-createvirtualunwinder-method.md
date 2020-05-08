---
title: Método ICorDebugDataTarget2::CreateVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
ms.openlocfilehash: 7a479fba9bbcf28c60474fffc6219af23e62c251
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976493"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="39dbb-102">Método ICorDebugDataTarget2::CreateVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="39dbb-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="39dbb-103">Cria um novo unwinder de pilha que inicia o desenrolamento de um contexto inicial (que não é necessariamente folha de um thread).</span><span class="sxs-lookup"><span data-stu-id="39dbb-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39dbb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39dbb-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a><span data-ttu-id="39dbb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="39dbb-105">Parameters</span></span>  
 <span data-ttu-id="39dbb-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="39dbb-106">nativeThreadID</span></span>  
 <span data-ttu-id="39dbb-107">[in] O ID de thread nativo do thread cuja pilha será desenrolada.</span><span class="sxs-lookup"><span data-stu-id="39dbb-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="39dbb-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="39dbb-108">contextFlags</span></span>  
 <span data-ttu-id="39dbb-109">[in] Sinalizadores que especificam quais partes do contexto são definidos em `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="39dbb-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="39dbb-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="39dbb-110">cbContext</span></span>  
 <span data-ttu-id="39dbb-111">[in] O tamanho do `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="39dbb-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="39dbb-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="39dbb-112">initialContext</span></span>  
 <span data-ttu-id="39dbb-113">[in] Os dados no contexto.</span><span class="sxs-lookup"><span data-stu-id="39dbb-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="39dbb-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="39dbb-114">ppUnwinder</span></span>  
 <span data-ttu-id="39dbb-115">[out] Um ponteiro para o endereço de um objeto de interface ICorDebugVirtualUnwinder.</span><span class="sxs-lookup"><span data-stu-id="39dbb-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39dbb-116">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="39dbb-116">Return Value</span></span>  
 <span data-ttu-id="39dbb-117">`S_OK` se bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="39dbb-117">`S_OK` if successful.</span></span> <span data-ttu-id="39dbb-118">Qualquer outro `HRESULT` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="39dbb-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="39dbb-119">Qualquer falha `HRESULT` recebida pelo MSCorDbi é considerada fatal e faz [ICorDebug](icordebug-interface.md) com que os métodos `CORDBG_E_DATA_TARGET_ERROR`ICorDebug sejam retornados.</span><span class="sxs-lookup"><span data-stu-id="39dbb-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39dbb-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="39dbb-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39dbb-121">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="39dbb-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39dbb-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="39dbb-122">Requirements</span></span>  
 <span data-ttu-id="39dbb-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39dbb-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39dbb-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39dbb-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39dbb-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39dbb-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39dbb-126">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39dbb-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39dbb-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39dbb-127">See also</span></span>

- [<span data-ttu-id="39dbb-128">Interface ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="39dbb-128">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="39dbb-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="39dbb-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
