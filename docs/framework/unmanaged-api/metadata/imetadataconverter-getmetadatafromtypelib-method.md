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
ms.openlocfilehash: 8f8c0c2cb8dea8ad2b9c0040654122ef5942aca0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008385"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="92c3b-102">Método IMetaDataConverter::GetMetaDataFromTypeLib</span><span class="sxs-lookup"><span data-stu-id="92c3b-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="92c3b-103">Obtém um ponteiro de interface para uma instância de [IMetaDataImport](imetadataimport-interface.md) que representa a assinatura de metadados da biblioteca de tipos representada pela `ITypeLib` instância especificada.</span><span class="sxs-lookup"><span data-stu-id="92c3b-103">Gets an interface pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92c3b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92c3b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92c3b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="92c3b-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="92c3b-106">no Ponteiro para um `ITypeLib` objeto que representa a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="92c3b-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="92c3b-107">fora Ponteiro para um local que recebe o endereço da `IMetaDataImport` instância que representa a assinatura de metadados.</span><span class="sxs-lookup"><span data-stu-id="92c3b-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92c3b-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92c3b-108">Requirements</span></span>  
 <span data-ttu-id="92c3b-109">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92c3b-109">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92c3b-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="92c3b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="92c3b-111">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="92c3b-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="92c3b-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92c3b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92c3b-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="92c3b-113">See also</span></span>

- [<span data-ttu-id="92c3b-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="92c3b-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="92c3b-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="92c3b-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
