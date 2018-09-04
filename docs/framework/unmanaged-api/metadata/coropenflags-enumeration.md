---
title: Enumeração CorOpenFlags
ms.date: 03/30/2017
api_name:
- CorOpenFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorOpenFlags
helpviewer_keywords:
- CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c08b1f6be41de63886115e5aed6bcad901658bb5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509214"
---
# <a name="coropenflags-enumeration"></a><span data-ttu-id="46d10-102">Enumeração CorOpenFlags</span><span class="sxs-lookup"><span data-stu-id="46d10-102">CorOpenFlags Enumeration</span></span>
<span data-ttu-id="46d10-103">Contém valores de sinalizadores que controlam o comportamento dos metadados ao abrir arquivos de manifesto.</span><span class="sxs-lookup"><span data-stu-id="46d10-103">Contains flag values that control metadata behavior upon opening manifest files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46d10-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="46d10-104">Syntax</span></span>  
  
```  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="46d10-105">Membros</span><span class="sxs-lookup"><span data-stu-id="46d10-105">Members</span></span>  
  
|<span data-ttu-id="46d10-106">Membro</span><span class="sxs-lookup"><span data-stu-id="46d10-106">Member</span></span>|<span data-ttu-id="46d10-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="46d10-107">Description</span></span>|  
|------------|-----------------|  
|`ofRead`|<span data-ttu-id="46d10-108">Indica se o arquivo deve ser aberto como somente leitura.</span><span class="sxs-lookup"><span data-stu-id="46d10-108">Indicates that the file should be opened for reading only.</span></span>|  
|`ofWrite`|<span data-ttu-id="46d10-109">Indica se o arquivo deve ser aberto para gravação.</span><span class="sxs-lookup"><span data-stu-id="46d10-109">Indicates that the file should be opened for writing.</span></span><br /><br /> <span data-ttu-id="46d10-110">Se você estiver usando o sinalizador `ofWrite` ao abrir um arquivo .winmd, deverá passar também o sinalizador `ofNoTransform`.</span><span class="sxs-lookup"><span data-stu-id="46d10-110">If you are using the `ofWrite` flag when opening a .winmd file, you should also pass the `ofNoTransform` flag.</span></span>|  
|`ofReadWriteMask`|<span data-ttu-id="46d10-111">Uma máscara para leitura e gravação.</span><span class="sxs-lookup"><span data-stu-id="46d10-111">A mask for reading and writing.</span></span>|  
|`ofCopyMemory`|<span data-ttu-id="46d10-112">Indica se o arquivo deve ser lido na memória.</span><span class="sxs-lookup"><span data-stu-id="46d10-112">Indicates that the file should be read into memory.</span></span> <span data-ttu-id="46d10-113">Os metadados devem manter sua própria cópia.</span><span class="sxs-lookup"><span data-stu-id="46d10-113">Metadata should maintain its own copy.</span></span>|  
|`ofCacheImage`|<span data-ttu-id="46d10-114">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="46d10-114">Obsolete.</span></span> <span data-ttu-id="46d10-115">Este sinalizador é ignorado.</span><span class="sxs-lookup"><span data-stu-id="46d10-115">This flag is ignored.</span></span>|  
|`ofManifestMetadata`|<span data-ttu-id="46d10-116">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="46d10-116">Obsolete.</span></span> <span data-ttu-id="46d10-117">Este sinalizador é ignorado.</span><span class="sxs-lookup"><span data-stu-id="46d10-117">This flag is ignored.</span></span>|  
|`ofReadOnly`|<span data-ttu-id="46d10-118">Indica se o arquivo deve ser aberto para leitura e se uma chamada para `QueryInterface` para um [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) não pode ser feita.</span><span class="sxs-lookup"><span data-stu-id="46d10-118">Indicates that the file should be opened for reading, and that a call to `QueryInterface` for an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) cannot be made.</span></span>|  
|`ofTakeOwnership`|<span data-ttu-id="46d10-119">Indica que a memória foi alocada usando uma chamada para [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) e será liberada pelos metadados.</span><span class="sxs-lookup"><span data-stu-id="46d10-119">Indicates that the memory was allocated using a call to [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) and will be freed by the metadata.</span></span>|  
|`ofNoTypeLib`|<span data-ttu-id="46d10-120">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="46d10-120">Obsolete.</span></span> <span data-ttu-id="46d10-121">Este sinalizador é ignorado.</span><span class="sxs-lookup"><span data-stu-id="46d10-121">This flag is ignored.</span></span>|  
|`ofNoTransform`|<span data-ttu-id="46d10-122">Indica se as transformações automáticas de arquivos .winmd devem ser desabilitadas.</span><span class="sxs-lookup"><span data-stu-id="46d10-122">Indicates that automatic transforms of .winmd files should be disabled.</span></span> <span data-ttu-id="46d10-123">Em outras palavras, a projeção de um tipo de Tempo de Execução do Windows para um tipo de .NET Framework deve ser desabilitada.</span><span class="sxs-lookup"><span data-stu-id="46d10-123">In other words, the projection of a Windows Runtime type to a .NET Framework type should be disabled.</span></span> <span data-ttu-id="46d10-124">Para obter mais informações, consulte [sob o escopo com o .NET e o tempo de execução do Windows](https://msdn.microsoft.com/magazine/jj651569.aspx).</span><span class="sxs-lookup"><span data-stu-id="46d10-124">For more information, see [Underneath the Hood with .NET and the Windows Runtime](https://msdn.microsoft.com/magazine/jj651569.aspx).</span></span>|  
|`ofReserved1`|<span data-ttu-id="46d10-125">Reservado para uso interno.</span><span class="sxs-lookup"><span data-stu-id="46d10-125">Reserved for internal use.</span></span>|  
|`ofReserved2`|<span data-ttu-id="46d10-126">Reservado para uso interno.</span><span class="sxs-lookup"><span data-stu-id="46d10-126">Reserved for internal use.</span></span>|  
|`ofReserved`|<span data-ttu-id="46d10-127">Reservado para uso interno.</span><span class="sxs-lookup"><span data-stu-id="46d10-127">Reserved for internal use.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="46d10-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="46d10-128">Requirements</span></span>  
 <span data-ttu-id="46d10-129">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46d10-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46d10-130">**Cabeçalho:** corhdr. H</span><span class="sxs-lookup"><span data-stu-id="46d10-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="46d10-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46d10-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46d10-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46d10-132">See Also</span></span>  
 [<span data-ttu-id="46d10-133">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="46d10-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
