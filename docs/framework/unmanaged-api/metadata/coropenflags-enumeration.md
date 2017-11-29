---
title: "Enumeração CorOpenFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorOpenFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorOpenFlags
helpviewer_keywords: CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c7599a4b85a166aedd7a2293b79699b3ef03d14d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="coropenflags-enumeration"></a><span data-ttu-id="ceab1-102">Enumeração CorOpenFlags</span><span class="sxs-lookup"><span data-stu-id="ceab1-102">CorOpenFlags Enumeration</span></span>
<span data-ttu-id="ceab1-103">Contém valores de sinalizadores que controlam o comportamento dos metadados ao abrir arquivos de manifesto.</span><span class="sxs-lookup"><span data-stu-id="ceab1-103">Contains flag values that control metadata behavior upon opening manifest files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceab1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ceab1-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ceab1-105">Membros</span><span class="sxs-lookup"><span data-stu-id="ceab1-105">Members</span></span>  
  
|<span data-ttu-id="ceab1-106">Membro</span><span class="sxs-lookup"><span data-stu-id="ceab1-106">Member</span></span>|<span data-ttu-id="ceab1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ceab1-107">Description</span></span>|  
|------------|-----------------|  
|`ofRead`|<span data-ttu-id="ceab1-108">Indica se o arquivo deve ser aberto como somente leitura.</span><span class="sxs-lookup"><span data-stu-id="ceab1-108">Indicates that the file should be opened for reading only.</span></span>|  
|`ofWrite`|<span data-ttu-id="ceab1-109">Indica se o arquivo deve ser aberto para gravação.</span><span class="sxs-lookup"><span data-stu-id="ceab1-109">Indicates that the file should be opened for writing.</span></span><br /><br /> <span data-ttu-id="ceab1-110">Se você estiver usando o sinalizador `ofWrite` ao abrir um arquivo .winmd, deverá passar também o sinalizador `ofNoTransform`.</span><span class="sxs-lookup"><span data-stu-id="ceab1-110">If you are using the `ofWrite` flag when opening a .winmd file, you should also pass the `ofNoTransform` flag.</span></span>|  
|`ofReadWriteMask`|<span data-ttu-id="ceab1-111">Uma máscara para leitura e gravação.</span><span class="sxs-lookup"><span data-stu-id="ceab1-111">A mask for reading and writing.</span></span>|  
|`ofCopyMemory`|<span data-ttu-id="ceab1-112">Indica se o arquivo deve ser lido na memória.</span><span class="sxs-lookup"><span data-stu-id="ceab1-112">Indicates that the file should be read into memory.</span></span> <span data-ttu-id="ceab1-113">Os metadados devem manter sua própria cópia.</span><span class="sxs-lookup"><span data-stu-id="ceab1-113">Metadata should maintain its own copy.</span></span>|  
|`ofCacheImage`|<span data-ttu-id="ceab1-114">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="ceab1-114">Obsolete.</span></span> <span data-ttu-id="ceab1-115">Este sinalizador é ignorado.</span><span class="sxs-lookup"><span data-stu-id="ceab1-115">This flag is ignored.</span></span>|  
|`ofManifestMetadata`|<span data-ttu-id="ceab1-116">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="ceab1-116">Obsolete.</span></span> <span data-ttu-id="ceab1-117">Este sinalizador é ignorado.</span><span class="sxs-lookup"><span data-stu-id="ceab1-117">This flag is ignored.</span></span>|  
|`ofReadOnly`|<span data-ttu-id="ceab1-118">Indica que o arquivo deve ser aberto para leitura e que uma chamada para `QueryInterface` para um [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) não podem ser feitas.</span><span class="sxs-lookup"><span data-stu-id="ceab1-118">Indicates that the file should be opened for reading, and that a call to `QueryInterface` for an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) cannot be made.</span></span>|  
|`ofTakeOwnership`|<span data-ttu-id="ceab1-119">Indica que a memória foi alocada usando uma chamada para [CoTaskMemAlloc](http://msdn.microsoft.com/en-us/c4cb588d-9482-4f90-a92e-75b604540d5c) e será liberado pelos metadados.</span><span class="sxs-lookup"><span data-stu-id="ceab1-119">Indicates that the memory was allocated using a call to [CoTaskMemAlloc](http://msdn.microsoft.com/en-us/c4cb588d-9482-4f90-a92e-75b604540d5c) and will be freed by the metadata.</span></span>|  
|`ofNoTypeLib`|<span data-ttu-id="ceab1-120">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="ceab1-120">Obsolete.</span></span> <span data-ttu-id="ceab1-121">Este sinalizador é ignorado.</span><span class="sxs-lookup"><span data-stu-id="ceab1-121">This flag is ignored.</span></span>|  
|`ofNoTransform`|<span data-ttu-id="ceab1-122">Indica se as transformações automáticas de arquivos .winmd devem ser desabilitadas.</span><span class="sxs-lookup"><span data-stu-id="ceab1-122">Indicates that automatic transforms of .winmd files should be disabled.</span></span> <span data-ttu-id="ceab1-123">Em outras palavras, a projeção de um tipo de Tempo de Execução do Windows para um tipo de .NET Framework deve ser desabilitada.</span><span class="sxs-lookup"><span data-stu-id="ceab1-123">In other words, the projection of a Windows Runtime type to a .NET Framework type should be disabled.</span></span> <span data-ttu-id="ceab1-124">Para obter mais informações, consulte [sob o escopo com o .NET e o tempo de execução do Windows](http://msdn.microsoft.com/magazine/jj651569.aspx).</span><span class="sxs-lookup"><span data-stu-id="ceab1-124">For more information, see [Underneath the Hood with .NET and the Windows Runtime](http://msdn.microsoft.com/magazine/jj651569.aspx).</span></span>|  
|`ofReserved1`|<span data-ttu-id="ceab1-125">Reservado para uso interno.</span><span class="sxs-lookup"><span data-stu-id="ceab1-125">Reserved for internal use.</span></span>|  
|`ofReserved2`|<span data-ttu-id="ceab1-126">Reservado para uso interno.</span><span class="sxs-lookup"><span data-stu-id="ceab1-126">Reserved for internal use.</span></span>|  
|`ofReserved`|<span data-ttu-id="ceab1-127">Reservado para uso interno.</span><span class="sxs-lookup"><span data-stu-id="ceab1-127">Reserved for internal use.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ceab1-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ceab1-128">Requirements</span></span>  
 <span data-ttu-id="ceab1-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ceab1-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ceab1-130">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="ceab1-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ceab1-131">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ceab1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceab1-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ceab1-132">See Also</span></span>  
 [<span data-ttu-id="ceab1-133">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="ceab1-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
