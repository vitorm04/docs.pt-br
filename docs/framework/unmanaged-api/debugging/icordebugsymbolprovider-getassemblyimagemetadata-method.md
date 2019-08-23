---
title: 'Método ICorDebugSymbolProvider:: GetAssemblyImageMetadata'
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad86c42d0f23de25fe0e5b9123a0dba3695d8d64
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964654"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="aa3bc-102">Método ICorDebugSymbolProvider:: GetAssemblyImageMetadata</span><span class="sxs-lookup"><span data-stu-id="aa3bc-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="aa3bc-103">Retorna os metadados de um assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="aa3bc-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa3bc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa3bc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa3bc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa3bc-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="aa3bc-106">fora Um ponteiro para o endereço de um objeto [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) que contém informações sobre o tamanho e o endereço dos metadados do assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="aa3bc-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa3bc-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa3bc-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa3bc-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="aa3bc-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa3bc-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa3bc-109">Requirements</span></span>  
 <span data-ttu-id="aa3bc-110">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa3bc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa3bc-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa3bc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa3bc-112">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa3bc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa3bc-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa3bc-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa3bc-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa3bc-114">See also</span></span>

- [<span data-ttu-id="aa3bc-115">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="aa3bc-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="aa3bc-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="aa3bc-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
