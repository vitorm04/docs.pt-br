---
title: Método ICorDebugAssembly2::IsFullyTrusted
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd3b977a894f8cb1fc9a866f5a43265d917db513
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645559"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="f8c73-102">Método ICorDebugAssembly2::IsFullyTrusted</span><span class="sxs-lookup"><span data-stu-id="f8c73-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>
<span data-ttu-id="f8c73-103">Obtém um valor que indica se o assembly foi concedido confiança total pelo sistema de segurança de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f8c73-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8c73-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f8c73-104">Syntax</span></span>  
  
```  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8c73-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8c73-105">Parameters</span></span>  
 `pbFullyTrusted`  
 <span data-ttu-id="f8c73-106">[out] `true` se o assembly tiver sido concedido confiança total pelo sistema de segurança de tempo de execução; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="f8c73-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8c73-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f8c73-107">Remarks</span></span>  
 <span data-ttu-id="f8c73-108">Esse método retorna um HRESULT de CORDBG_E_NOTREADY se a política de segurança para o assembly ainda não foi resolvida, ou seja, se não houver código no assembly foi executada ainda.</span><span class="sxs-lookup"><span data-stu-id="f8c73-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8c73-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f8c73-109">Requirements</span></span>  
 <span data-ttu-id="f8c73-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8c73-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8c73-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8c73-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8c73-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8c73-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8c73-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8c73-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
