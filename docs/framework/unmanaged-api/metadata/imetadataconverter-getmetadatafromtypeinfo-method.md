---
title: Método IMetaDataConverter::GetMetaDataFromTypeInfo
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeInfo
helpviewer_keywords:
- GetMetaDataFromTypeInfo method [.NET Framework metadata]
- IMetaDataConverter::GetMetaDataFromTypeInfo method [.NET Framework metadata]
ms.assetid: d44484bb-23a3-49c3-9e46-69d0d9ab4f0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b87bc814179b35f594ec8fab812055ff0182c5c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044480"
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="3a097-102">Método IMetaDataConverter::GetMetaDataFromTypeInfo</span><span class="sxs-lookup"><span data-stu-id="3a097-102">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>
<span data-ttu-id="3a097-103">Obtém um ponteiro para um [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instância que representa a assinatura de metadados da biblioteca de tipos referenciada pelo especificado `ITypeInfo` instância.</span><span class="sxs-lookup"><span data-stu-id="3a097-103">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a097-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a097-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a097-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3a097-105">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="3a097-106">[in] Um ponteiro para um `ITypeInfo` objeto que faz referência à biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="3a097-106">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="3a097-107">[out] Um ponteiro para um local que recebe o endereço do `IMetaDataImport` instância que representa a assinatura de metadados.</span><span class="sxs-lookup"><span data-stu-id="3a097-107">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a097-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a097-108">Requirements</span></span>  
 <span data-ttu-id="3a097-109">**Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a097-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a097-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3a097-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3a097-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3a097-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3a097-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a097-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a097-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a097-113">See also</span></span>

- [<span data-ttu-id="3a097-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="3a097-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3a097-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="3a097-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
