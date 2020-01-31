---
title: 'Método ICorDebugSymbolProvider:: GetAssemblyImageBytes'
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: b7a8f942d493b7b775a31dce5ab4d351a77cfe5f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791669"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="90f5d-102">Método ICorDebugSymbolProvider:: GetAssemblyImageBytes</span><span class="sxs-lookup"><span data-stu-id="90f5d-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="90f5d-103">Lê dados de um assembly mesclado, dado um endereço virtual relativo (RVA) no assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="90f5d-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90f5d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90f5d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90f5d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="90f5d-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="90f5d-106">no Um RVA (endereço virtual relativo) em um assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="90f5d-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="90f5d-107">O número de bytes a serem lidos do assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="90f5d-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="90f5d-108">Um ponteiro para o endereço de um objeto [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) que contém informações sobre o buffer de memória com metadados de assembly mesclados.</span><span class="sxs-lookup"><span data-stu-id="90f5d-108">A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90f5d-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="90f5d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90f5d-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="90f5d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90f5d-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="90f5d-111">Requirements</span></span>  
 <span data-ttu-id="90f5d-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90f5d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90f5d-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90f5d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90f5d-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90f5d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90f5d-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90f5d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90f5d-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="90f5d-116">See also</span></span>

- [<span data-ttu-id="90f5d-117">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="90f5d-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="90f5d-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="90f5d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
