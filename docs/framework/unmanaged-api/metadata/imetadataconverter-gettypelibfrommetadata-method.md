---
title: "Método IMetaDataConverter::GetTypeLibFromMetaData"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1e7665eabf46d4bda822dcb41125ccfcee6d8516
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="2c3a3-102">Método IMetaDataConverter::GetTypeLibFromMetaData</span><span class="sxs-lookup"><span data-stu-id="2c3a3-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="2c3a3-103">Obtém um ponteiro para um `ITypeLib` instância que representa a biblioteca de tipos que tem os nomes de biblioteca e o módulo especificados.</span><span class="sxs-lookup"><span data-stu-id="2c3a3-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c3a3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2c3a3-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c3a3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c3a3-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="2c3a3-106">[in] O nome do módulo da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="2c3a3-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="2c3a3-107">[in] O nome da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="2c3a3-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="2c3a3-108">[out] Um ponteiro para um local que recebe o endereço do `ITypeLib` instância que representa a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="2c3a3-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c3a3-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2c3a3-109">Requirements</span></span>  
 <span data-ttu-id="2c3a3-110">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c3a3-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c3a3-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2c3a3-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2c3a3-112">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="2c3a3-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2c3a3-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c3a3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c3a3-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c3a3-114">See Also</span></span>  
 [<span data-ttu-id="2c3a3-115">Interface IMetaDataConverter</span><span class="sxs-lookup"><span data-stu-id="2c3a3-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
