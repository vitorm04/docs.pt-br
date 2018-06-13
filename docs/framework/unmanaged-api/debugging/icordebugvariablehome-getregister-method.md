---
title: Método ICorDebugVariableHome::GetRegister
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e06c98067fea9368ac8f750d9187636d2ca9a8c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420102"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="0a961-102">Método ICorDebugVariableHome::GetRegister</span><span class="sxs-lookup"><span data-stu-id="0a961-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="0a961-103">Obtém o registro que contém uma variável com um tipo de local de `VLT_REGISTER`e o registro de base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="0a961-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a961-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0a961-104">Syntax</span></span>  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0a961-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0a961-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="0a961-106">[out] Um valor de enumeração CorDebugRegister que indica o registro para uma variável com um tipo de local de `VLT_REGISTER`e o registro de base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="0a961-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a961-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0a961-107">Return Value</span></span>  
 <span data-ttu-id="0a961-108">O método retorna os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="0a961-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="0a961-109">Valor</span><span class="sxs-lookup"><span data-stu-id="0a961-109">Value</span></span>|<span data-ttu-id="0a961-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a961-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="0a961-111">A variável está no registro indicado pelo `pRegister` argumento.</span><span class="sxs-lookup"><span data-stu-id="0a961-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="0a961-112">A variável não está em um registro ou um local relativo ao registro.</span><span class="sxs-lookup"><span data-stu-id="0a961-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a961-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0a961-113">Requirements</span></span>  
 <span data-ttu-id="0a961-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a961-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a961-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a961-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a961-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a961-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a961-117">**Versões do .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a961-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a961-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a961-118">See Also</span></span>  
 [<span data-ttu-id="0a961-119">Enumeração VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="0a961-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 [<span data-ttu-id="0a961-120">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="0a961-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
