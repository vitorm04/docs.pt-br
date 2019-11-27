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
ms.openlocfilehash: 6391e819d53c3ed8f0d596b15c4a2bb268f72fd5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436275"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="0589b-102">Método IMetaDataConverter::GetMetaDataFromTypeLib</span><span class="sxs-lookup"><span data-stu-id="0589b-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="0589b-103">Obtém um ponteiro de interface para uma instância de [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) que representa a assinatura de metadados da biblioteca de tipos representada pela instância de `ITypeLib` especificada.</span><span class="sxs-lookup"><span data-stu-id="0589b-103">Gets an interface pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0589b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0589b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,   
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0589b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0589b-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="0589b-106">no Ponteiro para um objeto `ITypeLib` que representa a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="0589b-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="0589b-107">fora Ponteiro para um local que recebe o endereço da instância de `IMetaDataImport` que representa a assinatura de metadados.</span><span class="sxs-lookup"><span data-stu-id="0589b-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0589b-108">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="0589b-108">Requirements</span></span>  
 <span data-ttu-id="0589b-109">**Plataforma:** Consulte [requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0589b-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0589b-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0589b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0589b-111">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0589b-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0589b-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0589b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0589b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0589b-113">See also</span></span>

- [<span data-ttu-id="0589b-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="0589b-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="0589b-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="0589b-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
