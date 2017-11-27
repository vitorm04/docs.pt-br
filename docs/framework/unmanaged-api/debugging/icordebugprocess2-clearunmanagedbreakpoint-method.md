---
title: "Método ICorDebugProcess2::ClearUnmanagedBreakpoint"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ca1514eaa916f5e607e49b5a5713763f855d937
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="abcd4-102">Método ICorDebugProcess2::ClearUnmanagedBreakpoint</span><span class="sxs-lookup"><span data-stu-id="abcd4-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="abcd4-103">Remove um definido anteriormente ponto de interrupção no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="abcd4-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abcd4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="abcd4-104">Syntax</span></span>  
  
```  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="abcd4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="abcd4-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="abcd4-106">[in] Um `CORDB_ADDRESS` valor que especifica o endereço no qual o ponto de interrupção foi definido.</span><span class="sxs-lookup"><span data-stu-id="abcd4-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abcd4-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="abcd4-107">Remarks</span></span>  
 <span data-ttu-id="abcd4-108">O ponto de interrupção especificado tenha sido previamente definido por uma chamada anterior para [Icordebugprocess2](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="abcd4-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="abcd4-109">O `ClearUnmanagedBreakpoint` método pode ser chamado enquanto o processo está sendo depurado está em execução.</span><span class="sxs-lookup"><span data-stu-id="abcd4-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="abcd4-110">O `ClearUnmanagedBreakpoint` método retorna um código de falha se o depurador está anexado no modo somente gerenciados ou se nenhum ponto de interrupção existe no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="abcd4-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abcd4-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="abcd4-111">Requirements</span></span>  
 <span data-ttu-id="abcd4-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abcd4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abcd4-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abcd4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abcd4-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abcd4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abcd4-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abcd4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
