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
ms.openlocfilehash: 55934ef08b10764bb705d7c166621ec7cfcadd0a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108506"
---
# <a name="coropenflags-enumeration"></a><span data-ttu-id="81e4c-102">Enumeração CorOpenFlags</span><span class="sxs-lookup"><span data-stu-id="81e4c-102">CorOpenFlags Enumeration</span></span>
<span data-ttu-id="81e4c-103">Contém valores de sinalizadores que controlam o comportamento dos metadados ao abrir arquivos de manifesto.</span><span class="sxs-lookup"><span data-stu-id="81e4c-103">Contains flag values that control metadata behavior upon opening manifest files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81e4c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81e4c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="81e4c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="81e4c-105">Members</span></span>  
  
|<span data-ttu-id="81e4c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="81e4c-106">Member</span></span>|<span data-ttu-id="81e4c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="81e4c-107">Description</span></span>|  
|------------|-----------------|  
|`ofRead`|<span data-ttu-id="81e4c-108">Indica se o arquivo deve ser aberto como somente leitura.</span><span class="sxs-lookup"><span data-stu-id="81e4c-108">Indicates that the file should be opened for reading only.</span></span>|  
|`ofWrite`|<span data-ttu-id="81e4c-109">Indica se o arquivo deve ser aberto para gravação.</span><span class="sxs-lookup"><span data-stu-id="81e4c-109">Indicates that the file should be opened for writing.</span></span><br /><br /> <span data-ttu-id="81e4c-110">Se você estiver usando o sinalizador `ofWrite` ao abrir um arquivo .winmd, deverá passar também o sinalizador `ofNoTransform`.</span><span class="sxs-lookup"><span data-stu-id="81e4c-110">If you are using the `ofWrite` flag when opening a .winmd file, you should also pass the `ofNoTransform` flag.</span></span>|  
|`ofReadWriteMask`|<span data-ttu-id="81e4c-111">Uma máscara para leitura e gravação.</span><span class="sxs-lookup"><span data-stu-id="81e4c-111">A mask for reading and writing.</span></span>|  
|`ofCopyMemory`|<span data-ttu-id="81e4c-112">Indica se o arquivo deve ser lido na memória.</span><span class="sxs-lookup"><span data-stu-id="81e4c-112">Indicates that the file should be read into memory.</span></span> <span data-ttu-id="81e4c-113">Os metadados devem manter sua própria cópia.</span><span class="sxs-lookup"><span data-stu-id="81e4c-113">Metadata should maintain its own copy.</span></span>|  
|`ofCacheImage`|<span data-ttu-id="81e4c-114">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="81e4c-114">Obsolete.</span></span> <span data-ttu-id="81e4c-115">Este sinalizador é ignorado.</span><span class="sxs-lookup"><span data-stu-id="81e4c-115">This flag is ignored.</span></span>|  
|`ofManifestMetadata`|<span data-ttu-id="81e4c-116">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="81e4c-116">Obsolete.</span></span> <span data-ttu-id="81e4c-117">Este sinalizador é ignorado.</span><span class="sxs-lookup"><span data-stu-id="81e4c-117">This flag is ignored.</span></span>|  
|`ofReadOnly`|<span data-ttu-id="81e4c-118">Indica se o arquivo deve ser aberto para leitura e se uma chamada para `QueryInterface` para um [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) não pode ser feita.</span><span class="sxs-lookup"><span data-stu-id="81e4c-118">Indicates that the file should be opened for reading, and that a call to `QueryInterface` for an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) cannot be made.</span></span>|  
|`ofTakeOwnership`|<span data-ttu-id="81e4c-119">Indica que a memória foi alocada usando uma chamada para [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) e será liberada pelos metadados.</span><span class="sxs-lookup"><span data-stu-id="81e4c-119">Indicates that the memory was allocated using a call to [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) and will be freed by the metadata.</span></span>|  
|`ofNoTypeLib`|<span data-ttu-id="81e4c-120">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="81e4c-120">Obsolete.</span></span> <span data-ttu-id="81e4c-121">Este sinalizador é ignorado.</span><span class="sxs-lookup"><span data-stu-id="81e4c-121">This flag is ignored.</span></span>|  
|`ofNoTransform`|<span data-ttu-id="81e4c-122">Indica se as transformações automáticas de arquivos .winmd devem ser desabilitadas.</span><span class="sxs-lookup"><span data-stu-id="81e4c-122">Indicates that automatic transforms of .winmd files should be disabled.</span></span> <span data-ttu-id="81e4c-123">Em outras palavras, a projeção de um tipo de Tempo de Execução do Windows para um tipo de .NET Framework deve ser desabilitada.</span><span class="sxs-lookup"><span data-stu-id="81e4c-123">In other words, the projection of a Windows Runtime type to a .NET Framework type should be disabled.</span></span> <span data-ttu-id="81e4c-124">Para obter mais informações, consulte [tempo de execução do Windows e o CLR - sob os bastidores com o .NET e o tempo de execução do Windows](https://msdn.microsoft.com/magazine/jj651569.aspx).</span><span class="sxs-lookup"><span data-stu-id="81e4c-124">For more information, see [Windows Runtime and the CLR - Underneath the Hood with .NET and the Windows Runtime](https://msdn.microsoft.com/magazine/jj651569.aspx).</span></span>|  
|`ofReserved1`|<span data-ttu-id="81e4c-125">Reservado para uso interno.</span><span class="sxs-lookup"><span data-stu-id="81e4c-125">Reserved for internal use.</span></span>|  
|`ofReserved2`|<span data-ttu-id="81e4c-126">Reservado para uso interno.</span><span class="sxs-lookup"><span data-stu-id="81e4c-126">Reserved for internal use.</span></span>|  
|`ofReserved`|<span data-ttu-id="81e4c-127">Reservado para uso interno.</span><span class="sxs-lookup"><span data-stu-id="81e4c-127">Reserved for internal use.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="81e4c-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81e4c-128">Requirements</span></span>  
 <span data-ttu-id="81e4c-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81e4c-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81e4c-130">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="81e4c-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="81e4c-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81e4c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e4c-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81e4c-132">See also</span></span>

- [<span data-ttu-id="81e4c-133">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="81e4c-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
