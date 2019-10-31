---
title: 'Método ICorDebugVariableSymbol:: GetValue'
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
ms.openlocfilehash: 5ef7e67efb2bafd9b9f52203246fd7d1590e6107
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120961"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="07e35-102">Método ICorDebugVariableSymbol:: GetValue</span><span class="sxs-lookup"><span data-stu-id="07e35-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="07e35-103">Obtém o valor de uma variável como uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="07e35-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07e35-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07e35-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07e35-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="07e35-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="07e35-106">no O deslocamento inicial na variável a partir da qual o valor deve ser lido.</span><span class="sxs-lookup"><span data-stu-id="07e35-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="07e35-107">Esse parâmetro é usado ao ler campos de membro em um objeto.</span><span class="sxs-lookup"><span data-stu-id="07e35-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="07e35-108">no O tamanho em bytes do argumento `context`.</span><span class="sxs-lookup"><span data-stu-id="07e35-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="07e35-109">no O contexto de thread usado para ler o valor.</span><span class="sxs-lookup"><span data-stu-id="07e35-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="07e35-110">no O tamanho em bytes do buffer de `pValue`.</span><span class="sxs-lookup"><span data-stu-id="07e35-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="07e35-111">fora O número de bytes realmente gravados no buffer de `pValue`.</span><span class="sxs-lookup"><span data-stu-id="07e35-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="07e35-112">fora Uma matriz de bytes que contém o valor da variável.</span><span class="sxs-lookup"><span data-stu-id="07e35-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07e35-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="07e35-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07e35-114">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="07e35-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07e35-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="07e35-115">Requirements</span></span>  
 <span data-ttu-id="07e35-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07e35-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07e35-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07e35-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07e35-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07e35-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07e35-119">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07e35-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07e35-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07e35-120">See also</span></span>

- [<span data-ttu-id="07e35-121">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="07e35-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="07e35-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="07e35-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
