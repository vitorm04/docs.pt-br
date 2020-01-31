---
title: 'Método ICorDebugSymbolProvider:: GetTypeProps'
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
ms.openlocfilehash: 5fa091eaf2cf93b0c645effeec3c959d42665fc9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791541"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="e6fe0-102">Método ICorDebugSymbolProvider:: GetTypeProps</span><span class="sxs-lookup"><span data-stu-id="e6fe0-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="e6fe0-103">Retorna informações sobre as propriedades de um tipo, como o número de assinatura de seus parâmetros genéricos, considerando um endereço virtual relativo (RVA) em uma vtable.</span><span class="sxs-lookup"><span data-stu-id="e6fe0-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6fe0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6fe0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6fe0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e6fe0-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="e6fe0-106">no Um RVA (endereço virtual relativo) em uma vtable.</span><span class="sxs-lookup"><span data-stu-id="e6fe0-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="e6fe0-107">no O tamanho da matriz de `signature`.</span><span class="sxs-lookup"><span data-stu-id="e6fe0-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="e6fe0-108">Consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="e6fe0-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="e6fe0-109">fora fora Um ponteiro para o tamanho da matriz de `signature` retornada.</span><span class="sxs-lookup"><span data-stu-id="e6fe0-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="e6fe0-110">fora Um buffer que contém as assinaturas TypeSpec de todos os parâmetros genéricos.</span><span class="sxs-lookup"><span data-stu-id="e6fe0-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6fe0-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="e6fe0-111">Remarks</span></span>  
 <span data-ttu-id="e6fe0-112">Para obter o tamanho necessário da matriz de `signature` do tipo, defina o argumento `cbSignature` como 0 e `signature` como **nulo**.</span><span class="sxs-lookup"><span data-stu-id="e6fe0-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="e6fe0-113">Quando o método retornar, `pcbSignature` conterá o número de bytes necessários para a matriz `signature`.</span><span class="sxs-lookup"><span data-stu-id="e6fe0-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e6fe0-114">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e6fe0-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6fe0-115">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="e6fe0-115">Requirements</span></span>  
 <span data-ttu-id="e6fe0-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6fe0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6fe0-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6fe0-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6fe0-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6fe0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6fe0-119">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6fe0-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6fe0-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="e6fe0-120">See also</span></span>

- [<span data-ttu-id="e6fe0-121">Método GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="e6fe0-121">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="e6fe0-122">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="e6fe0-122">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="e6fe0-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e6fe0-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
