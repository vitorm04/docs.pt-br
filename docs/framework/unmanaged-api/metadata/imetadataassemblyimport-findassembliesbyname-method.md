---
title: Método IMetaDataAssemblyImport::FindAssembliesByName
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindAssembliesByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b388dae0f109ff366f83c92de99b00b80bcc01a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108713"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="f1217-102">Método IMetaDataAssemblyImport::FindAssembliesByName</span><span class="sxs-lookup"><span data-stu-id="f1217-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="f1217-103">Obtém uma matriz de assemblies com especificado `szAssemblyName` parâmetro, usando as regras padrão empregadas pelo common language runtime (CLR) para resolver referências.</span><span class="sxs-lookup"><span data-stu-id="f1217-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1217-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1217-104">Syntax</span></span>  
  
```  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1217-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f1217-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="f1217-106">[in] O diretório raiz no qual pesquisar o assembly determinado.</span><span class="sxs-lookup"><span data-stu-id="f1217-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="f1217-107">Se esse valor é definido como `null`, `FindAssembliesByName` ficará apenas no cache de assembly global para o assembly.</span><span class="sxs-lookup"><span data-stu-id="f1217-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="f1217-108">[in] Uma lista de subdiretórios separados por ponto-e-vírgula (por exemplo, "bin; bin2"), sob o diretório raiz, no qual pesquisar o assembly.</span><span class="sxs-lookup"><span data-stu-id="f1217-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="f1217-109">Esses diretórios são investigados, além daqueles especificados nas regras de investigação de padrão.</span><span class="sxs-lookup"><span data-stu-id="f1217-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="f1217-110">[in] O nome do assembly para localizar.</span><span class="sxs-lookup"><span data-stu-id="f1217-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="f1217-111">O formato dessa cadeia de caracteres é definido na página de referência de classe para <xref:System.Reflection.AssemblyName>.</span><span class="sxs-lookup"><span data-stu-id="f1217-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="f1217-112">[in] Uma matriz do tipo [IUnknown](/cpp/atl/iunknown) na qual colocar o `IMetadataAssemblyImport` ponteiros de interface.</span><span class="sxs-lookup"><span data-stu-id="f1217-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f1217-113">[out] O número máximo de ponteiros de interface que pode ser colocado em `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="f1217-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="f1217-114">[out] O número de ponteiros de interface retornado.</span><span class="sxs-lookup"><span data-stu-id="f1217-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="f1217-115">Ou seja, o número de ponteiros de interface realmente colocados nos `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="f1217-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1217-116">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f1217-116">Return Value</span></span>  
  
|<span data-ttu-id="f1217-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f1217-117">HRESULT</span></span>|<span data-ttu-id="f1217-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1217-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f1217-119">`FindAssembliesByName` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f1217-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f1217-120">Não há nenhum assembly.</span><span class="sxs-lookup"><span data-stu-id="f1217-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1217-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1217-121">Remarks</span></span>  
 <span data-ttu-id="f1217-122">Recebe um nome de assembly, o `FindAssembliesByName` método encontra o assembly, seguindo as regras padrão para resolver referências de assembly.</span><span class="sxs-lookup"><span data-stu-id="f1217-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="f1217-123">(Para obter mais informações, consulte [como o tempo de execução Localiza Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` permite que o chamador configurar vários aspectos do contexto de resolvedor de assembly, como o caminho de pesquisa de base e privada de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f1217-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="f1217-124">O `FindAssembliesByName` método requer que o CLR a ser inicializado no processo para invocar a lógica de resolução de assembly.</span><span class="sxs-lookup"><span data-stu-id="f1217-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="f1217-125">Portanto, você deve chamar [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passando COINITEE_DEFAULT) antes de chamar `FindAssembliesByName`e, em seguida, execute com uma chamada para [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="f1217-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="f1217-126">`FindAssembliesByName` Retorna um [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) ponteiro para o arquivo que contém o manifesto do assembly para o nome do assembly que é passado.</span><span class="sxs-lookup"><span data-stu-id="f1217-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="f1217-127">Se o nome do assembly determinado não for totalmente especificado (por exemplo, se ele não inclui uma versão), vários assemblies podem ser retornados.</span><span class="sxs-lookup"><span data-stu-id="f1217-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="f1217-128">`FindAssembliesByName` é normalmente usado por um compilador que tenta localizar um assembly referenciado em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="f1217-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1217-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f1217-129">Requirements</span></span>  
 <span data-ttu-id="f1217-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1217-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1217-131">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f1217-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1217-132">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f1217-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f1217-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1217-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1217-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1217-134">See also</span></span>

- [<span data-ttu-id="f1217-135">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="f1217-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="f1217-136">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="f1217-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
