---
title: "Método IMetaDataAssemblyImport::FindAssembliesByName"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindAssembliesByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d6518fdcf1bef8eaea74818f69f46bb6df26e31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="0b5aa-102">Método IMetaDataAssemblyImport::FindAssembliesByName</span><span class="sxs-lookup"><span data-stu-id="0b5aa-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="0b5aa-103">Obtém uma matriz de assemblies com especificado `szAssemblyName` parâmetro, usando as regras padrão usadas pelo common language runtime (CLR) para resolver referências.</span><span class="sxs-lookup"><span data-stu-id="0b5aa-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b5aa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b5aa-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="0b5aa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b5aa-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="0b5aa-106">[in] O diretório raiz no qual procurar o assembly fornecido.</span><span class="sxs-lookup"><span data-stu-id="0b5aa-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="0b5aa-107">Se esse valor é definido como `null`, `FindAssembliesByName` parecerá apenas no cache de assembly global para o assembly.</span><span class="sxs-lookup"><span data-stu-id="0b5aa-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="0b5aa-108">[in] Uma lista de subdiretórios separados por ponto-e-vírgula (por exemplo, "bin; bin2"), no diretório raiz da pesquisa para o assembly.</span><span class="sxs-lookup"><span data-stu-id="0b5aa-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="0b5aa-109">Esses diretórios são investigados além daqueles especificados no padrão de regras de investigação.</span><span class="sxs-lookup"><span data-stu-id="0b5aa-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="0b5aa-110">[in] O nome do assembly para localizar.</span><span class="sxs-lookup"><span data-stu-id="0b5aa-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="0b5aa-111">O formato dessa cadeia de caracteres é definido na página de referência de classe para <xref:System.Reflection.AssemblyName>.</span><span class="sxs-lookup"><span data-stu-id="0b5aa-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="0b5aa-112">[in] Uma matriz do tipo <<!--zzxref:IUnknown --> `IUnknown`> na qual colocar o `IMetadataAssemblyImport` ponteiros de interface.</span><span class="sxs-lookup"><span data-stu-id="0b5aa-112">[in] An array of type <<!--zzxref:IUnknown --> `IUnknown`> in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0b5aa-113">[out] O número máximo de ponteiros de interface que pode ser colocado em `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="0b5aa-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="0b5aa-114">[out] O número de ponteiros de interface é retornado.</span><span class="sxs-lookup"><span data-stu-id="0b5aa-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="0b5aa-115">Ou seja, o número de ponteiros de interface, na verdade, colocados em `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="0b5aa-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b5aa-116">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0b5aa-116">Return Value</span></span>  
  
|<span data-ttu-id="0b5aa-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b5aa-117">HRESULT</span></span>|<span data-ttu-id="0b5aa-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b5aa-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0b5aa-119">`FindAssembliesByName`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="0b5aa-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0b5aa-120">Não há nenhum assembly.</span><span class="sxs-lookup"><span data-stu-id="0b5aa-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b5aa-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="0b5aa-121">Remarks</span></span>  
 <span data-ttu-id="0b5aa-122">Recebe um nome de assembly, o `FindAssembliesByName` método encontra o assembly, seguindo as regras padrão para resolver referências de assembly.</span><span class="sxs-lookup"><span data-stu-id="0b5aa-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="0b5aa-123">(Para obter mais informações, consulte [como o tempo de execução Localiza Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` permite que o chamador configurar vários aspectos do contexto de resolvedor de assembly, como caminho de pesquisa de base e privados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0b5aa-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="0b5aa-124">O `FindAssembliesByName` método requer que o CLR a ser inicializado no processo para invocar a lógica de resolução de assembly.</span><span class="sxs-lookup"><span data-stu-id="0b5aa-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="0b5aa-125">Portanto, você deve chamar [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passando COINITEE_DEFAULT) antes de chamar `FindAssembliesByName`e, em seguida, execute com uma chamada para [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="0b5aa-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="0b5aa-126">`FindAssembliesByName`Retorna um [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) ponteiro para o arquivo que contém o manifesto do assembly para o nome do assembly que é transmitido.</span><span class="sxs-lookup"><span data-stu-id="0b5aa-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="0b5aa-127">Se o nome do assembly fornecido não é totalmente especificado (por exemplo, se ele não inclui uma versão), vários assemblies podem ser retornados.</span><span class="sxs-lookup"><span data-stu-id="0b5aa-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="0b5aa-128">`FindAssembliesByName`é normalmente usado por um compilador que tenta localizar um assembly referenciado em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="0b5aa-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b5aa-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0b5aa-129">Requirements</span></span>  
 <span data-ttu-id="0b5aa-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b5aa-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b5aa-131">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0b5aa-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b5aa-132">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="0b5aa-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b5aa-133">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b5aa-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b5aa-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b5aa-134">See Also</span></span>  
 [<span data-ttu-id="0b5aa-135">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="0b5aa-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="0b5aa-136">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="0b5aa-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
