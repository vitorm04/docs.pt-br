---
title: Método ICorDebugMemoryBuffer::GetStartAddress
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58649a0fc12ce63a1307af5d831dbf5e0d5a776a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136975"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="d8c2e-102">Método ICorDebugMemoryBuffer::GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="d8c2e-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="d8c2e-103">Obtém o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="d8c2e-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8c2e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8c2e-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8c2e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d8c2e-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="d8c2e-106">[out] Um ponteiro para o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="d8c2e-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8c2e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d8c2e-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="d8c2e-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d8c2e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8c2e-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d8c2e-109">Requirements</span></span>  
 <span data-ttu-id="d8c2e-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8c2e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8c2e-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8c2e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8c2e-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8c2e-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d8c2e-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="d8c2e-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d8c2e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8c2e-114">See also</span></span>

- [<span data-ttu-id="d8c2e-115">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="d8c2e-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="d8c2e-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d8c2e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
