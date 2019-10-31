---
title: Enumeração HOST_TYPE
ms.date: 03/30/2017
api_name:
- HOST_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- HOST_TYPE
helpviewer_keywords:
- HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type:
- apiref
ms.openlocfilehash: cc0cea10b4a209583fb7afb551a6b80d52ad7f62
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127023"
---
# <a name="host_type-enumeration"></a><span data-ttu-id="cfcff-102">Enumeração HOST_TYPE</span><span class="sxs-lookup"><span data-stu-id="cfcff-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="cfcff-103">Contém valores que especificam o tipo de host que está iniciando um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cfcff-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfcff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cfcff-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="cfcff-105">Membros</span><span class="sxs-lookup"><span data-stu-id="cfcff-105">Members</span></span>  
  
|<span data-ttu-id="cfcff-106">Membro</span><span class="sxs-lookup"><span data-stu-id="cfcff-106">Member</span></span>|<span data-ttu-id="cfcff-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cfcff-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="cfcff-108">Inicie o aplicativo em AppLaunch. exe.</span><span class="sxs-lookup"><span data-stu-id="cfcff-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="cfcff-109">Use esse valor para aplicativos parcialmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="cfcff-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="cfcff-110">Inicie o aplicativo diretamente.</span><span class="sxs-lookup"><span data-stu-id="cfcff-110">Launch the application directly.</span></span> <span data-ttu-id="cfcff-111">Ou seja, inicie o aplicativo a partir de seu próprio arquivo. exe.</span><span class="sxs-lookup"><span data-stu-id="cfcff-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="cfcff-112">Use esse valor para aplicativos totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="cfcff-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="cfcff-113">O mesmo que HOST_TYPE_APPLAUNCH.</span><span class="sxs-lookup"><span data-stu-id="cfcff-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cfcff-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cfcff-114">Requirements</span></span>  
 <span data-ttu-id="cfcff-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfcff-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfcff-116">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cfcff-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cfcff-117">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cfcff-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cfcff-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfcff-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfcff-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfcff-119">See also</span></span>

- [<span data-ttu-id="cfcff-120">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="cfcff-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
