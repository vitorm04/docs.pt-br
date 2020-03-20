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
ms.openlocfilehash: ef573eb9a572c27e685289b2740a55e898be2093
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177626"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="bad5a-102">Método IMetaDataConverter::GetTypeLibFromMetaData</span><span class="sxs-lookup"><span data-stu-id="bad5a-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="bad5a-103">Obtém um `ITypeLib` ponteiro para uma instância que representa a biblioteca de tipos que tem os nomes de biblioteca e módulo especificados.</span><span class="sxs-lookup"><span data-stu-id="bad5a-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bad5a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bad5a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,
    [in]  BSTR     strTlbName,
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bad5a-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="bad5a-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="bad5a-106">[em] O nome do módulo da biblioteca do tipo.</span><span class="sxs-lookup"><span data-stu-id="bad5a-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="bad5a-107">[em] O nome da biblioteca do tipo.</span><span class="sxs-lookup"><span data-stu-id="bad5a-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="bad5a-108">[fora] Um ponteiro para um local que `ITypeLib` recebe o endereço da instância que representa a biblioteca do tipo.</span><span class="sxs-lookup"><span data-stu-id="bad5a-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bad5a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bad5a-109">Requirements</span></span>  
 <span data-ttu-id="bad5a-110">**Plataforma:** Consulte [os requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bad5a-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bad5a-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bad5a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bad5a-112">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bad5a-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bad5a-113">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bad5a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bad5a-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="bad5a-114">See also</span></span>

- [<span data-ttu-id="bad5a-115">Interface IMetaDataConverter</span><span class="sxs-lookup"><span data-stu-id="bad5a-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
