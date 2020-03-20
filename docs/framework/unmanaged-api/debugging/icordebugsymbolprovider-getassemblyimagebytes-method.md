---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes Method
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: 6361b12802876ef480acbe1cc13f32b77ba0be49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178488"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="8f233-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span><span class="sxs-lookup"><span data-stu-id="8f233-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="8f233-103">Lê dados de um conjunto mesclado dado um endereço virtual relativo (RVA) no conjunto mesclado.</span><span class="sxs-lookup"><span data-stu-id="8f233-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f233-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f233-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f233-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="8f233-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="8f233-106">[em] Um endereço virtual relativo (RVA) em um conjunto mesclado.</span><span class="sxs-lookup"><span data-stu-id="8f233-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="8f233-107">O número de bytes a serem lidos da montagem fundida.</span><span class="sxs-lookup"><span data-stu-id="8f233-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="8f233-108">Um ponteiro para o endereço de um objeto [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) que contém informações sobre o buffer de memória com metadados de montagem mesclados.</span><span class="sxs-lookup"><span data-stu-id="8f233-108">A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f233-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="8f233-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8f233-110">Este método está disponível apenas com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8f233-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f233-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8f233-111">Requirements</span></span>  
 <span data-ttu-id="8f233-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f233-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f233-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f233-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f233-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f233-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f233-115">**.NET Framework Versions:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f233-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f233-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="8f233-116">See also</span></span>

- [<span data-ttu-id="8f233-117">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="8f233-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="8f233-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8f233-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
