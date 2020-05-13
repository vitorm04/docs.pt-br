---
title: 'Método ICorDebugSymbolProvider:: GetAssemblyImageBytes'
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: a555acb9e23098b0a0f70924032771b1ae18e88e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376111"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="67133-102">Método ICorDebugSymbolProvider:: GetAssemblyImageBytes</span><span class="sxs-lookup"><span data-stu-id="67133-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="67133-103">Lê dados de um assembly mesclado, dado um endereço virtual relativo (RVA) no assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="67133-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67133-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="67133-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67133-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="67133-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="67133-106">no Um RVA (endereço virtual relativo) em um assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="67133-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="67133-107">O número de bytes a serem lidos do assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="67133-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="67133-108">Um ponteiro para o endereço de um objeto [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) que contém informações sobre o buffer de memória com metadados de assembly mesclados.</span><span class="sxs-lookup"><span data-stu-id="67133-108">A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67133-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="67133-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67133-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="67133-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67133-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="67133-111">Requirements</span></span>  
 <span data-ttu-id="67133-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67133-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67133-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67133-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67133-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67133-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67133-115">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67133-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67133-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="67133-116">See also</span></span>

- [<span data-ttu-id="67133-117">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="67133-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="67133-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="67133-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
