---
title: "Método ICorDebugFunction2::SetJMCStatus"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ecbcd5b8171a169fbfdd7175d3d9dfbbcb3855f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="49688-102">Método ICorDebugFunction2::SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="49688-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="49688-103">Marca a função representada por esse ICorDebugFunction2 para apenas meu código passo a passo.</span><span class="sxs-lookup"><span data-stu-id="49688-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49688-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49688-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49688-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="49688-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="49688-106">[in] Definido como `true` para marcar a função como código de usuário; caso contrário, é definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="49688-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="49688-107">Valores de Retorno</span><span class="sxs-lookup"><span data-stu-id="49688-107">Return Values</span></span>  
  
|<span data-ttu-id="49688-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="49688-108">HRESULT</span></span>|<span data-ttu-id="49688-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="49688-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="49688-110">A função foi marcada com êxito.</span><span class="sxs-lookup"><span data-stu-id="49688-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="49688-111">A função não pode ser marcada como código de usuário porque ele não pode ser depurado.</span><span class="sxs-lookup"><span data-stu-id="49688-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49688-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="49688-112">Remarks</span></span>  
 <span data-ttu-id="49688-113">Um seletor de apenas meu código vai ignorar o código de não usuário.</span><span class="sxs-lookup"><span data-stu-id="49688-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="49688-114">Código do usuário deve ser um subconjunto de código depurável.</span><span class="sxs-lookup"><span data-stu-id="49688-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49688-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="49688-115">Requirements</span></span>  
 <span data-ttu-id="49688-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49688-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49688-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49688-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49688-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49688-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49688-119">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49688-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
