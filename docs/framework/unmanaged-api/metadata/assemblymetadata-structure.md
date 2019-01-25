---
title: Estrutura ASSEMBLYMETADATA
ms.date: 03/30/2017
api_name:
- ASSEMBLYMETADATA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ASSEMBLYMETADATA
helpviewer_keywords:
- ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f988f95c28e6d2248882fb033b8d8c4d3c629229
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744187"
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="f7e1e-102">Estrutura ASSEMBLYMETADATA</span><span class="sxs-lookup"><span data-stu-id="f7e1e-102">ASSEMBLYMETADATA Structure</span></span>
<span data-ttu-id="f7e1e-103">Contém informações sobre o assembly referenciado, inclusive sua versão e seu nível de suporte para as localidades, processadores e sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7e1e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7e1e-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="f7e1e-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f7e1e-105">Members</span></span>  
  
|<span data-ttu-id="f7e1e-106">Membro</span><span class="sxs-lookup"><span data-stu-id="f7e1e-106">Member</span></span>|<span data-ttu-id="f7e1e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7e1e-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="f7e1e-108">O número de versão principal do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="f7e1e-109">Esse valor não pode ser zero.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-109">This value cannot be zero.</span></span> <span data-ttu-id="f7e1e-110">Se todos os bits de `usMajorVersion` forem definidos, a versão principal não for especificada.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="f7e1e-111">O número de versão secundária do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="f7e1e-112">Esse valor não pode ser zero.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-112">This value cannot be zero.</span></span> <span data-ttu-id="f7e1e-113">Se todos os bits de `usMinorVersion` forem definidos, a versão secundária não for especificada.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="f7e1e-114">O número de build do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="f7e1e-115">Esse valor não pode ser zero.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-115">This value cannot be zero.</span></span> <span data-ttu-id="f7e1e-116">Se todos os bits de `usBuildNumber` forem definidos, o número de build não for especificado.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="f7e1e-117">O número de revisão do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="f7e1e-118">Esse valor não pode ser zero.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-118">This value cannot be zero.</span></span> <span data-ttu-id="f7e1e-119">Se todos os bits de `usRevisionNumber` forem definidos, o número de revisão não for especificado.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="f7e1e-120">Uma lista de nomes de localidades em conformidade com a especificação RFC1766, separada por ponto e vírgula, especificando as localidades com suporte no assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="f7e1e-121">Um valor nulo indica a independência de localidade.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-121">A null value indicates locale independence.</span></span> <span data-ttu-id="f7e1e-122">**Observação:**  No .NET Framework versão 1.0 não é possível especificar mais de uma localidade.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="f7e1e-123">O tamanho em caracteres largos da `szLocale`.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="f7e1e-124">Uma matriz de identificadores, conforme definido em Winnt. h, para os tipos de processador que são compatíveis com o assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="f7e1e-125">Um valor NULL indica a independência do processador.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="f7e1e-126">O comprimento da matriz `rdwProcessor`.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="f7e1e-127">Uma matriz de [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instâncias especificando os sistemas operacionais que são compatíveis com o assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-127">An array of [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="f7e1e-128">Um valor NULL indica a independência do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="f7e1e-129">O comprimento da matriz `rOS`.</span><span class="sxs-lookup"><span data-stu-id="f7e1e-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f7e1e-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f7e1e-130">Requirements</span></span>  
 <span data-ttu-id="f7e1e-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7e1e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7e1e-132">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f7e1e-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f7e1e-133">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f7e1e-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f7e1e-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7e1e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7e1e-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7e1e-135">See also</span></span>
- [<span data-ttu-id="f7e1e-136">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="f7e1e-136">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="f7e1e-137">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="f7e1e-137">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="f7e1e-138">Estrutura OSINFO</span><span class="sxs-lookup"><span data-stu-id="f7e1e-138">OSINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
