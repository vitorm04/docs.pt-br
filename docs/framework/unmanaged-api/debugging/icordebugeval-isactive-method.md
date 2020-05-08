---
title: Método ICorDebugEval::IsActive
ms.date: 03/30/2017
api_name:
- ICorDebugEval.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::IsActive method [.NET Framework debugging]
ms.assetid: bf2bba24-d278-43bd-b1c5-35680e748d3e
topic_type:
- apiref
ms.openlocfilehash: 4ee055812eb8dce2dc86f834dde92d7de5e1fdf9
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976207"
---
# <a name="icordebugevalisactive-method"></a><span data-ttu-id="8975b-102">Método ICorDebugEval::IsActive</span><span class="sxs-lookup"><span data-stu-id="8975b-102">ICorDebugEval::IsActive Method</span></span>
<span data-ttu-id="8975b-103">Obtém um valor que indica se este objeto ICorDebugEval está em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="8975b-103">Gets a value that indicates whether this ICorDebugEval object is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8975b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8975b-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL              *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8975b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8975b-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="8975b-106">fora Ponteiro para um valor que indica se essa avaliação está ativa.</span><span class="sxs-lookup"><span data-stu-id="8975b-106">[out] Pointer to a value that indicates whether this evaluation is active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8975b-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8975b-107">Requirements</span></span>  
 <span data-ttu-id="8975b-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8975b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8975b-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8975b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8975b-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8975b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8975b-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8975b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
