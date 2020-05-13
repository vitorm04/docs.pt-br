---
title: 'Método ICorDebugMemoryBuffer:: GetStartAddress'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: 47369c744ee42fb03857a3e69063a04e4f509d0d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212341"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="d2d12-102">Método ICorDebugMemoryBuffer:: GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="d2d12-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="d2d12-103">Obtém o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="d2d12-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2d12-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2d12-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2d12-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d2d12-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="d2d12-106">fora Um ponteiro para o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="d2d12-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2d12-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d2d12-107">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="d2d12-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d2d12-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2d12-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d2d12-109">Requirements</span></span>  
 <span data-ttu-id="d2d12-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2d12-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2d12-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2d12-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2d12-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2d12-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2d12-113">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2d12-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2d12-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="d2d12-114">See also</span></span>

- [<span data-ttu-id="d2d12-115">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="d2d12-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="d2d12-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d2d12-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
