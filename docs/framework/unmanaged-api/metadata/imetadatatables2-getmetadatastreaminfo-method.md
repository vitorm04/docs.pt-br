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
ms.openlocfilehash: 756b0ff726c31bf096a1c1b70004c3ff82fe9979
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450031"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="a9d67-102">Método IMetaDataTables2::GetMetaDataStreamInfo</span><span class="sxs-lookup"><span data-stu-id="a9d67-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>
<span data-ttu-id="a9d67-103">Obtém o nome, o tamanho e o conteúdo do fluxo de metadados no índice especificado.</span><span class="sxs-lookup"><span data-stu-id="a9d67-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9d67-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9d67-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9d67-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a9d67-105">Parameters</span></span>  
 `ix`  
 <span data-ttu-id="a9d67-106">[in] O índice do fluxo de metadados solicitada.</span><span class="sxs-lookup"><span data-stu-id="a9d67-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="a9d67-107">[out] Um ponteiro para o nome do fluxo.</span><span class="sxs-lookup"><span data-stu-id="a9d67-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="a9d67-108">[out] Um ponteiro para o fluxo de metadados.</span><span class="sxs-lookup"><span data-stu-id="a9d67-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="a9d67-109">[out] O tamanho, em bytes, de `ppv`.</span><span class="sxs-lookup"><span data-stu-id="a9d67-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9d67-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a9d67-110">Requirements</span></span>  
 <span data-ttu-id="a9d67-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9d67-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9d67-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a9d67-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9d67-113">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a9d67-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9d67-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9d67-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9d67-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9d67-115">See Also</span></span>  
 [<span data-ttu-id="a9d67-116">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="a9d67-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 [<span data-ttu-id="a9d67-117">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="a9d67-117">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
