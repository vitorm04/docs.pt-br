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
ms.openlocfilehash: 3945b1dea62dc0616d669356faf60f0d09cfb084
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210295"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="eac44-102">Método ICorDebugILFrame::EnumerateArguments</span><span class="sxs-lookup"><span data-stu-id="eac44-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="eac44-103">Obtém um enumerador para os argumentos neste quadro.</span><span class="sxs-lookup"><span data-stu-id="eac44-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eac44-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eac44-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eac44-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eac44-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="eac44-106">fora Um ponteiro para o endereço de um objeto ICorDebugValueEnum que é o enumerador para os argumentos neste quadro.</span><span class="sxs-lookup"><span data-stu-id="eac44-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eac44-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="eac44-107">Remarks</span></span>  
 <span data-ttu-id="eac44-108">`EnumerateArguments`Obtém um enumerador que pode listar os argumentos disponíveis no quadro de chamada que é representado por esse objeto ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="eac44-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="eac44-109">A lista incluirá argumentos que são [vararg](/cpp/windows/vararg) (ou seja, um número variável de argumentos), bem como argumentos que não são `vararg` .</span><span class="sxs-lookup"><span data-stu-id="eac44-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eac44-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eac44-110">Requirements</span></span>  
 <span data-ttu-id="eac44-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eac44-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eac44-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eac44-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eac44-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eac44-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eac44-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eac44-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
