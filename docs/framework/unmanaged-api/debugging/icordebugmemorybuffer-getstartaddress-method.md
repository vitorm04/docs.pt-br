---
title: 'Método ICorDebugMemoryBuffer:: GetStartAddress'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: e2876398ceaf863bbb3c7e576d59b89c52f1bdaf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127984"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="6d015-102">Método ICorDebugMemoryBuffer:: GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="6d015-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="6d015-103">Obtém o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="6d015-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d015-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d015-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d015-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6d015-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="6d015-106">fora Um ponteiro para o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="6d015-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d015-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="6d015-107">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="6d015-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6d015-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d015-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6d015-109">Requirements</span></span>  
 <span data-ttu-id="6d015-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d015-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d015-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d015-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d015-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d015-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d015-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d015-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d015-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d015-114">See also</span></span>

- [<span data-ttu-id="6d015-115">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="6d015-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="6d015-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6d015-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
