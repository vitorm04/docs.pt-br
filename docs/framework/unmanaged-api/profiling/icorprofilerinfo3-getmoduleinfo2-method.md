---
title: Método ICorProfilerInfo3::GetModuleInfo2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetModuleInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetModuleInfo2
helpviewer_keywords:
- ICorProfilerInfo3::GetModuleInfo2 method [.NET Framework profiling]
- GetModuleInfo2 method [.NET Framework profiling]
ms.assetid: f1f6b8f3-dcfc-49e8-be76-ea50ea90d5a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 188517104d4163ad1b391c2bab3bc41a2697e63d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478070"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a><span data-ttu-id="705e9-102">Método ICorProfilerInfo3::GetModuleInfo2</span><span class="sxs-lookup"><span data-stu-id="705e9-102">ICorProfilerInfo3::GetModuleInfo2 Method</span></span>
<span data-ttu-id="705e9-103">Dado um ID de módulo, retorna o nome do arquivo do módulo, a ID do pai do módulo de assembly e um bitmask que descreve as propriedades do módulo.</span><span class="sxs-lookup"><span data-stu-id="705e9-103">Given a module ID, returns the file name of the module, the ID of the module's parent assembly, and a bitmask that describes the properties of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="705e9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="705e9-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="705e9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="705e9-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="705e9-106">[in] A ID do módulo para o qual as informações serão recuperadas.</span><span class="sxs-lookup"><span data-stu-id="705e9-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="705e9-107">[out] O endereço básico no qual o módulo é carregado.</span><span class="sxs-lookup"><span data-stu-id="705e9-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="705e9-108">[in] O comprimento, em caracteres, da `szName` buffer de retorno.</span><span class="sxs-lookup"><span data-stu-id="705e9-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="705e9-109">[out] Um ponteiro para o total de caracteres do nome de arquivo do módulo que é retornado.</span><span class="sxs-lookup"><span data-stu-id="705e9-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="705e9-110">[out] Um buffer de caractere largo fornecido pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="705e9-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="705e9-111">Quando o método retorna, esse buffer contém o nome do arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="705e9-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="705e9-112">[out] Um ponteiro para a ID do assembly do pai do módulo.</span><span class="sxs-lookup"><span data-stu-id="705e9-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
 `pdwModuleFlags`  
 <span data-ttu-id="705e9-113">[out] Um bitmask de valores da [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) enumeração que especificam as propriedades do módulo.</span><span class="sxs-lookup"><span data-stu-id="705e9-113">[out] A bitmask of values from the [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) enumeration that specify the properties of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="705e9-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="705e9-114">Remarks</span></span>  
 <span data-ttu-id="705e9-115">Para módulos dinâmicos, o `szName` parâmetro é o nome de metadados do módulo e o endereço básico é 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="705e9-115">For dynamic modules, the `szName` parameter is the metadata name of the module, and the base address is 0 (zero).</span></span> <span data-ttu-id="705e9-116">O nome de metadados é o valor na coluna Nome da tabela de módulo dentro de metadados.</span><span class="sxs-lookup"><span data-stu-id="705e9-116">The metadata name is the value in the Name column from the Module table inside metadata.</span></span> <span data-ttu-id="705e9-117">Isso também é exposto como o <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> propriedade para o código gerenciado e como o `szName` parâmetro do [imetadataimport:: Getscopeprops](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) método ao código de cliente de metadados não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="705e9-117">This is also exposed as the <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> property to managed code, and as the `szName` parameter of the [IMetaDataImport::GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) method to unmanaged metadata client code.</span></span>  
  
 <span data-ttu-id="705e9-118">Embora o `GetModuleInfo2` método pode ser chamado assim que a ID do módulo existe, a ID do assembly pai não estarão disponível até que o criador de perfil recebe as [ICorProfilerCallback:: Moduleattachedtoassembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="705e9-118">Although the `GetModuleInfo2` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="705e9-119">Quando `GetModuleInfo2` é retornado, você deve verificar se o `szName` buffer era grande o suficiente para conter o nome completo do arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="705e9-119">When `GetModuleInfo2` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="705e9-120">Para fazer isso, o valor de comparação que `pcchName` aponta para com o valor da `cchName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="705e9-120">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="705e9-121">Se `pcchName` aponta para um valor maior que `cchName`, alocar uma maior `szName` buffer, atualize `cchName` com o novo e maior tamanho e a chamada `GetModuleInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="705e9-121">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo2` again.</span></span>  
  
 <span data-ttu-id="705e9-122">Como alternativa, você pode primeiro chamar `GetModuleInfo2` com um comprimento de zero `szName` buffer para obter o tamanho do buffer correto.</span><span class="sxs-lookup"><span data-stu-id="705e9-122">Alternatively, you can first call `GetModuleInfo2` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="705e9-123">Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcchName` e chamar `GetModuleInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="705e9-123">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="705e9-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="705e9-124">Requirements</span></span>  
 <span data-ttu-id="705e9-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="705e9-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="705e9-126">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="705e9-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="705e9-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="705e9-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="705e9-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="705e9-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="705e9-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="705e9-129">See also</span></span>
- [<span data-ttu-id="705e9-130">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="705e9-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="705e9-131">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="705e9-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="705e9-132">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="705e9-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
