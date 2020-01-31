---
title: Método ICorProfilerFunctionEnum::Next
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Next
helpviewer_keywords:
- ICorProfilerFunctionEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 5ed4aa83-ce56-4b9f-9237-5da7587787fe
topic_type:
- apiref
ms.openlocfilehash: 9c7fa25712858d1119b45fc742a5d23454b55273
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864460"
---
# <a name="icorprofilerfunctionenumnext-method"></a><span data-ttu-id="7a2c6-102">Método ICorProfilerFunctionEnum::Next</span><span class="sxs-lookup"><span data-stu-id="7a2c6-102">ICorProfilerFunctionEnum::Next Method</span></span>
<span data-ttu-id="7a2c6-103">Obtém o número especificado de funções contíguas de uma coleção sequencial de funções, começando na posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="7a2c6-103">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a2c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7a2c6-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a2c6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7a2c6-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7a2c6-106">no O número de funções a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="7a2c6-106">[in] The number of functions to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="7a2c6-107">fora Uma matriz de valores de `COR_PRF_FUNCTION`, cada um representando uma função recuperada.</span><span class="sxs-lookup"><span data-stu-id="7a2c6-107">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7a2c6-108">fora Um ponteiro para o número de funções realmente retornadas na matriz de `ids`.</span><span class="sxs-lookup"><span data-stu-id="7a2c6-108">[out] A pointer to the number of functions actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a2c6-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7a2c6-109">Return Value</span></span>  
 <span data-ttu-id="7a2c6-110">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="7a2c6-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7a2c6-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7a2c6-111">HRESULT</span></span>|<span data-ttu-id="7a2c6-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7a2c6-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7a2c6-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7a2c6-113">S_OK</span></span>|<span data-ttu-id="7a2c6-114">`celt` elementos foram retornados.</span><span class="sxs-lookup"><span data-stu-id="7a2c6-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="7a2c6-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7a2c6-115">S_FALSE</span></span>|<span data-ttu-id="7a2c6-116">Foram retornados menos de `celt` elementos, o que indica que a enumeração foi concluída.</span><span class="sxs-lookup"><span data-stu-id="7a2c6-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7a2c6-117">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="7a2c6-117">Requirements</span></span>  
 <span data-ttu-id="7a2c6-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a2c6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a2c6-119">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7a2c6-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7a2c6-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a2c6-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a2c6-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a2c6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a2c6-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="7a2c6-122">See also</span></span>

- [<span data-ttu-id="7a2c6-123">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="7a2c6-123">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="7a2c6-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="7a2c6-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
