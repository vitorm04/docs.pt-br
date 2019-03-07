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
ms.openlocfilehash: a8ecb529534f4ed1a1d12d9613ebd46f8b99fdb8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487493"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="a44ec-102">Método IMetaDataImport::GetTypeSpecFromToken</span><span class="sxs-lookup"><span data-stu-id="a44ec-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="a44ec-103">Obtém a assinatura de metadados de binários da especificação do tipo representada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="a44ec-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a44ec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a44ec-104">Syntax</span></span>  
  
```  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a44ec-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a44ec-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="a44ec-106">[in] O token de TypeSpec associado com a assinatura de metadados solicitada.</span><span class="sxs-lookup"><span data-stu-id="a44ec-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="a44ec-107">[out] Um ponteiro para a assinatura de metadados de binário.</span><span class="sxs-lookup"><span data-stu-id="a44ec-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="a44ec-108">[out] O tamanho, em bytes, da assinatura de metadados.</span><span class="sxs-lookup"><span data-stu-id="a44ec-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a44ec-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a44ec-109">Return Value</span></span>  
 <span data-ttu-id="a44ec-110">Um HRESULT que indica êxito ou falha.</span><span class="sxs-lookup"><span data-stu-id="a44ec-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="a44ec-111">Falhas podem ser testadas com a macro FAILED.</span><span class="sxs-lookup"><span data-stu-id="a44ec-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a44ec-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a44ec-112">Requirements</span></span>  
 <span data-ttu-id="a44ec-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a44ec-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a44ec-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a44ec-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a44ec-115">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a44ec-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a44ec-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a44ec-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a44ec-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a44ec-117">See also</span></span>
- [<span data-ttu-id="a44ec-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="a44ec-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a44ec-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="a44ec-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
