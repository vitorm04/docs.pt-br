---
title: Estrutura ASSEMBLYMETADATA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASSEMBLYMETADATA
api_location: mscoree.dll
api_type: COM
f1_keywords: ASSEMBLYMETADATA
helpviewer_keywords: ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 819510c14bd67e7fcc739a19ea945f16b2a66c9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="3f9b2-102">Estrutura ASSEMBLYMETADATA</span><span class="sxs-lookup"><span data-stu-id="3f9b2-102">ASSEMBLYMETADATA Structure</span></span>
<span data-ttu-id="3f9b2-103">Contém informações sobre o assembly referenciado, inclusive sua versão e seu nível de suporte para localidades, processadores e sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f9b2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3f9b2-104">Syntax</span></span>  
  
```  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a><span data-ttu-id="3f9b2-105">Membros</span><span class="sxs-lookup"><span data-stu-id="3f9b2-105">Members</span></span>  
  
|<span data-ttu-id="3f9b2-106">Membro</span><span class="sxs-lookup"><span data-stu-id="3f9b2-106">Member</span></span>|<span data-ttu-id="3f9b2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3f9b2-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="3f9b2-108">O número de versão principal do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="3f9b2-109">Esse valor não pode ser zero.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-109">This value cannot be zero.</span></span> <span data-ttu-id="3f9b2-110">Se todos os bits de `usMajorVersion` estão configurados, a versão principal não for especificada.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="3f9b2-111">O número de versão secundária do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="3f9b2-112">Esse valor não pode ser zero.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-112">This value cannot be zero.</span></span> <span data-ttu-id="3f9b2-113">Se todos os bits de `usMinorVersion` estão configurados, a versão secundária não está especificada.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="3f9b2-114">O número de compilação do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="3f9b2-115">Esse valor não pode ser zero.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-115">This value cannot be zero.</span></span> <span data-ttu-id="3f9b2-116">Se todos os bits de `usBuildNumber` estão configurados, o número de compilação não é especificado.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="3f9b2-117">O número de revisão do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="3f9b2-118">Esse valor não pode ser zero.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-118">This value cannot be zero.</span></span> <span data-ttu-id="3f9b2-119">Se todos os bits de `usRevisionNumber` estão configurados, o número de revisão não for especificado.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="3f9b2-120">Uma lista de nomes de localidades em conformidade com a especificação RFC1766, separada por ponto e vírgula, especificando as localidades com suporte pelo assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="3f9b2-121">Um valor nulo indica independência de localidade.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-121">A null value indicates locale independence.</span></span> <span data-ttu-id="3f9b2-122">**Observação:** no .NET Framework versão 1.0 não é possível especificar mais de uma localidade.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="3f9b2-123">O tamanho em caracteres largos de `szLocale`.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="3f9b2-124">Uma matriz de identificadores, conforme definido em Winnt. h, para os tipos de processador que são suportados pelo assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="3f9b2-125">Um valor NULL indica independência de processador.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="3f9b2-126">O comprimento do `rdwProcessor` matriz.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="3f9b2-127">Uma matriz de [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instâncias especificando os sistemas operacionais que têm suporte para o assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-127">An array of [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="3f9b2-128">Um valor NULL indica independência de sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="3f9b2-129">O comprimento do `rOS` matriz.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f9b2-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3f9b2-130">Requirements</span></span>  
 <span data-ttu-id="3f9b2-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f9b2-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f9b2-132">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3f9b2-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f9b2-133">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="3f9b2-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f9b2-134">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f9b2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f9b2-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f9b2-135">See Also</span></span>  
 [<span data-ttu-id="3f9b2-136">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="3f9b2-136">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="3f9b2-137">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="3f9b2-137">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="3f9b2-138">Estrutura OSINFO</span><span class="sxs-lookup"><span data-stu-id="3f9b2-138">OSINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
