---
title: ICorDebugVariableSymbol::Método GetName
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: abc0e368f259df1a3542b0fc8e7fbfd7e06cf6eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178448"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="3a71d-102">ICorDebugVariableSymbol::Método GetName</span><span class="sxs-lookup"><span data-stu-id="3a71d-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="3a71d-103">Recebe o nome de uma variável.</span><span class="sxs-lookup"><span data-stu-id="3a71d-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a71d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a71d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a71d-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="3a71d-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="3a71d-106">[em] O número de `szName` caracteres no buffer.</span><span class="sxs-lookup"><span data-stu-id="3a71d-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3a71d-107">[fora] Um ponteiro para o número de `szName` caracteres realmente escrito no buffer.</span><span class="sxs-lookup"><span data-stu-id="3a71d-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="3a71d-108">Um ponteiro para uma matriz de caracteres que contém o nome da variável.</span><span class="sxs-lookup"><span data-stu-id="3a71d-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a71d-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a71d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a71d-110">Este método está disponível apenas com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3a71d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a71d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a71d-111">Requirements</span></span>  
 <span data-ttu-id="3a71d-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a71d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a71d-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a71d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a71d-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a71d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a71d-115">**.NET Framework Versions:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a71d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a71d-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="3a71d-116">See also</span></span>

- [<span data-ttu-id="3a71d-117">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="3a71d-117">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="3a71d-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3a71d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
