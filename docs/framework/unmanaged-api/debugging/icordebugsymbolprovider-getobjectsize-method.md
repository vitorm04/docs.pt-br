---
title: "Método ICorDebugSymbolProvider::GetObjectSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f8817eb79c825a02ec5654ec340dedd6c77889a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="f743b-102">Método ICorDebugSymbolProvider::GetObjectSize</span><span class="sxs-lookup"><span data-stu-id="f743b-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="f743b-103">Retorna o tamanho do objeto para um objeto com base em sua assinatura typespec.</span><span class="sxs-lookup"><span data-stu-id="f743b-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f743b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f743b-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f743b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f743b-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="f743b-106">[in] O número de bytes na assinatura typespec.</span><span class="sxs-lookup"><span data-stu-id="f743b-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="f743b-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="f743b-107">typeSig</span></span>  
 <span data-ttu-id="f743b-108">[in] A assinatura typespec.</span><span class="sxs-lookup"><span data-stu-id="f743b-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="f743b-109">[out] Um ponteiro para o tamanho do objeto.</span><span class="sxs-lookup"><span data-stu-id="f743b-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f743b-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f743b-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f743b-111">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f743b-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f743b-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f743b-112">Requirements</span></span>  
 <span data-ttu-id="f743b-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f743b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f743b-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f743b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f743b-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f743b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f743b-116">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f743b-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f743b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f743b-117">See Also</span></span>  
 [<span data-ttu-id="f743b-118">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="f743b-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="f743b-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f743b-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
