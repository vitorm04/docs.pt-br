---
title: Coclass CorpubPublish
ms.date: 03/30/2017
api_name:
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d1ca8ea9d00de8a07c67977cf108c50268802e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739362"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="b374e-102">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="b374e-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="b374e-103">Fornece interfaces para a publicação de informações sobre domínios de aplicativos e processos.</span><span class="sxs-lookup"><span data-stu-id="b374e-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b374e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b374e-104">Syntax</span></span>  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="b374e-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="b374e-105">Interfaces</span></span>  
  
|<span data-ttu-id="b374e-106">Interface</span><span class="sxs-lookup"><span data-stu-id="b374e-106">Interface</span></span>|<span data-ttu-id="b374e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b374e-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="b374e-108">Interface ICorPublish</span><span class="sxs-lookup"><span data-stu-id="b374e-108">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|<span data-ttu-id="b374e-109">Fornece métodos para a publicação de informações sobre processos e os domínios de aplicativo em um desses processos.</span><span class="sxs-lookup"><span data-stu-id="b374e-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="b374e-110">Interface ICorPublishAppDomain</span><span class="sxs-lookup"><span data-stu-id="b374e-110">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|<span data-ttu-id="b374e-111">Representa e fornece informações sobre um domínio de aplicativo em um processo.</span><span class="sxs-lookup"><span data-stu-id="b374e-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="b374e-112">Interface ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="b374e-112">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|<span data-ttu-id="b374e-113">Fornece métodos que percorrem uma coleção de domínios de aplicativo que existem atualmente dentro de um processo.</span><span class="sxs-lookup"><span data-stu-id="b374e-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="b374e-114">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="b374e-114">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|<span data-ttu-id="b374e-115">Representa um processo que está em execução em um computador.</span><span class="sxs-lookup"><span data-stu-id="b374e-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="b374e-116">Interface ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="b374e-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|<span data-ttu-id="b374e-117">Fornece métodos que percorrem uma coleção de processos em execução em um computador.</span><span class="sxs-lookup"><span data-stu-id="b374e-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b374e-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="b374e-118">Remarks</span></span>  
 <span data-ttu-id="b374e-119">Um cenário típico de publicação envolve um desenvolvedor que deseja depurar código gerenciado que está em execução em um computador em um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b374e-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="b374e-120">O ambiente de hospedagem pode estar executando mais de um domínio de aplicativo dentro de um processo.</span><span class="sxs-lookup"><span data-stu-id="b374e-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="b374e-121">O desenvolvedor gostaria de usar uma interface gráfica do usuário ou outros meios para listar todos os processos que estão em execução no computador e escolher um processo específico.</span><span class="sxs-lookup"><span data-stu-id="b374e-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="b374e-122">A listagem deve incluir todos os domínios de aplicativo dentro de processos que estão executando o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b374e-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="b374e-123">O desenvolvedor pode, em seguida, identificar o domínio de aplicativo específico e anexar um depurador ao domínio.</span><span class="sxs-lookup"><span data-stu-id="b374e-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b374e-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b374e-124">Requirements</span></span>  
 <span data-ttu-id="b374e-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b374e-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b374e-126">**Cabeçalho:** CorPub.idl</span><span class="sxs-lookup"><span data-stu-id="b374e-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="b374e-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b374e-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b374e-128">**Versões do .NET framework:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b374e-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b374e-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b374e-129">See also</span></span>

- [<span data-ttu-id="b374e-130">Depuração</span><span class="sxs-lookup"><span data-stu-id="b374e-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
