---
title: Método ICorDebugAssembly::GetAppDomain
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type:
- apiref
ms.openlocfilehash: 81936052c3fa2ad4fb77b503341b8b4873b80695
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894941"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="ff197-102">Método ICorDebugAssembly::GetAppDomain</span><span class="sxs-lookup"><span data-stu-id="ff197-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="ff197-103">Obtém um ponteiro de interface para o domínio do aplicativo que `ICorDebugAssembly` contém essa instância.</span><span class="sxs-lookup"><span data-stu-id="ff197-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff197-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff197-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff197-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ff197-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="ff197-106">fora Um ponteiro para o endereço de uma interface ICorDebugAppDomain que representa o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff197-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff197-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ff197-107">Remarks</span></span>  
 <span data-ttu-id="ff197-108">Se esse assembly for o assembly do sistema `GetAppDomain` , retornará NULL.</span><span class="sxs-lookup"><span data-stu-id="ff197-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff197-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ff197-109">Requirements</span></span>  
 <span data-ttu-id="ff197-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff197-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff197-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff197-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff197-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff197-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff197-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff197-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
