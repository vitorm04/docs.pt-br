---
title: 'Método ICorDebugSymbolProvider:: GetMethodProps'
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: 58642d0a9b1cfe1fd969f39fa7e5ab22a8dbfa05
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791579"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="4652a-102">Método ICorDebugSymbolProvider:: GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="4652a-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="4652a-103">Retorna informações sobre as propriedades do método, como o token de metadados do método e informações sobre seus parâmetros genéricos, considerando um endereço virtual relativo (RVA) nesse método.</span><span class="sxs-lookup"><span data-stu-id="4652a-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4652a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4652a-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4652a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4652a-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="4652a-106">no Um endereço virtual relativo no método sobre quais informações serão recuperadas.</span><span class="sxs-lookup"><span data-stu-id="4652a-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="4652a-107">fora Um ponteiro para o token de metadados do método.</span><span class="sxs-lookup"><span data-stu-id="4652a-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="4652a-108">fora Um ponteiro para o número de parâmetros genéricos associados a este método.</span><span class="sxs-lookup"><span data-stu-id="4652a-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="4652a-109">no O tamanho da matriz de `signature`.</span><span class="sxs-lookup"><span data-stu-id="4652a-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="4652a-110">Consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="4652a-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="4652a-111">fora Um ponteiro para o tamanho da matriz de `signature` retornada.</span><span class="sxs-lookup"><span data-stu-id="4652a-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="4652a-112">fora Um buffer que contém as assinaturas TypeSpec de todos os parâmetros genéricos.</span><span class="sxs-lookup"><span data-stu-id="4652a-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4652a-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="4652a-113">Remarks</span></span>  
 <span data-ttu-id="4652a-114">Para obter o tamanho necessário da matriz de `signature` do método, defina o argumento `cbSignature` como 0 e `signature` como **nulo**.</span><span class="sxs-lookup"><span data-stu-id="4652a-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="4652a-115">Quando o método retornar, `pcbSignature` conterá o número de bytes necessários para a matriz `signature`.</span><span class="sxs-lookup"><span data-stu-id="4652a-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4652a-116">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4652a-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4652a-117">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="4652a-117">Requirements</span></span>  
 <span data-ttu-id="4652a-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4652a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4652a-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4652a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4652a-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4652a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4652a-121">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4652a-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4652a-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="4652a-122">See also</span></span>

- [<span data-ttu-id="4652a-123">Método GetTypeProps</span><span class="sxs-lookup"><span data-stu-id="4652a-123">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="4652a-124">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="4652a-124">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="4652a-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4652a-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
