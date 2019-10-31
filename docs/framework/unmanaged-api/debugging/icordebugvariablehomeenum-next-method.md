---
title: 'Método ICorDebugVariableHomeEnum:: Next'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type:
- apiref
ms.openlocfilehash: 9c2c16789fb61099c9b7c58154810739d225af1f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121929"
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="22f9e-102">Método ICorDebugVariableHomeEnum:: Next</span><span class="sxs-lookup"><span data-stu-id="22f9e-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="22f9e-103">Obtém o número especificado de instâncias [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) que contêm informações sobre as variáveis e os argumentos locais em uma função.</span><span class="sxs-lookup"><span data-stu-id="22f9e-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22f9e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22f9e-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22f9e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="22f9e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="22f9e-106">no O número de objetos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="22f9e-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="22f9e-107">Uma matriz de ponteiros, cada um dos quais aponta para um objeto [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) que fornece informações sobre uma variável local ou um argumento de uma função.</span><span class="sxs-lookup"><span data-stu-id="22f9e-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="22f9e-108">fora O número de instâncias realmente retornadas em objetos.</span><span class="sxs-lookup"><span data-stu-id="22f9e-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22f9e-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="22f9e-109">Return Value</span></span>  
 <span data-ttu-id="22f9e-110">O método retorna os valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="22f9e-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="22f9e-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="22f9e-111">HRESULT</span></span>|<span data-ttu-id="22f9e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="22f9e-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="22f9e-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="22f9e-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="22f9e-114">O número real de instâncias recuperadas, conforme refletido em `pceltFetched`, é menor que o número de instâncias solicitadas.</span><span class="sxs-lookup"><span data-stu-id="22f9e-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22f9e-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="22f9e-115">Remarks</span></span>  
 <span data-ttu-id="22f9e-116">O método [ICorDebugVariableHomeEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) recupera um máximo de `celt` objetos começando na posição atual do enumerador.</span><span class="sxs-lookup"><span data-stu-id="22f9e-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="22f9e-117">Quando o método retorna, `pceltFetched` contém o número real de objetos recuperados.</span><span class="sxs-lookup"><span data-stu-id="22f9e-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22f9e-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="22f9e-118">Requirements</span></span>  
 <span data-ttu-id="22f9e-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22f9e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22f9e-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22f9e-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22f9e-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22f9e-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22f9e-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22f9e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22f9e-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22f9e-123">See also</span></span>

- [<span data-ttu-id="22f9e-124">Interface ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="22f9e-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
- [<span data-ttu-id="22f9e-125">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="22f9e-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
