---
title: "Método ICorDebugLoadedModule::GetBaseAddress"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b192c606697896371202e98945f83623bbb99bb9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="165b6-102">Método ICorDebugLoadedModule::GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="165b6-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="165b6-103">Obtém o endereço base do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="165b6-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="165b6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="165b6-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="165b6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="165b6-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="165b6-106">[out] Um ponteiro para o endereço base do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="165b6-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="165b6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="165b6-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="165b6-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="165b6-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="165b6-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="165b6-109">Requirements</span></span>  
 <span data-ttu-id="165b6-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="165b6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="165b6-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="165b6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="165b6-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="165b6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="165b6-113">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="165b6-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="165b6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="165b6-114">See Also</span></span>  
 [<span data-ttu-id="165b6-115">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="165b6-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="165b6-116">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="165b6-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
