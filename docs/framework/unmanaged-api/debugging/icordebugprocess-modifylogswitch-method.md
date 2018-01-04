---
title: "Método ICorDebugProcess::ModifyLogSwitch"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.ModifyLogSwitch
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::ModifyLogSwitch
helpviewer_keywords:
- ICorDebugProcess::ModifyLogSwitch method [.NET Framework debugging]
- ModifyLogSwitch method [.NET Framework debugging]
ms.assetid: 5fd30875-555e-4e96-877b-5dd266cde7c4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e5fb515229c566ee47bf99fe1a5985389e2a425
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="1ded6-102">Método ICorDebugProcess::ModifyLogSwitch</span><span class="sxs-lookup"><span data-stu-id="1ded6-102">ICorDebugProcess::ModifyLogSwitch Method</span></span>
<span data-ttu-id="1ded6-103">Define o nível de severidade da opção de log especificado.</span><span class="sxs-lookup"><span data-stu-id="1ded6-103">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ded6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ded6-104">Syntax</span></span>  
  
```  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ded6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1ded6-105">Parameters</span></span>  
 `pLogSwitchName`  
 <span data-ttu-id="1ded6-106">[in] Um ponteiro para uma cadeia de caracteres que especifica o nome da opção de log.</span><span class="sxs-lookup"><span data-stu-id="1ded6-106">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="1ded6-107">[in] O nível de severidade a ser definido para a opção de log especificado.</span><span class="sxs-lookup"><span data-stu-id="1ded6-107">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ded6-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ded6-108">Remarks</span></span>  
 <span data-ttu-id="1ded6-109">Este método é válido somente após o [Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) ocorreu o retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="1ded6-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ded6-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1ded6-110">Requirements</span></span>  
 <span data-ttu-id="1ded6-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ded6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ded6-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ded6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ded6-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ded6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ded6-114">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ded6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
