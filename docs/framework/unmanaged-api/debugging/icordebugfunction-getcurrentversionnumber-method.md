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
ms.openlocfilehash: 0530ba742a739003bfa33079ad75cb1e6f5f5e59
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124012"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="a834f-102">Método ICorDebugFunction::GetCurrentVersionNumber</span><span class="sxs-lookup"><span data-stu-id="a834f-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="a834f-103">Obtém o número de versão da edição mais recente feita à função representada por esse objeto ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="a834f-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a834f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a834f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a834f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a834f-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="a834f-106">fora Um ponteiro para um valor inteiro que é o número de versão da edição mais recente feita nessa função.</span><span class="sxs-lookup"><span data-stu-id="a834f-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a834f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a834f-107">Remarks</span></span>  
 <span data-ttu-id="a834f-108">O número de versão da edição mais recente feita a essa função pode ser maior que o número de versão da própria função.</span><span class="sxs-lookup"><span data-stu-id="a834f-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="a834f-109">Use o método [ICorDebugFunction2:: GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) ou o método [ICorDebugCode:: GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) para recuperar o número de versão da função.</span><span class="sxs-lookup"><span data-stu-id="a834f-109">Use either the [ICorDebugFunction2::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a834f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a834f-110">Requirements</span></span>  
 <span data-ttu-id="a834f-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a834f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a834f-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a834f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a834f-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a834f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a834f-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a834f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
