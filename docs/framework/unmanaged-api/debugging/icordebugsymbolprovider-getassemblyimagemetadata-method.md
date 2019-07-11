---
title: Método ICorDebugSymbolProvider::GetAssemblyImageMetadata
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d96aa82e9fd8b651ab005cba4945f6977c1e3d3a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771509"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="f3149-102">Método ICorDebugSymbolProvider::GetAssemblyImageMetadata</span><span class="sxs-lookup"><span data-stu-id="f3149-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="f3149-103">Retorna os metadados de um assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="f3149-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3149-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3149-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3149-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f3149-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="f3149-106">[out] Um ponteiro para o endereço de um [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objeto que contém informações sobre o tamanho e o endereço de metadados do assembly mesclada.</span><span class="sxs-lookup"><span data-stu-id="f3149-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3149-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f3149-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3149-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f3149-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3149-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f3149-109">Requirements</span></span>  
 <span data-ttu-id="f3149-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3149-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3149-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3149-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3149-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3149-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3149-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3149-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3149-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3149-114">See also</span></span>

- [<span data-ttu-id="f3149-115">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="f3149-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="f3149-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f3149-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
