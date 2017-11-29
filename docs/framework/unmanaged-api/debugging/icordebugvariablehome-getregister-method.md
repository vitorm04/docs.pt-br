---
title: "Método ICorDebugVariableHome::GetRegister"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetRegister
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7f16e4bfe4767e1b49d7dacf0481e8911a90e178
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="51b19-102">Método ICorDebugVariableHome::GetRegister</span><span class="sxs-lookup"><span data-stu-id="51b19-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="51b19-103">Obtém o registro que contém uma variável com um tipo de local de `VLT_REGISTER`e o registro de base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="51b19-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51b19-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51b19-104">Syntax</span></span>  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51b19-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="51b19-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="51b19-106">[out] Um valor de enumeração CorDebugRegister que indica o registro para uma variável com um tipo de local de `VLT_REGISTER`e o registro de base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="51b19-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51b19-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="51b19-107">Return Value</span></span>  
 <span data-ttu-id="51b19-108">O método retorna os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="51b19-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="51b19-109">Valor</span><span class="sxs-lookup"><span data-stu-id="51b19-109">Value</span></span>|<span data-ttu-id="51b19-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="51b19-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="51b19-111">A variável está no registro indicado pelo `pRegister` argumento.</span><span class="sxs-lookup"><span data-stu-id="51b19-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="51b19-112">A variável não está em um registro ou um local relativo ao registro.</span><span class="sxs-lookup"><span data-stu-id="51b19-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="51b19-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="51b19-113">Requirements</span></span>  
 <span data-ttu-id="51b19-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51b19-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51b19-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51b19-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51b19-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51b19-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51b19-117">**Versões do .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51b19-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51b19-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51b19-118">See Also</span></span>  
 [<span data-ttu-id="51b19-119">Enumeração VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="51b19-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 [<span data-ttu-id="51b19-120">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="51b19-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
