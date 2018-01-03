---
title: "Método ICorDebugMemoryBuffer::GetSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 658fb2ce289b4b8cabfcf0cc2ea5f8dace2ec754
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="e23f0-102">Método ICorDebugMemoryBuffer::GetSize</span><span class="sxs-lookup"><span data-stu-id="e23f0-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="e23f0-103">Obtém o tamanho do buffer de memória em bytes.</span><span class="sxs-lookup"><span data-stu-id="e23f0-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e23f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e23f0-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e23f0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e23f0-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="e23f0-106">[out] Um ponteiro para o tamanho do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="e23f0-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e23f0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e23f0-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e23f0-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e23f0-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e23f0-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e23f0-109">Requirements</span></span>  
 <span data-ttu-id="e23f0-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e23f0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e23f0-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e23f0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e23f0-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e23f0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e23f0-113">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e23f0-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e23f0-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e23f0-114">See Also</span></span>  
 [<span data-ttu-id="e23f0-115">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="e23f0-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="e23f0-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e23f0-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
