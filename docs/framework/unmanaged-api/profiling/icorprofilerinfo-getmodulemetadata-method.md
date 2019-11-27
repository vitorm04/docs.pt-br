---
title: Método ICorProfilerInfo::GetModuleMetaData
ms.date: 03/30/2017
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
ms.openlocfilehash: c7bf8e3ebedb17a4536b604909434c3e004fc828
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439832"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="e288f-102">Método ICorProfilerInfo::GetModuleMetaData</span><span class="sxs-lookup"><span data-stu-id="e288f-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="e288f-103">Obtém uma instância de interface de metadados que mapeia para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="e288f-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e288f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e288f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e288f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e288f-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="e288f-106">no A ID do módulo para o qual a instância de interface será mapeada.</span><span class="sxs-lookup"><span data-stu-id="e288f-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="e288f-107">no Um valor da enumeração [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) que especifica o modo para abrir arquivos de manifesto.</span><span class="sxs-lookup"><span data-stu-id="e288f-107">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="e288f-108">Somente os bits `ofRead`, `ofWrite` e `ofNoTransform` são válidos.</span><span class="sxs-lookup"><span data-stu-id="e288f-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="e288f-109">no A ID de referência (GUID) da interface de metadados cuja instância será recuperada.</span><span class="sxs-lookup"><span data-stu-id="e288f-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="e288f-110">Consulte [interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) para obter uma lista das interfaces.</span><span class="sxs-lookup"><span data-stu-id="e288f-110">See [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="e288f-111">fora Um ponteiro para o endereço da instância da interface de metadados.</span><span class="sxs-lookup"><span data-stu-id="e288f-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e288f-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="e288f-112">Remarks</span></span>  
 <span data-ttu-id="e288f-113">Você pode solicitar que os metadados sejam abertos no modo de leitura/gravação, mas isso resultará em uma execução de metadados mais lenta do programa, pois as alterações feitas nos metadados não podem ser otimizadas como eram do compilador.</span><span class="sxs-lookup"><span data-stu-id="e288f-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="e288f-114">Alguns módulos (como módulos de recurso) não têm metadados.</span><span class="sxs-lookup"><span data-stu-id="e288f-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="e288f-115">Nesses casos, `GetModuleMetaData` retornará um valor HRESULT de S_FALSE e um nulo em \*`ppOut`.</span><span class="sxs-lookup"><span data-stu-id="e288f-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e288f-116">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e288f-116">Requirements</span></span>  
 <span data-ttu-id="e288f-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e288f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e288f-118">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e288f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e288f-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e288f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e288f-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e288f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e288f-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e288f-121">See also</span></span>

- [<span data-ttu-id="e288f-122">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="e288f-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
