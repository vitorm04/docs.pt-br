---
title: "Método ICLRMetadataLocator::GetMetadata"
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
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8758a96464d1465d92fb17314f1e36ab8d9169c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a><span data-ttu-id="2af51-102">Método ICLRMetadataLocator::GetMetadata</span><span class="sxs-lookup"><span data-stu-id="2af51-102">ICLRMetadataLocator::GetMetadata Method</span></span>
<span data-ttu-id="2af51-103">Chamado o common language runtime (CLR) acesso serviços de dados para recuperar os metadados de uma imagem.</span><span class="sxs-lookup"><span data-stu-id="2af51-103">Called by the common language runtime (CLR) data access services to retrieve the metadata of an image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2af51-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2af51-104">Syntax</span></span>  
  
```  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2af51-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2af51-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="2af51-106">[in] Uma cadeia de caracteres que especifica o caminho do arquivo de imagem.</span><span class="sxs-lookup"><span data-stu-id="2af51-106">[in] A string that specifies the path of the image file.</span></span>  
  
 `imageTimestamp`  
 <span data-ttu-id="2af51-107">[in] O carimbo de hora do arquivo de imagem.</span><span class="sxs-lookup"><span data-stu-id="2af51-107">[in] The time stamp of the image file.</span></span>  
  
 `imageSize`  
 <span data-ttu-id="2af51-108">[in] O tamanho do arquivo de imagem.</span><span class="sxs-lookup"><span data-stu-id="2af51-108">[in] The size of the image file.</span></span>  
  
 `mvid`  
 <span data-ttu-id="2af51-109">[in] O identificador global exclusivo da imagem.</span><span class="sxs-lookup"><span data-stu-id="2af51-109">[in] The globally unique identifier of the image.</span></span>  
  
 `mdRva`  
 <span data-ttu-id="2af51-110">[in] O virtual endereço relativo (RVA) dos metadados.</span><span class="sxs-lookup"><span data-stu-id="2af51-110">[in] The relative virtual address (RVA) of the metadata.</span></span> <span data-ttu-id="2af51-111">O endereço é relativo ao endereço de base de imagem.</span><span class="sxs-lookup"><span data-stu-id="2af51-111">The address is relative to the image base address.</span></span>  
  
 `flags`  
 <span data-ttu-id="2af51-112">[in] Reservado para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="2af51-112">[in] Reserved for future use.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="2af51-113">[in] O tamanho do buffer no qual os metadados.</span><span class="sxs-lookup"><span data-stu-id="2af51-113">[in] The size of the buffer in which to place the metadata.</span></span>  
  
 `buffer`  
 <span data-ttu-id="2af51-114">[out] O buffer no qual os metadados.</span><span class="sxs-lookup"><span data-stu-id="2af51-114">[out] The buffer in which to place the metadata.</span></span>  
  
 `dataSize`  
 <span data-ttu-id="2af51-115">[out] O tamanho dos metadados que é retornado.</span><span class="sxs-lookup"><span data-stu-id="2af51-115">[out] The size of the metadata that is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2af51-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="2af51-116">Remarks</span></span>  
 <span data-ttu-id="2af51-117">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="2af51-117">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2af51-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2af51-118">Requirements</span></span>  
 <span data-ttu-id="2af51-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2af51-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2af51-120">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="2af51-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2af51-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2af51-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2af51-122">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2af51-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2af51-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2af51-123">See Also</span></span>  
 [<span data-ttu-id="2af51-124">Interface ICLRMetadataLocator</span><span class="sxs-lookup"><span data-stu-id="2af51-124">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
