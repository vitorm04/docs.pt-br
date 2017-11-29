---
title: "Método ICorDebugStaticFieldSymbol::GetAddress"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 20c0c934772625d27057957d00e53fb4b485c4fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="507f8-102">Método ICorDebugStaticFieldSymbol::GetAddress</span><span class="sxs-lookup"><span data-stu-id="507f8-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="507f8-103">Obtém o endereço de um campo estático.</span><span class="sxs-lookup"><span data-stu-id="507f8-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="507f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="507f8-104">Syntax</span></span>  
  
```  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="507f8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="507f8-105">Parameters</span></span>  
 <span data-ttu-id="507f8-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="507f8-106">pRVA</span></span>  
 <span data-ttu-id="507f8-107">[out] Um ponteiro para o endereço virtual relativo (RVA) do campo estático.</span><span class="sxs-lookup"><span data-stu-id="507f8-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="507f8-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="507f8-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="507f8-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="507f8-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="507f8-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="507f8-110">Requirements</span></span>  
 <span data-ttu-id="507f8-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="507f8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="507f8-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="507f8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="507f8-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="507f8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="507f8-114">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="507f8-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="507f8-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="507f8-115">See Also</span></span>  
 [<span data-ttu-id="507f8-116">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="507f8-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="507f8-117">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="507f8-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
