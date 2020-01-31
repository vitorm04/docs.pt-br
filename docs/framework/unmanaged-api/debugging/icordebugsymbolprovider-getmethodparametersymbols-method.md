---
title: 'Método ICorDebugSymbolProvider:: GetMethodParameterSymbols'
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
ms.openlocfilehash: a940077e50ff251111ca6eedaee49401775644d3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791592"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="bbeae-102">Método ICorDebugSymbolProvider:: GetMethodParameterSymbols</span><span class="sxs-lookup"><span data-stu-id="bbeae-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="bbeae-103">Obtém os símbolos de parâmetro de um método de acordo com o endereço virtual relativo (RVA) desse método.</span><span class="sxs-lookup"><span data-stu-id="bbeae-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbeae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bbeae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbeae-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bbeae-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="bbeae-106">no O endereço virtual relativo nativo do método.</span><span class="sxs-lookup"><span data-stu-id="bbeae-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="bbeae-107">no O número de símbolos locais solicitados.</span><span class="sxs-lookup"><span data-stu-id="bbeae-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="bbeae-108">fora Um ponteiro para o número de símbolos recuperados pelo método.</span><span class="sxs-lookup"><span data-stu-id="bbeae-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="bbeae-109">fora Um ponteiro para uma matriz [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) que contém os símbolos locais do método.</span><span class="sxs-lookup"><span data-stu-id="bbeae-109">[out] A pointer to an [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbeae-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="bbeae-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bbeae-111">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bbeae-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbeae-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="bbeae-112">Requirements</span></span>  
 <span data-ttu-id="bbeae-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbeae-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbeae-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bbeae-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbeae-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbeae-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbeae-116">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbeae-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbeae-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="bbeae-117">See also</span></span>

- [<span data-ttu-id="bbeae-118">Método GetMethodLocalSymbols</span><span class="sxs-lookup"><span data-stu-id="bbeae-118">GetMethodLocalSymbols Method</span></span>](icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [<span data-ttu-id="bbeae-119">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="bbeae-119">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="bbeae-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="bbeae-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
