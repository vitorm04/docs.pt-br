---
title: "Enumeração AssemblyFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 605817ef23246f708b6cf46a93072cde3003ab43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="02902-102">Enumeração AssemblyFlags</span><span class="sxs-lookup"><span data-stu-id="02902-102">AssemblyFlags Enumeration</span></span>
<span data-ttu-id="02902-103">Contém valores que descrevem os recursos de tempo de execução de um assembly.</span><span class="sxs-lookup"><span data-stu-id="02902-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02902-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02902-104">Syntax</span></span>  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="02902-105">Membros</span><span class="sxs-lookup"><span data-stu-id="02902-105">Members</span></span>  
  
|<span data-ttu-id="02902-106">Membro</span><span class="sxs-lookup"><span data-stu-id="02902-106">Member</span></span>|<span data-ttu-id="02902-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="02902-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="02902-108">Especifica que as definições de tipo exportado implícitas dentro dos arquivos que compõem o assembly.</span><span class="sxs-lookup"><span data-stu-id="02902-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="02902-109">Nas versões do .NET Framework 1.0 e 1.1, esse valor é sempre devem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="02902-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="02902-110">Especifica que as definições de recursos são implícitas dentro dos arquivos que compõem o assembly.</span><span class="sxs-lookup"><span data-stu-id="02902-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="02902-111">No .NET Framework 1.0 e 1.1, esse valor é sempre devem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="02902-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="02902-112">Especifica que o assembly não é possível executar com outras versões se estiverem sendo executados no mesmo domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="02902-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="02902-113">Especifica que o assembly não é possível executar com outras versões se estiverem sendo executados no mesmo processo.</span><span class="sxs-lookup"><span data-stu-id="02902-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="02902-114">Especifica que o assembly não é possível executar com outras versões se estiverem sendo executados no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="02902-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02902-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="02902-115">Remarks</span></span>  
 <span data-ttu-id="02902-116">Os valores entre 0x0010 e 0x0070, inclusive, são usados para descrever os recursos de compatibilidade lado a lado do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="02902-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="02902-117">Se nenhum desses valores estiverem definidos, o assembly deve para ser compatível com o lado a lado.</span><span class="sxs-lookup"><span data-stu-id="02902-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02902-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="02902-118">Requirements</span></span>  
 <span data-ttu-id="02902-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02902-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02902-120">**Cabeçalho:** MsCorEE.h</span><span class="sxs-lookup"><span data-stu-id="02902-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="02902-121">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="02902-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="02902-122">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02902-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02902-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02902-123">See Also</span></span>  
 [<span data-ttu-id="02902-124">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="02902-124">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="02902-125">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="02902-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
