---
title: "Método IMetaDataImport::GetTypeSpecFromToken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetTypeSpecFromToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10d4d9dcad2494410cc361617d5292c519b6dc00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="b40db-102">Método IMetaDataImport::GetTypeSpecFromToken</span><span class="sxs-lookup"><span data-stu-id="b40db-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="b40db-103">Obtém a assinatura de metadados binário da especificação de tipo representada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="b40db-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b40db-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b40db-104">Syntax</span></span>  
  
```  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b40db-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b40db-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="b40db-106">[in] O token TypeSpec associado à assinatura de metadados solicitada.</span><span class="sxs-lookup"><span data-stu-id="b40db-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="b40db-107">[out] Um ponteiro para a assinatura de metadados binário.</span><span class="sxs-lookup"><span data-stu-id="b40db-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="b40db-108">[out] O tamanho, em bytes, da assinatura de metadados.</span><span class="sxs-lookup"><span data-stu-id="b40db-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b40db-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b40db-109">Return Value</span></span>  
 <span data-ttu-id="b40db-110">Um HRESULT que indica êxito ou falha.</span><span class="sxs-lookup"><span data-stu-id="b40db-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="b40db-111">Falhas podem ser testadas com a macro falhou.</span><span class="sxs-lookup"><span data-stu-id="b40db-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b40db-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b40db-112">Requirements</span></span>  
 <span data-ttu-id="b40db-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b40db-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b40db-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b40db-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b40db-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b40db-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b40db-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b40db-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b40db-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b40db-117">See Also</span></span>  
 [<span data-ttu-id="b40db-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b40db-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b40db-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b40db-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
