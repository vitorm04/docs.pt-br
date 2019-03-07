---
title: Método ICorDebugSymbolProvider::GetAssemblyImageBytes
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c44260d3b5baa18bc24f85cdbea94016b43291e2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489774"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="93a11-102">Método ICorDebugSymbolProvider::GetAssemblyImageBytes</span><span class="sxs-lookup"><span data-stu-id="93a11-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="93a11-103">Lê dados de um assembly mesclado de acordo com um endereço virtual relativo (RVA) no assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="93a11-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93a11-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="93a11-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93a11-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="93a11-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="93a11-106">[in] Um endereço virtual relativo (RVA) em um assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="93a11-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="93a11-107">O número de bytes a serem lidos a partir do assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="93a11-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="93a11-108">Um ponteiro para o endereço de um [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objeto que contém informações sobre o buffer de memória com metadados do assembly mesclada.</span><span class="sxs-lookup"><span data-stu-id="93a11-108">A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93a11-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="93a11-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93a11-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="93a11-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93a11-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="93a11-111">Requirements</span></span>  
 <span data-ttu-id="93a11-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93a11-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93a11-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93a11-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93a11-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93a11-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93a11-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93a11-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93a11-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93a11-116">See also</span></span>
- [<span data-ttu-id="93a11-117">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="93a11-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="93a11-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="93a11-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
