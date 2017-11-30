---
title: "Método ICorDebugVariableSymbol::SetValue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 12c13259d20301b0f485a6041fa884b0996cbbdc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="25477-102">Método ICorDebugVariableSymbol::SetValue</span><span class="sxs-lookup"><span data-stu-id="25477-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="25477-103">Atribui o valor de uma matriz de bytes a uma variável.</span><span class="sxs-lookup"><span data-stu-id="25477-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25477-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25477-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="25477-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="25477-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="25477-106">[in] O deslocamento inicial da variável no qual definir o valor.</span><span class="sxs-lookup"><span data-stu-id="25477-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="25477-107">Esse parâmetro é usado durante a gravação em campos de membro em um objeto.</span><span class="sxs-lookup"><span data-stu-id="25477-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="25477-108">[in] O identificador de thread do thread cujo contexto deve ser atualizado para refletir o novo valor.</span><span class="sxs-lookup"><span data-stu-id="25477-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="25477-109">[in] O tamanho em bytes do contexto do thread.</span><span class="sxs-lookup"><span data-stu-id="25477-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="25477-110">[in] O contexto do thread usado para gravar o valor.</span><span class="sxs-lookup"><span data-stu-id="25477-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="25477-111">[in] O tamanho em bytes do `pValue` buffer.</span><span class="sxs-lookup"><span data-stu-id="25477-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="25477-112">[in] O buffer que contém o valor a ser definido.</span><span class="sxs-lookup"><span data-stu-id="25477-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25477-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="25477-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25477-114">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="25477-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25477-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="25477-115">Requirements</span></span>  
 <span data-ttu-id="25477-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25477-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25477-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25477-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25477-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25477-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25477-119">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25477-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25477-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25477-120">See Also</span></span>  
 [<span data-ttu-id="25477-121">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="25477-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="25477-122">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="25477-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
