---
title: "Método ICorDebugVariableHome::GetArgumentIndex"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetArgumentIndex
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentiIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 175e45758d26d8168279c825d41ee58d049edf0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="e6a29-102">Método ICorDebugVariableHome::GetArgumentIndex</span><span class="sxs-lookup"><span data-stu-id="e6a29-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>
<span data-ttu-id="e6a29-103">Obtém o índice de um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="e6a29-103">Gets the index of a function argument.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6a29-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6a29-104">Syntax</span></span>  
  
```  
HRESULT GetArgumentIndex(  
    [out] ULONG32* pArgumentIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6a29-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e6a29-105">Parameters</span></span>  
 `pArgumentIndex`  
 <span data-ttu-id="e6a29-106">[out] Um ponteiro para o índice do argumento.</span><span class="sxs-lookup"><span data-stu-id="e6a29-106">[out] A pointer to the argument index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6a29-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e6a29-107">Return Value</span></span>  
 <span data-ttu-id="e6a29-108">O método retorna os seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="e6a29-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="e6a29-109">Valor</span><span class="sxs-lookup"><span data-stu-id="e6a29-109">Value</span></span>|<span data-ttu-id="e6a29-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6a29-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="e6a29-111">A chamada do método retornou um índice de argumento válido.</span><span class="sxs-lookup"><span data-stu-id="e6a29-111">The method call returned a valid argument index.</span></span>|  
|`E_FAIL`|<span data-ttu-id="e6a29-112">Atual [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instância representa uma variável local.</span><span class="sxs-lookup"><span data-stu-id="e6a29-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6a29-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="e6a29-113">Remarks</span></span>  
 <span data-ttu-id="e6a29-114">O índice de argumento pode ser usado para recuperar metadados para esse argumento.</span><span class="sxs-lookup"><span data-stu-id="e6a29-114">The argument index can be used to retrieve metadata for this argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6a29-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e6a29-115">Requirements</span></span>  
 <span data-ttu-id="e6a29-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6a29-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6a29-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6a29-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6a29-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6a29-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6a29-119">**Versões do .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6a29-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6a29-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6a29-120">See Also</span></span>  
 [<span data-ttu-id="e6a29-121">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="e6a29-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
