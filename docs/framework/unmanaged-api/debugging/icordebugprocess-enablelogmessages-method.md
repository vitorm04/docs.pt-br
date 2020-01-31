---
title: Método ICorDebugProcess::EnableLogMessages
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnableLogMessages
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnableLogMessages
helpviewer_keywords:
- ICorDebugProcess::EnableLogMessages method [.NET Framework debugging]
- EnableLogMessages method [.NET Framework debugging]
ms.assetid: 14a4e5a3-3eaf-4f53-9dd1-762726963a23
topic_type:
- apiref
ms.openlocfilehash: 6b1ccffa4f24122e643a64270f44945afdbc8fff
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792646"
---
# <a name="icordebugprocessenablelogmessages-method"></a><span data-ttu-id="fbd85-102">Método ICorDebugProcess::EnableLogMessages</span><span class="sxs-lookup"><span data-stu-id="fbd85-102">ICorDebugProcess::EnableLogMessages Method</span></span>
<span data-ttu-id="fbd85-103">Habilita e desabilita a transmissão de mensagens de log para o depurador.</span><span class="sxs-lookup"><span data-stu-id="fbd85-103">Enables and disables the transmission of log messages to the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbd85-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbd85-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbd85-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fbd85-105">Parameters</span></span>  
 `fOnOff`  
 <span data-ttu-id="fbd85-106">[in] `true` habilita a transmissão de mensagens de log; `false` desabilita a transmissão.</span><span class="sxs-lookup"><span data-stu-id="fbd85-106">[in] `true` enables the transmission of log messages; `false` disables the transmission.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbd85-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="fbd85-107">Remarks</span></span>  
 <span data-ttu-id="fbd85-108">Esse método é válido somente depois que o retorno de chamada [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) ocorre.</span><span class="sxs-lookup"><span data-stu-id="fbd85-108">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback occurs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbd85-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="fbd85-109">Requirements</span></span>  
 <span data-ttu-id="fbd85-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbd85-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbd85-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fbd85-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fbd85-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbd85-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbd85-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbd85-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
