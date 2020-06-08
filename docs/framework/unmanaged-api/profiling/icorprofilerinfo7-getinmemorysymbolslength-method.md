---
title: 'Método ICorProfilerInfo7:: GetInMemorySymbolsLength'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
ms.openlocfilehash: 43d6bdeae5f522bd73b0bdf3a5c403ec69ee384c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495432"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="120a1-102">Método ICorProfilerInfo7:: GetInMemorySymbolsLength</span><span class="sxs-lookup"><span data-stu-id="120a1-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>
<span data-ttu-id="120a1-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="120a1-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="120a1-104">Retorna o comprimento de um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="120a1-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="120a1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="120a1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="120a1-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="120a1-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="120a1-107">no O identificador do módulo que contém o fluxo na memória.</span><span class="sxs-lookup"><span data-stu-id="120a1-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="120a1-108">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="120a1-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="120a1-109">fora Um ponteiro para um `DWORD` valor que, quando o método retorna, contém o comprimento do fluxo em bytes.</span><span class="sxs-lookup"><span data-stu-id="120a1-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="120a1-110">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="120a1-110">Return Value</span></span>  
 <span data-ttu-id="120a1-111">O método retorna `S_OK` se o comprimento do fluxo de memória pode ser determinado, mesmo se for zero (0).</span><span class="sxs-lookup"><span data-stu-id="120a1-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="120a1-112">O método retorna `CORPROF_E_MODULE_IS_DYNAMIC` se o método foi criado usando <xref:System.Reflection.Emit?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="120a1-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="120a1-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="120a1-113">Remarks</span></span>  
 <span data-ttu-id="120a1-114">Se o módulo tiver símbolos na memória, o comprimento do fluxo será colocado em `pCountSymbolBytes` .</span><span class="sxs-lookup"><span data-stu-id="120a1-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="120a1-115">Se o módulo não tiver símbolos na memória, `*pCountSymbolBytes = 0` .</span><span class="sxs-lookup"><span data-stu-id="120a1-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="120a1-116">A implementação atual não oferece suporte a Reflection. Emit.</span><span class="sxs-lookup"><span data-stu-id="120a1-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="120a1-117">Se o módulo foi criado usando Reflection. Emit, o método retornará `CORPROF_E_MODULE_IS_DYNAMIC` .</span><span class="sxs-lookup"><span data-stu-id="120a1-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="120a1-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="120a1-118">Requirements</span></span>  
 <span data-ttu-id="120a1-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="120a1-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="120a1-120">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="120a1-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="120a1-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="120a1-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="120a1-122">**.NET Framework versões:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="120a1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="120a1-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="120a1-123">See also</span></span>

- [<span data-ttu-id="120a1-124">Interface ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="120a1-124">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
