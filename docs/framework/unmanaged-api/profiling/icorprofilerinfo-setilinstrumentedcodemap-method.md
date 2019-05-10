---
title: Método ICorProfilerInfo::SetILInstrumentedCodeMap
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1ec0f986efe24b0b69df9d2ecd93335f7ac5db28
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64606642"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="a9343-102">Método ICorProfilerInfo::SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="a9343-102">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="a9343-103">Define um mapa de código para a função especificada usando as entradas de mapa especificadas Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="a9343-103">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9343-104">No .NET Framework versão 2.0, chamando `SetILInstrumentedCodeMap` em um `FunctionID` que representa um genérico de função em um domínio de aplicativo específico afetará todas as instâncias dessa função no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a9343-104">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9343-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9343-105">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9343-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a9343-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a9343-107">[in] A ID da função para o qual definir o mapa de código.</span><span class="sxs-lookup"><span data-stu-id="a9343-107">[in] The ID of the function for which to set the code map.</span></span>  
  
 `fStartJit`  
 <span data-ttu-id="a9343-108">[in] Um valor booliano que indica se a chamada para o `SetILInstrumentedCodeMap` método é o primeiro para um determinado `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="a9343-108">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="a9343-109">Definir `fStartJit` à `true` na primeira chamada para `SetILInstrumentedCodeMap` para um determinado `FunctionID`e, ao `false` daí em diante.</span><span class="sxs-lookup"><span data-stu-id="a9343-109">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>  
  
 `cILMapEntries`  
 <span data-ttu-id="a9343-110">[in] O número de elementos no `cILMapEntries` matriz.</span><span class="sxs-lookup"><span data-stu-id="a9343-110">[in] The number of elements in the `cILMapEntries` array.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="a9343-111">[in] Uma matriz de estruturas COR_IL_MAP, cada um deles especifica um deslocamento do MSIL.</span><span class="sxs-lookup"><span data-stu-id="a9343-111">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9343-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="a9343-112">Remarks</span></span>  
 <span data-ttu-id="a9343-113">Um criador de perfil geralmente insere instruções dentro do código-fonte de um método para instrumentar o método (por exemplo, para notificar quando uma linha de origem especificado for atingida).</span><span class="sxs-lookup"><span data-stu-id="a9343-113">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="a9343-114">`SetILInstrumentedCodeMap` permite que um criador de perfil mapear as instruções MSIL originais para seus novos locais.</span><span class="sxs-lookup"><span data-stu-id="a9343-114">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="a9343-115">Um criador de perfil pode usar o [ICorProfilerInfo:: Getiltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) método para obter o deslocamento do MSIL original para um determinado deslocamento nativo.</span><span class="sxs-lookup"><span data-stu-id="a9343-115">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>  
  
 <span data-ttu-id="a9343-116">O depurador assumirá que cada deslocamento antigo se refere a um deslocamento dentro do código MSIL original, sem modificações de MSIL, e cada novo deslocamento refere-se para o deslocamento do MSIL dentro do código novo, instrumentado.</span><span class="sxs-lookup"><span data-stu-id="a9343-116">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="a9343-117">O mapa deve ser classificado em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="a9343-117">The map should be sorted in increasing order.</span></span> <span data-ttu-id="a9343-118">Para depuração funcione corretamente, siga estas diretrizes:</span><span class="sxs-lookup"><span data-stu-id="a9343-118">For stepping to work properly, follow these guidelines:</span></span>  
  
- <span data-ttu-id="a9343-119">Não reorganize o código instrumentado de MSIL.</span><span class="sxs-lookup"><span data-stu-id="a9343-119">Do not reorder instrumented MSIL code.</span></span>  
  
- <span data-ttu-id="a9343-120">Não remova o código MSIL original.</span><span class="sxs-lookup"><span data-stu-id="a9343-120">Do not remove the original MSIL code.</span></span>  
  
- <span data-ttu-id="a9343-121">Inclua entradas para todos os pontos de sequência do arquivo de banco de dados (PDB) de programa no mapa.</span><span class="sxs-lookup"><span data-stu-id="a9343-121">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="a9343-122">O mapa não interpola entradas ausentes.</span><span class="sxs-lookup"><span data-stu-id="a9343-122">The map does not interpolate missing entries.</span></span> <span data-ttu-id="a9343-123">Então, como o mapa a seguir:</span><span class="sxs-lookup"><span data-stu-id="a9343-123">So, given the following map:</span></span>  
  
     <span data-ttu-id="a9343-124">(0 antigo, 0 novos)</span><span class="sxs-lookup"><span data-stu-id="a9343-124">(0 old, 0 new)</span></span>  
  
     <span data-ttu-id="a9343-125">(5 antigo, 10 novos)</span><span class="sxs-lookup"><span data-stu-id="a9343-125">(5 old, 10 new)</span></span>  
  
     <span data-ttu-id="a9343-126">(9 antigo, 20 novas)</span><span class="sxs-lookup"><span data-stu-id="a9343-126">(9 old, 20 new)</span></span>  
  
    - <span data-ttu-id="a9343-127">Um deslocamento antigo de 0, 1, 2, 3 ou 4 será mapeado para o novo deslocamento 0.</span><span class="sxs-lookup"><span data-stu-id="a9343-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>  
  
    - <span data-ttu-id="a9343-128">Um deslocamento antigo de 5, 6, 7 ou 8 será mapeado para o novo deslocamento de 10.</span><span class="sxs-lookup"><span data-stu-id="a9343-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
    - <span data-ttu-id="a9343-129">Um deslocamento antigo de 9 ou superior será mapeado para o novo deslocamento 20.</span><span class="sxs-lookup"><span data-stu-id="a9343-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
    - <span data-ttu-id="a9343-130">Um novo deslocamento de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 será mapeado para o deslocamento antigo 0.</span><span class="sxs-lookup"><span data-stu-id="a9343-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
    - <span data-ttu-id="a9343-131">Um novo deslocamento de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 será mapeado para o deslocamento antigo 5.</span><span class="sxs-lookup"><span data-stu-id="a9343-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
    - <span data-ttu-id="a9343-132">Um novo deslocamento de 20 ou superior será mapeado para o deslocamento antigo 9.</span><span class="sxs-lookup"><span data-stu-id="a9343-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9343-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a9343-133">Requirements</span></span>  
 <span data-ttu-id="a9343-134">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9343-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9343-135">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a9343-135">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a9343-136">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9343-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9343-137">**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9343-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9343-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9343-138">See also</span></span>

- [<span data-ttu-id="a9343-139">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="a9343-139">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
