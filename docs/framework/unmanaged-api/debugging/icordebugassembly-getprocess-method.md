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
ms.openlocfilehash: c9cb599dd27a809ed5245c9570cddb8110be8172
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894923"
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="88f1c-102">Método ICorDebugAssembly::GetProcess</span><span class="sxs-lookup"><span data-stu-id="88f1c-102">ICorDebugAssembly::GetProcess Method</span></span>
<span data-ttu-id="88f1c-103">Obtém um ponteiro de interface para o processo no qual essa instância de ICorDebugAssembly está em execução.</span><span class="sxs-lookup"><span data-stu-id="88f1c-103">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88f1c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88f1c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88f1c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="88f1c-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="88f1c-106">fora Um ponteiro para uma interface ICorDebugProcess que representa o processo.</span><span class="sxs-lookup"><span data-stu-id="88f1c-106">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88f1c-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88f1c-107">Requirements</span></span>  
 <span data-ttu-id="88f1c-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88f1c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88f1c-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88f1c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88f1c-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88f1c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88f1c-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88f1c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
