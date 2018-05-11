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
ms.openlocfilehash: fa79382d597d303d492e3a441c15a422697be279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="82d23-102">Método ICorDebug::Initialize</span><span class="sxs-lookup"><span data-stu-id="82d23-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="82d23-103">Inicializa o objeto `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="82d23-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82d23-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82d23-104">Syntax</span></span>  
  
```  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="82d23-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="82d23-105">Remarks</span></span>  
 <span data-ttu-id="82d23-106">O depurador deve chamar `Initialize` na criação de serviços de tempo para inicializar a depuração.</span><span class="sxs-lookup"><span data-stu-id="82d23-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="82d23-107">Esse método deve ser chamado antes de qualquer outro método em `ICorDebug` é chamado.</span><span class="sxs-lookup"><span data-stu-id="82d23-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82d23-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82d23-108">Requirements</span></span>  
 <span data-ttu-id="82d23-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82d23-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82d23-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82d23-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82d23-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82d23-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82d23-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82d23-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82d23-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82d23-113">See Also</span></span>  
 [<span data-ttu-id="82d23-114">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="82d23-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
