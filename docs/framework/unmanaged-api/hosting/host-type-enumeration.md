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
ms.openlocfilehash: e8dda83df8a320733f45dbcc13599cdf37d26492
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617146"
---
# <a name="host_type-enumeration"></a><span data-ttu-id="53625-102">Enumeração HOST_TYPE</span><span class="sxs-lookup"><span data-stu-id="53625-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="53625-103">Contém valores que especificam o tipo de host que está iniciando um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53625-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53625-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53625-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="53625-105">Membros</span><span class="sxs-lookup"><span data-stu-id="53625-105">Members</span></span>  
  
|<span data-ttu-id="53625-106">Membro</span><span class="sxs-lookup"><span data-stu-id="53625-106">Member</span></span>|<span data-ttu-id="53625-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="53625-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="53625-108">Inicie o aplicativo em AppLaunch. exe.</span><span class="sxs-lookup"><span data-stu-id="53625-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="53625-109">Use esse valor para aplicativos parcialmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="53625-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="53625-110">Inicie o aplicativo diretamente.</span><span class="sxs-lookup"><span data-stu-id="53625-110">Launch the application directly.</span></span> <span data-ttu-id="53625-111">Ou seja, inicie o aplicativo a partir de seu próprio arquivo. exe.</span><span class="sxs-lookup"><span data-stu-id="53625-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="53625-112">Use esse valor para aplicativos totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="53625-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="53625-113">O mesmo que HOST_TYPE_APPLAUNCH.</span><span class="sxs-lookup"><span data-stu-id="53625-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="53625-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="53625-114">Requirements</span></span>  
 <span data-ttu-id="53625-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53625-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53625-116">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="53625-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="53625-117">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="53625-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53625-118">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53625-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53625-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="53625-119">See also</span></span>

- [<span data-ttu-id="53625-120">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="53625-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
