---
title: Método ICorDebugMDA::GetFlags
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetFlags
helpviewer_keywords:
- ICorDebugMDA::GetFlags method [.NET Framework debugging]
- GetFlags method [.NET Framework debugging]
ms.assetid: 87ce7c5b-fd82-453e-bf55-c8a32150b183
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a35e9f7cf43105db05408f285cd89dbd839a4cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969033"
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="78aa5-102">Método ICorDebugMDA::GetFlags</span><span class="sxs-lookup"><span data-stu-id="78aa5-102">ICorDebugMDA::GetFlags Method</span></span>
<span data-ttu-id="78aa5-103">Obtém os sinalizadores associados com o Assistente para depuração gerenciada (MDA) representado por [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="78aa5-103">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78aa5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78aa5-104">Syntax</span></span>  
  
```  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78aa5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="78aa5-105">Parameters</span></span>  
 `pFlags`  
 <span data-ttu-id="78aa5-106">[in] Uma combinação bit a bit do [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) valores de enumeração que especificam as configurações dos sinalizadores para esse MDA.</span><span class="sxs-lookup"><span data-stu-id="78aa5-106">[in] A bitwise combination of the [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78aa5-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="78aa5-107">Requirements</span></span>  
 <span data-ttu-id="78aa5-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78aa5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78aa5-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78aa5-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78aa5-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78aa5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78aa5-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78aa5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78aa5-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78aa5-112">See also</span></span>

- [<span data-ttu-id="78aa5-113">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="78aa5-113">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="78aa5-114">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="78aa5-114">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
