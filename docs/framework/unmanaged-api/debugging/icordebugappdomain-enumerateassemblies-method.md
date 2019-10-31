---
title: Método ICorDebugAppDomain::EnumerateAssemblies
ms.date: 03/30/2017
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
ms.openlocfilehash: 573b08fcf2ce0fa5ce3187df6ae6a1c2cc385f52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134002"
---
# <a name="icordebugappdomainenumerateassemblies-method"></a><span data-ttu-id="85146-102">Método ICorDebugAppDomain::EnumerateAssemblies</span><span class="sxs-lookup"><span data-stu-id="85146-102">ICorDebugAppDomain::EnumerateAssemblies Method</span></span>
<span data-ttu-id="85146-103">Obtém um enumerador para os assemblies no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="85146-103">Gets an enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85146-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="85146-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateAssemblies (  
    [out] ICorDebugAssemblyEnum  **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85146-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="85146-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="85146-106">fora Um ponteiro para o endereço de um objeto ICorDebugAssemblyEnum que é o enumerador para os assemblies no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="85146-106">[out] A pointer to the address of an ICorDebugAssemblyEnum object that is the enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85146-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="85146-107">Requirements</span></span>  
 <span data-ttu-id="85146-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85146-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85146-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85146-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85146-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85146-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85146-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85146-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
