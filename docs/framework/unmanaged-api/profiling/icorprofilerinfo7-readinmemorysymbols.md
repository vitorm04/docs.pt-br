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
ms.openlocfilehash: ae51490be96f3eb6524831c93739c3befbc30b37
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132032"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="da781-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="da781-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="da781-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="da781-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="da781-104">Lê bytes de um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="da781-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da781-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da781-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da781-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="da781-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="da781-107">no O identificador do módulo que contém o fluxo na memória.</span><span class="sxs-lookup"><span data-stu-id="da781-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="da781-108">no O deslocamento dentro do fluxo na memória no qual começar a ler os bytes.</span><span class="sxs-lookup"><span data-stu-id="da781-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="da781-109">fora Um ponteiro para o buffer para o qual os dados serão copiados.</span><span class="sxs-lookup"><span data-stu-id="da781-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="da781-110">O buffer deve ter `countSymbolBytes` de espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="da781-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="da781-111">no O número de bytes a serem copiados.</span><span class="sxs-lookup"><span data-stu-id="da781-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="da781-112">fora Quando o método retorna, contém o número real de bytes lidos.</span><span class="sxs-lookup"><span data-stu-id="da781-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da781-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="da781-113">Return Value</span></span>  
 <span data-ttu-id="da781-114">`S_OK`, se um número diferente de zero de bytes tiver sido lido.</span><span class="sxs-lookup"><span data-stu-id="da781-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="da781-115">`CORPROF_E_MODULE_IS_DYNAMIC`, se o módulo foi criado usando <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="da781-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da781-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="da781-116">Remarks</span></span>  
 <span data-ttu-id="da781-117">O método `ReadInMemorySymbols` tenta ler `countSymbolBytes` de dados começando na `symbolsReadOffset` de deslocamento no fluxo na memória.</span><span class="sxs-lookup"><span data-stu-id="da781-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="da781-118">Os dados são copiados para `pSymbolBytes`, que deve ter `countSymbolBytes` de espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="da781-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="da781-119">`pCountSymbolsBytesRead` contém o número real de bytes lidos, que pode ser menor que `countSymbolBytes` se o final do fluxo for atingido.</span><span class="sxs-lookup"><span data-stu-id="da781-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da781-120">A implementação atual não oferece suporte a Reflection. Emit.</span><span class="sxs-lookup"><span data-stu-id="da781-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="da781-121">Se o módulo foi criado usando Reflection. Emit, o método retornará `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="da781-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da781-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da781-122">Requirements</span></span>  
 <span data-ttu-id="da781-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da781-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da781-124">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="da781-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="da781-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da781-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da781-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da781-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da781-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da781-127">See also</span></span>

- [<span data-ttu-id="da781-128">Interface ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="da781-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
