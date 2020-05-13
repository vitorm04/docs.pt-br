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
ms.openlocfilehash: 5e28ccb53771be4a2b6681e2491094d15f01904e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379975"
---
# <a name="icordebugtypegetrank-method"></a><span data-ttu-id="08b29-102">Método ICorDebugType::GetRank</span><span class="sxs-lookup"><span data-stu-id="08b29-102">ICorDebugType::GetRank Method</span></span>
<span data-ttu-id="08b29-103">Obtém o número de dimensões em um tipo de matriz.</span><span class="sxs-lookup"><span data-stu-id="08b29-103">Gets the number of dimensions in an array type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08b29-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08b29-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08b29-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="08b29-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="08b29-106">fora Um ponteiro para o número de dimensões.</span><span class="sxs-lookup"><span data-stu-id="08b29-106">[out] A pointer to the number of dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08b29-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="08b29-107">Requirements</span></span>  
 <span data-ttu-id="08b29-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08b29-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08b29-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="08b29-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08b29-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08b29-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08b29-111">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08b29-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
