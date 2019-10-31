---
title: 'Método ICorDebugVariableHome:: getlocationtype'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type:
- apiref
ms.openlocfilehash: 1dd4e9510831b4c878e9c1246dabe4add919130c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125106"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="21f61-102">Método ICorDebugVariableHome:: getlocationtype</span><span class="sxs-lookup"><span data-stu-id="21f61-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="21f61-103">Obtém o tipo do local nativo da variável.</span><span class="sxs-lookup"><span data-stu-id="21f61-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21f61-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21f61-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21f61-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="21f61-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="21f61-106">fora Um ponteiro para o tipo do local nativo da variável.</span><span class="sxs-lookup"><span data-stu-id="21f61-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="21f61-107">Consulte a enumeração [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="21f61-107">See the [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21f61-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="21f61-108">Requirements</span></span>  
 <span data-ttu-id="21f61-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21f61-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21f61-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21f61-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21f61-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21f61-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21f61-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21f61-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f61-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21f61-113">See also</span></span>

- [<span data-ttu-id="21f61-114">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="21f61-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="21f61-115">Enumeração VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="21f61-115">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
