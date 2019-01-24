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
ms.openlocfilehash: 6a2db1aea04ae060623bc39a52ed6990f6137f82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606434"
---
# <a name="hosttype-enumeration"></a><span data-ttu-id="8ae98-102">Enumeração HOST_TYPE</span><span class="sxs-lookup"><span data-stu-id="8ae98-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="8ae98-103">Contém valores que especificam o tipo de host que está iniciando um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8ae98-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ae98-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ae98-104">Syntax</span></span>  
  
```  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="8ae98-105">Membros</span><span class="sxs-lookup"><span data-stu-id="8ae98-105">Members</span></span>  
  
|<span data-ttu-id="8ae98-106">Membro</span><span class="sxs-lookup"><span data-stu-id="8ae98-106">Member</span></span>|<span data-ttu-id="8ae98-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ae98-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="8ae98-108">Inicie o aplicativo de AppLaunch.exe.</span><span class="sxs-lookup"><span data-stu-id="8ae98-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="8ae98-109">Use esse valor para os aplicativos parcialmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="8ae98-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="8ae98-110">Inicie o aplicativo diretamente.</span><span class="sxs-lookup"><span data-stu-id="8ae98-110">Launch the application directly.</span></span> <span data-ttu-id="8ae98-111">Ou seja, inicie o aplicativo de seu próprio arquivo .exe.</span><span class="sxs-lookup"><span data-stu-id="8ae98-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="8ae98-112">Use esse valor para os aplicativos totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="8ae98-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="8ae98-113">Mesmo que HOST_TYPE_APPLAUNCH.</span><span class="sxs-lookup"><span data-stu-id="8ae98-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8ae98-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8ae98-114">Requirements</span></span>  
 <span data-ttu-id="8ae98-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ae98-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ae98-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8ae98-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ae98-117">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ae98-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ae98-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ae98-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ae98-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ae98-119">See also</span></span>
- [<span data-ttu-id="8ae98-120">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="8ae98-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
