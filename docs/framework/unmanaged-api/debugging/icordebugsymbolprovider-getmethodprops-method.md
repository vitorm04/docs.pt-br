---
title: 'Método ICorDebugSymbolProvider:: GetMethodProps'
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: c9e73c4de7389405d9e4b643036709ff2dbb82e6
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379572"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="1adea-102">Método ICorDebugSymbolProvider:: GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="1adea-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="1adea-103">Retorna informações sobre as propriedades do método, como o token de metadados do método e informações sobre seus parâmetros genéricos, considerando um endereço virtual relativo (RVA) nesse método.</span><span class="sxs-lookup"><span data-stu-id="1adea-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1adea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1adea-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1adea-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1adea-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="1adea-106">no Um endereço virtual relativo no método sobre quais informações serão recuperadas.</span><span class="sxs-lookup"><span data-stu-id="1adea-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="1adea-107">fora Um ponteiro para o token de metadados do método.</span><span class="sxs-lookup"><span data-stu-id="1adea-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="1adea-108">fora Um ponteiro para o número de parâmetros genéricos associados a este método.</span><span class="sxs-lookup"><span data-stu-id="1adea-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="1adea-109">no O tamanho da `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="1adea-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="1adea-110">Consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="1adea-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="1adea-111">fora Um ponteiro para o tamanho da matriz retornada `signature` .</span><span class="sxs-lookup"><span data-stu-id="1adea-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="1adea-112">fora Um buffer que contém as assinaturas TypeSpec de todos os parâmetros genéricos.</span><span class="sxs-lookup"><span data-stu-id="1adea-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1adea-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="1adea-113">Remarks</span></span>  
 <span data-ttu-id="1adea-114">Para obter o tamanho necessário da matriz do método `signature` , defina o `cbSignature` argumento como 0 e `signature` como **nulo**.</span><span class="sxs-lookup"><span data-stu-id="1adea-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="1adea-115">Quando o método retornar, `pcbSignature` conterá o número de bytes necessários para a `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="1adea-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1adea-116">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1adea-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1adea-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1adea-117">Requirements</span></span>  
 <span data-ttu-id="1adea-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1adea-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1adea-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1adea-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1adea-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1adea-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1adea-121">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1adea-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1adea-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="1adea-122">See also</span></span>

- [<span data-ttu-id="1adea-123">Método GetTypeProps</span><span class="sxs-lookup"><span data-stu-id="1adea-123">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="1adea-124">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="1adea-124">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="1adea-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1adea-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
