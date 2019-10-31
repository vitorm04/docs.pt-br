---
title: 'Método ICorDebugMemoryBuffer:: GetSize'
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
ms.openlocfilehash: 1693860abe99884ee443be0666dfb6b485a219a0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128000"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="265d9-102">Método ICorDebugMemoryBuffer:: GetSize</span><span class="sxs-lookup"><span data-stu-id="265d9-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="265d9-103">Obtém o tamanho do buffer de memória em bytes.</span><span class="sxs-lookup"><span data-stu-id="265d9-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="265d9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="265d9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="265d9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="265d9-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="265d9-106">fora Um ponteiro para o tamanho do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="265d9-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="265d9-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="265d9-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="265d9-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="265d9-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="265d9-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="265d9-109">Requirements</span></span>  
 <span data-ttu-id="265d9-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="265d9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="265d9-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="265d9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="265d9-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="265d9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="265d9-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="265d9-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="265d9-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="265d9-114">See also</span></span>

- [<span data-ttu-id="265d9-115">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="265d9-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="265d9-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="265d9-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
