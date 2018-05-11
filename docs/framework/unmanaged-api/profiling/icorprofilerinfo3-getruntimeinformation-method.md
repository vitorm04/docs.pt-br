---
title: Método ICorProfilerInfo3::GetRuntimeInformation
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67e1d20f7faf38fa37083f1a5b1cc0c1060b7a32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="796df-102">Método ICorProfilerInfo3::GetRuntimeInformation</span><span class="sxs-lookup"><span data-stu-id="796df-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="796df-103">Fornece informações de versão sobre o common language runtime (CLR) que está sendo analisado.</span><span class="sxs-lookup"><span data-stu-id="796df-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="796df-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="796df-104">Syntax</span></span>  
  
```  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="796df-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="796df-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="796df-106">[out] A ID do representante de uma instância do CLR em execução em um processo.</span><span class="sxs-lookup"><span data-stu-id="796df-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="796df-107">Isso é o mesmo que o `ClrInstanceID` que informa que o rastreamento de eventos do evento de inicialização do Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="796df-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="796df-108">[out] O tipo de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="796df-108">[out] The runtime type.</span></span> <span data-ttu-id="796df-109">Este parâmetro retorna `COR_PRF_DESKTOP_CLR` para a versão da área de trabalho do CLR, ou `COR_PRF_CORE_CLR` para a versão principal do CLR usado no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="796df-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="796df-110">[out] O número de versão principal do CLR.</span><span class="sxs-lookup"><span data-stu-id="796df-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="796df-111">[out] O número de versão secundária do CLR.</span><span class="sxs-lookup"><span data-stu-id="796df-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="796df-112">[out] O número de versão de compilação do CLR.</span><span class="sxs-lookup"><span data-stu-id="796df-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="796df-113">[out] O número de versão do CLR que está associado uma atualização de software.</span><span class="sxs-lookup"><span data-stu-id="796df-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="796df-114">[in] O comprimento, em caracteres, do buffer que `szVersionString` aponta para.</span><span class="sxs-lookup"><span data-stu-id="796df-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="796df-115">[out] O comprimento, em caracteres, de `szVersionString`.</span><span class="sxs-lookup"><span data-stu-id="796df-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="796df-116">[out] A cadeia de caracteres de versão do CLR.</span><span class="sxs-lookup"><span data-stu-id="796df-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="796df-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="796df-117">Remarks</span></span>  
 <span data-ttu-id="796df-118">Você pode passar null para qualquer parâmetro.</span><span class="sxs-lookup"><span data-stu-id="796df-118">You may pass null for any parameter.</span></span> <span data-ttu-id="796df-119">No entanto, `pcchVersionString` não pode ser nulo, a menos que `szVersionString` também será null.</span><span class="sxs-lookup"><span data-stu-id="796df-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="796df-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="796df-120">Requirements</span></span>  
 <span data-ttu-id="796df-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="796df-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="796df-122">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="796df-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="796df-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="796df-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="796df-124">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="796df-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="796df-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="796df-125">See Also</span></span>  
 [<span data-ttu-id="796df-126">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="796df-126">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="796df-127">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="796df-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="796df-128">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="796df-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
