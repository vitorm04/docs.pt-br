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
ms.openlocfilehash: a21198c70512af703e106870d1bc3f7882d62fe9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="51427-102">Método ICorDebugMemoryBuffer::GetSize</span><span class="sxs-lookup"><span data-stu-id="51427-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="51427-103">Obtém o tamanho do buffer de memória em bytes.</span><span class="sxs-lookup"><span data-stu-id="51427-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51427-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51427-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51427-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="51427-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="51427-106">[out] Um ponteiro para o tamanho do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="51427-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51427-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="51427-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51427-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="51427-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51427-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="51427-109">Requirements</span></span>  
 <span data-ttu-id="51427-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51427-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51427-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51427-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51427-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51427-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51427-113">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51427-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51427-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51427-114">See Also</span></span>  
 [<span data-ttu-id="51427-115">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="51427-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="51427-116">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="51427-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
