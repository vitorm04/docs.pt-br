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
ms.openlocfilehash: a675cc301d2dd32f87e3864a3123e2044761ef91
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868350"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="b88ef-102">Método ICorProfilerInfo7:: GetInMemorySymbolsLength</span><span class="sxs-lookup"><span data-stu-id="b88ef-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>
<span data-ttu-id="b88ef-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="b88ef-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="b88ef-104">Retorna o comprimento de um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="b88ef-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b88ef-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b88ef-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b88ef-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b88ef-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="b88ef-107">no O identificador do módulo que contém o fluxo na memória.</span><span class="sxs-lookup"><span data-stu-id="b88ef-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="b88ef-108">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="b88ef-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="b88ef-109">fora Um ponteiro para um valor `DWORD` que, quando o método retorna, contém o comprimento do fluxo em bytes.</span><span class="sxs-lookup"><span data-stu-id="b88ef-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b88ef-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b88ef-110">Return Value</span></span>  
 <span data-ttu-id="b88ef-111">O método retornará `S_OK` se o comprimento do fluxo de memória puder ser determinado, mesmo se for zero (0).</span><span class="sxs-lookup"><span data-stu-id="b88ef-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="b88ef-112">O método retornará `CORPROF_E_MODULE_IS_DYNAMIC` se o método tiver sido criado usando <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b88ef-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b88ef-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="b88ef-113">Remarks</span></span>  
 <span data-ttu-id="b88ef-114">Se o módulo tiver símbolos na memória, o comprimento do fluxo será colocado em `pCountSymbolBytes`.</span><span class="sxs-lookup"><span data-stu-id="b88ef-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="b88ef-115">Se o módulo não tiver símbolos na memória, `*pCountSymbolBytes = 0`.</span><span class="sxs-lookup"><span data-stu-id="b88ef-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b88ef-116">A implementação atual não oferece suporte a Reflection. Emit.</span><span class="sxs-lookup"><span data-stu-id="b88ef-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="b88ef-117">Se o módulo foi criado usando Reflection. Emit, o método retornará `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="b88ef-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b88ef-118">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b88ef-118">Requirements</span></span>  
 <span data-ttu-id="b88ef-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b88ef-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b88ef-120">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b88ef-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b88ef-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b88ef-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b88ef-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b88ef-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b88ef-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="b88ef-123">See also</span></span>

- [<span data-ttu-id="b88ef-124">Interface ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="b88ef-124">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
