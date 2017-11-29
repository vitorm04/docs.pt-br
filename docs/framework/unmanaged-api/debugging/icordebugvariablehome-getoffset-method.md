---
title: "Método ICorDebugVariableHome::GetOffset"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetOffset
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ddedc83e4e51cf12a3f8a0504d90bda7f944a6d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="77fef-102">Método ICorDebugVariableHome::GetOffset</span><span class="sxs-lookup"><span data-stu-id="77fef-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="77fef-103">Obtém o deslocamento do registro base para uma variável.</span><span class="sxs-lookup"><span data-stu-id="77fef-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77fef-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77fef-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77fef-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="77fef-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="77fef-106">[out] O deslocamento do registro base.</span><span class="sxs-lookup"><span data-stu-id="77fef-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77fef-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="77fef-107">Return Value</span></span>  
 <span data-ttu-id="77fef-108">O método retorna os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="77fef-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="77fef-109">Valor</span><span class="sxs-lookup"><span data-stu-id="77fef-109">Value</span></span>|<span data-ttu-id="77fef-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="77fef-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="77fef-111">A variável está em um local relativo ao registro de memória.</span><span class="sxs-lookup"><span data-stu-id="77fef-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="77fef-112">A variável não está em um local relativo ao registro de memória.</span><span class="sxs-lookup"><span data-stu-id="77fef-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="77fef-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77fef-113">Requirements</span></span>  
 <span data-ttu-id="77fef-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77fef-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77fef-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77fef-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77fef-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77fef-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77fef-117">**Versões do .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77fef-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77fef-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77fef-118">See Also</span></span>  
 [<span data-ttu-id="77fef-119">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="77fef-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
