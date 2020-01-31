---
title: Método ICorDebugDataTarget2::CreateVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
ms.openlocfilehash: 9fc4facda6253d0c68dcf89b2a1b06e639734efe
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788847"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="5c1d2-102">Método ICorDebugDataTarget2::CreateVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="5c1d2-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="5c1d2-103">Cria um novo unwinder de pilha que inicia o desenrolamento de um contexto inicial (que não é necessariamente folha de um thread).</span><span class="sxs-lookup"><span data-stu-id="5c1d2-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c1d2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c1d2-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c1d2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5c1d2-105">Parameters</span></span>  
 <span data-ttu-id="5c1d2-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="5c1d2-106">nativeThreadID</span></span>  
 <span data-ttu-id="5c1d2-107">[in] O ID de thread nativo do thread cuja pilha será desenrolada.</span><span class="sxs-lookup"><span data-stu-id="5c1d2-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="5c1d2-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="5c1d2-108">contextFlags</span></span>  
 <span data-ttu-id="5c1d2-109">[in] Sinalizadores que especificam quais partes do contexto são definidos em `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="5c1d2-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="5c1d2-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="5c1d2-110">cbContext</span></span>  
 <span data-ttu-id="5c1d2-111">[in] O tamanho do `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="5c1d2-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="5c1d2-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="5c1d2-112">initialContext</span></span>  
 <span data-ttu-id="5c1d2-113">[in] Os dados no contexto.</span><span class="sxs-lookup"><span data-stu-id="5c1d2-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="5c1d2-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="5c1d2-114">ppUnwinder</span></span>  
 <span data-ttu-id="5c1d2-115">[out] Um ponteiro para o endereço de um objeto de interface ICorDebugVirtualUnwinder.</span><span class="sxs-lookup"><span data-stu-id="5c1d2-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c1d2-116">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5c1d2-116">Return Value</span></span>  
 <span data-ttu-id="5c1d2-117">`S_OK` se bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="5c1d2-117">`S_OK` if successful.</span></span> <span data-ttu-id="5c1d2-118">Qualquer outro `HRESULT` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="5c1d2-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="5c1d2-119">Qualquer falha `HRESULT` recebida pelo MSCorDbi é considerada fatal e faz com que os métodos [ICorDebug](icordebug-interface.md) sejam retornados `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="5c1d2-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c1d2-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="5c1d2-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c1d2-121">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5c1d2-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c1d2-122">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="5c1d2-122">Requirements</span></span>  
 <span data-ttu-id="5c1d2-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c1d2-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c1d2-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c1d2-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c1d2-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c1d2-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c1d2-126">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c1d2-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c1d2-127">Veja também</span><span class="sxs-lookup"><span data-stu-id="5c1d2-127">See also</span></span>

- [<span data-ttu-id="5c1d2-128">Interface ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="5c1d2-128">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="5c1d2-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5c1d2-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
