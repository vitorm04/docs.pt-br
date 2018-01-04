---
title: "Método ICorDebugLoadedModule::GetSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1fb340845afac0f5a13f7c4646d11ac057ebd054
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="2abc5-102">Método ICorDebugLoadedModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="2abc5-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="2abc5-103">Obtém o tamanho em bytes do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="2abc5-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2abc5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2abc5-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2abc5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2abc5-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="2abc5-106">[out] Um ponteiro para o número de bytes no módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="2abc5-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2abc5-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2abc5-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2abc5-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2abc5-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2abc5-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2abc5-109">Requirements</span></span>  
 <span data-ttu-id="2abc5-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2abc5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2abc5-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2abc5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2abc5-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2abc5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2abc5-113">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2abc5-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2abc5-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2abc5-114">See Also</span></span>  
 [<span data-ttu-id="2abc5-115">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="2abc5-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="2abc5-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2abc5-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
