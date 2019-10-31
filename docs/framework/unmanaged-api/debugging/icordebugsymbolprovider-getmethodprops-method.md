---
title: 'Método ICorDebugSymbolProvider:: GetMethodProps'
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: 811106216e1e454ddf342af1578f74c80ba2acc9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138824"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="6fbba-102">Método ICorDebugSymbolProvider:: GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="6fbba-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="6fbba-103">Retorna informações sobre as propriedades do método, como o token de metadados do método e informações sobre seus parâmetros genéricos, considerando um endereço virtual relativo (RVA) nesse método.</span><span class="sxs-lookup"><span data-stu-id="6fbba-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fbba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6fbba-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6fbba-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6fbba-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="6fbba-106">no Um endereço virtual relativo no método sobre quais informações serão recuperadas.</span><span class="sxs-lookup"><span data-stu-id="6fbba-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="6fbba-107">fora Um ponteiro para o token de metadados do método.</span><span class="sxs-lookup"><span data-stu-id="6fbba-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="6fbba-108">fora Um ponteiro para o número de parâmetros genéricos associados a este método.</span><span class="sxs-lookup"><span data-stu-id="6fbba-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="6fbba-109">no O tamanho da matriz de `signature`.</span><span class="sxs-lookup"><span data-stu-id="6fbba-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="6fbba-110">Consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="6fbba-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="6fbba-111">fora Um ponteiro para o tamanho da matriz de `signature` retornada.</span><span class="sxs-lookup"><span data-stu-id="6fbba-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="6fbba-112">fora Um buffer que contém as assinaturas TypeSpec de todos os parâmetros genéricos.</span><span class="sxs-lookup"><span data-stu-id="6fbba-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fbba-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="6fbba-113">Remarks</span></span>  
 <span data-ttu-id="6fbba-114">Para obter o tamanho necessário da matriz de `signature` do método, defina o argumento `cbSignature` como 0 e `signature` como **nulo**.</span><span class="sxs-lookup"><span data-stu-id="6fbba-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="6fbba-115">Quando o método retornar, `pcbSignature` conterá o número de bytes necessários para a matriz `signature`.</span><span class="sxs-lookup"><span data-stu-id="6fbba-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6fbba-116">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6fbba-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fbba-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6fbba-117">Requirements</span></span>  
 <span data-ttu-id="6fbba-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fbba-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fbba-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6fbba-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fbba-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fbba-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fbba-121">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fbba-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fbba-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fbba-122">See also</span></span>

- [<span data-ttu-id="6fbba-123">Método GetTypeProps</span><span class="sxs-lookup"><span data-stu-id="6fbba-123">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="6fbba-124">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="6fbba-124">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="6fbba-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6fbba-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
