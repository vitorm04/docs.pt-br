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
ms.openlocfilehash: a5cda98cac0bc3fc6fb101fd0404b062224cb578
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134089"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="ad869-102">Método ICorDebug::Initialize</span><span class="sxs-lookup"><span data-stu-id="ad869-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="ad869-103">Inicializa o objeto `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="ad869-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad869-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad869-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ad869-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="ad869-105">Remarks</span></span>  
 <span data-ttu-id="ad869-106">O depurador deve chamar `Initialize` no momento da criação para inicializar os serviços de depuração.</span><span class="sxs-lookup"><span data-stu-id="ad869-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="ad869-107">Esse método deve ser chamado antes que qualquer outro método em `ICorDebug` seja chamado.</span><span class="sxs-lookup"><span data-stu-id="ad869-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad869-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad869-108">Requirements</span></span>  
 <span data-ttu-id="ad869-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad869-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad869-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad869-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad869-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad869-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad869-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad869-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad869-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad869-113">See also</span></span>

- [<span data-ttu-id="ad869-114">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="ad869-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
