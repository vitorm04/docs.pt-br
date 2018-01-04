---
title: ICorProfilerInfo7::ReadInMemorySymbols
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type: COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5851f73cc899ef21d8a5dcfd8f03617641a6625a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="80e19-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="80e19-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="80e19-103">[Com suporte no [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="80e19-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="80e19-104">Leituras de bytes de um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="80e19-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80e19-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80e19-105">Syntax</span></span>  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80e19-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="80e19-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="80e19-107">[in] O identificador do módulo que contém o fluxo de memória.</span><span class="sxs-lookup"><span data-stu-id="80e19-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="80e19-108">[in] O deslocamento dentro do fluxo de memória no qual iniciar a leitura de bytes.</span><span class="sxs-lookup"><span data-stu-id="80e19-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="80e19-109">[out] Um ponteiro para o buffer no qual os dados serão copiados.</span><span class="sxs-lookup"><span data-stu-id="80e19-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="80e19-110">O buffer deve ter `countSymbolBytes` de espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="80e19-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="80e19-111">[in] O número de bytes a serem copiados.</span><span class="sxs-lookup"><span data-stu-id="80e19-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="80e19-112">[out] Quando o método retorna, contém o número real de bytes lidos.</span><span class="sxs-lookup"><span data-stu-id="80e19-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80e19-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="80e19-113">Return Value</span></span>  
 <span data-ttu-id="80e19-114">`S_OK`, se um número diferente de zero de bytes foram lidos.</span><span class="sxs-lookup"><span data-stu-id="80e19-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="80e19-115">`CORPROF_E_MODULE_IS_DYNAMIC`, se o módulo foi criado usando <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="80e19-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80e19-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="80e19-116">Remarks</span></span>  
 <span data-ttu-id="80e19-117">O `ReadInMemorySymbols` método tenta ler `countSymbolBytes` de dados que inicia no deslocamento `symbolsReadOffset` dentro do fluxo de memória.</span><span class="sxs-lookup"><span data-stu-id="80e19-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="80e19-118">Os dados são copiados para `pSymbolBytes`, que deve ter `countSymbolBytes` de espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="80e19-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="80e19-119">`pCountSymbolsBytesRead`contém o número real de bytes lidos, que pode ser menor do que `countSymbolBytes` se o fim do fluxo for atingido.</span><span class="sxs-lookup"><span data-stu-id="80e19-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80e19-120">A implementação atual não oferece suporte a Reflection. Emit.</span><span class="sxs-lookup"><span data-stu-id="80e19-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="80e19-121">Se o módulo foi criado usando Reflection. Emit, o método retornará `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="80e19-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80e19-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80e19-122">Requirements</span></span>  
 <span data-ttu-id="80e19-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80e19-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80e19-124">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="80e19-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="80e19-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80e19-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80e19-126">**Versões do .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80e19-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e19-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80e19-127">See Also</span></span>  
 [<span data-ttu-id="80e19-128">Interface ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="80e19-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
