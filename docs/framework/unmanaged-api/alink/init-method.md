---
title: Método Init
ms.date: 03/30/2017
api_name:
- IALink.Init
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- Init
helpviewer_keywords:
- Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 60602462376543fe934bb3c58bc4988fa8ab34bf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119360"
---
# <a name="init-method"></a><span data-ttu-id="10e7f-102">Método Init</span><span class="sxs-lookup"><span data-stu-id="10e7f-102">Init Method</span></span>
<span data-ttu-id="10e7f-103">Prepara os objetos que implementam o [IALink Interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) para uso.</span><span class="sxs-lookup"><span data-stu-id="10e7f-103">Prepares objects implementing the [IALink Interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10e7f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10e7f-104">Syntax</span></span>  
  
```  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="10e7f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="10e7f-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="10e7f-106">[IMetaDataDispenserEx Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) ponteiro para o repositório de metadados.</span><span class="sxs-lookup"><span data-stu-id="10e7f-106">[IMetaDataDispenserEx Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="10e7f-107">[IMetaDataError Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) ponteiro para uma interface de tratamento de erro opcional.</span><span class="sxs-lookup"><span data-stu-id="10e7f-107">[IMetaDataError Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10e7f-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="10e7f-108">Return Value</span></span>  
 <span data-ttu-id="10e7f-109">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="10e7f-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10e7f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="10e7f-110">Requirements</span></span>  
 <span data-ttu-id="10e7f-111">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="10e7f-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10e7f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10e7f-112">See also</span></span>

- [<span data-ttu-id="10e7f-113">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="10e7f-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="10e7f-114">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="10e7f-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="10e7f-115">API do ALink</span><span class="sxs-lookup"><span data-stu-id="10e7f-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
