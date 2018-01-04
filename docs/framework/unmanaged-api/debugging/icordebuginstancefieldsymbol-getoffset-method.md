---
title: "Método ICorDebugInstanceFieldSymbol::GetOffset"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ab38a19d2bd2d06f2a04d7efafcdad6956ad7c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="7745e-102">Método ICorDebugInstanceFieldSymbol::GetOffset</span><span class="sxs-lookup"><span data-stu-id="7745e-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="7745e-103">Obtém o deslocamento de bytes deste campo de instância em sua classe pai.</span><span class="sxs-lookup"><span data-stu-id="7745e-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7745e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7745e-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7745e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7745e-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="7745e-106">Um ponteiro para o número de bytes que este campo de instância é deslocado em sua classe pai.</span><span class="sxs-lookup"><span data-stu-id="7745e-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7745e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="7745e-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7745e-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7745e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7745e-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7745e-109">Requirements</span></span>  
 <span data-ttu-id="7745e-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7745e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7745e-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7745e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7745e-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7745e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7745e-113">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7745e-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7745e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7745e-114">See Also</span></span>  
 [<span data-ttu-id="7745e-115">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="7745e-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="7745e-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="7745e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
