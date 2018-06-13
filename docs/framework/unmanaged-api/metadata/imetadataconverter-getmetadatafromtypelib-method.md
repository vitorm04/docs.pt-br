---
title: Método IMetaDataConverter::GetMetaDataFromTypeLib
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeLib
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib
helpviewer_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib method [.NET Framework metadata]
- GetMetaDataFromTypeLib method [.NET Framework metadata]
ms.assetid: 97dc3a56-adfa-431f-889e-06a35ac84d51
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdd2aeb54e9d3c78c58b1a8b497839e876038dfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443633"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="f9819-102">Método IMetaDataConverter::GetMetaDataFromTypeLib</span><span class="sxs-lookup"><span data-stu-id="f9819-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="f9819-103">Obtém um ponteiro de interface para um [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instância que representa a assinatura de metadados do tipo de biblioteca representada pelo `ITypeLib` instância.</span><span class="sxs-lookup"><span data-stu-id="f9819-103">Gets an interface pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9819-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9819-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,   
    [out] IMetaDataImport **ppMDI  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9819-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f9819-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="f9819-106">[in] Ponteiro para uma `ITypeLib` objeto que representa a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="f9819-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="f9819-107">[out] Ponteiro para um local que recebe o endereço do `IMetaDataImport` instância que representa a assinatura de metadados.</span><span class="sxs-lookup"><span data-stu-id="f9819-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9819-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f9819-108">Requirements</span></span>  
 <span data-ttu-id="f9819-109">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9819-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9819-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f9819-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f9819-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f9819-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f9819-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9819-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9819-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9819-113">See Also</span></span>  
 [<span data-ttu-id="f9819-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f9819-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f9819-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="f9819-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
