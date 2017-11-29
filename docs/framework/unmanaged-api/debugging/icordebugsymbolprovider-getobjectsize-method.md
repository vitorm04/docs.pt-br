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
ms.openlocfilehash: ea9e0fcae9f98869884ad887a6c24de342512b87
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="75d3c-102">Método ICorDebugSymbolProvider::GetObjectSize</span><span class="sxs-lookup"><span data-stu-id="75d3c-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="75d3c-103">Retorna o tamanho do objeto para um objeto com base em sua assinatura typespec.</span><span class="sxs-lookup"><span data-stu-id="75d3c-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75d3c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75d3c-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75d3c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75d3c-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="75d3c-106">[in] O número de bytes na assinatura typespec.</span><span class="sxs-lookup"><span data-stu-id="75d3c-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="75d3c-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="75d3c-107">typeSig</span></span>  
 <span data-ttu-id="75d3c-108">[in] A assinatura typespec.</span><span class="sxs-lookup"><span data-stu-id="75d3c-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="75d3c-109">[out] Um ponteiro para o tamanho do objeto.</span><span class="sxs-lookup"><span data-stu-id="75d3c-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75d3c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="75d3c-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75d3c-111">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="75d3c-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75d3c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="75d3c-112">Requirements</span></span>  
 <span data-ttu-id="75d3c-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75d3c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75d3c-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75d3c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75d3c-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75d3c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75d3c-116">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75d3c-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75d3c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75d3c-117">See Also</span></span>  
 [<span data-ttu-id="75d3c-118">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="75d3c-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="75d3c-119">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="75d3c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
