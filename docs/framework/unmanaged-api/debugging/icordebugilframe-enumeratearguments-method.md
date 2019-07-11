---
title: Método ICorDebugILFrame::EnumerateArguments
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateArguments
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 499f58cc0a3f2d1b3c159435ed7d9b523f25e29e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757894"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="e3480-102">Método ICorDebugILFrame::EnumerateArguments</span><span class="sxs-lookup"><span data-stu-id="e3480-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="e3480-103">Obtém um enumerador para os argumentos neste quadro.</span><span class="sxs-lookup"><span data-stu-id="e3480-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3480-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3480-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3480-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e3480-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="e3480-106">[out] Um ponteiro para o endereço de um objeto ICorDebugValueEnum que é o enumerador para os argumentos neste quadro.</span><span class="sxs-lookup"><span data-stu-id="e3480-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3480-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3480-107">Remarks</span></span>  
 <span data-ttu-id="e3480-108">`EnumerateArguments` Obtém um enumerador que pode listar os argumentos disponíveis no quadro de chamada que é representado por esse objeto ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="e3480-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="e3480-109">A lista incluirá os argumentos que são [vararg](/cpp/windows/vararg) (ou seja, um número variável de argumentos), bem como os argumentos que não são `vararg`.</span><span class="sxs-lookup"><span data-stu-id="e3480-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3480-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3480-110">Requirements</span></span>  
 <span data-ttu-id="e3480-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3480-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3480-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3480-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3480-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3480-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3480-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3480-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
