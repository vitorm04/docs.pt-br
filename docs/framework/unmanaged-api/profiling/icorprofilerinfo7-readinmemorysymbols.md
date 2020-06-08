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
ms.openlocfilehash: 6732457220d795bbf8ae54277ef9f5c07cf96359
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495353"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="6efba-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="6efba-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="6efba-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="6efba-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="6efba-104">Lê bytes de um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="6efba-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6efba-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6efba-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6efba-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6efba-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="6efba-107">no O identificador do módulo que contém o fluxo na memória.</span><span class="sxs-lookup"><span data-stu-id="6efba-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="6efba-108">no O deslocamento dentro do fluxo na memória no qual começar a ler os bytes.</span><span class="sxs-lookup"><span data-stu-id="6efba-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="6efba-109">fora Um ponteiro para o buffer para o qual os dados serão copiados.</span><span class="sxs-lookup"><span data-stu-id="6efba-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="6efba-110">O buffer deve ter `countSymbolBytes` espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="6efba-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="6efba-111">no O número de bytes a serem copiados.</span><span class="sxs-lookup"><span data-stu-id="6efba-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="6efba-112">fora Quando o método retorna, contém o número real de bytes lidos.</span><span class="sxs-lookup"><span data-stu-id="6efba-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6efba-113">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="6efba-113">Return Value</span></span>  
 <span data-ttu-id="6efba-114">`S_OK`, se um número diferente de zero de bytes tiver sido lido.</span><span class="sxs-lookup"><span data-stu-id="6efba-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="6efba-115">`CORPROF_E_MODULE_IS_DYNAMIC`, se o módulo foi criado usando <xref:System.Reflection.Emit> .</span><span class="sxs-lookup"><span data-stu-id="6efba-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6efba-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="6efba-116">Remarks</span></span>  
 <span data-ttu-id="6efba-117">O `ReadInMemorySymbols` método tenta ler os `countSymbolBytes` dados começando no deslocamento `symbolsReadOffset` dentro do fluxo na memória.</span><span class="sxs-lookup"><span data-stu-id="6efba-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="6efba-118">Os dados são copiados para o `pSymbolBytes` , que deve ter `countSymbolBytes` espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="6efba-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="6efba-119">`pCountSymbolsBytesRead`contém o número real de bytes lidos, que pode ser menor que `countSymbolBytes` se o final do fluxo for atingido.</span><span class="sxs-lookup"><span data-stu-id="6efba-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6efba-120">A implementação atual não oferece suporte a Reflection. Emit.</span><span class="sxs-lookup"><span data-stu-id="6efba-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="6efba-121">Se o módulo foi criado usando Reflection. Emit, o método retornará `CORPROF_E_MODULE_IS_DYNAMIC` .</span><span class="sxs-lookup"><span data-stu-id="6efba-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6efba-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6efba-122">Requirements</span></span>  
 <span data-ttu-id="6efba-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6efba-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6efba-124">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6efba-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6efba-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6efba-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6efba-126">**.NET Framework versões:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6efba-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6efba-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="6efba-127">See also</span></span>

- [<span data-ttu-id="6efba-128">Interface ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="6efba-128">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
