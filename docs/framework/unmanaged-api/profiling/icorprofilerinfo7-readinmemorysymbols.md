---
title: ICorProfilerInfo7::ReadInMemorySymbols
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 662863ec69e464dafe893552f1d81755313acc75
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153316"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="c3a15-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="c3a15-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="c3a15-103">[Com suporte no [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="c3a15-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="c3a15-104">Lê os bytes do fluxo símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="c3a15-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3a15-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3a15-105">Syntax</span></span>  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3a15-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3a15-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="c3a15-107">[in] O identificador do módulo que contém o fluxo de memória.</span><span class="sxs-lookup"><span data-stu-id="c3a15-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="c3a15-108">[in] O deslocamento dentro do fluxo de memória no qual iniciar a leitura dos bytes.</span><span class="sxs-lookup"><span data-stu-id="c3a15-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="c3a15-109">[out] Um ponteiro para o buffer no qual os dados serão copiados.</span><span class="sxs-lookup"><span data-stu-id="c3a15-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="c3a15-110">O buffer deve ter `countSymbolBytes` de espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="c3a15-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="c3a15-111">[in] O número de bytes a serem copiados.</span><span class="sxs-lookup"><span data-stu-id="c3a15-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="c3a15-112">[out] Quando o método retorna, contém o número real de bytes lidos.</span><span class="sxs-lookup"><span data-stu-id="c3a15-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3a15-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c3a15-113">Return Value</span></span>  
 <span data-ttu-id="c3a15-114">`S_OK`, se um número diferente de zero de bytes foram lidos.</span><span class="sxs-lookup"><span data-stu-id="c3a15-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="c3a15-115">`CORPROF_E_MODULE_IS_DYNAMIC`, se o módulo foi criado usando <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="c3a15-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3a15-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3a15-116">Remarks</span></span>  
 <span data-ttu-id="c3a15-117">O `ReadInMemorySymbols` método tenta ler `countSymbolBytes` dos dados começando no deslocamento `symbolsReadOffset` dentro do fluxo de memória.</span><span class="sxs-lookup"><span data-stu-id="c3a15-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="c3a15-118">Os dados são copiados para `pSymbolBytes`, que deve ter `countSymbolBytes` de espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="c3a15-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="c3a15-119">`pCountSymbolsBytesRead` contém o número real de bytes lidos, que pode ser menor do que `countSymbolBytes` se o final do fluxo for atingido.</span><span class="sxs-lookup"><span data-stu-id="c3a15-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3a15-120">A implementação atual não oferece suporte a Reflection. Emit.</span><span class="sxs-lookup"><span data-stu-id="c3a15-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="c3a15-121">Se o módulo foi criado usando Reflection. Emit, o método retorna `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="c3a15-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3a15-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3a15-122">Requirements</span></span>  
 <span data-ttu-id="c3a15-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3a15-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3a15-124">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c3a15-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c3a15-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3a15-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3a15-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3a15-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3a15-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3a15-127">See also</span></span>

- [<span data-ttu-id="c3a15-128">Interface ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="c3a15-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
