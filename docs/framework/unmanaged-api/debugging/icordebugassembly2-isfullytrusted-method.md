---
title: "Método ICorDebugAssembly2::IsFullyTrusted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly2.IsFullyTrusted
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 19058308876f80afdbaec73583242aa8ad3c33cb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="88638-102">Método ICorDebugAssembly2::IsFullyTrusted</span><span class="sxs-lookup"><span data-stu-id="88638-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>
<span data-ttu-id="88638-103">Obtém um valor que indica se o assembly foi concedido confiança total por sistema de segurança de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="88638-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88638-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88638-104">Syntax</span></span>  
  
```  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88638-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="88638-105">Parameters</span></span>  
 `pbFullyTrusted`  
 <span data-ttu-id="88638-106">[out] `true` se o assembly tiver sido concedido confiança total pelo sistema de segurança de tempo de execução; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="88638-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88638-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="88638-107">Remarks</span></span>  
 <span data-ttu-id="88638-108">Esse método retorna um HRESULT de CORDBG_E_NOTREADY se a política de segurança para o assembly ainda não foi resolvida, ou seja, se nenhum código no assembly tiver sido executado ainda.</span><span class="sxs-lookup"><span data-stu-id="88638-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88638-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88638-109">Requirements</span></span>  
 <span data-ttu-id="88638-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88638-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88638-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88638-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88638-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88638-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88638-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88638-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
