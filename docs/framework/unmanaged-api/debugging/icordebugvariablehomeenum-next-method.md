---
title: "Método ICorDebugVariableHomeEnum::Next"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHomeEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3bab158cbbe2eaf6e52ae0df6a0eed86d3d0b8ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="858f9-102">Método ICorDebugVariableHomeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="858f9-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="858f9-103">Obtém o número especificado de [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instâncias que contêm informações sobre as variáveis locais e os argumentos em uma função.</span><span class="sxs-lookup"><span data-stu-id="858f9-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="858f9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="858f9-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="858f9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="858f9-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="858f9-106">[in] O número de objetos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="858f9-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="858f9-107">Uma matriz de ponteiros, cada qual apontando para um [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objeto que fornece informações sobre uma variável local ou argumento de uma função.</span><span class="sxs-lookup"><span data-stu-id="858f9-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="858f9-108">[out] O número de instâncias de fato retornadas nos objetos.</span><span class="sxs-lookup"><span data-stu-id="858f9-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="858f9-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="858f9-109">Return Value</span></span>  
 <span data-ttu-id="858f9-110">O método retorna os seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="858f9-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="858f9-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="858f9-111">HRESULT</span></span>|<span data-ttu-id="858f9-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="858f9-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="858f9-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="858f9-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="858f9-114">Recuperar o número real de instâncias, conforme refletido em `pceltFetched`, é menor que o número de instâncias solicitadas.</span><span class="sxs-lookup"><span data-stu-id="858f9-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="858f9-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="858f9-115">Remarks</span></span>  
 <span data-ttu-id="858f9-116">O [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) método recupera um máximo de `celt` objetos começando na posição atual do enumerador.</span><span class="sxs-lookup"><span data-stu-id="858f9-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="858f9-117">Quando o método retorna, `pceltFetched` contém o número real de objetos recuperados.</span><span class="sxs-lookup"><span data-stu-id="858f9-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="858f9-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="858f9-118">Requirements</span></span>  
 <span data-ttu-id="858f9-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="858f9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="858f9-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="858f9-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="858f9-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="858f9-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="858f9-122">**Versões do .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="858f9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="858f9-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="858f9-123">See Also</span></span>  
 [<span data-ttu-id="858f9-124">Interface ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="858f9-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 [<span data-ttu-id="858f9-125">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="858f9-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
