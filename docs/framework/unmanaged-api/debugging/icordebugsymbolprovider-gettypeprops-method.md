---
title: Método ICorDebugSymbolProvider::GetTypeProps
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5f9867dbdc244ed22948dbe9a07a7ea06292d6a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079078"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="4e735-102">Método ICorDebugSymbolProvider::GetTypeProps</span><span class="sxs-lookup"><span data-stu-id="4e735-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="4e735-103">Retorna informações sobre propriedades de um tipo, como o número de assinatura de seus parâmetros genéricos, considerando um endereço virtual relativo (RVA) em uma vtable.</span><span class="sxs-lookup"><span data-stu-id="4e735-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e735-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4e735-104">Syntax</span></span>  
  
```  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e735-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4e735-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="4e735-106">[in] Um endereço virtual relativo (RVA) em uma vtable.</span><span class="sxs-lookup"><span data-stu-id="4e735-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="4e735-107">[in] O tamanho do `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="4e735-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="4e735-108">Consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="4e735-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="4e735-109">[out] [out] Um ponteiro para o tamanho de retornado `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="4e735-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="4e735-110">[out] Um buffer que contém as assinaturas de typespec de todos os parâmetros genéricos.</span><span class="sxs-lookup"><span data-stu-id="4e735-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e735-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="4e735-111">Remarks</span></span>  
 <span data-ttu-id="4e735-112">Para obter o tamanho necessário do tipo de `signature` matriz, defina a `cbSignature` argumento como 0 e `signature` à **nulo**.</span><span class="sxs-lookup"><span data-stu-id="4e735-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="4e735-113">Quando o método retorna, `pcbSignature` conterá o número de bytes necessários para o `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="4e735-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e735-114">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4e735-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e735-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4e735-115">Requirements</span></span>  
 <span data-ttu-id="4e735-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e735-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e735-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e735-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e735-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e735-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4e735-119">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="4e735-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4e735-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e735-120">See also</span></span>

- [<span data-ttu-id="4e735-121">Método GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="4e735-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="4e735-122">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="4e735-122">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="4e735-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4e735-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
