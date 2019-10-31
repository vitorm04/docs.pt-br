---
title: Método ICorDebugType::GetRank
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetRank
helpviewer_keywords:
- GetRank method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetRank method [.NET Framework debugging]
ms.assetid: 72d3d927-f590-4f2d-8f60-448f3dfb96af
topic_type:
- apiref
ms.openlocfilehash: 9a00177faabfcad56d70ec5c64328c90675c1532
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138769"
---
# <a name="icordebugtypegetrank-method"></a><span data-ttu-id="d7452-102">Método ICorDebugType::GetRank</span><span class="sxs-lookup"><span data-stu-id="d7452-102">ICorDebugType::GetRank Method</span></span>
<span data-ttu-id="d7452-103">Obtém o número de dimensões em um tipo de matriz.</span><span class="sxs-lookup"><span data-stu-id="d7452-103">Gets the number of dimensions in an array type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7452-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7452-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7452-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d7452-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="d7452-106">fora Um ponteiro para o número de dimensões.</span><span class="sxs-lookup"><span data-stu-id="d7452-106">[out] A pointer to the number of dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7452-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d7452-107">Requirements</span></span>  
 <span data-ttu-id="d7452-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7452-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7452-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7452-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7452-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7452-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7452-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7452-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
