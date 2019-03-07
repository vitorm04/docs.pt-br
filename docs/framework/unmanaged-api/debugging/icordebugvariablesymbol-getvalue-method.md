---
title: Método ICorDebugVariableSymbol::GetValue
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c626d21f391899a15e5ea35c47d00f1f539fea4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488858"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="a586c-102">Método ICorDebugVariableSymbol::GetValue</span><span class="sxs-lookup"><span data-stu-id="a586c-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="a586c-103">Obtém o valor de uma variável como uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="a586c-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a586c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a586c-104">Syntax</span></span>  
  
```  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a586c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a586c-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="a586c-106">[in] O deslocamento inicial da variável da qual ler o valor.</span><span class="sxs-lookup"><span data-stu-id="a586c-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="a586c-107">Esse parâmetro é usado durante a leitura de campos de membro em um objeto.</span><span class="sxs-lookup"><span data-stu-id="a586c-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="a586c-108">[in] O tamanho em bytes do `context` argumento.</span><span class="sxs-lookup"><span data-stu-id="a586c-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="a586c-109">[in] O contexto do thread usado para ler o valor.</span><span class="sxs-lookup"><span data-stu-id="a586c-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="a586c-110">[in] O tamanho em bytes do `pValue` buffer.</span><span class="sxs-lookup"><span data-stu-id="a586c-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="a586c-111">[out] O número de bytes realmente gravados a `pValue` buffer.</span><span class="sxs-lookup"><span data-stu-id="a586c-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="a586c-112">[out] Uma matriz de bytes que contém o valor da variável.</span><span class="sxs-lookup"><span data-stu-id="a586c-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a586c-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="a586c-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a586c-114">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a586c-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a586c-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a586c-115">Requirements</span></span>  
 <span data-ttu-id="a586c-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a586c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a586c-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a586c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a586c-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a586c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a586c-119">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a586c-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a586c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a586c-120">See also</span></span>
- [<span data-ttu-id="a586c-121">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="a586c-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="a586c-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a586c-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
