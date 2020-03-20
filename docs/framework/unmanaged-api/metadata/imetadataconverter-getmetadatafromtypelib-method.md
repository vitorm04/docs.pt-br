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
ms.openlocfilehash: 09a1605deda5b51be604c3b8f0c69fa5adcf9dc0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175948"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="dbe83-102">Método IMetaDataConverter::GetMetaDataFromTypeLib</span><span class="sxs-lookup"><span data-stu-id="dbe83-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="dbe83-103">Obtém um ponteiro de interface para uma instância [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) que representa a `ITypeLib` assinatura de metadados da biblioteca de tipos representada pela instância especificada.</span><span class="sxs-lookup"><span data-stu-id="dbe83-103">Gets an interface pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbe83-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dbe83-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbe83-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="dbe83-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="dbe83-106">[em] Ponteiro para `ITypeLib` um objeto que representa a biblioteca do tipo.</span><span class="sxs-lookup"><span data-stu-id="dbe83-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="dbe83-107">[fora] Pointer para um local que `IMetaDataImport` recebe o endereço da instância que representa a assinatura de metadados.</span><span class="sxs-lookup"><span data-stu-id="dbe83-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbe83-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dbe83-108">Requirements</span></span>  
 <span data-ttu-id="dbe83-109">**Plataforma:** Consulte [os requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbe83-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbe83-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dbe83-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dbe83-111">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dbe83-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dbe83-112">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbe83-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbe83-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="dbe83-113">See also</span></span>

- [<span data-ttu-id="dbe83-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="dbe83-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="dbe83-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="dbe83-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
