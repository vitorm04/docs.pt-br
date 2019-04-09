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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108713"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="29f7b-102">Método IMetaDataAssemblyImport::FindAssembliesByName</span><span class="sxs-lookup"><span data-stu-id="29f7b-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="29f7b-103">Obtém uma matriz de assemblies com especificado `szAssemblyName` parâmetro, usando as regras padrão empregadas pelo common language runtime (CLR) para resolver referências.</span><span class="sxs-lookup"><span data-stu-id="29f7b-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29f7b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29f7b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="29f7b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="29f7b-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="29f7b-106">[in] O diretório raiz no qual pesquisar o assembly determinado.</span><span class="sxs-lookup"><span data-stu-id="29f7b-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="29f7b-107">Se esse valor é definido como `null`, `FindAssembliesByName` ficará apenas no cache de assembly global para o assembly.</span><span class="sxs-lookup"><span data-stu-id="29f7b-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="29f7b-108">[in] Uma lista de subdiretórios separados por ponto-e-vírgula (por exemplo, "bin; bin2"), sob o diretório raiz, no qual pesquisar o assembly.</span><span class="sxs-lookup"><span data-stu-id="29f7b-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="29f7b-109">Esses diretórios são investigados, além daqueles especificados nas regras de investigação de padrão.</span><span class="sxs-lookup"><span data-stu-id="29f7b-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="29f7b-110">[in] O nome do assembly para localizar.</span><span class="sxs-lookup"><span data-stu-id="29f7b-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="29f7b-111">O formato dessa cadeia de caracteres é definido na página de referência de classe para <xref:System.Reflection.AssemblyName>.</span><span class="sxs-lookup"><span data-stu-id="29f7b-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="29f7b-112">[in] Uma matriz do tipo [IUnknown](/cpp/atl/iunknown) na qual colocar o `IMetadataAssemblyImport` ponteiros de interface.</span><span class="sxs-lookup"><span data-stu-id="29f7b-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="29f7b-113">[out] O número máximo de ponteiros de interface que pode ser colocado em `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="29f7b-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="29f7b-114">[out] O número de ponteiros de interface retornado.</span><span class="sxs-lookup"><span data-stu-id="29f7b-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="29f7b-115">Ou seja, o número de ponteiros de interface realmente colocados nos `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="29f7b-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29f7b-116">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="29f7b-116">Return Value</span></span>  
  
|<span data-ttu-id="29f7b-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29f7b-117">HRESULT</span></span>|<span data-ttu-id="29f7b-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="29f7b-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName` <span data-ttu-id="29f7b-119">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="29f7b-119">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="29f7b-120">Não há nenhum assembly.</span><span class="sxs-lookup"><span data-stu-id="29f7b-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29f7b-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="29f7b-121">Remarks</span></span>  
 <span data-ttu-id="29f7b-122">Recebe um nome de assembly, o `FindAssembliesByName` método encontra o assembly, seguindo as regras padrão para resolver referências de assembly.</span><span class="sxs-lookup"><span data-stu-id="29f7b-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="29f7b-123">(Para obter mais informações, consulte [como o tempo de execução Localiza Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` permite que o chamador configurar vários aspectos do contexto de resolvedor de assembly, como o caminho de pesquisa de base e privada de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="29f7b-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="29f7b-124">O `FindAssembliesByName` método requer que o CLR a ser inicializado no processo para invocar a lógica de resolução de assembly.</span><span class="sxs-lookup"><span data-stu-id="29f7b-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="29f7b-125">Portanto, você deve chamar [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passando COINITEE_DEFAULT) antes de chamar `FindAssembliesByName`e, em seguida, execute com uma chamada para [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="29f7b-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 `FindAssembliesByName` <span data-ttu-id="29f7b-126">Retorna um [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) ponteiro para o arquivo que contém o manifesto do assembly para o nome do assembly que é passado.</span><span class="sxs-lookup"><span data-stu-id="29f7b-126">returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="29f7b-127">Se o nome do assembly determinado não for totalmente especificado (por exemplo, se ele não inclui uma versão), vários assemblies podem ser retornados.</span><span class="sxs-lookup"><span data-stu-id="29f7b-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 `FindAssembliesByName` <span data-ttu-id="29f7b-128">é normalmente usado por um compilador que tenta localizar um assembly referenciado em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="29f7b-128">is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29f7b-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29f7b-129">Requirements</span></span>  
 <span data-ttu-id="29f7b-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29f7b-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29f7b-131">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="29f7b-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="29f7b-132">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="29f7b-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="29f7b-133">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="29f7b-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="29f7b-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29f7b-134">See also</span></span>

- [<span data-ttu-id="29f7b-135">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="29f7b-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="29f7b-136">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="29f7b-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
