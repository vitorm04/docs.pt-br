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
ms.openlocfilehash: 0ccc45482f691d9950c641ef126a657052a280e8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213617"
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="aa293-102">Interface ICorDebugProcess3</span><span class="sxs-lookup"><span data-stu-id="aa293-102">ICorDebugProcess3 Interface</span></span>
<span data-ttu-id="aa293-103">Controla as notificações personalizadas do depurador.</span><span class="sxs-lookup"><span data-stu-id="aa293-103">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aa293-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="aa293-104">Methods</span></span>  
  
|<span data-ttu-id="aa293-105">Método</span><span class="sxs-lookup"><span data-stu-id="aa293-105">Method</span></span>|<span data-ttu-id="aa293-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa293-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aa293-107">Método SetEnableCustomNotification</span><span class="sxs-lookup"><span data-stu-id="aa293-107">SetEnableCustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="aa293-108">Habilita e desabilita as notificações do depurador personalizados do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="aa293-108">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa293-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa293-109">Remarks</span></span>  
 <span data-ttu-id="aa293-110">Essa interface estende logicamente as interfaces ICorDebugProcess e ICorDebugProcess2.</span><span class="sxs-lookup"><span data-stu-id="aa293-110">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa293-111">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="aa293-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa293-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa293-112">Requirements</span></span>  
 <span data-ttu-id="aa293-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa293-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa293-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa293-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa293-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa293-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="aa293-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="aa293-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="aa293-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa293-117">See also</span></span>

- [<span data-ttu-id="aa293-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="aa293-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="aa293-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="aa293-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
