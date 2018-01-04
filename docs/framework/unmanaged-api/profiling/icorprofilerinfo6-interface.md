---
title: Interface ICorProfilerInfo6
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfilerInfo6
api_location: mscorwks.dll
api_type: COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 805f1e451b2c13c356d904c42dff87304aa2093c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="fdcf1-102">Interface ICorProfilerInfo6</span><span class="sxs-lookup"><span data-stu-id="fdcf1-102">ICorProfilerInfo6 Interface</span></span>
<span data-ttu-id="fdcf1-103">[Com suporte no .NET Framework 4.6 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="fdcf1-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="fdcf1-104">Uma subclasse de [ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) que fornece um enumerador para todos os métodos que são definidos em um módulo especificado do NGen e embutido um determinado método.</span><span class="sxs-lookup"><span data-stu-id="fdcf1-104">A subclass of [ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fdcf1-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="fdcf1-105">Methods</span></span>  
  
|<span data-ttu-id="fdcf1-106">Método</span><span class="sxs-lookup"><span data-stu-id="fdcf1-106">Method</span></span>|<span data-ttu-id="fdcf1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdcf1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fdcf1-108">Método ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod</span><span class="sxs-lookup"><span data-stu-id="fdcf1-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="fdcf1-109">Retorna um enumerador para todos os métodos que pertencem a um módulo NGen especificado e que são embutida no corpo de um método específico.</span><span class="sxs-lookup"><span data-stu-id="fdcf1-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fdcf1-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fdcf1-110">Requirements</span></span>  
 <span data-ttu-id="fdcf1-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdcf1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdcf1-112">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fdcf1-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fdcf1-113">**Versões do .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdcf1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdcf1-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fdcf1-114">See Also</span></span>  
 [<span data-ttu-id="fdcf1-115">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="fdcf1-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
