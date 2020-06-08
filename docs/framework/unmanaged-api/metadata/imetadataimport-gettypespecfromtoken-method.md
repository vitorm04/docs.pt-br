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
ms.openlocfilehash: 43e9671afa92d36966e51bbdc630db4a9d9083b7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503492"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="4990d-102">Método IMetaDataImport::GetTypeSpecFromToken</span><span class="sxs-lookup"><span data-stu-id="4990d-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="4990d-103">Obtém a assinatura de metadados binários da especificação de tipo representada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="4990d-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4990d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4990d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (
   [in]  mdTypeSpec            typespec,
   [out] PCCOR_SIGNATURE       *ppvSig,
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4990d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4990d-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="4990d-106">no O token TypeSpec associado à assinatura de metadados solicitada.</span><span class="sxs-lookup"><span data-stu-id="4990d-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="4990d-107">fora Um ponteiro para a assinatura de metadados binários.</span><span class="sxs-lookup"><span data-stu-id="4990d-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="4990d-108">fora O tamanho, em bytes, da assinatura de metadados.</span><span class="sxs-lookup"><span data-stu-id="4990d-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4990d-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="4990d-109">Return Value</span></span>  
 <span data-ttu-id="4990d-110">Um HRESULT que indica êxito ou falha.</span><span class="sxs-lookup"><span data-stu-id="4990d-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="4990d-111">As falhas podem ser testadas com a macro com falha.</span><span class="sxs-lookup"><span data-stu-id="4990d-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4990d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4990d-112">Requirements</span></span>  
 <span data-ttu-id="4990d-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4990d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4990d-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4990d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4990d-115">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4990d-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4990d-116">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4990d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4990d-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="4990d-117">See also</span></span>

- [<span data-ttu-id="4990d-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="4990d-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4990d-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="4990d-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
