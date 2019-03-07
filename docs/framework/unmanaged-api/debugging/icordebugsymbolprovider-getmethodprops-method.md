---
title: Método ICorDebugSymbolProvider::GetMethodProps
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9dacfd6538dbf42a757a0e3534978238421644ae
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490431"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="754eb-102">Método ICorDebugSymbolProvider::GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="754eb-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="754eb-103">Retorna informações sobre as propriedades do método, como o método token de metadados e informações sobre seus parâmetros genéricos, considerando um endereço virtual relativo (RVA) nesse método.</span><span class="sxs-lookup"><span data-stu-id="754eb-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="754eb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="754eb-104">Syntax</span></span>  
  
```  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="754eb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="754eb-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="754eb-106">[in] Um endereço virtual relativo no método sobre quais informações deverá ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="754eb-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="754eb-107">[out] Um ponteiro para o token de metadados do método.</span><span class="sxs-lookup"><span data-stu-id="754eb-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="754eb-108">[out] Um ponteiro para o número de parâmetros genéricos associados com esse método.</span><span class="sxs-lookup"><span data-stu-id="754eb-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="754eb-109">[in] O tamanho do `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="754eb-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="754eb-110">Consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="754eb-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="754eb-111">[out] Um ponteiro para o tamanho de retornado `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="754eb-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="754eb-112">[out] Um buffer que contém as assinaturas de typespec de todos os parâmetros genéricos.</span><span class="sxs-lookup"><span data-stu-id="754eb-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="754eb-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="754eb-113">Remarks</span></span>  
 <span data-ttu-id="754eb-114">Para obter o tamanho necessário do que o método `signature` matriz, defina a `cbSignature` argumento como 0 e `signature` para **nulo**.</span><span class="sxs-lookup"><span data-stu-id="754eb-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="754eb-115">Quando o método retorna, `pcbSignature` conterá o número de bytes necessários para o `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="754eb-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="754eb-116">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="754eb-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="754eb-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="754eb-117">Requirements</span></span>  
 <span data-ttu-id="754eb-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="754eb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="754eb-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="754eb-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="754eb-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="754eb-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="754eb-121">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="754eb-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="754eb-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="754eb-122">See also</span></span>
- [<span data-ttu-id="754eb-123">Método GetTypeProps</span><span class="sxs-lookup"><span data-stu-id="754eb-123">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="754eb-124">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="754eb-124">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="754eb-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="754eb-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
