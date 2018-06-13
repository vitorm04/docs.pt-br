---
title: Método ICorDebugMemoryBuffer::GetStartAddress
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1aa816ea9e6185791e09bcdb0e47c50761a5ebc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422927"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="81e40-102">Método ICorDebugMemoryBuffer::GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="81e40-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="81e40-103">Obtém o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="81e40-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81e40-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81e40-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81e40-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="81e40-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="81e40-106">[out] Um ponteiro para o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="81e40-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81e40-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="81e40-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="81e40-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="81e40-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81e40-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81e40-109">Requirements</span></span>  
 <span data-ttu-id="81e40-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81e40-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81e40-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81e40-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81e40-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81e40-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81e40-113">**Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81e40-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e40-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81e40-114">See Also</span></span>  
 [<span data-ttu-id="81e40-115">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="81e40-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="81e40-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="81e40-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
