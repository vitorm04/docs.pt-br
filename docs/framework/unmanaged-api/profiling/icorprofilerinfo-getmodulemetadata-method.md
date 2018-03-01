---
title: "Método ICorProfilerInfo::GetModuleMetaData"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6ad52460bcd6eb320e970cd0ce2078f2e93df353
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="78a92-102">Método ICorProfilerInfo::GetModuleMetaData</span><span class="sxs-lookup"><span data-stu-id="78a92-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="78a92-103">Obtém uma instância da interface de metadados que é mapeado para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="78a92-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78a92-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78a92-104">Syntax</span></span>  
  
```  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78a92-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="78a92-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="78a92-106">[in] A ID do módulo ao qual a instância da interface será mapeada.</span><span class="sxs-lookup"><span data-stu-id="78a92-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="78a92-107">[in] Um valor de [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeração que especifica o modo para abrir arquivos de manifesto.</span><span class="sxs-lookup"><span data-stu-id="78a92-107">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="78a92-108">Somente o `ofRead`, `ofWrite` e `ofNoTransform` bits são válidos.</span><span class="sxs-lookup"><span data-stu-id="78a92-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="78a92-109">[in] A referência de ID (GUID) da interface de metadados cuja instância será recuperada.</span><span class="sxs-lookup"><span data-stu-id="78a92-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="78a92-110">Consulte [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) para obter uma lista das interfaces.</span><span class="sxs-lookup"><span data-stu-id="78a92-110">See [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="78a92-111">[out] Um ponteiro para o endereço da instância de interface de metadados.</span><span class="sxs-lookup"><span data-stu-id="78a92-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78a92-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="78a92-112">Remarks</span></span>  
 <span data-ttu-id="78a92-113">Você pode solicitar os metadados a ser aberto no modo de leitura/gravação, mas isso resultará em execução mais lenta de metadados do programa, alterações feitas em metadados não podem ser otimizados como estavam do compilador.</span><span class="sxs-lookup"><span data-stu-id="78a92-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="78a92-114">Alguns módulos (por exemplo, os módulos de recurso) não tem nenhum metadado.</span><span class="sxs-lookup"><span data-stu-id="78a92-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="78a92-115">Nesses casos, `GetModuleMetaData` retornará um valor HRESULT S_FALSE e um valor nulo em \*`ppOut`.</span><span class="sxs-lookup"><span data-stu-id="78a92-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78a92-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="78a92-116">Requirements</span></span>  
 <span data-ttu-id="78a92-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78a92-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78a92-118">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="78a92-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="78a92-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78a92-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78a92-120">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78a92-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78a92-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78a92-121">See Also</span></span>  
 [<span data-ttu-id="78a92-122">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="78a92-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
