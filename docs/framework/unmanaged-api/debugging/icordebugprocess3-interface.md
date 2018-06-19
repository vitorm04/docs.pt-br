---
title: Interface ICorDebugProcess3
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3
helpviewer_keywords:
- ICorDebugProcess3 interface [.NET Framework debugging]
ms.assetid: ced9c82e-d7b0-4806-a151-98b6611d3097
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95c2218aadd62902ff9bc7f2e6a190aa2ce241ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418841"
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="55979-102">Interface ICorDebugProcess3</span><span class="sxs-lookup"><span data-stu-id="55979-102">ICorDebugProcess3 Interface</span></span>
<span data-ttu-id="55979-103">Controla as notificações personalizadas do depurador.</span><span class="sxs-lookup"><span data-stu-id="55979-103">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="55979-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="55979-104">Methods</span></span>  
  
|<span data-ttu-id="55979-105">Método</span><span class="sxs-lookup"><span data-stu-id="55979-105">Method</span></span>|<span data-ttu-id="55979-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="55979-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="55979-107">Método SetEnableCustomNotification</span><span class="sxs-lookup"><span data-stu-id="55979-107">SetEnableCustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="55979-108">Ativa e desativa as notificações do depurador personalizados do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="55979-108">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55979-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="55979-109">Remarks</span></span>  
 <span data-ttu-id="55979-110">Essa interface logicamente estende as interfaces ICorDebugProcess e ICorDebugProcess2.</span><span class="sxs-lookup"><span data-stu-id="55979-110">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55979-111">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="55979-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55979-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="55979-112">Requirements</span></span>  
 <span data-ttu-id="55979-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55979-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55979-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55979-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55979-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55979-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55979-116">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55979-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55979-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55979-117">See Also</span></span>  
 [<span data-ttu-id="55979-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="55979-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="55979-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="55979-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
