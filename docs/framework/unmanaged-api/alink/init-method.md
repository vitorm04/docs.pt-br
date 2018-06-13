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
ms.openlocfilehash: b512389078ab022208c4b163edc8501a900669ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400358"
---
# <a name="init-method"></a><span data-ttu-id="7f4fc-102">Método Init</span><span class="sxs-lookup"><span data-stu-id="7f4fc-102">Init Method</span></span>
<span data-ttu-id="7f4fc-103">Prepara os objetos que implementam o [IALink Interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) para uso.</span><span class="sxs-lookup"><span data-stu-id="7f4fc-103">Prepares objects implementing the [IALink Interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f4fc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f4fc-104">Syntax</span></span>  
  
```  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f4fc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7f4fc-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="7f4fc-106">[IMetaDataDispenserEx Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) ponteiro para o repositório de metadados.</span><span class="sxs-lookup"><span data-stu-id="7f4fc-106">[IMetaDataDispenserEx Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="7f4fc-107">[IMetaDataError Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) ponteiro para uma interface de tratamento de erros opcional.</span><span class="sxs-lookup"><span data-stu-id="7f4fc-107">[IMetaDataError Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f4fc-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7f4fc-108">Return Value</span></span>  
 <span data-ttu-id="7f4fc-109">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="7f4fc-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f4fc-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7f4fc-110">Requirements</span></span>  
 <span data-ttu-id="7f4fc-111">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="7f4fc-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f4fc-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f4fc-112">See Also</span></span>  
 [<span data-ttu-id="7f4fc-113">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="7f4fc-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="7f4fc-114">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="7f4fc-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="7f4fc-115">API do ALink</span><span class="sxs-lookup"><span data-stu-id="7f4fc-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
