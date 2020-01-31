---
title: 'Método ICorDebugMemoryBuffer:: GetStartAddress'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: f2b09c847a6bf577b78c8155f85f07b93877fbe9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793164"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="358af-102">Método ICorDebugMemoryBuffer:: GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="358af-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="358af-103">Obtém o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="358af-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="358af-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="358af-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="358af-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="358af-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="358af-106">fora Um ponteiro para o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="358af-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="358af-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="358af-107">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="358af-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="358af-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="358af-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="358af-109">Requirements</span></span>  
 <span data-ttu-id="358af-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="358af-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="358af-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="358af-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="358af-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="358af-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="358af-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="358af-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="358af-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="358af-114">See also</span></span>

- [<span data-ttu-id="358af-115">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="358af-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="358af-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="358af-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
