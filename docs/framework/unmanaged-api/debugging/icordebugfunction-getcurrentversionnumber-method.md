---
title: Método ICorDebugFunction::GetCurrentVersionNumber
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
ms.openlocfilehash: 5e080e9aa89816b24aa2eb1b6b1be823922e86fb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794516"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="e4bd2-102">Método ICorDebugFunction::GetCurrentVersionNumber</span><span class="sxs-lookup"><span data-stu-id="e4bd2-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="e4bd2-103">Obtém o número de versão da edição mais recente feita à função representada por esse objeto ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="e4bd2-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4bd2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4bd2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4bd2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e4bd2-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="e4bd2-106">fora Um ponteiro para um valor inteiro que é o número de versão da edição mais recente feita nessa função.</span><span class="sxs-lookup"><span data-stu-id="e4bd2-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4bd2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4bd2-107">Remarks</span></span>  
 <span data-ttu-id="e4bd2-108">O número de versão da edição mais recente feita a essa função pode ser maior que o número de versão da própria função.</span><span class="sxs-lookup"><span data-stu-id="e4bd2-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="e4bd2-109">Use o método [ICorDebugFunction2:: GetVersionNumber](icordebugfunction2-getversionnumber-method.md) ou o método [ICorDebugCode:: GetVersionNumber](icordebugcode-getversionnumber-method.md) para recuperar o número de versão da função.</span><span class="sxs-lookup"><span data-stu-id="e4bd2-109">Use either the [ICorDebugFunction2::GetVersionNumber](icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4bd2-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="e4bd2-110">Requirements</span></span>  
 <span data-ttu-id="e4bd2-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4bd2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4bd2-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4bd2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4bd2-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4bd2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4bd2-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4bd2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
