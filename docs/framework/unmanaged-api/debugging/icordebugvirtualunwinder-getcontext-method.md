---
title: Método ICorDebugVirtualUnwinder::GetContext
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3125fd5081e68237714bcb10f760b73ce7509f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946192"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="b0936-102">Método ICorDebugVirtualUnwinder::GetContext</span><span class="sxs-lookup"><span data-stu-id="b0936-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="b0936-103">Obtém o contexto atual deste desenrolador.</span><span class="sxs-lookup"><span data-stu-id="b0936-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0936-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b0936-104">Syntax</span></span>  
  
```  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0936-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b0936-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="b0936-106">[in] Sinalizadores que especificam quais partes do contexto para retornar (definidos em Winnt. H).</span><span class="sxs-lookup"><span data-stu-id="b0936-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="b0936-107">[in] O número de bytes em `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="b0936-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="b0936-108">[out] Um ponteiro para o número de bytes realmente gravados `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="b0936-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="b0936-109">[out] Uma matriz de bytes que contém o contexto atual deste desenrolador.</span><span class="sxs-lookup"><span data-stu-id="b0936-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0936-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b0936-110">Return Value</span></span>  
 <span data-ttu-id="b0936-111">Qualquer valor HRESULT recebida pelo mscordbi com falha é considerada fatal e fará com que as APIs de ICorDebug retornar `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="b0936-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0936-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="b0936-112">Remarks</span></span>  
 <span data-ttu-id="b0936-113">Você define o valor inicial do `contextBuf` argumento para o buffer de contexto retornado ao chamar o [icordebugstackwalk:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="b0936-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0936-114">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b0936-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="b0936-115">Porque desenrolamento maio apenas restaurar um subconjunto de registros, como não-volátil registra somente, o contexto pode não coincidir com o estado de registro no momento da chamada do método real.</span><span class="sxs-lookup"><span data-stu-id="b0936-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0936-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b0936-116">Requirements</span></span>  
 <span data-ttu-id="b0936-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0936-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0936-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0936-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0936-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0936-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0936-120">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0936-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0936-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0936-121">See also</span></span>

- [<span data-ttu-id="b0936-122">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="b0936-122">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="b0936-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b0936-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
