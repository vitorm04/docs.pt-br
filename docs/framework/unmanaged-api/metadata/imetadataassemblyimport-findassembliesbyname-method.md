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
ms.openlocfilehash: d2693a94f02214df6d7265b26e3d70d91adcf8a7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503829"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="52f64-102">Método IMetaDataAssemblyImport::FindAssembliesByName</span><span class="sxs-lookup"><span data-stu-id="52f64-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="52f64-103">Obtém uma matriz de assemblies com o `szAssemblyName` parâmetro especificado, usando as regras padrão empregadas pelo Common Language Runtime (CLR) para resolver referências.</span><span class="sxs-lookup"><span data-stu-id="52f64-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52f64-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52f64-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="52f64-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="52f64-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="52f64-106">no O diretório raiz no qual Pesquisar o assembly fornecido.</span><span class="sxs-lookup"><span data-stu-id="52f64-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="52f64-107">Se esse valor for definido como `null` , o `FindAssembliesByName` irá procurar somente no cache de assembly global do assembly.</span><span class="sxs-lookup"><span data-stu-id="52f64-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="52f64-108">no Uma lista de subdiretórios delimitados por ponto-e-vírgula (por exemplo, "bin; BIN2"), sob o diretório raiz, no qual Pesquisar o assembly.</span><span class="sxs-lookup"><span data-stu-id="52f64-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="52f64-109">Esses diretórios são investigados além daqueles especificados nas regras de investigação padrão.</span><span class="sxs-lookup"><span data-stu-id="52f64-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="52f64-110">no O nome do assembly a ser localizado.</span><span class="sxs-lookup"><span data-stu-id="52f64-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="52f64-111">O formato dessa cadeia de caracteres é definido na página de referência de classe para <xref:System.Reflection.AssemblyName> .</span><span class="sxs-lookup"><span data-stu-id="52f64-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="52f64-112">no Uma matriz do tipo [IUnknown](/cpp/atl/iunknown) na qual colocar os `IMetadataAssemblyImport` ponteiros de interface.</span><span class="sxs-lookup"><span data-stu-id="52f64-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="52f64-113">fora O número máximo de ponteiros de interface que podem ser colocados em `ppIUnk` .</span><span class="sxs-lookup"><span data-stu-id="52f64-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="52f64-114">fora O número de ponteiros de interface retornados.</span><span class="sxs-lookup"><span data-stu-id="52f64-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="52f64-115">Ou seja, o número de ponteiros de interface inseridos na verdade `ppIUnk` .</span><span class="sxs-lookup"><span data-stu-id="52f64-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52f64-116">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="52f64-116">Return Value</span></span>  
  
|<span data-ttu-id="52f64-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="52f64-117">HRESULT</span></span>|<span data-ttu-id="52f64-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="52f64-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="52f64-119">`FindAssembliesByName`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="52f64-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="52f64-120">Não há assemblies.</span><span class="sxs-lookup"><span data-stu-id="52f64-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52f64-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="52f64-121">Remarks</span></span>  
 <span data-ttu-id="52f64-122">Dado um nome de assembly, o `FindAssembliesByName` método localiza o assembly seguindo as regras padrão para resolver referências de assembly.</span><span class="sxs-lookup"><span data-stu-id="52f64-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="52f64-123">(Para obter mais informações, consulte [como o tempo de execução localiza assemblies](../../deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName`permite que o chamador configure vários aspectos do contexto do resolvedor de assembly, como base do aplicativo e caminho de pesquisa particular.</span><span class="sxs-lookup"><span data-stu-id="52f64-123">(For more information, see [How the Runtime Locates Assemblies](../../deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="52f64-124">O `FindAssembliesByName` método requer que o CLR seja inicializado no processo para invocar a lógica de resolução do assembly.</span><span class="sxs-lookup"><span data-stu-id="52f64-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="52f64-125">Portanto, você deve chamar o [codeinitialize](../hosting/coinitializeee-function.md) (passando COINITEE_DEFAULT) antes de chamar `FindAssembliesByName` e, em seguida, seguir com uma chamada para [CoUninitializeCor](../hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="52f64-125">Therefore, you must call [CoInitializeEE](../hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="52f64-126">`FindAssembliesByName`Retorna um ponteiro [IMetaDataImport](imetadataimport-interface.md) para o arquivo que contém o manifesto do assembly para o nome do assembly que é passado.</span><span class="sxs-lookup"><span data-stu-id="52f64-126">`FindAssembliesByName` returns an [IMetaDataImport](imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="52f64-127">Se o nome do assembly fornecido não estiver totalmente especificado (por exemplo, se não incluir uma versão), vários assemblies poderão ser retornados.</span><span class="sxs-lookup"><span data-stu-id="52f64-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="52f64-128">`FindAssembliesByName`é comumente usado por um compilador que tenta localizar um assembly referenciado no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="52f64-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52f64-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="52f64-129">Requirements</span></span>  
 <span data-ttu-id="52f64-130">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52f64-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52f64-131">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="52f64-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="52f64-132">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="52f64-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="52f64-133">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52f64-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52f64-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="52f64-134">See also</span></span>

- [<span data-ttu-id="52f64-135">Como o runtime localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="52f64-135">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="52f64-136">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="52f64-136">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
