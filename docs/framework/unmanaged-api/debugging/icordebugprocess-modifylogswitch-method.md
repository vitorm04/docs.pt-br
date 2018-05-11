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
ms.openlocfilehash: 20ceed164631169b3a47809381b2cc4e630ae718
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="231cb-102">Método ICorDebugProcess::ModifyLogSwitch</span><span class="sxs-lookup"><span data-stu-id="231cb-102">ICorDebugProcess::ModifyLogSwitch Method</span></span>
<span data-ttu-id="231cb-103">Define o nível de severidade da opção de log especificado.</span><span class="sxs-lookup"><span data-stu-id="231cb-103">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="231cb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="231cb-104">Syntax</span></span>  
  
```  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="231cb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="231cb-105">Parameters</span></span>  
 `pLogSwitchName`  
 <span data-ttu-id="231cb-106">[in] Um ponteiro para uma cadeia de caracteres que especifica o nome da opção de log.</span><span class="sxs-lookup"><span data-stu-id="231cb-106">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="231cb-107">[in] O nível de severidade a ser definido para a opção de log especificado.</span><span class="sxs-lookup"><span data-stu-id="231cb-107">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="231cb-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="231cb-108">Remarks</span></span>  
 <span data-ttu-id="231cb-109">Este método é válido somente após o [Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) ocorreu o retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="231cb-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="231cb-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="231cb-110">Requirements</span></span>  
 <span data-ttu-id="231cb-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="231cb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="231cb-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="231cb-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="231cb-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="231cb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="231cb-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="231cb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
