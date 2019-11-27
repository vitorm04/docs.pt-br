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
ms.openlocfilehash: 986ae69e7ebb8f607be5d37fab426bcc787abb26
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445647"
---
# <a name="init-method"></a><span data-ttu-id="ebe0e-102">Método Init</span><span class="sxs-lookup"><span data-stu-id="ebe0e-102">Init Method</span></span>
<span data-ttu-id="ebe0e-103">Prepara objetos que implementam a [interface IALink](ialink-interface.md) para uso.</span><span class="sxs-lookup"><span data-stu-id="ebe0e-103">Prepares objects implementing the [IALink Interface](ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebe0e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ebe0e-104">Syntax</span></span>  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebe0e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ebe0e-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="ebe0e-106">Ponteiro de [interface IMetaDataDispenserEx](../metadata/imetadatadispenserex-interface.md) para o dispensador de metadados.</span><span class="sxs-lookup"><span data-stu-id="ebe0e-106">[IMetaDataDispenserEx Interface](../metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="ebe0e-107">Ponteiro de [interface IMetaDataError](../metadata/imetadataerror-interface.md) para uma interface de tratamento de erro opcional.</span><span class="sxs-lookup"><span data-stu-id="ebe0e-107">[IMetaDataError Interface](../metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebe0e-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ebe0e-108">Return Value</span></span>  
 <span data-ttu-id="ebe0e-109">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="ebe0e-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebe0e-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ebe0e-110">Requirements</span></span>  
 <span data-ttu-id="ebe0e-111">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="ebe0e-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebe0e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebe0e-112">See also</span></span>

- [<span data-ttu-id="ebe0e-113">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="ebe0e-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ebe0e-114">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="ebe0e-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ebe0e-115">API do ALink</span><span class="sxs-lookup"><span data-stu-id="ebe0e-115">ALink API</span></span>](index.md)
