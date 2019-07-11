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
ms.openlocfilehash: e7e060d2f72609b470dbd5060746a1458f5eed9d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782306"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="0fafc-102">Método IMetaDataImport::GetTypeSpecFromToken</span><span class="sxs-lookup"><span data-stu-id="0fafc-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="0fafc-103">Obtém a assinatura de metadados de binários da especificação do tipo representada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="0fafc-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fafc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0fafc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fafc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0fafc-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="0fafc-106">[in] O token de TypeSpec associado com a assinatura de metadados solicitada.</span><span class="sxs-lookup"><span data-stu-id="0fafc-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="0fafc-107">[out] Um ponteiro para a assinatura de metadados de binário.</span><span class="sxs-lookup"><span data-stu-id="0fafc-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="0fafc-108">[out] O tamanho, em bytes, da assinatura de metadados.</span><span class="sxs-lookup"><span data-stu-id="0fafc-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0fafc-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0fafc-109">Return Value</span></span>  
 <span data-ttu-id="0fafc-110">Um HRESULT que indica êxito ou falha.</span><span class="sxs-lookup"><span data-stu-id="0fafc-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="0fafc-111">Falhas podem ser testadas com a macro FAILED.</span><span class="sxs-lookup"><span data-stu-id="0fafc-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fafc-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0fafc-112">Requirements</span></span>  
 <span data-ttu-id="0fafc-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fafc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fafc-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0fafc-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0fafc-115">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0fafc-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0fafc-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fafc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fafc-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0fafc-117">See also</span></span>

- [<span data-ttu-id="0fafc-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="0fafc-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0fafc-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="0fafc-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
