---
title: 'Método ICorDebugMemoryBuffer:: GetSize'
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
ms.openlocfilehash: 51c13b67951c714d1aec602ffea22891328565a0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793181"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="438ea-102">Método ICorDebugMemoryBuffer:: GetSize</span><span class="sxs-lookup"><span data-stu-id="438ea-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="438ea-103">Obtém o tamanho do buffer de memória em bytes.</span><span class="sxs-lookup"><span data-stu-id="438ea-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="438ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="438ea-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="438ea-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="438ea-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="438ea-106">fora Um ponteiro para o tamanho do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="438ea-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="438ea-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="438ea-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="438ea-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="438ea-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="438ea-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="438ea-109">Requirements</span></span>  
 <span data-ttu-id="438ea-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="438ea-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="438ea-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="438ea-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="438ea-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="438ea-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="438ea-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="438ea-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="438ea-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="438ea-114">See also</span></span>

- [<span data-ttu-id="438ea-115">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="438ea-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="438ea-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="438ea-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
