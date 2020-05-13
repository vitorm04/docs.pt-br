---
title: 'Método ICorDebugMemoryBuffer:: GetSize'
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
ms.openlocfilehash: 1bef2e2d0e1a1cef74c7568fdd2e9b7986500488
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212599"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="1b3a4-102">Método ICorDebugMemoryBuffer:: GetSize</span><span class="sxs-lookup"><span data-stu-id="1b3a4-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="1b3a4-103">Obtém o tamanho do buffer de memória em bytes.</span><span class="sxs-lookup"><span data-stu-id="1b3a4-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b3a4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b3a4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b3a4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1b3a4-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="1b3a4-106">fora Um ponteiro para o tamanho do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="1b3a4-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b3a4-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b3a4-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b3a4-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1b3a4-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b3a4-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1b3a4-109">Requirements</span></span>  
 <span data-ttu-id="1b3a4-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b3a4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b3a4-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b3a4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b3a4-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b3a4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b3a4-113">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b3a4-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b3a4-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="1b3a4-114">See also</span></span>

- [<span data-ttu-id="1b3a4-115">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="1b3a4-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="1b3a4-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1b3a4-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
