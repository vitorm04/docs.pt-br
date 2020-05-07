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
ms.openlocfilehash: dd82709064fe7f7d912d93f4b3f0248769f02b9e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894881"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="4e2c3-102">Método ICorDebugAssembly2::IsFullyTrusted</span><span class="sxs-lookup"><span data-stu-id="4e2c3-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>
<span data-ttu-id="4e2c3-103">Obtém um valor que indica se o assembly recebeu confiança total pelo sistema de segurança de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4e2c3-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e2c3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4e2c3-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e2c3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4e2c3-105">Parameters</span></span>  
 `pbFullyTrusted`  
 <span data-ttu-id="4e2c3-106">fora `true` se o assembly tiver recebido confiança total pelo sistema de segurança de tempo de execução; caso contrário `false`,.</span><span class="sxs-lookup"><span data-stu-id="4e2c3-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e2c3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4e2c3-107">Remarks</span></span>  
 <span data-ttu-id="4e2c3-108">Esse método retornará um HRESULT de CORDBG_E_NOTREADY se a política de segurança para o assembly ainda não tiver sido resolvida, ou seja, se nenhum código no assembly tiver sido executado ainda.</span><span class="sxs-lookup"><span data-stu-id="4e2c3-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e2c3-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4e2c3-109">Requirements</span></span>  
 <span data-ttu-id="4e2c3-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e2c3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e2c3-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e2c3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e2c3-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e2c3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e2c3-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e2c3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
