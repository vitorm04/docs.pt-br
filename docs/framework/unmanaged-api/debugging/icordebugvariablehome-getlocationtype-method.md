---
title: Método ICorDebugVariableHome::GetLocationType
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af879cbbf8edfd05e79d9b77b0c1fb71b2c835c3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224293"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="1839e-102">Método ICorDebugVariableHome::GetLocationType</span><span class="sxs-lookup"><span data-stu-id="1839e-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="1839e-103">Obtém o tipo de local nativo da variável.</span><span class="sxs-lookup"><span data-stu-id="1839e-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1839e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1839e-104">Syntax</span></span>  
  
```  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1839e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1839e-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="1839e-106">[out] Um ponteiro para o tipo de local de nativo da variável.</span><span class="sxs-lookup"><span data-stu-id="1839e-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="1839e-107">Consulte a [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) enumeração para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="1839e-107">See the [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1839e-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1839e-108">Requirements</span></span>  
 <span data-ttu-id="1839e-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1839e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1839e-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1839e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1839e-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1839e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1839e-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1839e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1839e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1839e-113">See also</span></span>

- [<span data-ttu-id="1839e-114">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="1839e-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="1839e-115">Enumeração VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="1839e-115">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
