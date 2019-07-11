---
title: Método ICLRMetadataLocator::GetMetadata
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 235b93f4176858372a83331730ddea8b97179cc8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738364"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a><span data-ttu-id="c2b9f-102">Método ICLRMetadataLocator::GetMetadata</span><span class="sxs-lookup"><span data-stu-id="c2b9f-102">ICLRMetadataLocator::GetMetadata Method</span></span>
<span data-ttu-id="c2b9f-103">Chamado pelo common language runtime (CLR) dados serviço de acesso para recuperar os metadados de uma imagem.</span><span class="sxs-lookup"><span data-stu-id="c2b9f-103">Called by the common language runtime (CLR) data access services to retrieve the metadata of an image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2b9f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2b9f-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="c2b9f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2b9f-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="c2b9f-106">[in] Uma cadeia de caracteres que especifica o caminho do arquivo de imagem.</span><span class="sxs-lookup"><span data-stu-id="c2b9f-106">[in] A string that specifies the path of the image file.</span></span>  
  
 `imageTimestamp`  
 <span data-ttu-id="c2b9f-107">[in] O carimbo de hora do arquivo de imagem.</span><span class="sxs-lookup"><span data-stu-id="c2b9f-107">[in] The time stamp of the image file.</span></span>  
  
 `imageSize`  
 <span data-ttu-id="c2b9f-108">[in] O tamanho do arquivo de imagem.</span><span class="sxs-lookup"><span data-stu-id="c2b9f-108">[in] The size of the image file.</span></span>  
  
 `mvid`  
 <span data-ttu-id="c2b9f-109">[in] O identificador global exclusivo da imagem.</span><span class="sxs-lookup"><span data-stu-id="c2b9f-109">[in] The globally unique identifier of the image.</span></span>  
  
 `mdRva`  
 <span data-ttu-id="c2b9f-110">[in] O endereço virtual relativo (RVA) dos metadados.</span><span class="sxs-lookup"><span data-stu-id="c2b9f-110">[in] The relative virtual address (RVA) of the metadata.</span></span> <span data-ttu-id="c2b9f-111">O endereço é relativo ao endereço de base de imagem.</span><span class="sxs-lookup"><span data-stu-id="c2b9f-111">The address is relative to the image base address.</span></span>  
  
 `flags`  
 <span data-ttu-id="c2b9f-112">[in] Reservado para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="c2b9f-112">[in] Reserved for future use.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="c2b9f-113">[in] O tamanho do buffer no qual colocar os metadados.</span><span class="sxs-lookup"><span data-stu-id="c2b9f-113">[in] The size of the buffer in which to place the metadata.</span></span>  
  
 `buffer`  
 <span data-ttu-id="c2b9f-114">[out] O buffer no qual colocar os metadados.</span><span class="sxs-lookup"><span data-stu-id="c2b9f-114">[out] The buffer in which to place the metadata.</span></span>  
  
 `dataSize`  
 <span data-ttu-id="c2b9f-115">[out] O tamanho dos metadados que é retornado.</span><span class="sxs-lookup"><span data-stu-id="c2b9f-115">[out] The size of the metadata that is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2b9f-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2b9f-116">Remarks</span></span>  
 <span data-ttu-id="c2b9f-117">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="c2b9f-117">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2b9f-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2b9f-118">Requirements</span></span>  
 <span data-ttu-id="c2b9f-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2b9f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2b9f-120">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="c2b9f-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c2b9f-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2b9f-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2b9f-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2b9f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2b9f-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2b9f-123">See also</span></span>

- [<span data-ttu-id="c2b9f-124">Interface ICLRMetadataLocator</span><span class="sxs-lookup"><span data-stu-id="c2b9f-124">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
