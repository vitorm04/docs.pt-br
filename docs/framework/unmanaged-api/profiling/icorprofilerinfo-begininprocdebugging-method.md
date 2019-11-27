---
title: Método ICorProfilerInfo::BeginInprocDebugging
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
ms.openlocfilehash: fffc028c7706c86e8384483cc92ebad90b292861
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447741"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="2a25c-102">Método ICorProfilerInfo::BeginInprocDebugging</span><span class="sxs-lookup"><span data-stu-id="2a25c-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="2a25c-103">Inicializa o suporte à depuração em processo.</span><span class="sxs-lookup"><span data-stu-id="2a25c-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="2a25c-104">Esse método é obsoleto no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="2a25c-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a25c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a25c-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a25c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2a25c-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="2a25c-107">no Defina esse valor como `true` para inicializar o suporte à depuração somente para o thread atual; Defina-o como `false` para inicializar o suporte à depuração para todos os threads.</span><span class="sxs-lookup"><span data-stu-id="2a25c-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="2a25c-108">fora O ponteiro para um valor retornado que identifica a sessão de depuração.</span><span class="sxs-lookup"><span data-stu-id="2a25c-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a25c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a25c-109">Remarks</span></span>  
 <span data-ttu-id="2a25c-110">Os serviços de depuração CLR oferecem suporte à depuração em processo limitada no .NET Framework versões 1,0 e 1,1.</span><span class="sxs-lookup"><span data-stu-id="2a25c-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="2a25c-111">A depuração em processo habilitou um criador de perfil para usar as partes de inspeção da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="2a25c-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="2a25c-112">No entanto, devido aos comentários do cliente, a depuração em processo foi removida da .NET Framework na versão 2,0 e substituída por um conjunto de funcionalidades que está mais alinhado com a API de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="2a25c-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a25c-113">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="2a25c-113">Requirements</span></span>  
 <span data-ttu-id="2a25c-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a25c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a25c-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2a25c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2a25c-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a25c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a25c-117">**Versão do .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="2a25c-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a25c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a25c-118">See also</span></span>

- [<span data-ttu-id="2a25c-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="2a25c-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
