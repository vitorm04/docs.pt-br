---
title: Interface ICorProfilerInfo6
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
ms.openlocfilehash: 80ac17a96e5c1c8c32cfc336da6c2be30eaf80fd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868363"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="93616-102">Interface ICorProfilerInfo6</span><span class="sxs-lookup"><span data-stu-id="93616-102">ICorProfilerInfo6 Interface</span></span>
<span data-ttu-id="93616-103">[Com suporte no .NET Framework 4,6 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="93616-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="93616-104">Uma subclasse de [ICorProfilerInfo5](icorprofilerinfo5-interface.md) que fornece um enumerador para todos os métodos que são definidos em um determinado módulo NGen e embutidos em um determinado método.</span><span class="sxs-lookup"><span data-stu-id="93616-104">A subclass of [ICorProfilerInfo5](icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93616-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="93616-105">Methods</span></span>  
  
|<span data-ttu-id="93616-106">Método</span><span class="sxs-lookup"><span data-stu-id="93616-106">Method</span></span>|<span data-ttu-id="93616-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="93616-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93616-108">Método ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod</span><span class="sxs-lookup"><span data-stu-id="93616-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="93616-109">Retorna um enumerador para todos os métodos que pertencem a um determinado módulo NGen e que são embutidos no corpo de um determinado método.</span><span class="sxs-lookup"><span data-stu-id="93616-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="93616-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="93616-110">Requirements</span></span>  
 <span data-ttu-id="93616-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93616-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93616-112">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="93616-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="93616-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93616-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93616-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="93616-114">See also</span></span>

- [<span data-ttu-id="93616-115">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="93616-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
