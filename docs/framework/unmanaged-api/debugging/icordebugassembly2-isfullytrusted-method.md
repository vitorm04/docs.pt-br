---
title: "Método ICorDebugAssembly2::IsFullyTrusted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAssembly2.IsFullyTrusted
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d155a12a8b281e427f00706cbc6e10a80804c7c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="b37b8-102">Método ICorDebugAssembly2::IsFullyTrusted</span><span class="sxs-lookup"><span data-stu-id="b37b8-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>
<span data-ttu-id="b37b8-103">Obtém um valor que indica se o assembly foi concedido confiança total por sistema de segurança de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b37b8-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b37b8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b37b8-104">Syntax</span></span>  
  
```  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b37b8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b37b8-105">Parameters</span></span>  
 `pbFullyTrusted`  
 <span data-ttu-id="b37b8-106">[out] `true` se o assembly tiver sido concedido confiança total pelo sistema de segurança de tempo de execução; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="b37b8-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b37b8-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b37b8-107">Remarks</span></span>  
 <span data-ttu-id="b37b8-108">Esse método retorna um HRESULT de CORDBG_E_NOTREADY se a política de segurança para o assembly ainda não foi resolvida, ou seja, se nenhum código no assembly tiver sido executado ainda.</span><span class="sxs-lookup"><span data-stu-id="b37b8-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b37b8-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b37b8-109">Requirements</span></span>  
 <span data-ttu-id="b37b8-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b37b8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b37b8-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b37b8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b37b8-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b37b8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b37b8-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b37b8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
