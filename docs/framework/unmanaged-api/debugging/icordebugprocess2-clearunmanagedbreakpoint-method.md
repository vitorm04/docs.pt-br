---
title: Método ICorDebugProcess2::ClearUnmanagedBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc34ab9c8dbfe10282f36a241a4e433debef7dd0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420489"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="0e83a-102">Método ICorDebugProcess2::ClearUnmanagedBreakpoint</span><span class="sxs-lookup"><span data-stu-id="0e83a-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="0e83a-103">Remove um definido anteriormente ponto de interrupção no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="0e83a-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e83a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e83a-104">Syntax</span></span>  
  
```  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e83a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0e83a-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="0e83a-106">[in] Um `CORDB_ADDRESS` valor que especifica o endereço no qual o ponto de interrupção foi definido.</span><span class="sxs-lookup"><span data-stu-id="0e83a-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e83a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="0e83a-107">Remarks</span></span>  
 <span data-ttu-id="0e83a-108">O ponto de interrupção especificado tenha sido previamente definido por uma chamada anterior para [Icordebugprocess2](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="0e83a-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="0e83a-109">O `ClearUnmanagedBreakpoint` método pode ser chamado enquanto o processo está sendo depurado está em execução.</span><span class="sxs-lookup"><span data-stu-id="0e83a-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="0e83a-110">O `ClearUnmanagedBreakpoint` método retorna um código de falha se o depurador está anexado no modo somente gerenciados ou se nenhum ponto de interrupção existe no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="0e83a-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e83a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0e83a-111">Requirements</span></span>  
 <span data-ttu-id="0e83a-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e83a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e83a-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e83a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e83a-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e83a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e83a-115">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e83a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
