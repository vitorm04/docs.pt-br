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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4fced656168952c1064de213405147baf7856b2c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737351"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="34224-102">Método ICorDebugAssembly::GetAppDomain</span><span class="sxs-lookup"><span data-stu-id="34224-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="34224-103">Obtém um ponteiro de interface para o domínio do aplicativo que contém este `ICorDebugAssembly` instância.</span><span class="sxs-lookup"><span data-stu-id="34224-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34224-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34224-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34224-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34224-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="34224-106">[out] Um ponteiro para o endereço de uma interface ICorDebugAppDomain que representa o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="34224-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34224-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="34224-107">Remarks</span></span>  
 <span data-ttu-id="34224-108">Se esse assembly é o assembly do sistema, `GetAppDomain` retorna null.</span><span class="sxs-lookup"><span data-stu-id="34224-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34224-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34224-109">Requirements</span></span>  
 <span data-ttu-id="34224-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34224-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34224-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34224-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34224-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34224-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34224-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34224-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
