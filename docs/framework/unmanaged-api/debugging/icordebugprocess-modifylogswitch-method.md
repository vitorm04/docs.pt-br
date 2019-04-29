---
title: Método ICorDebugProcess::ModifyLogSwitch
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ModifyLogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ModifyLogSwitch
helpviewer_keywords:
- ICorDebugProcess::ModifyLogSwitch method [.NET Framework debugging]
- ModifyLogSwitch method [.NET Framework debugging]
ms.assetid: 5fd30875-555e-4e96-877b-5dd266cde7c4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b1c85499e5269027da2c2a01ab67aab2c5da626
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775532"
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="3192a-102">Método ICorDebugProcess::ModifyLogSwitch</span><span class="sxs-lookup"><span data-stu-id="3192a-102">ICorDebugProcess::ModifyLogSwitch Method</span></span>
<span data-ttu-id="3192a-103">Define o nível de severidade da opção de log especificado.</span><span class="sxs-lookup"><span data-stu-id="3192a-103">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3192a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3192a-104">Syntax</span></span>  
  
```  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3192a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3192a-105">Parameters</span></span>  
 `pLogSwitchName`  
 <span data-ttu-id="3192a-106">[in] Um ponteiro para uma cadeia de caracteres que especifica o nome do comutador de log.</span><span class="sxs-lookup"><span data-stu-id="3192a-106">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="3192a-107">[in] O nível de severidade a ser definido para a opção de log especificado.</span><span class="sxs-lookup"><span data-stu-id="3192a-107">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3192a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="3192a-108">Remarks</span></span>  
 <span data-ttu-id="3192a-109">Este método é válido somente após o [icordebugmanagedcallback:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) retorno de chamada tenha ocorrido.</span><span class="sxs-lookup"><span data-stu-id="3192a-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3192a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3192a-110">Requirements</span></span>  
 <span data-ttu-id="3192a-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3192a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3192a-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3192a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3192a-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3192a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3192a-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3192a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
