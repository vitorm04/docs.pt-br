---
title: Método ICorDebugFunction2::GetVersionNumber
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cc9c2af62184c83857b82445941f6087a05c2c3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497165"
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="c833f-102">Método ICorDebugFunction2::GetVersionNumber</span><span class="sxs-lookup"><span data-stu-id="c833f-102">ICorDebugFunction2::GetVersionNumber Method</span></span>
<span data-ttu-id="c833f-103">Obtém a versão de editar e continuar dessa função.</span><span class="sxs-lookup"><span data-stu-id="c833f-103">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c833f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c833f-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c833f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c833f-105">Parameters</span></span>  
 `pnVersion`  
 <span data-ttu-id="c833f-106">[out] Um ponteiro para um inteiro que é o número de versão da função que é representado por esse objeto ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="c833f-106">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c833f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c833f-107">Remarks</span></span>  
 <span data-ttu-id="c833f-108">O tempo de execução mantém controle sobre o número de edições que foram executadas para cada módulo durante uma sessão de depuração.</span><span class="sxs-lookup"><span data-stu-id="c833f-108">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="c833f-109">O número de versão de uma função é um mais do que o número da edição que introduziu a função.</span><span class="sxs-lookup"><span data-stu-id="c833f-109">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="c833f-110">Versão original da função é 1.</span><span class="sxs-lookup"><span data-stu-id="c833f-110">The function's original version is version 1.</span></span> <span data-ttu-id="c833f-111">O número é incrementado para um módulo sempre [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) é chamado no módulo.</span><span class="sxs-lookup"><span data-stu-id="c833f-111">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="c833f-112">Portanto, se o corpo da função foi substituído na primeira e a terceira chamada para `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` pode retornar a versão 1, 2 ou 4 para essa função, mas não a versão 3.</span><span class="sxs-lookup"><span data-stu-id="c833f-112">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="c833f-113">(Essa função não teria nenhuma versão 3).</span><span class="sxs-lookup"><span data-stu-id="c833f-113">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="c833f-114">O número de versão é controlado separadamente para cada módulo.</span><span class="sxs-lookup"><span data-stu-id="c833f-114">The version number is tracked separately for each module.</span></span> <span data-ttu-id="c833f-115">Portanto, se você executar quatro edições no módulo 1 e nenhuma no módulo 2, sua próxima edição no módulo 1 atribuirá um número de versão de 6 para todas as funções editadas no módulo 1.</span><span class="sxs-lookup"><span data-stu-id="c833f-115">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="c833f-116">Se o mesmo Editar toques módulo 2, as funções no módulo 2 obterá um número de versão 2.</span><span class="sxs-lookup"><span data-stu-id="c833f-116">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="c833f-117">O número de versão são obtidos com o `GetVersionNumber` método pode ser menor do que o obtido pela [ICorDebugFunction:: Getcurrentversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span><span class="sxs-lookup"><span data-stu-id="c833f-117">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="c833f-118">O [icordebugcode:: Getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) método executa a mesma operação que `ICorDebugFunction2::GetVersionNumber`.</span><span class="sxs-lookup"><span data-stu-id="c833f-118">The [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c833f-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c833f-119">Requirements</span></span>  
 <span data-ttu-id="c833f-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c833f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c833f-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c833f-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c833f-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c833f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c833f-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c833f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
