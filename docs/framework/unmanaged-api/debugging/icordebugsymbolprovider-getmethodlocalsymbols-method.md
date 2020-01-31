---
title: 'Método ICorDebugSymbolProvider:: GetMethodLocalSymbols'
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
ms.openlocfilehash: 41fc8e94ec8a5c8794674bebb32494bb3806e69d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791613"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a><span data-ttu-id="30614-102">Método ICorDebugSymbolProvider:: GetMethodLocalSymbols</span><span class="sxs-lookup"><span data-stu-id="30614-102">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span></span>
<span data-ttu-id="30614-103">Obtém os símbolos locais de um método de acordo com o endereço virtual relativo (RVA) desse método.</span><span class="sxs-lookup"><span data-stu-id="30614-103">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30614-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30614-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30614-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="30614-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="30614-106">no O endereço virtual relativo nativo do método.</span><span class="sxs-lookup"><span data-stu-id="30614-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="30614-107">no O número de símbolos locais solicitados.</span><span class="sxs-lookup"><span data-stu-id="30614-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="30614-108">fora Um ponteiro para o número de símbolos recuperados pelo método.</span><span class="sxs-lookup"><span data-stu-id="30614-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="30614-109">fora Um ponteiro para uma matriz [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) que contém os símbolos locais do método.</span><span class="sxs-lookup"><span data-stu-id="30614-109">[out] A pointer to an [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30614-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="30614-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30614-111">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="30614-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30614-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="30614-112">Requirements</span></span>  
 <span data-ttu-id="30614-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30614-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30614-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30614-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30614-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30614-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30614-116">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30614-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30614-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="30614-117">See also</span></span>

- [<span data-ttu-id="30614-118">Método GetMethodParameterSymbols</span><span class="sxs-lookup"><span data-stu-id="30614-118">GetMethodParameterSymbols Method</span></span>](icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [<span data-ttu-id="30614-119">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="30614-119">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="30614-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="30614-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
