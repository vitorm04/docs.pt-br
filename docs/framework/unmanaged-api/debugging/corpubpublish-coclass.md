---
title: Coclass CorpubPublish
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorpubPublish Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CorpubPublish
helpviewer_keywords: CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c1565c9321e64536139e02b239fbeb4247a58a3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="56abd-102">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="56abd-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="56abd-103">Fornece interfaces para publicar as informações sobre domínios de aplicativos e processos.</span><span class="sxs-lookup"><span data-stu-id="56abd-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56abd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="56abd-104">Syntax</span></span>  
  
```  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="56abd-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="56abd-105">Interfaces</span></span>  
  
|<span data-ttu-id="56abd-106">Interface</span><span class="sxs-lookup"><span data-stu-id="56abd-106">Interface</span></span>|<span data-ttu-id="56abd-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="56abd-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="56abd-108">Interface ICorPublish</span><span class="sxs-lookup"><span data-stu-id="56abd-108">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|<span data-ttu-id="56abd-109">Fornece métodos para publicar as informações sobre processos e os domínios de aplicativo nesses processos.</span><span class="sxs-lookup"><span data-stu-id="56abd-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="56abd-110">Interface ICorPublishAppDomain</span><span class="sxs-lookup"><span data-stu-id="56abd-110">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|<span data-ttu-id="56abd-111">Representa e fornece informações sobre um domínio de aplicativo em um processo.</span><span class="sxs-lookup"><span data-stu-id="56abd-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="56abd-112">Interface ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="56abd-112">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|<span data-ttu-id="56abd-113">Fornece métodos que atravessam uma coleção de domínios de aplicativo que existem dentro de um processo.</span><span class="sxs-lookup"><span data-stu-id="56abd-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="56abd-114">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="56abd-114">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|<span data-ttu-id="56abd-115">Representa um processo que está em execução em um computador.</span><span class="sxs-lookup"><span data-stu-id="56abd-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="56abd-116">Interface ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="56abd-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|<span data-ttu-id="56abd-117">Fornece métodos que atravessam uma coleção de processos em execução em um computador.</span><span class="sxs-lookup"><span data-stu-id="56abd-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56abd-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="56abd-118">Remarks</span></span>  
 <span data-ttu-id="56abd-119">Um cenário típico de publicação envolve um desenvolvedor que deseja depurar código gerenciado que está em execução em um computador em um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="56abd-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="56abd-120">O ambiente de hospedagem pode estar executando mais de um domínio de aplicativo dentro de um processo.</span><span class="sxs-lookup"><span data-stu-id="56abd-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="56abd-121">O desenvolvedor gostaria de usar uma interface gráfica do usuário ou outros meios para listar todos os processos que estão em execução no computador e selecione um processo específico.</span><span class="sxs-lookup"><span data-stu-id="56abd-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="56abd-122">A listagem deve incluir todos os domínios de aplicativo dentro de processos que estão executando o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="56abd-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="56abd-123">O desenvolvedor pode, em seguida, identificar o domínio de aplicativo específico e anexar um depurador ao domínio.</span><span class="sxs-lookup"><span data-stu-id="56abd-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56abd-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="56abd-124">Requirements</span></span>  
 <span data-ttu-id="56abd-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56abd-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56abd-126">**Cabeçalho:** CorPub.idl</span><span class="sxs-lookup"><span data-stu-id="56abd-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="56abd-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56abd-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56abd-128">**Versões do .NET framework:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56abd-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56abd-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56abd-129">See Also</span></span>  
 [<span data-ttu-id="56abd-130">Depuração</span><span class="sxs-lookup"><span data-stu-id="56abd-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
