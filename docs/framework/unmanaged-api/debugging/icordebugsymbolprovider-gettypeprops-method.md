---
title: 'Método ICorDebugSymbolProvider:: GetTypeProps'
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c8ea3a201cc94ef7bdf679371ef43ab2641b791
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955543"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="664cd-102">Método ICorDebugSymbolProvider:: GetTypeProps</span><span class="sxs-lookup"><span data-stu-id="664cd-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="664cd-103">Retorna informações sobre as propriedades de um tipo, como o número de assinatura de seus parâmetros genéricos, considerando um endereço virtual relativo (RVA) em uma vtable.</span><span class="sxs-lookup"><span data-stu-id="664cd-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="664cd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="664cd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="664cd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="664cd-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="664cd-106">no Um RVA (endereço virtual relativo) em uma vtable.</span><span class="sxs-lookup"><span data-stu-id="664cd-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="664cd-107">no O tamanho da `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="664cd-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="664cd-108">Consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="664cd-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="664cd-109">fora fora Um ponteiro para o tamanho da matriz retornada `signature` .</span><span class="sxs-lookup"><span data-stu-id="664cd-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="664cd-110">fora Um buffer que contém as assinaturas TypeSpec de todos os parâmetros genéricos.</span><span class="sxs-lookup"><span data-stu-id="664cd-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="664cd-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="664cd-111">Remarks</span></span>  
 <span data-ttu-id="664cd-112">Para obter o tamanho necessário da matriz `signature` do tipo, defina o `cbSignature` argumento como 0 e `signature` como **nulo**.</span><span class="sxs-lookup"><span data-stu-id="664cd-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="664cd-113">Quando o método retornar, `pcbSignature` conterá o número de bytes necessários para a `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="664cd-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="664cd-114">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="664cd-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="664cd-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="664cd-115">Requirements</span></span>  
 <span data-ttu-id="664cd-116">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="664cd-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="664cd-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="664cd-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="664cd-118">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="664cd-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="664cd-119">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="664cd-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="664cd-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="664cd-120">See also</span></span>

- [<span data-ttu-id="664cd-121">Método GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="664cd-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="664cd-122">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="664cd-122">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="664cd-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="664cd-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
