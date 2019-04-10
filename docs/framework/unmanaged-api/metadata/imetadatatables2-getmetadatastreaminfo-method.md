---
title: Método IMetaDataTables2::GetMetaDataStreamInfo
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0f70187ba9bd71225162e6e10184e4992b5600f5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228842"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="af367-102">Método IMetaDataTables2::GetMetaDataStreamInfo</span><span class="sxs-lookup"><span data-stu-id="af367-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>
<span data-ttu-id="af367-103">Obtém o nome, o tamanho e o conteúdo do fluxo de metadados no índice especificado.</span><span class="sxs-lookup"><span data-stu-id="af367-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af367-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af367-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af367-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="af367-105">Parameters</span></span>  
 `ix`  
 <span data-ttu-id="af367-106">[in] O índice do fluxo de metadados solicitada.</span><span class="sxs-lookup"><span data-stu-id="af367-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="af367-107">[out] Um ponteiro para o nome do fluxo.</span><span class="sxs-lookup"><span data-stu-id="af367-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="af367-108">[out] Um ponteiro para o fluxo de metadados.</span><span class="sxs-lookup"><span data-stu-id="af367-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="af367-109">[out] O tamanho, em bytes, do `ppv`.</span><span class="sxs-lookup"><span data-stu-id="af367-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af367-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af367-110">Requirements</span></span>  
 <span data-ttu-id="af367-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af367-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af367-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="af367-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="af367-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="af367-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="af367-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="af367-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="af367-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af367-115">See also</span></span>

- [<span data-ttu-id="af367-116">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="af367-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [<span data-ttu-id="af367-117">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="af367-117">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
