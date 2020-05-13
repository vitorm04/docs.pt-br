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
ms.openlocfilehash: b47580022b98ea02584a94b3f74b3fd1c276f297
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212900"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="11af3-102">Método ICorDebugFunction::GetCurrentVersionNumber</span><span class="sxs-lookup"><span data-stu-id="11af3-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="11af3-103">Obtém o número de versão da edição mais recente feita à função representada por esse objeto ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="11af3-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11af3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11af3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11af3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="11af3-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="11af3-106">fora Um ponteiro para um valor inteiro que é o número de versão da edição mais recente feita nessa função.</span><span class="sxs-lookup"><span data-stu-id="11af3-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11af3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="11af3-107">Remarks</span></span>  
 <span data-ttu-id="11af3-108">O número de versão da edição mais recente feita a essa função pode ser maior que o número de versão da própria função.</span><span class="sxs-lookup"><span data-stu-id="11af3-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="11af3-109">Use o método [ICorDebugFunction2:: GetVersionNumber](icordebugfunction2-getversionnumber-method.md) ou o método [ICorDebugCode:: GetVersionNumber](icordebugcode-getversionnumber-method.md) para recuperar o número de versão da função.</span><span class="sxs-lookup"><span data-stu-id="11af3-109">Use either the [ICorDebugFunction2::GetVersionNumber](icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11af3-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11af3-110">Requirements</span></span>  
 <span data-ttu-id="11af3-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11af3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11af3-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11af3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11af3-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11af3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11af3-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11af3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
