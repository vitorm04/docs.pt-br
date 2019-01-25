---
title: Método ICorDebugMemoryBuffer::GetStartAddress
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29149ceb155cdfdf7b735d6939809e80f2ba4dc0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695537"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="23a6f-102">Método ICorDebugMemoryBuffer::GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="23a6f-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="23a6f-103">Obtém o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="23a6f-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23a6f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23a6f-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23a6f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="23a6f-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="23a6f-106">[out] Um ponteiro para o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="23a6f-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23a6f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="23a6f-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="23a6f-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="23a6f-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23a6f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="23a6f-109">Requirements</span></span>  
 <span data-ttu-id="23a6f-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23a6f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23a6f-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23a6f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23a6f-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23a6f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23a6f-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23a6f-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23a6f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23a6f-114">See also</span></span>
- [<span data-ttu-id="23a6f-115">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="23a6f-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="23a6f-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="23a6f-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
