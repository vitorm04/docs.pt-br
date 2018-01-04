---
title: "Método ICorDebugSymbolProvider::GetAssemblyImageBytes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23c6dc836aefe1dd89431e003058ba2056eba3ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="755d3-102">Método ICorDebugSymbolProvider::GetAssemblyImageBytes</span><span class="sxs-lookup"><span data-stu-id="755d3-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="755d3-103">Lê dados de um assembly mesclado fornecido um endereço virtual relativo (RVA) no assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="755d3-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="755d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="755d3-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="755d3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="755d3-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="755d3-106">[in] Um virtual endereço relativo (RVA) em um assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="755d3-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="755d3-107">O número de bytes a serem lidos do assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="755d3-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="755d3-108">Um ponteiro para o endereço de um [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objeto que contém informações sobre o buffer de memória com metadados de assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="755d3-108">A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="755d3-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="755d3-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="755d3-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="755d3-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="755d3-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="755d3-111">Requirements</span></span>  
 <span data-ttu-id="755d3-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="755d3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="755d3-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="755d3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="755d3-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="755d3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="755d3-115">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="755d3-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="755d3-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="755d3-116">See Also</span></span>  
 [<span data-ttu-id="755d3-117">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="755d3-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="755d3-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="755d3-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
