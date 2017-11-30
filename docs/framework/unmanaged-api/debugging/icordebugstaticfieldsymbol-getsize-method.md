---
title: "Método ICorDebugStaticFieldSymbol::GetSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 256a15952cd52c5a096e1f0b8c7fc2086cde226c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="2984e-102">Método ICorDebugStaticFieldSymbol::GetSize</span><span class="sxs-lookup"><span data-stu-id="2984e-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="2984e-103">Obtém o tamanho em bytes do campo estático.</span><span class="sxs-lookup"><span data-stu-id="2984e-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2984e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2984e-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2984e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2984e-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="2984e-106">[out] Um ponteiro para o comprimento do campo.</span><span class="sxs-lookup"><span data-stu-id="2984e-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2984e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2984e-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2984e-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2984e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2984e-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2984e-109">Requirements</span></span>  
 <span data-ttu-id="2984e-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2984e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2984e-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2984e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2984e-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2984e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2984e-113">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2984e-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2984e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2984e-114">See Also</span></span>  
 [<span data-ttu-id="2984e-115">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="2984e-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="2984e-116">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="2984e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
