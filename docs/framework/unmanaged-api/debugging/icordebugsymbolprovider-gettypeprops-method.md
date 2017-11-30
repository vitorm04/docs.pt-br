---
title: "Método ICorDebugSymbolProvider::GetTypeProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ba736caf8d8d823a4cb56c75aa2202ad616983fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="cede2-102">Método ICorDebugSymbolProvider::GetTypeProps</span><span class="sxs-lookup"><span data-stu-id="cede2-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="cede2-103">Retorna informações sobre propriedades de um tipo, como o número de assinatura de seus parâmetros genéricos, dado um endereço virtual relativo (RVA) em uma vtable.</span><span class="sxs-lookup"><span data-stu-id="cede2-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cede2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cede2-104">Syntax</span></span>  
  
```  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cede2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cede2-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="cede2-106">[in] Um virtual endereço relativo (RVA) em uma vtable.</span><span class="sxs-lookup"><span data-stu-id="cede2-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="cede2-107">[in] O tamanho do `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="cede2-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="cede2-108">Consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="cede2-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="cede2-109">[out] [out] Um ponteiro para o tamanho do retornado `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="cede2-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="cede2-110">[out] Um buffer que contém as assinaturas typespec de todos os parâmetros genéricos.</span><span class="sxs-lookup"><span data-stu-id="cede2-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cede2-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="cede2-111">Remarks</span></span>  
 <span data-ttu-id="cede2-112">Para obter o tamanho necessário do tipo de `signature` de matriz, defina o `cbSignature` argumento como 0 e `signature` para **nulo**.</span><span class="sxs-lookup"><span data-stu-id="cede2-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="cede2-113">Quando o método retorna, `pcbSignature` conterá o número de bytes necessários para o `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="cede2-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cede2-114">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cede2-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cede2-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cede2-115">Requirements</span></span>  
 <span data-ttu-id="cede2-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cede2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cede2-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cede2-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cede2-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cede2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cede2-119">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cede2-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cede2-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cede2-120">See Also</span></span>  
 [<span data-ttu-id="cede2-121">Método GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="cede2-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)  
 [<span data-ttu-id="cede2-122">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="cede2-122">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="cede2-123">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="cede2-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
