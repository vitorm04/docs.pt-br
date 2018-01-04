---
title: "Enumeração RUNTIME_INFO_FLAGS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: RUNTIME_INFO_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: RUNTIME_INFO_FLAGS
helpviewer_keywords: RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d050972857ba652ae0b40727260f681c383208b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="runtimeinfoflags-enumeration"></a><span data-ttu-id="c2f22-102">Enumeração RUNTIME_INFO_FLAGS</span><span class="sxs-lookup"><span data-stu-id="c2f22-102">RUNTIME_INFO_FLAGS Enumeration</span></span>
<span data-ttu-id="c2f22-103">Contém valores que indicam quais informações sobre o common language runtime (CLR) devem ser retornadas.</span><span class="sxs-lookup"><span data-stu-id="c2f22-103">Contains values that indicate what information about the common language runtime (CLR) should be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2f22-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2f22-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="c2f22-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c2f22-105">Members</span></span>  
  
|<span data-ttu-id="c2f22-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c2f22-106">Member</span></span>|<span data-ttu-id="c2f22-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2f22-107">Description</span></span>|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|<span data-ttu-id="c2f22-108">Indica que as informações de diretório não devem ser incluídas.</span><span class="sxs-lookup"><span data-stu-id="c2f22-108">Indicates that directory information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|<span data-ttu-id="c2f22-109">Indica que as informações de versão não devem ser incluídas.</span><span class="sxs-lookup"><span data-stu-id="c2f22-109">Indicates that version information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|<span data-ttu-id="c2f22-110">Indica que uma caixa de diálogo de erro não deve ser mostrada em caso de falha.</span><span class="sxs-lookup"><span data-stu-id="c2f22-110">Indicates that an error dialog box should not be shown upon failure.</span></span>|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|<span data-ttu-id="c2f22-111">Indica que os efeitos de chamar o [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) função com o sinalizador SEM_FAILCRITICALERRORS deve ser substituída.</span><span class="sxs-lookup"><span data-stu-id="c2f22-111">Indicates that the effects of calling the [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) function with the SEM_FAILCRITICALERRORS flag should be overridden.</span></span> <span data-ttu-id="c2f22-112">Ou seja, uma caixa de diálogo de instalação deve ser mostrada após a falha, em vez de ser suprimida.</span><span class="sxs-lookup"><span data-stu-id="c2f22-112">That is, an installation dialog box should be shown upon failure, instead of being suppressed.</span></span>|  
|`RUNTIME_INFO_REQUEST_AMD64`|<span data-ttu-id="c2f22-113">Indica uma solicitação para obter informações sobre uma versão compatível com 64 AMD do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c2f22-113">Indicates a request for information about an AMD-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_IA64`|<span data-ttu-id="c2f22-114">Indica uma solicitação para obter informações sobre uma versão compatível do IA-64 do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c2f22-114">Indicates a request for information about an IA-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_X86`|<span data-ttu-id="c2f22-115">Indica uma solicitação para obter informações sobre uma versão compatível com x86 do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c2f22-115">Indicates a request for information about an x86-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_UPGRADE_VERSION`|<span data-ttu-id="c2f22-116">Indica que as informações de atualização de versão devem ser incluídas.</span><span class="sxs-lookup"><span data-stu-id="c2f22-116">Indicates that version upgrade information should be included.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2f22-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2f22-117">Remarks</span></span>  
 <span data-ttu-id="c2f22-118">Os seguintes sinalizadores de arquitetura de plataforma podem ser especificada apenas uma por vez e não podem ser combinados:</span><span class="sxs-lookup"><span data-stu-id="c2f22-118">The following platform architecture flags can be specified only one at a time and cannot be combined:</span></span>  
  
-   <span data-ttu-id="c2f22-119">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="c2f22-119">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
-   <span data-ttu-id="c2f22-120">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="c2f22-120">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
-   <span data-ttu-id="c2f22-121">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="c2f22-121">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2f22-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2f22-122">Requirements</span></span>  
 <span data-ttu-id="c2f22-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2f22-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2f22-124">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c2f22-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2f22-125">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c2f22-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2f22-126">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2f22-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2f22-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2f22-127">See Also</span></span>  
 [<span data-ttu-id="c2f22-128">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="c2f22-128">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
