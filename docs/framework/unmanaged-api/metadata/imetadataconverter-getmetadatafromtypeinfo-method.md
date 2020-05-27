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
ms.openlocfilehash: f9f3e3f196f74a7dea3c722925f1d03968688882
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008996"
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="0f674-102">Método IMetaDataConverter::GetMetaDataFromTypeInfo</span><span class="sxs-lookup"><span data-stu-id="0f674-102">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>
<span data-ttu-id="0f674-103">Obtém um ponteiro para uma instância de [IMetaDataImport](imetadataimport-interface.md) que representa a assinatura de metadados da biblioteca de tipos referenciada pela `ITypeInfo` instância especificada.</span><span class="sxs-lookup"><span data-stu-id="0f674-103">Gets a pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f674-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f674-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f674-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0f674-105">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="0f674-106">no Um ponteiro para um `ITypeInfo` objeto que se refere à biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="0f674-106">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="0f674-107">fora Um ponteiro para um local que recebe o endereço da `IMetaDataImport` instância que representa a assinatura de metadados.</span><span class="sxs-lookup"><span data-stu-id="0f674-107">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f674-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0f674-108">Requirements</span></span>  
 <span data-ttu-id="0f674-109">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f674-109">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f674-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0f674-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0f674-111">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0f674-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0f674-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f674-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f674-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="0f674-113">See also</span></span>

- [<span data-ttu-id="0f674-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="0f674-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="0f674-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="0f674-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
