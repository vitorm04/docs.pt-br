---
title: Método IMetaDataConverter::GetTypeLibFromMetaData
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetTypeLibFromMetaData
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c0943971dc4858e2dce4d977f6f906b26f8ad51e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231000"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="cbecc-102">Método IMetaDataConverter::GetTypeLibFromMetaData</span><span class="sxs-lookup"><span data-stu-id="cbecc-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="cbecc-103">Obtém um ponteiro para um `ITypeLib` instância que representa a biblioteca de tipos que tem os nomes de biblioteca e o módulo especificados.</span><span class="sxs-lookup"><span data-stu-id="cbecc-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbecc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cbecc-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbecc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cbecc-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="cbecc-106">[in] O nome do módulo da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="cbecc-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="cbecc-107">[in] O nome da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="cbecc-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="cbecc-108">[out] Um ponteiro para um local que recebe o endereço do `ITypeLib` instância que representa a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="cbecc-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbecc-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cbecc-109">Requirements</span></span>  
 <span data-ttu-id="cbecc-110">**Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbecc-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbecc-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cbecc-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cbecc-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="cbecc-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cbecc-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbecc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbecc-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cbecc-114">See also</span></span>

- [<span data-ttu-id="cbecc-115">Interface IMetaDataConverter</span><span class="sxs-lookup"><span data-stu-id="cbecc-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
