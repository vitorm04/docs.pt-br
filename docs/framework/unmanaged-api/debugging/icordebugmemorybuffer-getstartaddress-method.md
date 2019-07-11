---
title: Método ICorDebugMemoryBuffer::GetStartAddress
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9208d07b697c3bb8a99e13582eda70dcb8dd826b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752778"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="75a8d-102">Método ICorDebugMemoryBuffer::GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="75a8d-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="75a8d-103">Obtém o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="75a8d-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75a8d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75a8d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75a8d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75a8d-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="75a8d-106">[out] Um ponteiro para o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="75a8d-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75a8d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="75a8d-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="75a8d-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="75a8d-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75a8d-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="75a8d-109">Requirements</span></span>  
 <span data-ttu-id="75a8d-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75a8d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75a8d-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75a8d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75a8d-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75a8d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75a8d-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75a8d-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75a8d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75a8d-114">See also</span></span>

- [<span data-ttu-id="75a8d-115">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="75a8d-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="75a8d-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="75a8d-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
