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
ms.workload: dotnet
ms.openlocfilehash: 2433274c2b8fa3ac547696c03a0d0e25c8b63082
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="95b14-102">Método ICorDebugVariableSymbol::SetValue</span><span class="sxs-lookup"><span data-stu-id="95b14-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="95b14-103">Atribui o valor de uma matriz de bytes a uma variável.</span><span class="sxs-lookup"><span data-stu-id="95b14-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95b14-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95b14-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="95b14-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="95b14-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="95b14-106">[in] O deslocamento inicial da variável no qual definir o valor.</span><span class="sxs-lookup"><span data-stu-id="95b14-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="95b14-107">Esse parâmetro é usado durante a gravação em campos de membro em um objeto.</span><span class="sxs-lookup"><span data-stu-id="95b14-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="95b14-108">[in] O identificador de thread do thread cujo contexto deve ser atualizado para refletir o novo valor.</span><span class="sxs-lookup"><span data-stu-id="95b14-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="95b14-109">[in] O tamanho em bytes do contexto do thread.</span><span class="sxs-lookup"><span data-stu-id="95b14-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="95b14-110">[in] O contexto do thread usado para gravar o valor.</span><span class="sxs-lookup"><span data-stu-id="95b14-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="95b14-111">[in] O tamanho em bytes do `pValue` buffer.</span><span class="sxs-lookup"><span data-stu-id="95b14-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="95b14-112">[in] O buffer que contém o valor a ser definido.</span><span class="sxs-lookup"><span data-stu-id="95b14-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95b14-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="95b14-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95b14-114">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="95b14-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95b14-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="95b14-115">Requirements</span></span>  
 <span data-ttu-id="95b14-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95b14-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95b14-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95b14-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95b14-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95b14-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95b14-119">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95b14-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95b14-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95b14-120">See Also</span></span>  
 [<span data-ttu-id="95b14-121">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="95b14-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="95b14-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="95b14-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
