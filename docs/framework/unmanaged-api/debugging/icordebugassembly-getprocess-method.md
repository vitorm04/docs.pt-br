---
title: Método ICorDebugAssembly::GetProcess
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetProcess
helpviewer_keywords:
- ICorDebugAssembly::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: ea52be06-0a16-4f57-afca-4287d72e76c4
topic_type:
- apiref
ms.openlocfilehash: 49b234b065eb66dc2ec0bc7e991117c5b54a92f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73196342"
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="ac2b2-102">Método ICorDebugAssembly::GetProcess</span><span class="sxs-lookup"><span data-stu-id="ac2b2-102">ICorDebugAssembly::GetProcess Method</span></span>
<span data-ttu-id="ac2b2-103">Obtém um ponteiro de interface para o processo no qual essa instância de ICorDebugAssembly está em execução.</span><span class="sxs-lookup"><span data-stu-id="ac2b2-103">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac2b2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac2b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac2b2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac2b2-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="ac2b2-106">fora Um ponteiro para uma interface ICorDebugProcess que representa o processo.</span><span class="sxs-lookup"><span data-stu-id="ac2b2-106">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac2b2-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac2b2-107">Requirements</span></span>  
 <span data-ttu-id="ac2b2-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac2b2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac2b2-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac2b2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac2b2-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac2b2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac2b2-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac2b2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
