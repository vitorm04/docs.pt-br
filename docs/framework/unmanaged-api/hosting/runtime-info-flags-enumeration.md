---
title: Enumeração RUNTIME_INFO_FLAGS
ms.date: 03/30/2017
api_name:
- RUNTIME_INFO_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RUNTIME_INFO_FLAGS
helpviewer_keywords:
- RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0f4b6e024d75d9334f91373f9d3bbd2c5e41093
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622504"
---
# <a name="runtimeinfoflags-enumeration"></a><span data-ttu-id="6887d-102">Enumeração RUNTIME_INFO_FLAGS</span><span class="sxs-lookup"><span data-stu-id="6887d-102">RUNTIME_INFO_FLAGS Enumeration</span></span>
<span data-ttu-id="6887d-103">Contém valores que indicam quais informações sobre o common language runtime (CLR) devem ser retornadas.</span><span class="sxs-lookup"><span data-stu-id="6887d-103">Contains values that indicate what information about the common language runtime (CLR) should be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6887d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6887d-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="6887d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="6887d-105">Members</span></span>  
  
|<span data-ttu-id="6887d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="6887d-106">Member</span></span>|<span data-ttu-id="6887d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6887d-107">Description</span></span>|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|<span data-ttu-id="6887d-108">Indica que as informações de diretório não devem ser incluídas.</span><span class="sxs-lookup"><span data-stu-id="6887d-108">Indicates that directory information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|<span data-ttu-id="6887d-109">Indica que as informações de versão não devem ser incluídas.</span><span class="sxs-lookup"><span data-stu-id="6887d-109">Indicates that version information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|<span data-ttu-id="6887d-110">Indica que uma caixa de diálogo de erro não deve ser mostrada em caso de falha.</span><span class="sxs-lookup"><span data-stu-id="6887d-110">Indicates that an error dialog box should not be shown upon failure.</span></span>|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|<span data-ttu-id="6887d-111">Indica que os efeitos da chamada a [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) função com o sinalizador SEM_FAILCRITICALERRORS deve ser substituída.</span><span class="sxs-lookup"><span data-stu-id="6887d-111">Indicates that the effects of calling the [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) function with the SEM_FAILCRITICALERRORS flag should be overridden.</span></span> <span data-ttu-id="6887d-112">Ou seja, uma caixa de diálogo de instalação deve ser mostrada em caso de falha, em vez de ser suprimida.</span><span class="sxs-lookup"><span data-stu-id="6887d-112">That is, an installation dialog box should be shown upon failure, instead of being suppressed.</span></span>|  
|`RUNTIME_INFO_REQUEST_AMD64`|<span data-ttu-id="6887d-113">Indica uma solicitação para obter informações sobre uma versão compatível com 64 AMD de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6887d-113">Indicates a request for information about an AMD-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_IA64`|<span data-ttu-id="6887d-114">Indica uma solicitação para obter informações sobre uma versão compatível do IA-64 do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6887d-114">Indicates a request for information about an IA-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_X86`|<span data-ttu-id="6887d-115">Indica uma solicitação para obter informações sobre uma versão compatível com x86 do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6887d-115">Indicates a request for information about an x86-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_UPGRADE_VERSION`|<span data-ttu-id="6887d-116">Indica que as informações de atualização de versão devem ser incluídas.</span><span class="sxs-lookup"><span data-stu-id="6887d-116">Indicates that version upgrade information should be included.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6887d-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="6887d-117">Remarks</span></span>  
 <span data-ttu-id="6887d-118">Os seguintes sinalizadores de arquitetura de plataforma podem ser especificado apenas um por vez e não podem ser combinados:</span><span class="sxs-lookup"><span data-stu-id="6887d-118">The following platform architecture flags can be specified only one at a time and cannot be combined:</span></span>  
  
- <span data-ttu-id="6887d-119">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="6887d-119">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="6887d-120">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="6887d-120">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="6887d-121">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="6887d-121">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6887d-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6887d-122">Requirements</span></span>  
 <span data-ttu-id="6887d-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6887d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6887d-124">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6887d-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6887d-125">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6887d-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6887d-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6887d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6887d-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6887d-127">See also</span></span>

- [<span data-ttu-id="6887d-128">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="6887d-128">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
