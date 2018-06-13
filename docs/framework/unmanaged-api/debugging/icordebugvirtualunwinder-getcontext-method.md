---
title: Método ICorDebugVirtualUnwinder::GetContext
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96410466f17bf6b4e8fff235d434f470cabd9249
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422878"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="ac35d-102">Método ICorDebugVirtualUnwinder::GetContext</span><span class="sxs-lookup"><span data-stu-id="ac35d-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="ac35d-103">Obtém o contexto atual deste unwinder.</span><span class="sxs-lookup"><span data-stu-id="ac35d-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac35d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac35d-104">Syntax</span></span>  
  
```  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac35d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac35d-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="ac35d-106">[in] Sinalizadores que especificam quais partes do contexto para retornar (definido em Winnt. H).</span><span class="sxs-lookup"><span data-stu-id="ac35d-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="ac35d-107">[in] O número de bytes em `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="ac35d-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="ac35d-108">[out] Um ponteiro para o número de bytes gravados `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="ac35d-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="ac35d-109">[out] Uma matriz de bytes que contém o contexto atual deste unwinder.</span><span class="sxs-lookup"><span data-stu-id="ac35d-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac35d-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ac35d-110">Return Value</span></span>  
 <span data-ttu-id="ac35d-111">Qualquer falha valor HRESULT recebida pelo mscordbi é considerado fatal e fará com que ICorDebug APIs retornar `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="ac35d-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac35d-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac35d-112">Remarks</span></span>  
 <span data-ttu-id="ac35d-113">Definir o valor inicial do `contextBuf` argumento para o buffer de contexto retornado ao chamar o [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="ac35d-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac35d-114">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ac35d-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="ac35d-115">Porque o desenrolamento pode apenas restaurar um subconjunto de registros, como não volátil registra somente, o contexto pode não corresponder exatamente o estado do registro no momento da chamada do método real.</span><span class="sxs-lookup"><span data-stu-id="ac35d-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac35d-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac35d-116">Requirements</span></span>  
 <span data-ttu-id="ac35d-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac35d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac35d-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac35d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac35d-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac35d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac35d-120">**Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac35d-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac35d-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac35d-121">See Also</span></span>  
 [<span data-ttu-id="ac35d-122">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="ac35d-122">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="ac35d-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ac35d-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
