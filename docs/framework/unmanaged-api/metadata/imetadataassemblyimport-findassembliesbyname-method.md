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
ms.openlocfilehash: c0f81e3767d4ea3bc336203fbe8c914b4e2bd07b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177797"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="cf75c-102">Método IMetaDataAssemblyImport::FindAssembliesByName</span><span class="sxs-lookup"><span data-stu-id="cf75c-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="cf75c-103">Obtém uma matriz de conjuntos com o parâmetro especificado, `szAssemblyName` usando as regras padrão empregadas pelo tempo de execução da linguagem comum (CLR) para resolver referências.</span><span class="sxs-lookup"><span data-stu-id="cf75c-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf75c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf75c-104">Syntax</span></span>  
  
```cpp  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,
    [in]  LPCWSTR     szPrivateBin,
    [in]  LPCWSTR     szAssemblyName,
    [out] IUnknown    *ppIUnk[],
    [in]  ULONG       cMax,
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf75c-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="cf75c-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="cf75c-106">[em] O diretório raiz em que procurar a assembléia dada.</span><span class="sxs-lookup"><span data-stu-id="cf75c-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="cf75c-107">Se este valor `null`for `FindAssembliesByName` definido como , será olhar apenas no cache de montagem global para a montagem.</span><span class="sxs-lookup"><span data-stu-id="cf75c-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="cf75c-108">[em] Uma lista de subdiretórios delimitados por ponto e vírgula (por exemplo, bin;bin2), o diretório raiz, no qual procurar a montagem.</span><span class="sxs-lookup"><span data-stu-id="cf75c-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="cf75c-109">Esses diretórios são sondados além daqueles especificados nas regras de sondagem padrão.</span><span class="sxs-lookup"><span data-stu-id="cf75c-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="cf75c-110">[em] O nome da assembléia para encontrar.</span><span class="sxs-lookup"><span data-stu-id="cf75c-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="cf75c-111">O formato desta seqüência é definido <xref:System.Reflection.AssemblyName>na página de referência da classe para .</span><span class="sxs-lookup"><span data-stu-id="cf75c-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="cf75c-112">[em] Uma matriz do tipo [IUnknown](/cpp/atl/iunknown) `IMetadataAssemblyImport` para colocar os ponteiros de interface.</span><span class="sxs-lookup"><span data-stu-id="cf75c-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cf75c-113">[fora] O número máximo de ponteiros de `ppIUnk`interface que podem ser colocados em .</span><span class="sxs-lookup"><span data-stu-id="cf75c-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="cf75c-114">[fora] O número de ponteiros de interface retornou.</span><span class="sxs-lookup"><span data-stu-id="cf75c-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="cf75c-115">Ou seja, o número de ponteiros de interface realmente colocados em `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="cf75c-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf75c-116">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="cf75c-116">Return Value</span></span>  
  
|<span data-ttu-id="cf75c-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cf75c-117">HRESULT</span></span>|<span data-ttu-id="cf75c-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf75c-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="cf75c-119">`FindAssembliesByName`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="cf75c-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="cf75c-120">Não há assembléias.</span><span class="sxs-lookup"><span data-stu-id="cf75c-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf75c-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="cf75c-121">Remarks</span></span>  
 <span data-ttu-id="cf75c-122">Dado um nome `FindAssembliesByName` de montagem, o método encontra a montagem seguindo as regras padrão para resolver referências de montagem.</span><span class="sxs-lookup"><span data-stu-id="cf75c-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="cf75c-123">(Para obter mais informações, [consulte Como o Runtime localiza conjuntos](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` permite que o chamador configure vários aspectos do contexto de resolução de montagem, como base de aplicativo e caminho de pesquisa privado.</span><span class="sxs-lookup"><span data-stu-id="cf75c-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="cf75c-124">O `FindAssembliesByName` método exige que a CLR seja inicializada no processo, a fim de invocar a lógica de resolução da montagem.</span><span class="sxs-lookup"><span data-stu-id="cf75c-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="cf75c-125">Portanto, você deve ligar para [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) `FindAssembliesByName`(passando COINITEE_DEFAULT) antes de ligar e, em seguida, seguir com uma chamada para [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="cf75c-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="cf75c-126">`FindAssembliesByName`retorna um ponteiro [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) para o arquivo que contém o manifesto de montagem para o nome de montagem que é passado.</span><span class="sxs-lookup"><span data-stu-id="cf75c-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="cf75c-127">Se o nome de montagem dado não for totalmente especificado (por exemplo, se ele não incluir uma versão), vários conjuntos poderão ser retornados.</span><span class="sxs-lookup"><span data-stu-id="cf75c-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="cf75c-128">`FindAssembliesByName`é comumente usado por um compilador que tenta encontrar um conjunto referenciado no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="cf75c-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf75c-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cf75c-129">Requirements</span></span>  
 <span data-ttu-id="cf75c-130">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf75c-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf75c-131">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cf75c-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cf75c-132">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf75c-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cf75c-133">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf75c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf75c-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="cf75c-134">See also</span></span>

- [<span data-ttu-id="cf75c-135">Como o runtime localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="cf75c-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="cf75c-136">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="cf75c-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
