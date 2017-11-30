---
title: "Método ICorDebugSymbolProvider::GetMethodProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 58406f3f47e5d6eabd55420dc57148dc7f264726
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="a67b3-102">Método ICorDebugSymbolProvider::GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="a67b3-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="a67b3-103">Retorna informações sobre propriedades de método, como o método token de metadados e informações sobre seus parâmetros genéricos, dado um endereço virtual relativo (RVA) nesse método.</span><span class="sxs-lookup"><span data-stu-id="a67b3-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a67b3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a67b3-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="a67b3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a67b3-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="a67b3-106">[in] Um endereço virtual relativo no método sobre quais informações são a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="a67b3-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="a67b3-107">[out] Um ponteiro para o token de metadados do método.</span><span class="sxs-lookup"><span data-stu-id="a67b3-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="a67b3-108">[out] Um ponteiro para o número de parâmetros genéricos associados a este método.</span><span class="sxs-lookup"><span data-stu-id="a67b3-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="a67b3-109">[in] O tamanho do `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="a67b3-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="a67b3-110">Consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="a67b3-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="a67b3-111">[out] Um ponteiro para o tamanho do retornado `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="a67b3-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="a67b3-112">[out] Um buffer que contém as assinaturas typespec de todos os parâmetros genéricos.</span><span class="sxs-lookup"><span data-stu-id="a67b3-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a67b3-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="a67b3-113">Remarks</span></span>  
 <span data-ttu-id="a67b3-114">Para obter o tamanho necessário do método `signature` de matriz, defina o `cbSignature` argumento como 0 e `signature` para **nulo**.</span><span class="sxs-lookup"><span data-stu-id="a67b3-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="a67b3-115">Quando o método retorna, `pcbSignature` conterá o número de bytes necessários para o `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="a67b3-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a67b3-116">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a67b3-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a67b3-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a67b3-117">Requirements</span></span>  
 <span data-ttu-id="a67b3-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a67b3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a67b3-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a67b3-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a67b3-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a67b3-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a67b3-121">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a67b3-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a67b3-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a67b3-122">See Also</span></span>  
 [<span data-ttu-id="a67b3-123">Método GetTypeProps</span><span class="sxs-lookup"><span data-stu-id="a67b3-123">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)  
 [<span data-ttu-id="a67b3-124">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="a67b3-124">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="a67b3-125">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="a67b3-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
