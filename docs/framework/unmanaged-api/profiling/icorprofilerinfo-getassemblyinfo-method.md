---
title: "Método ICorProfilerInfo::GetAssemblyInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetAssemblyInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d4eab4a4bfbf91fd86a3742600f3383a8d374905
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="3fd9d-102">Método ICorProfilerInfo::GetAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="3fd9d-102">ICorProfilerInfo::GetAssemblyInfo Method</span></span>
<span data-ttu-id="3fd9d-103">Aceita uma ID de assembly e retorna o nome do assembly e a ID do seu módulo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="3fd9d-103">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fd9d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3fd9d-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3fd9d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3fd9d-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="3fd9d-106">[in] O identificador do assembly.</span><span class="sxs-lookup"><span data-stu-id="3fd9d-106">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="3fd9d-107">[in] O comprimento, em caracteres, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="3fd9d-107">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3fd9d-108">[out] Um ponteiro para o total de caracteres do nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="3fd9d-108">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="3fd9d-109">[out] Um buffer de caractere largo fornecida pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="3fd9d-109">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="3fd9d-110">Quando a função retorna, ele conterá o nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="3fd9d-110">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="3fd9d-111">[out] Um ponteiro para a ID do domínio do aplicativo que contém o assembly.</span><span class="sxs-lookup"><span data-stu-id="3fd9d-111">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="3fd9d-112">[out] Um ponteiro para a ID do módulo de manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="3fd9d-112">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fd9d-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="3fd9d-113">Remarks</span></span>  
 <span data-ttu-id="3fd9d-114">Depois que este método retorna, você deve verificar se o `szName` buffer era grande o suficiente para conter o nome completo do assembly.</span><span class="sxs-lookup"><span data-stu-id="3fd9d-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="3fd9d-115">Para fazer isso, o valor de comparação que `pcchName` aponta para com o valor de `cchName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3fd9d-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="3fd9d-116">Se `pcchName` aponta para um valor que é maior do que `cchName`, alocar uma maior `szName` buffer, atualize `cchName` com o novo tamanho maior e chame `GetAssemblyInfo` novamente.</span><span class="sxs-lookup"><span data-stu-id="3fd9d-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="3fd9d-117">Como alternativa, você pode primeiro chamar `GetAssemblyInfo` com um comprimento zero `szName` buffer para obter o tamanho do buffer correto.</span><span class="sxs-lookup"><span data-stu-id="3fd9d-117">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="3fd9d-118">Em seguida, você pode ajustar o tamanho do buffer com base no valor retornado em `pcchName` e chame `GetAssemblyInfo` novamente.</span><span class="sxs-lookup"><span data-stu-id="3fd9d-118">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fd9d-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3fd9d-119">Requirements</span></span>  
 <span data-ttu-id="3fd9d-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fd9d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fd9d-121">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3fd9d-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3fd9d-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fd9d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fd9d-123">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fd9d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fd9d-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3fd9d-124">See Also</span></span>  
 [<span data-ttu-id="3fd9d-125">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="3fd9d-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="3fd9d-126">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="3fd9d-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="3fd9d-127">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="3fd9d-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
