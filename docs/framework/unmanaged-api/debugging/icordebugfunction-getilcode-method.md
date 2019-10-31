---
title: Método ICorDebugFunction::GetILCode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
ms.openlocfilehash: c2ce4b95de75bef3928e144656b565676568caa0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137908"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="eb830-102">Método ICorDebugFunction::GetILCode</span><span class="sxs-lookup"><span data-stu-id="eb830-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="eb830-103">Obtém a instância ICorDebugCode que representa o código MSIL (Microsoft Intermediate Language) associado a este objeto ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="eb830-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb830-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb830-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb830-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eb830-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="eb830-106">fora Um ponteiro para a instância de `ICorDebugCode`, ou NULL, se a função não foi compilada em MSIL.</span><span class="sxs-lookup"><span data-stu-id="eb830-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb830-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb830-107">Remarks</span></span>  
 <span data-ttu-id="eb830-108">Se editar e continuar tiver sido permitido nessa função, o método `GetILCode` obterá o código MSIL correspondente à versão editada da função do código no Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="eb830-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb830-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eb830-109">Requirements</span></span>  
 <span data-ttu-id="eb830-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb830-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb830-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb830-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb830-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb830-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb830-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb830-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
