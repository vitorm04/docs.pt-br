---
title: Método ICorDebugSymbolProvider::GetAssemblyImageBytes
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 103e724c37ae356729dd5bba3ff66c0f443f6eaa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953511"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="9a02b-102">Método ICorDebugSymbolProvider::GetAssemblyImageBytes</span><span class="sxs-lookup"><span data-stu-id="9a02b-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="9a02b-103">Lê dados de um assembly mesclado de acordo com um endereço virtual relativo (RVA) no assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="9a02b-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a02b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a02b-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a02b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9a02b-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="9a02b-106">[in] Um endereço virtual relativo (RVA) em um assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="9a02b-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="9a02b-107">O número de bytes a serem lidos a partir do assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="9a02b-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="9a02b-108">Um ponteiro para o endereço de um [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objeto que contém informações sobre o buffer de memória com metadados do assembly mesclada.</span><span class="sxs-lookup"><span data-stu-id="9a02b-108">A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a02b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a02b-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a02b-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9a02b-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a02b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9a02b-111">Requirements</span></span>  
 <span data-ttu-id="9a02b-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a02b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a02b-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a02b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a02b-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a02b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a02b-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a02b-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a02b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a02b-116">See also</span></span>

- [<span data-ttu-id="9a02b-117">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="9a02b-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="9a02b-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9a02b-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
