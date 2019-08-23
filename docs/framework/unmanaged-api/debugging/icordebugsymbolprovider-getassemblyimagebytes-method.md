---
title: 'Método ICorDebugSymbolProvider:: GetAssemblyImageBytes'
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf6e707b6176ccd205785aafa6c5a1adf0a3fc78
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964669"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="069af-102">Método ICorDebugSymbolProvider:: GetAssemblyImageBytes</span><span class="sxs-lookup"><span data-stu-id="069af-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="069af-103">Lê dados de um assembly mesclado, dado um endereço virtual relativo (RVA) no assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="069af-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="069af-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="069af-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="069af-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="069af-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="069af-106">no Um RVA (endereço virtual relativo) em um assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="069af-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="069af-107">O número de bytes a serem lidos do assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="069af-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="069af-108">Um ponteiro para o endereço de um objeto [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) que contém informações sobre o buffer de memória com metadados de assembly mesclados.</span><span class="sxs-lookup"><span data-stu-id="069af-108">A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="069af-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="069af-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="069af-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="069af-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="069af-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="069af-111">Requirements</span></span>  
 <span data-ttu-id="069af-112">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="069af-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="069af-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="069af-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="069af-114">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="069af-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="069af-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="069af-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="069af-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="069af-116">See also</span></span>

- [<span data-ttu-id="069af-117">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="069af-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="069af-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="069af-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
