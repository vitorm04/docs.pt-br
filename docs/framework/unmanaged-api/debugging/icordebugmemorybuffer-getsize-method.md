---
title: Método ICorDebugMemoryBuffer::GetSize
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: caf95e0b5c8d4ae942bb428f53d4e58313e0e78e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414745"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="2b8cb-102">Método ICorDebugMemoryBuffer::GetSize</span><span class="sxs-lookup"><span data-stu-id="2b8cb-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="2b8cb-103">Obtém o tamanho do buffer de memória em bytes.</span><span class="sxs-lookup"><span data-stu-id="2b8cb-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b8cb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b8cb-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b8cb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2b8cb-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="2b8cb-106">[out] Um ponteiro para o tamanho do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="2b8cb-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b8cb-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b8cb-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b8cb-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2b8cb-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b8cb-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2b8cb-109">Requirements</span></span>  
 <span data-ttu-id="2b8cb-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b8cb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b8cb-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b8cb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b8cb-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b8cb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b8cb-113">**Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b8cb-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b8cb-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b8cb-114">See Also</span></span>  
 [<span data-ttu-id="2b8cb-115">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="2b8cb-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="2b8cb-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2b8cb-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
