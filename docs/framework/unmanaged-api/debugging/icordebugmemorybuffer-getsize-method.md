---
title: Método ICorDebugMemoryBuffer::GetSize
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d687f2bbd3c20564368d4246961b56382ea14cf5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916546"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="a99c8-102">Método ICorDebugMemoryBuffer::GetSize</span><span class="sxs-lookup"><span data-stu-id="a99c8-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="a99c8-103">Obtém o tamanho do buffer de memória em bytes.</span><span class="sxs-lookup"><span data-stu-id="a99c8-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a99c8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a99c8-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a99c8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a99c8-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="a99c8-106">[out] Um ponteiro para o tamanho do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="a99c8-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a99c8-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a99c8-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a99c8-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a99c8-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a99c8-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a99c8-109">Requirements</span></span>  
 <span data-ttu-id="a99c8-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a99c8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a99c8-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a99c8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a99c8-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a99c8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a99c8-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a99c8-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a99c8-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a99c8-114">See also</span></span>

- [<span data-ttu-id="a99c8-115">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="a99c8-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="a99c8-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a99c8-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
