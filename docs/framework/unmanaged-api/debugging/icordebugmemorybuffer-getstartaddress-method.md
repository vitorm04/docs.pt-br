---
title: Método ICorDebugMemoryBuffer::GetStartAddress
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f4f51c087112053aa7b76bff1f7c55016c8ff57
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474742"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="cb3d6-102">Método ICorDebugMemoryBuffer::GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="cb3d6-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="cb3d6-103">Obtém o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="cb3d6-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb3d6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb3d6-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb3d6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cb3d6-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="cb3d6-106">[out] Um ponteiro para o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="cb3d6-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb3d6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb3d6-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="cb3d6-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cb3d6-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb3d6-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cb3d6-109">Requirements</span></span>  
 <span data-ttu-id="cb3d6-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb3d6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb3d6-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb3d6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb3d6-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb3d6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb3d6-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb3d6-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb3d6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb3d6-114">See also</span></span>
- [<span data-ttu-id="cb3d6-115">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="cb3d6-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="cb3d6-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="cb3d6-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
