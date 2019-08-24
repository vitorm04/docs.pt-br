---
title: 'Método ICorDebugMemoryBuffer:: GetStartAddress'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1394624051baa9e7dd21e29788d5fab28332081b
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987547"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="f88cd-102">Método ICorDebugMemoryBuffer:: GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="f88cd-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="f88cd-103">Obtém o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="f88cd-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f88cd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f88cd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f88cd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f88cd-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="f88cd-106">fora Um ponteiro para o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="f88cd-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f88cd-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f88cd-107">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="f88cd-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f88cd-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f88cd-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f88cd-109">Requirements</span></span>  
 <span data-ttu-id="f88cd-110">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f88cd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f88cd-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f88cd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f88cd-112">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f88cd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f88cd-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f88cd-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f88cd-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f88cd-114">See also</span></span>

- [<span data-ttu-id="f88cd-115">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="f88cd-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="f88cd-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f88cd-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
