---
title: Método ICorDebug::Initialize
ms.date: 03/30/2017
api_name:
- ICorDebug.Initialize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Initialize
helpviewer_keywords:
- Initialize method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Initialize method [.NET Framework debugging]
ms.assetid: 6fae3b23-5c9f-47c0-85d8-6bb75e050786
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd09ce27c0fea9dca8fd86afc563651d68542e13
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173141"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="5e635-102">Método ICorDebug::Initialize</span><span class="sxs-lookup"><span data-stu-id="5e635-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="5e635-103">Inicializa o objeto `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="5e635-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e635-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e635-104">Syntax</span></span>  
  
```  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5e635-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="5e635-105">Remarks</span></span>  
 <span data-ttu-id="5e635-106">O depurador deve chamar `Initialize` na criação do tempo para inicializar a depuração de serviços.</span><span class="sxs-lookup"><span data-stu-id="5e635-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="5e635-107">Esse método deve ser chamado antes de qualquer outro método em `ICorDebug` é chamado.</span><span class="sxs-lookup"><span data-stu-id="5e635-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e635-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5e635-108">Requirements</span></span>  
 <span data-ttu-id="5e635-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e635-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e635-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e635-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e635-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e635-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5e635-112">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="5e635-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5e635-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e635-113">See also</span></span>

- [<span data-ttu-id="5e635-114">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="5e635-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
