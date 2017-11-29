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
ms.openlocfilehash: 480317a4ec0515411f1ca8156a5bc4d06aa3f38a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="c8921-102">Método ICorDebugVariableHomeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="c8921-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="c8921-103">Obtém o número especificado de [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instâncias que contêm informações sobre as variáveis locais e os argumentos em uma função.</span><span class="sxs-lookup"><span data-stu-id="c8921-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8921-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8921-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8921-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c8921-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c8921-106">[in] O número de objetos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="c8921-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="c8921-107">Uma matriz de ponteiros, cada qual apontando para um [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objeto que fornece informações sobre uma variável local ou argumento de uma função.</span><span class="sxs-lookup"><span data-stu-id="c8921-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c8921-108">[out] O número de instâncias de fato retornadas nos objetos.</span><span class="sxs-lookup"><span data-stu-id="c8921-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8921-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c8921-109">Return Value</span></span>  
 <span data-ttu-id="c8921-110">O método retorna os seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="c8921-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="c8921-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c8921-111">HRESULT</span></span>|<span data-ttu-id="c8921-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8921-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c8921-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="c8921-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c8921-114">Recuperar o número real de instâncias, conforme refletido em `pceltFetched`, é menor que o número de instâncias solicitadas.</span><span class="sxs-lookup"><span data-stu-id="c8921-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8921-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="c8921-115">Remarks</span></span>  
 <span data-ttu-id="c8921-116">O [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) método recupera um máximo de `celt` objetos começando na posição atual do enumerador.</span><span class="sxs-lookup"><span data-stu-id="c8921-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="c8921-117">Quando o método retorna, `pceltFetched` contém o número real de objetos recuperados.</span><span class="sxs-lookup"><span data-stu-id="c8921-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8921-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c8921-118">Requirements</span></span>  
 <span data-ttu-id="c8921-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8921-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8921-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8921-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8921-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8921-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8921-122">**Versões do .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8921-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8921-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8921-123">See Also</span></span>  
 [<span data-ttu-id="c8921-124">Interface ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="c8921-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 [<span data-ttu-id="c8921-125">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="c8921-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
