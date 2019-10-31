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
ms.openlocfilehash: 80643187045e7e96b9c18169c5e71287713d711f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106246"
---
# <a name="runtime_info_flags-enumeration"></a><span data-ttu-id="03726-102">Enumeração RUNTIME_INFO_FLAGS</span><span class="sxs-lookup"><span data-stu-id="03726-102">RUNTIME_INFO_FLAGS Enumeration</span></span>
<span data-ttu-id="03726-103">Contém valores que indicam quais informações sobre o Common Language Runtime (CLR) devem ser retornadas.</span><span class="sxs-lookup"><span data-stu-id="03726-103">Contains values that indicate what information about the common language runtime (CLR) should be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03726-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03726-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="03726-105">Membros</span><span class="sxs-lookup"><span data-stu-id="03726-105">Members</span></span>  
  
|<span data-ttu-id="03726-106">Membro</span><span class="sxs-lookup"><span data-stu-id="03726-106">Member</span></span>|<span data-ttu-id="03726-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="03726-107">Description</span></span>|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|<span data-ttu-id="03726-108">Indica que as informações de diretório não devem ser incluídas.</span><span class="sxs-lookup"><span data-stu-id="03726-108">Indicates that directory information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|<span data-ttu-id="03726-109">Indica que as informações de versão não devem ser incluídas.</span><span class="sxs-lookup"><span data-stu-id="03726-109">Indicates that version information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|<span data-ttu-id="03726-110">Indica que uma caixa de diálogo de erro não deve ser exibida após a falha.</span><span class="sxs-lookup"><span data-stu-id="03726-110">Indicates that an error dialog box should not be shown upon failure.</span></span>|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|<span data-ttu-id="03726-111">Indica que os efeitos da chamada da função [SetError](https://go.microsoft.com/fwlink/p/?LinkId=255242) com o sinalizador SEM_FAILCRITICALERRORS devem ser substituídos.</span><span class="sxs-lookup"><span data-stu-id="03726-111">Indicates that the effects of calling the [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) function with the SEM_FAILCRITICALERRORS flag should be overridden.</span></span> <span data-ttu-id="03726-112">Ou seja, uma caixa de diálogo de instalação deve ser mostrada após a falha, em vez de ser suprimida.</span><span class="sxs-lookup"><span data-stu-id="03726-112">That is, an installation dialog box should be shown upon failure, instead of being suppressed.</span></span>|  
|`RUNTIME_INFO_REQUEST_AMD64`|<span data-ttu-id="03726-113">Indica uma solicitação de informações sobre uma versão compatível com AMD-64 do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="03726-113">Indicates a request for information about an AMD-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_IA64`|<span data-ttu-id="03726-114">Indica uma solicitação de informações sobre uma versão compatível com IA-64 do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="03726-114">Indicates a request for information about an IA-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_X86`|<span data-ttu-id="03726-115">Indica uma solicitação de informações sobre uma versão compatível com x86 do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="03726-115">Indicates a request for information about an x86-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_UPGRADE_VERSION`|<span data-ttu-id="03726-116">Indica que as informações de atualização de versão devem ser incluídas.</span><span class="sxs-lookup"><span data-stu-id="03726-116">Indicates that version upgrade information should be included.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03726-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="03726-117">Remarks</span></span>  
 <span data-ttu-id="03726-118">Os seguintes sinalizadores de arquitetura de plataforma podem ser especificados apenas um de cada vez e não podem ser combinados:</span><span class="sxs-lookup"><span data-stu-id="03726-118">The following platform architecture flags can be specified only one at a time and cannot be combined:</span></span>  
  
- <span data-ttu-id="03726-119">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="03726-119">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="03726-120">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="03726-120">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="03726-121">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="03726-121">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03726-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03726-122">Requirements</span></span>  
 <span data-ttu-id="03726-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03726-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03726-124">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="03726-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="03726-125">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="03726-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03726-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03726-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03726-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03726-127">See also</span></span>

- [<span data-ttu-id="03726-128">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="03726-128">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
