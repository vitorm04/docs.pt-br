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
ms.openlocfilehash: 2a878ccf94fb4f6d67daa3a4dd42fcf98faf34a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748634"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="a4b8c-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="a4b8c-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="a4b8c-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="a4b8c-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="a4b8c-104">Lê os bytes do fluxo símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="a4b8c-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4b8c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a4b8c-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4b8c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a4b8c-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="a4b8c-107">[in] O identificador do módulo que contém o fluxo de memória.</span><span class="sxs-lookup"><span data-stu-id="a4b8c-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="a4b8c-108">[in] O deslocamento dentro do fluxo de memória no qual iniciar a leitura dos bytes.</span><span class="sxs-lookup"><span data-stu-id="a4b8c-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="a4b8c-109">[out] Um ponteiro para o buffer no qual os dados serão copiados.</span><span class="sxs-lookup"><span data-stu-id="a4b8c-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="a4b8c-110">O buffer deve ter `countSymbolBytes` de espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="a4b8c-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="a4b8c-111">[in] O número de bytes a serem copiados.</span><span class="sxs-lookup"><span data-stu-id="a4b8c-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="a4b8c-112">[out] Quando o método retorna, contém o número real de bytes lidos.</span><span class="sxs-lookup"><span data-stu-id="a4b8c-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4b8c-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a4b8c-113">Return Value</span></span>  
 <span data-ttu-id="a4b8c-114">`S_OK`, se um número diferente de zero de bytes foram lidos.</span><span class="sxs-lookup"><span data-stu-id="a4b8c-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="a4b8c-115">`CORPROF_E_MODULE_IS_DYNAMIC`, se o módulo foi criado usando <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="a4b8c-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4b8c-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="a4b8c-116">Remarks</span></span>  
 <span data-ttu-id="a4b8c-117">O `ReadInMemorySymbols` método tenta ler `countSymbolBytes` dos dados começando no deslocamento `symbolsReadOffset` dentro do fluxo de memória.</span><span class="sxs-lookup"><span data-stu-id="a4b8c-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="a4b8c-118">Os dados são copiados para `pSymbolBytes`, que deve ter `countSymbolBytes` de espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="a4b8c-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="a4b8c-119">`pCountSymbolsBytesRead` contém o número real de bytes lidos, que pode ser menor do que `countSymbolBytes` se o final do fluxo for atingido.</span><span class="sxs-lookup"><span data-stu-id="a4b8c-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4b8c-120">A implementação atual não oferece suporte a Reflection. Emit.</span><span class="sxs-lookup"><span data-stu-id="a4b8c-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="a4b8c-121">Se o módulo foi criado usando Reflection. Emit, o método retorna `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="a4b8c-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4b8c-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a4b8c-122">Requirements</span></span>  
 <span data-ttu-id="a4b8c-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4b8c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4b8c-124">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a4b8c-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a4b8c-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4b8c-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4b8c-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4b8c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b8c-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4b8c-127">See also</span></span>

- [<span data-ttu-id="a4b8c-128">Interface ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="a4b8c-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
