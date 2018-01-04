---
title: "Método ICorDebugSymbolProvider::GetAssemblyImageMetadata"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ff6b26dd9a0ed56e5194dc997270cf9d2dbe42b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="da184-102">Método ICorDebugSymbolProvider::GetAssemblyImageMetadata</span><span class="sxs-lookup"><span data-stu-id="da184-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="da184-103">Retorna os metadados de um assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="da184-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da184-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da184-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da184-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="da184-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="da184-106">[out] Um ponteiro para o endereço de um [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objeto que contém informações sobre o tamanho e o endereço de metadados do assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="da184-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da184-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="da184-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da184-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="da184-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da184-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da184-109">Requirements</span></span>  
 <span data-ttu-id="da184-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da184-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da184-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da184-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da184-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da184-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da184-113">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da184-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da184-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da184-114">See Also</span></span>  
 [<span data-ttu-id="da184-115">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="da184-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="da184-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="da184-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
