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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfb1cff3e95c5ff86d22913745b7d14982766b48
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175221"
---
# <a name="hosttype-enumeration"></a><span data-ttu-id="7450d-102">Enumeração HOST_TYPE</span><span class="sxs-lookup"><span data-stu-id="7450d-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="7450d-103">Contém valores que especificam o tipo de host que está iniciando um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7450d-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7450d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7450d-104">Syntax</span></span>  
  
```  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="7450d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="7450d-105">Members</span></span>  
  
|<span data-ttu-id="7450d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="7450d-106">Member</span></span>|<span data-ttu-id="7450d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7450d-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="7450d-108">Inicie o aplicativo de AppLaunch.exe.</span><span class="sxs-lookup"><span data-stu-id="7450d-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="7450d-109">Use esse valor para os aplicativos parcialmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="7450d-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="7450d-110">Inicie o aplicativo diretamente.</span><span class="sxs-lookup"><span data-stu-id="7450d-110">Launch the application directly.</span></span> <span data-ttu-id="7450d-111">Ou seja, inicie o aplicativo de seu próprio arquivo .exe.</span><span class="sxs-lookup"><span data-stu-id="7450d-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="7450d-112">Use esse valor para os aplicativos totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="7450d-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="7450d-113">Mesmo que HOST_TYPE_APPLAUNCH.</span><span class="sxs-lookup"><span data-stu-id="7450d-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7450d-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7450d-114">Requirements</span></span>  
 <span data-ttu-id="7450d-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7450d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7450d-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7450d-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7450d-117">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7450d-117">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7450d-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7450d-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7450d-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7450d-119">See also</span></span>

- [<span data-ttu-id="7450d-120">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="7450d-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
