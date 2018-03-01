---
title: "Método ICorDebugAppDomain::EnumerateAssemblies"
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
- ICorDebugAppDomain.EnumerateAssemblies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateAssemblies
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateAssemblies method [.NET Framework debugging]
- EnumerateAssemblies method [.NET Framework debugging]
ms.assetid: 7add64f9-19a8-46a9-be62-905d5e7d1bd8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 243cdd1cabe7813d4e92a9d1868a9f0b105e1da8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainenumerateassemblies-method"></a><span data-ttu-id="03e41-102">Método ICorDebugAppDomain::EnumerateAssemblies</span><span class="sxs-lookup"><span data-stu-id="03e41-102">ICorDebugAppDomain::EnumerateAssemblies Method</span></span>
<span data-ttu-id="03e41-103">Obtém um enumerador para os assemblies no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="03e41-103">Gets an enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03e41-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03e41-104">Syntax</span></span>  
  
```  
HRESULT EnumerateAssemblies (  
    [out] ICorDebugAssemblyEnum  **ppAssemblies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03e41-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="03e41-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="03e41-106">[out] Um ponteiro para o endereço de um objeto de ICorDebugAssemblyEnum que é o enumerador para os assemblies no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="03e41-106">[out] A pointer to the address of an ICorDebugAssemblyEnum object that is the enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03e41-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03e41-107">Requirements</span></span>  
 <span data-ttu-id="03e41-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03e41-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03e41-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03e41-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03e41-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03e41-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03e41-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03e41-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
