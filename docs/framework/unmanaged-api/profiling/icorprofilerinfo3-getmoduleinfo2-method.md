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
ms.openlocfilehash: e2a4df262e076c960640977bea0d22be19802140
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449674"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a><span data-ttu-id="a8025-102">Método ICorProfilerInfo3::GetModuleInfo2</span><span class="sxs-lookup"><span data-stu-id="a8025-102">ICorProfilerInfo3::GetModuleInfo2 Method</span></span>
<span data-ttu-id="a8025-103">Dada uma ID de módulo, retorna o nome do arquivo do módulo, a ID do assembly pai do módulo e um bitmask que descreve as propriedades do módulo.</span><span class="sxs-lookup"><span data-stu-id="a8025-103">Given a module ID, returns the file name of the module, the ID of the module's parent assembly, and a bitmask that describes the properties of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8025-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8025-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="a8025-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a8025-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="a8025-106">no A ID do módulo para o qual as informações serão recuperadas.</span><span class="sxs-lookup"><span data-stu-id="a8025-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="a8025-107">fora O endereço base no qual o módulo é carregado.</span><span class="sxs-lookup"><span data-stu-id="a8025-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="a8025-108">no O comprimento, em caracteres, do `szName` buffer de retorno.</span><span class="sxs-lookup"><span data-stu-id="a8025-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="a8025-109">fora Um ponteiro para o comprimento total do caractere do nome de arquivo do módulo que é retornado.</span><span class="sxs-lookup"><span data-stu-id="a8025-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="a8025-110">fora Um buffer de caracteres largo fornecido pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="a8025-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="a8025-111">Quando o método retorna, esse buffer contém o nome do arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="a8025-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="a8025-112">fora Um ponteiro para a ID do assembly pai do módulo.</span><span class="sxs-lookup"><span data-stu-id="a8025-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
 `pdwModuleFlags`  
 <span data-ttu-id="a8025-113">fora Uma bitmask de valores da enumeração [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) que especificam as propriedades do módulo.</span><span class="sxs-lookup"><span data-stu-id="a8025-113">[out] A bitmask of values from the [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) enumeration that specify the properties of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8025-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8025-114">Remarks</span></span>  
 <span data-ttu-id="a8025-115">Para módulos dinâmicos, o parâmetro `szName` é o nome de metadados do módulo e o endereço base é 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="a8025-115">For dynamic modules, the `szName` parameter is the metadata name of the module, and the base address is 0 (zero).</span></span> <span data-ttu-id="a8025-116">O nome dos metadados é o valor na coluna nome da tabela de módulos dentro dos metadados.</span><span class="sxs-lookup"><span data-stu-id="a8025-116">The metadata name is the value in the Name column from the Module table inside metadata.</span></span> <span data-ttu-id="a8025-117">Isso também é exposto como a propriedade <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> para código gerenciado e como o parâmetro `szName` do método [IMetaDataImport:: GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) para o código de cliente de metadados não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a8025-117">This is also exposed as the <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> property to managed code, and as the `szName` parameter of the [IMetaDataImport::GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) method to unmanaged metadata client code.</span></span>  
  
 <span data-ttu-id="a8025-118">Embora o método `GetModuleInfo2` possa ser chamado assim que a ID do módulo existir, a ID do assembly pai não estará disponível até que o criador de perfil receba o retorno de chamada [ICorProfilerCallback:: ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a8025-118">Although the `GetModuleInfo2` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="a8025-119">Quando `GetModuleInfo2` retorna, você deve verificar se o buffer de `szName` era grande o suficiente para conter o nome de arquivo completo do módulo.</span><span class="sxs-lookup"><span data-stu-id="a8025-119">When `GetModuleInfo2` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="a8025-120">Para fazer isso, compare o valor que `pcchName` aponta com o valor do parâmetro `cchName`.</span><span class="sxs-lookup"><span data-stu-id="a8025-120">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="a8025-121">Se `pcchName` apontar para um valor maior que `cchName`, aloque um buffer de `szName` maior, atualize `cchName` com o tamanho novo, maior e chame `GetModuleInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="a8025-121">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo2` again.</span></span>  
  
 <span data-ttu-id="a8025-122">Como alternativa, você pode primeiro chamar `GetModuleInfo2` com um buffer de `szName` de comprimento zero para obter o tamanho de buffer correto.</span><span class="sxs-lookup"><span data-stu-id="a8025-122">Alternatively, you can first call `GetModuleInfo2` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="a8025-123">Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcchName` e chamar `GetModuleInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="a8025-123">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8025-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a8025-124">Requirements</span></span>  
 <span data-ttu-id="a8025-125">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8025-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8025-126">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a8025-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a8025-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8025-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8025-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8025-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8025-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8025-129">See also</span></span>

- [<span data-ttu-id="a8025-130">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="a8025-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="a8025-131">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="a8025-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="a8025-132">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="a8025-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
