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
ms.openlocfilehash: e33029e8244fdfa180a79aa4a5b05b07f594d928
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860900"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="470e0-102">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="470e0-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="470e0-103">Fornece interfaces para publicar informações sobre processos e domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="470e0-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="470e0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="470e0-104">Syntax</span></span>  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="470e0-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="470e0-105">Interfaces</span></span>  
  
|<span data-ttu-id="470e0-106">Interface</span><span class="sxs-lookup"><span data-stu-id="470e0-106">Interface</span></span>|<span data-ttu-id="470e0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="470e0-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="470e0-108">Interface ICorPublish</span><span class="sxs-lookup"><span data-stu-id="470e0-108">ICorPublish Interface</span></span>](icorpublish-interface.md)|<span data-ttu-id="470e0-109">Fornece métodos para publicar informações sobre processos e os domínios de aplicativo nesses processos.</span><span class="sxs-lookup"><span data-stu-id="470e0-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="470e0-110">Interface ICorPublishAppDomain</span><span class="sxs-lookup"><span data-stu-id="470e0-110">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)|<span data-ttu-id="470e0-111">Representa e fornece informações sobre o, um domínio de aplicativo em um processo.</span><span class="sxs-lookup"><span data-stu-id="470e0-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="470e0-112">Interface ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="470e0-112">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)|<span data-ttu-id="470e0-113">Fornece métodos que atravessam uma coleção de domínios de aplicativo que existem atualmente dentro de um processo.</span><span class="sxs-lookup"><span data-stu-id="470e0-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="470e0-114">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="470e0-114">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)|<span data-ttu-id="470e0-115">Representa um processo que está sendo executado em um computador.</span><span class="sxs-lookup"><span data-stu-id="470e0-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="470e0-116">Interface ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="470e0-116">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)|<span data-ttu-id="470e0-117">Fornece métodos que atravessam uma coleção de processos que estão em execução em um computador.</span><span class="sxs-lookup"><span data-stu-id="470e0-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="470e0-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="470e0-118">Remarks</span></span>  
 <span data-ttu-id="470e0-119">Um cenário de publicação típico envolve um desenvolvedor que deseja depurar o código gerenciado que está sendo executado em um computador dentro de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="470e0-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="470e0-120">O ambiente de hospedagem pode estar executando mais de um domínio de aplicativo dentro de um processo.</span><span class="sxs-lookup"><span data-stu-id="470e0-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="470e0-121">O desenvolvedor gostaria de usar uma interface gráfica do usuário ou algum outro meio de listar todos os processos em execução no computador e escolher um processo específico.</span><span class="sxs-lookup"><span data-stu-id="470e0-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="470e0-122">A listagem deve incluir todos os domínios de aplicativo em processos que estejam executando código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="470e0-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="470e0-123">O desenvolvedor pode então identificar o domínio do aplicativo específico e anexar um depurador a esse domínio.</span><span class="sxs-lookup"><span data-stu-id="470e0-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="470e0-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="470e0-124">Requirements</span></span>  
 <span data-ttu-id="470e0-125">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="470e0-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="470e0-126">**Cabeçalho:** CorPub. idl</span><span class="sxs-lookup"><span data-stu-id="470e0-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="470e0-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="470e0-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="470e0-128">**.NET Framework versões:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="470e0-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="470e0-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="470e0-129">See also</span></span>

- [<span data-ttu-id="470e0-130">Depuração</span><span class="sxs-lookup"><span data-stu-id="470e0-130">Debugging</span></span>](index.md)
