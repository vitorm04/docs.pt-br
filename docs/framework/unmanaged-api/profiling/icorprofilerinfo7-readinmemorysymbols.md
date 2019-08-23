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
ms.openlocfilehash: 95b463b23c230d620d746e48da49d75238ef2cb7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955369"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="bd1bf-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="bd1bf-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="bd1bf-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="bd1bf-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="bd1bf-104">Lê bytes de um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="bd1bf-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd1bf-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd1bf-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd1bf-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bd1bf-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="bd1bf-107">no O identificador do módulo que contém o fluxo na memória.</span><span class="sxs-lookup"><span data-stu-id="bd1bf-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="bd1bf-108">no O deslocamento dentro do fluxo na memória no qual começar a ler os bytes.</span><span class="sxs-lookup"><span data-stu-id="bd1bf-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="bd1bf-109">fora Um ponteiro para o buffer para o qual os dados serão copiados.</span><span class="sxs-lookup"><span data-stu-id="bd1bf-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="bd1bf-110">O buffer deve ter `countSymbolBytes` espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="bd1bf-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="bd1bf-111">no O número de bytes a serem copiados.</span><span class="sxs-lookup"><span data-stu-id="bd1bf-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="bd1bf-112">fora Quando o método retorna, contém o número real de bytes lidos.</span><span class="sxs-lookup"><span data-stu-id="bd1bf-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd1bf-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bd1bf-113">Return Value</span></span>  
 <span data-ttu-id="bd1bf-114">`S_OK`, se um número diferente de zero de bytes tiver sido lido.</span><span class="sxs-lookup"><span data-stu-id="bd1bf-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="bd1bf-115">`CORPROF_E_MODULE_IS_DYNAMIC`, se o módulo foi criado usando <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="bd1bf-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd1bf-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="bd1bf-116">Remarks</span></span>  
 <span data-ttu-id="bd1bf-117">O `ReadInMemorySymbols` método tenta ler `countSymbolBytes` os dados começando no deslocamento `symbolsReadOffset` dentro do fluxo na memória.</span><span class="sxs-lookup"><span data-stu-id="bd1bf-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="bd1bf-118">Os dados são copiados `pSymbolBytes`para o, que deve ter `countSymbolBytes` espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="bd1bf-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="bd1bf-119">`pCountSymbolsBytesRead`contém o número real de bytes lidos, que pode ser menor `countSymbolBytes` que se o final do fluxo for atingido.</span><span class="sxs-lookup"><span data-stu-id="bd1bf-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd1bf-120">A implementação atual não oferece suporte a Reflection. Emit.</span><span class="sxs-lookup"><span data-stu-id="bd1bf-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="bd1bf-121">Se o módulo foi criado usando Reflection. Emit, o método retornará `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="bd1bf-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd1bf-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bd1bf-122">Requirements</span></span>  
 <span data-ttu-id="bd1bf-123">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd1bf-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd1bf-124">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bd1bf-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bd1bf-125">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd1bf-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd1bf-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd1bf-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd1bf-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd1bf-127">See also</span></span>

- [<span data-ttu-id="bd1bf-128">Interface ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="bd1bf-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
