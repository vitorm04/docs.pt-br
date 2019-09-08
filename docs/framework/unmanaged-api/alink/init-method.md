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
ms.openlocfilehash: bf96770dd58c9b84596c082a615f626ec723cc6c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787240"
---
# <a name="init-method"></a><span data-ttu-id="cebbb-102">Método Init</span><span class="sxs-lookup"><span data-stu-id="cebbb-102">Init Method</span></span>
<span data-ttu-id="cebbb-103">Prepara objetos que implementam a [interface IALink](ialink-interface.md) para uso.</span><span class="sxs-lookup"><span data-stu-id="cebbb-103">Prepares objects implementing the [IALink Interface](ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cebbb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cebbb-104">Syntax</span></span>  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="cebbb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cebbb-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="cebbb-106">Ponteiro de [interface IMetaDataDispenserEx](../metadata/imetadatadispenserex-interface.md) para o dispensador de metadados.</span><span class="sxs-lookup"><span data-stu-id="cebbb-106">[IMetaDataDispenserEx Interface](../metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="cebbb-107">Ponteiro de [interface IMetaDataError](../metadata/imetadataerror-interface.md) para uma interface de tratamento de erro opcional.</span><span class="sxs-lookup"><span data-stu-id="cebbb-107">[IMetaDataError Interface](../metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cebbb-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="cebbb-108">Return Value</span></span>  
 <span data-ttu-id="cebbb-109">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="cebbb-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cebbb-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cebbb-110">Requirements</span></span>  
 <span data-ttu-id="cebbb-111">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="cebbb-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cebbb-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cebbb-112">See also</span></span>

- [<span data-ttu-id="cebbb-113">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="cebbb-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="cebbb-114">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="cebbb-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="cebbb-115">API do ALink</span><span class="sxs-lookup"><span data-stu-id="cebbb-115">ALink API</span></span>](index.md)
