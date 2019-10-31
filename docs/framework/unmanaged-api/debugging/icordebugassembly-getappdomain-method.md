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
ms.openlocfilehash: 53042e722809a6574396648529c677d749154716
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132739"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="bd01a-102">Método ICorDebugAssembly::GetAppDomain</span><span class="sxs-lookup"><span data-stu-id="bd01a-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="bd01a-103">Obtém um ponteiro de interface para o domínio do aplicativo que contém esta instância de `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="bd01a-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd01a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd01a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd01a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bd01a-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="bd01a-106">fora Um ponteiro para o endereço de uma interface ICorDebugAppDomain que representa o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bd01a-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd01a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="bd01a-107">Remarks</span></span>  
 <span data-ttu-id="bd01a-108">Se esse assembly for o assembly do sistema, `GetAppDomain` retornará NULL.</span><span class="sxs-lookup"><span data-stu-id="bd01a-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd01a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bd01a-109">Requirements</span></span>  
 <span data-ttu-id="bd01a-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd01a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd01a-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd01a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd01a-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd01a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd01a-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd01a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
