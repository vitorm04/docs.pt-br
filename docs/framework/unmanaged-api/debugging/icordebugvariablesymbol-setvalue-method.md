---
title: Método ICorDebugVariableSymbol::SetValue
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5bfbadc5553e86b2db10d66298c8d24d2a0f8bde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946166"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="edf05-102">Método ICorDebugVariableSymbol::SetValue</span><span class="sxs-lookup"><span data-stu-id="edf05-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="edf05-103">Atribui o valor de uma matriz de bytes a uma variável.</span><span class="sxs-lookup"><span data-stu-id="edf05-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edf05-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="edf05-104">Syntax</span></span>  
  
```  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edf05-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="edf05-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="edf05-106">[in] O deslocamento inicial da variável no qual definir o valor.</span><span class="sxs-lookup"><span data-stu-id="edf05-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="edf05-107">Esse parâmetro é usado ao gravar em campos de membro em um objeto.</span><span class="sxs-lookup"><span data-stu-id="edf05-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="edf05-108">[in] O identificador de thread do thread cujo contexto deve ser atualizado para refletir o novo valor.</span><span class="sxs-lookup"><span data-stu-id="edf05-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="edf05-109">[in] O tamanho em bytes do que o contexto do thread.</span><span class="sxs-lookup"><span data-stu-id="edf05-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="edf05-110">[in] O contexto do thread usado para gravar o valor.</span><span class="sxs-lookup"><span data-stu-id="edf05-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="edf05-111">[in] O tamanho em bytes do `pValue` buffer.</span><span class="sxs-lookup"><span data-stu-id="edf05-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="edf05-112">[in] O buffer que contém o valor a ser definido.</span><span class="sxs-lookup"><span data-stu-id="edf05-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edf05-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="edf05-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="edf05-114">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="edf05-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edf05-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="edf05-115">Requirements</span></span>  
 <span data-ttu-id="edf05-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edf05-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edf05-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="edf05-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="edf05-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edf05-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edf05-119">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edf05-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf05-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="edf05-120">See also</span></span>

- [<span data-ttu-id="edf05-121">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="edf05-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="edf05-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="edf05-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
