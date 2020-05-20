---
title: Interface ICLRAssemblyReferenceList
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
ms.openlocfilehash: f1aa40ef868bf6ff7730e01ab66a6fec58af1196
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615872"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="f1dbe-102">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="f1dbe-102">ICLRAssemblyReferenceList Interface</span></span>
<span data-ttu-id="f1dbe-103">Gerencia uma lista de assemblies que são carregados pelo Common Language Runtime (CLR) e não pelo host.</span><span class="sxs-lookup"><span data-stu-id="f1dbe-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f1dbe-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="f1dbe-104">Methods</span></span>  
  
|<span data-ttu-id="f1dbe-105">Método</span><span class="sxs-lookup"><span data-stu-id="f1dbe-105">Method</span></span>|<span data-ttu-id="f1dbe-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1dbe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f1dbe-107">Método IsAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="f1dbe-107">IsAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="f1dbe-108">Obtém um valor que indica se o ponteiro fornecido faz referência a um assembly na lista.</span><span class="sxs-lookup"><span data-stu-id="f1dbe-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="f1dbe-109">Método IsStringAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="f1dbe-109">IsStringAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="f1dbe-110">Obtém um valor que indica se o nome fornecido corresponde ao nome de um assembly na lista.</span><span class="sxs-lookup"><span data-stu-id="f1dbe-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1dbe-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1dbe-111">Remarks</span></span>  
 <span data-ttu-id="f1dbe-112">Chame o método [ICLRAssemblyIdentityManager:: GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) para obter um ponteiro para uma instância do `ICLRAssemblyReferenceList` .</span><span class="sxs-lookup"><span data-stu-id="f1dbe-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1dbe-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f1dbe-113">Requirements</span></span>  
 <span data-ttu-id="f1dbe-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1dbe-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1dbe-115">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f1dbe-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f1dbe-116">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f1dbe-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1dbe-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1dbe-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1dbe-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="f1dbe-118">See also</span></span>

- [<span data-ttu-id="f1dbe-119">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="f1dbe-119">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="f1dbe-120">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="f1dbe-120">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="f1dbe-121">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="f1dbe-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
