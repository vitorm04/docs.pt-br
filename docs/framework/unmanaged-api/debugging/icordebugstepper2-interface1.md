---
title: Interface ICorDebugStepper2
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2
helpviewer_keywords:
- ICorDebugStepper2 interface [.NET Framework debugging]
ms.assetid: 7a191c2a-95ea-4d47-83b0-44de2b632d63
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 256f67d21a22ee4692d88311cc150736e61563a0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073040"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="51ece-102">Interface ICorDebugStepper2</span><span class="sxs-lookup"><span data-stu-id="51ece-102">ICorDebugStepper2 Interface</span></span>
<span data-ttu-id="51ece-103">Fornece suporte para apenas meu código (JMC) de depuração.</span><span class="sxs-lookup"><span data-stu-id="51ece-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="51ece-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="51ece-104">Methods</span></span>  
  
|<span data-ttu-id="51ece-105">Método</span><span class="sxs-lookup"><span data-stu-id="51ece-105">Method</span></span>|<span data-ttu-id="51ece-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="51ece-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51ece-107">Método SetJMC</span><span class="sxs-lookup"><span data-stu-id="51ece-107">SetJMC Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-setjmc-method.md)|<span data-ttu-id="51ece-108">Define um valor que especifica se este ICorDebugStepper etapas somente por meio de código que é criado pelo desenvolvedor do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="51ece-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51ece-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="51ece-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51ece-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="51ece-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51ece-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="51ece-111">Requirements</span></span>  
 <span data-ttu-id="51ece-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51ece-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51ece-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51ece-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51ece-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51ece-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="51ece-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="51ece-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="51ece-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51ece-116">See also</span></span>

- [<span data-ttu-id="51ece-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="51ece-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
