---
title: "Enumeração HOST_TYPE"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a8c910dd06109a8a69f29517812737d4b4dcef21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="hosttype-enumeration"></a><span data-ttu-id="25201-102">Enumeração HOST_TYPE</span><span class="sxs-lookup"><span data-stu-id="25201-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="25201-103">Contém valores que especificam o tipo de host que está iniciando um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25201-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25201-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25201-104">Syntax</span></span>  
  
```  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="25201-105">Membros</span><span class="sxs-lookup"><span data-stu-id="25201-105">Members</span></span>  
  
|<span data-ttu-id="25201-106">Membro</span><span class="sxs-lookup"><span data-stu-id="25201-106">Member</span></span>|<span data-ttu-id="25201-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="25201-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="25201-108">Inicie o aplicativo de AppLaunch.exe.</span><span class="sxs-lookup"><span data-stu-id="25201-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="25201-109">Use esse valor para aplicativos parcialmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="25201-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="25201-110">Inicie o aplicativo diretamente.</span><span class="sxs-lookup"><span data-stu-id="25201-110">Launch the application directly.</span></span> <span data-ttu-id="25201-111">Ou seja, inicie o aplicativo de seu próprio arquivo de .exe.</span><span class="sxs-lookup"><span data-stu-id="25201-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="25201-112">Use esse valor para aplicativos totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="25201-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="25201-113">Mesmo que HOST_TYPE_APPLAUNCH.</span><span class="sxs-lookup"><span data-stu-id="25201-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="25201-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="25201-114">Requirements</span></span>  
 <span data-ttu-id="25201-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25201-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25201-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="25201-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25201-117">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="25201-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25201-118">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25201-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25201-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25201-119">See Also</span></span>  
 [<span data-ttu-id="25201-120">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="25201-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
