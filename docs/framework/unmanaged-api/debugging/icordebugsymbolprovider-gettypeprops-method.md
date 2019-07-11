---
title: Método ICorDebugSymbolProvider::GetTypeProps
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 435a814d20e039c794f4f9eeb024d5afbfcd6dbd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771187"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="69da1-102">Método ICorDebugSymbolProvider::GetTypeProps</span><span class="sxs-lookup"><span data-stu-id="69da1-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="69da1-103">Retorna informações sobre propriedades de um tipo, como o número de assinatura de seus parâmetros genéricos, considerando um endereço virtual relativo (RVA) em uma vtable.</span><span class="sxs-lookup"><span data-stu-id="69da1-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69da1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69da1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69da1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="69da1-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="69da1-106">[in] Um endereço virtual relativo (RVA) em uma vtable.</span><span class="sxs-lookup"><span data-stu-id="69da1-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="69da1-107">[in] O tamanho do `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="69da1-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="69da1-108">Consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="69da1-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="69da1-109">[out] [out] Um ponteiro para o tamanho de retornado `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="69da1-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="69da1-110">[out] Um buffer que contém as assinaturas de typespec de todos os parâmetros genéricos.</span><span class="sxs-lookup"><span data-stu-id="69da1-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69da1-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="69da1-111">Remarks</span></span>  
 <span data-ttu-id="69da1-112">Para obter o tamanho necessário do tipo de `signature` matriz, defina a `cbSignature` argumento como 0 e `signature` à **nulo**.</span><span class="sxs-lookup"><span data-stu-id="69da1-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="69da1-113">Quando o método retorna, `pcbSignature` conterá o número de bytes necessários para o `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="69da1-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69da1-114">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="69da1-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69da1-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="69da1-115">Requirements</span></span>  
 <span data-ttu-id="69da1-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69da1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69da1-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69da1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69da1-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69da1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69da1-119">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69da1-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69da1-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69da1-120">See also</span></span>

- [<span data-ttu-id="69da1-121">Método GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="69da1-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="69da1-122">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="69da1-122">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="69da1-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="69da1-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
