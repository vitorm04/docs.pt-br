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
ms.openlocfilehash: 34b7cebfa063a3ad077b74a753fd37ba67ff53a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175311"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="d08dd-102">Método IMetaDataImport::GetTypeSpecFromToken</span><span class="sxs-lookup"><span data-stu-id="d08dd-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="d08dd-103">Obtém a assinatura binária de metadados da especificação do tipo representada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="d08dd-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d08dd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d08dd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (
   [in]  mdTypeSpec            typespec,
   [out] PCCOR_SIGNATURE       *ppvSig,
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d08dd-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="d08dd-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="d08dd-106">[em] O token TypeSpec associado à assinatura de metadados solicitada.</span><span class="sxs-lookup"><span data-stu-id="d08dd-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="d08dd-107">[fora] Um ponteiro para a assinatura binária de metadados.</span><span class="sxs-lookup"><span data-stu-id="d08dd-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="d08dd-108">[fora] O tamanho, em bytes, da assinatura de metadados.</span><span class="sxs-lookup"><span data-stu-id="d08dd-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d08dd-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d08dd-109">Return Value</span></span>  
 <span data-ttu-id="d08dd-110">Um HRESULT que indica sucesso ou fracasso.</span><span class="sxs-lookup"><span data-stu-id="d08dd-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="d08dd-111">As falhas podem ser testadas com a macro FAILED.</span><span class="sxs-lookup"><span data-stu-id="d08dd-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d08dd-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d08dd-112">Requirements</span></span>  
 <span data-ttu-id="d08dd-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d08dd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d08dd-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d08dd-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d08dd-115">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d08dd-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d08dd-116">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d08dd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d08dd-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="d08dd-117">See also</span></span>

- [<span data-ttu-id="d08dd-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="d08dd-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d08dd-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="d08dd-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
