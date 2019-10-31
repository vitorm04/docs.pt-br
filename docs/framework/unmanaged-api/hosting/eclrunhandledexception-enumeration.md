---
title: Enumeração EClrUnhandledException
ms.date: 03/30/2017
api_name:
- EClrUnhandledException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrUnhandledException
helpviewer_keywords:
- EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type:
- apiref
ms.openlocfilehash: 302db0d029b3811d151473323a7a60bd16a00ec1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131234"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="cba96-102">Enumeração EClrUnhandledException</span><span class="sxs-lookup"><span data-stu-id="cba96-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="cba96-103">Descreve as opções disponíveis para gerenciar exceções que não são manipuladas no código do usuário.</span><span class="sxs-lookup"><span data-stu-id="cba96-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cba96-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cba96-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="cba96-105">Membros</span><span class="sxs-lookup"><span data-stu-id="cba96-105">Members</span></span>  
  
|<span data-ttu-id="cba96-106">Membro</span><span class="sxs-lookup"><span data-stu-id="cba96-106">Member</span></span>|<span data-ttu-id="cba96-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cba96-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="cba96-108">Especifica que o comportamento padrão ocorre.</span><span class="sxs-lookup"><span data-stu-id="cba96-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="cba96-109">O processo é interrompido.</span><span class="sxs-lookup"><span data-stu-id="cba96-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="cba96-110">Especifica que o Common Language Runtime (CLR) ignora exceções sem tratamento e permite que o host determine qualquer ação adicional.</span><span class="sxs-lookup"><span data-stu-id="cba96-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cba96-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="cba96-111">Remarks</span></span>  
 <span data-ttu-id="cba96-112">Para especificar que o CLR se comporte como versões anteriores, use o membro `eHostDeterminedPolicy`.</span><span class="sxs-lookup"><span data-stu-id="cba96-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cba96-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cba96-113">Requirements</span></span>  
 <span data-ttu-id="cba96-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cba96-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cba96-115">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cba96-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cba96-116">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cba96-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cba96-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cba96-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cba96-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cba96-118">See also</span></span>

- [<span data-ttu-id="cba96-119">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="cba96-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="cba96-120">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="cba96-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="cba96-121">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="cba96-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="cba96-122">Método SetUnhandledExceptionPolicy</span><span class="sxs-lookup"><span data-stu-id="cba96-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="cba96-123">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="cba96-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="cba96-124">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="cba96-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
