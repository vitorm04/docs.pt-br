---
title: Método IMetaDataImport::GetTypeSpecFromToken
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeSpecFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 362cbe9ff19e74bafc73fde857d231185179efbe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079546"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="5cd67-102">Método IMetaDataImport::GetTypeSpecFromToken</span><span class="sxs-lookup"><span data-stu-id="5cd67-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="5cd67-103">Obtém a assinatura de metadados de binários da especificação do tipo representada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="5cd67-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cd67-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5cd67-104">Syntax</span></span>  
  
```  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cd67-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5cd67-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="5cd67-106">[in] O token de TypeSpec associado com a assinatura de metadados solicitada.</span><span class="sxs-lookup"><span data-stu-id="5cd67-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="5cd67-107">[out] Um ponteiro para a assinatura de metadados de binário.</span><span class="sxs-lookup"><span data-stu-id="5cd67-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="5cd67-108">[out] O tamanho, em bytes, da assinatura de metadados.</span><span class="sxs-lookup"><span data-stu-id="5cd67-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5cd67-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5cd67-109">Return Value</span></span>  
 <span data-ttu-id="5cd67-110">Um HRESULT que indica êxito ou falha.</span><span class="sxs-lookup"><span data-stu-id="5cd67-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="5cd67-111">Falhas podem ser testadas com a macro FAILED.</span><span class="sxs-lookup"><span data-stu-id="5cd67-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cd67-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5cd67-112">Requirements</span></span>  
 <span data-ttu-id="5cd67-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cd67-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cd67-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5cd67-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5cd67-115">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5cd67-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="5cd67-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="5cd67-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5cd67-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5cd67-117">See also</span></span>

- [<span data-ttu-id="5cd67-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="5cd67-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5cd67-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="5cd67-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
