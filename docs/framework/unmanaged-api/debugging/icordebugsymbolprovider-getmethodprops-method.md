---
title: 'Método ICorDebugSymbolProvider:: GetMethodProps'
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95610bc527b8f5b90df906b6260eb636d61dbcd8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957303"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="13371-102">Método ICorDebugSymbolProvider:: GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="13371-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="13371-103">Retorna informações sobre as propriedades do método, como o token de metadados do método e informações sobre seus parâmetros genéricos, considerando um endereço virtual relativo (RVA) nesse método.</span><span class="sxs-lookup"><span data-stu-id="13371-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13371-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13371-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13371-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="13371-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="13371-106">no Um endereço virtual relativo no método sobre quais informações serão recuperadas.</span><span class="sxs-lookup"><span data-stu-id="13371-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="13371-107">fora Um ponteiro para o token de metadados do método.</span><span class="sxs-lookup"><span data-stu-id="13371-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="13371-108">fora Um ponteiro para o número de parâmetros genéricos associados a este método.</span><span class="sxs-lookup"><span data-stu-id="13371-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="13371-109">no O tamanho da `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="13371-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="13371-110">Consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="13371-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="13371-111">fora Um ponteiro para o tamanho da matriz retornada `signature` .</span><span class="sxs-lookup"><span data-stu-id="13371-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="13371-112">fora Um buffer que contém as assinaturas TypeSpec de todos os parâmetros genéricos.</span><span class="sxs-lookup"><span data-stu-id="13371-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13371-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="13371-113">Remarks</span></span>  
 <span data-ttu-id="13371-114">Para obter o tamanho necessário da matriz `signature` do método, defina o `cbSignature` argumento como 0 e `signature` como **nulo**.</span><span class="sxs-lookup"><span data-stu-id="13371-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="13371-115">Quando o método retornar, `pcbSignature` conterá o número de bytes necessários para a `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="13371-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="13371-116">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="13371-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13371-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13371-117">Requirements</span></span>  
 <span data-ttu-id="13371-118">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13371-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13371-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13371-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13371-120">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13371-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13371-121">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13371-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13371-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13371-122">See also</span></span>

- [<span data-ttu-id="13371-123">Método GetTypeProps</span><span class="sxs-lookup"><span data-stu-id="13371-123">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="13371-124">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="13371-124">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="13371-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="13371-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
