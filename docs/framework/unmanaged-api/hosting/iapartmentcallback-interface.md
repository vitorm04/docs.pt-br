---
title: Interface IApartmentCallback
ms.date: 03/30/2017
api_name:
- IApartmentCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IApartmentCallback
helpviewer_keywords:
- IApartmentCallback interface [.NET Framework hosting]
ms.assetid: 57c33c58-bf0b-4533-b569-e6a682d02cba
topic_type:
- apiref
ms.openlocfilehash: fbf501d906ecc0bf55719fa33d1af2d4db1cc2ef
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617081"
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="31427-102">Interface IApartmentCallback</span><span class="sxs-lookup"><span data-stu-id="31427-102">IApartmentCallback Interface</span></span>
<span data-ttu-id="31427-103">Fornece métodos para fazer retornos de chamada em um apartamento.</span><span class="sxs-lookup"><span data-stu-id="31427-103">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="31427-104">Um *apartamento* é um contêiner lógico dentro de um processo para objetos que compartilham os mesmos requisitos de acesso de thread.</span><span class="sxs-lookup"><span data-stu-id="31427-104">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="31427-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="31427-105">Methods</span></span>  
  
|<span data-ttu-id="31427-106">Método</span><span class="sxs-lookup"><span data-stu-id="31427-106">Method</span></span>|<span data-ttu-id="31427-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="31427-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="31427-108">Método DoCallback</span><span class="sxs-lookup"><span data-stu-id="31427-108">DoCallback Method</span></span>](iapartmentcallback-docallback-method.md)|<span data-ttu-id="31427-109">Executa a função especificada em um apartamento.</span><span class="sxs-lookup"><span data-stu-id="31427-109">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="31427-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="31427-110">Requirements</span></span>  
 <span data-ttu-id="31427-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31427-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31427-112">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="31427-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="31427-113">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="31427-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31427-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31427-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31427-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="31427-115">See also</span></span>

- [<span data-ttu-id="31427-116">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="31427-116">Hosting Interfaces</span></span>](hosting-interfaces.md)
