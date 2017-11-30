---
title: "Método ICorProfilerInfo3::GetModuleInfo2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetModuleInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetModuleInfo2
helpviewer_keywords:
- ICorProfilerInfo3::GetModuleInfo2 method [.NET Framework profiling]
- GetModuleInfo2 method [.NET Framework profiling]
ms.assetid: f1f6b8f3-dcfc-49e8-be76-ea50ea90d5a7
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4b891f55ab79d32814f44eabf50343aa113b0835
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a><span data-ttu-id="f86d1-102">Método ICorProfilerInfo3::GetModuleInfo2</span><span class="sxs-lookup"><span data-stu-id="f86d1-102">ICorProfilerInfo3::GetModuleInfo2 Method</span></span>
<span data-ttu-id="f86d1-103">Especificado um ID de módulo, retorna o nome do arquivo do módulo, a ID do pai do módulo assembly e uma máscara de bits que descreve as propriedades do módulo.</span><span class="sxs-lookup"><span data-stu-id="f86d1-103">Given a module ID, returns the file name of the module, the ID of the module's parent assembly, and a bitmask that describes the properties of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f86d1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f86d1-104">Syntax</span></span>  
  
```  
HRESULT GetModuleInfo2(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, annotation("__out_ecount_part(cchName, *pcchName)")]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
    [out] DWORD                 *pdwModuleFlags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f86d1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f86d1-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="f86d1-106">[in] A ID do módulo para o qual as informações serão recuperadas.</span><span class="sxs-lookup"><span data-stu-id="f86d1-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="f86d1-107">[out] O endereço base no qual o módulo é carregado.</span><span class="sxs-lookup"><span data-stu-id="f86d1-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="f86d1-108">[in] O comprimento, em caracteres, do `szName` buffer de retorno.</span><span class="sxs-lookup"><span data-stu-id="f86d1-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f86d1-109">[out] Um ponteiro para o total de caracteres do nome de arquivo do módulo que é retornado.</span><span class="sxs-lookup"><span data-stu-id="f86d1-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="f86d1-110">[out] Um buffer de caractere largo fornecida pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="f86d1-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="f86d1-111">Quando o método retorna, esse buffer contém o nome de arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="f86d1-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="f86d1-112">[out] Um ponteiro para a ID do assembly do pai do módulo.</span><span class="sxs-lookup"><span data-stu-id="f86d1-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
 `pdwModuleFlags`  
 <span data-ttu-id="f86d1-113">[out] Um bitmask de valores da [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) enumeração que especifica as propriedades do módulo.</span><span class="sxs-lookup"><span data-stu-id="f86d1-113">[out] A bitmask of values from the [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) enumeration that specify the properties of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f86d1-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="f86d1-114">Remarks</span></span>  
 <span data-ttu-id="f86d1-115">Para módulos dinâmicos, o `szName` parâmetro é o nome de metadados do módulo e o endereço base for 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="f86d1-115">For dynamic modules, the `szName` parameter is the metadata name of the module, and the base address is 0 (zero).</span></span> <span data-ttu-id="f86d1-116">O nome de metadados é o valor na coluna Nome da tabela de módulo dentro de metadados.</span><span class="sxs-lookup"><span data-stu-id="f86d1-116">The metadata name is the value in the Name column from the Module table inside metadata.</span></span> <span data-ttu-id="f86d1-117">Isso também é exposto como o <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> propriedade para código gerenciado e como o `szName` parâmetro o [: Getscopeprops](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) método ao código do cliente não gerenciado de metadados.</span><span class="sxs-lookup"><span data-stu-id="f86d1-117">This is also exposed as the <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> property to managed code, and as the `szName` parameter of the [IMetaDataImport::GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) method to unmanaged metadata client code.</span></span>  
  
 <span data-ttu-id="f86d1-118">Embora o `GetModuleInfo2` método pode ser chamado como ID do módulo existe, a ID do assembly pai não estarão disponível até que o criador de perfil recebe o [: Moduleattachedtoassembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="f86d1-118">Although the `GetModuleInfo2` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="f86d1-119">Quando `GetModuleInfo2` retorna, você deve verificar se o `szName` buffer era grande o suficiente para conter o nome completo do arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="f86d1-119">When `GetModuleInfo2` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="f86d1-120">Para fazer isso, o valor de comparação que `pcchName` aponta para com o valor de `cchName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f86d1-120">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="f86d1-121">Se `pcchName` aponta para um valor que é maior do que `cchName`, alocar uma maior `szName` buffer, atualize `cchName` com o novo tamanho maior e chame `GetModuleInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="f86d1-121">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo2` again.</span></span>  
  
 <span data-ttu-id="f86d1-122">Como alternativa, você pode primeiro chamar `GetModuleInfo2` com um comprimento zero `szName` buffer para obter o tamanho do buffer correto.</span><span class="sxs-lookup"><span data-stu-id="f86d1-122">Alternatively, you can first call `GetModuleInfo2` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="f86d1-123">Você pode definir o tamanho do buffer para o valor retornado em `pcchName` e chame `GetModuleInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="f86d1-123">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f86d1-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f86d1-124">Requirements</span></span>  
 <span data-ttu-id="f86d1-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f86d1-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f86d1-126">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f86d1-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f86d1-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f86d1-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f86d1-128">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f86d1-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f86d1-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f86d1-129">See Also</span></span>  
 [<span data-ttu-id="f86d1-130">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="f86d1-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="f86d1-131">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="f86d1-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="f86d1-132">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="f86d1-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
