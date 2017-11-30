---
title: "Enumeração EClrUnhandledException"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrUnhandledException
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrUnhandledException
helpviewer_keywords: EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 67787072779e0cb22a339c2d13c972ba36f3ed61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="f2a56-102">Enumeração EClrUnhandledException</span><span class="sxs-lookup"><span data-stu-id="f2a56-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="f2a56-103">Descreve as opções disponíveis para o gerenciamento de exceções que são sem tratamento no código do usuário.</span><span class="sxs-lookup"><span data-stu-id="f2a56-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2a56-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2a56-104">Syntax</span></span>  
  
```  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="f2a56-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f2a56-105">Members</span></span>  
  
|<span data-ttu-id="f2a56-106">Membro</span><span class="sxs-lookup"><span data-stu-id="f2a56-106">Member</span></span>|<span data-ttu-id="f2a56-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2a56-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="f2a56-108">Especifica que o comportamento padrão ocorre.</span><span class="sxs-lookup"><span data-stu-id="f2a56-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="f2a56-109">O processo é interrompido.</span><span class="sxs-lookup"><span data-stu-id="f2a56-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="f2a56-110">Especifica que o common language runtime (CLR) ignora exceções sem tratamento e permite que o host determine nenhuma outra ação.</span><span class="sxs-lookup"><span data-stu-id="f2a56-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2a56-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="f2a56-111">Remarks</span></span>  
 <span data-ttu-id="f2a56-112">Para especificar que o CLR se comportam como nas versões anteriores, use o `eHostDeterminedPolicy` membro.</span><span class="sxs-lookup"><span data-stu-id="f2a56-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2a56-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2a56-113">Requirements</span></span>  
 <span data-ttu-id="f2a56-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2a56-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2a56-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f2a56-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f2a56-116">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f2a56-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2a56-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2a56-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a56-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2a56-118">See Also</span></span>  
 [<span data-ttu-id="f2a56-119">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="f2a56-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="f2a56-120">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="f2a56-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="f2a56-121">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="f2a56-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="f2a56-122">Método SetUnhandledExceptionPolicy</span><span class="sxs-lookup"><span data-stu-id="f2a56-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)  
 [<span data-ttu-id="f2a56-123">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="f2a56-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="f2a56-124">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="f2a56-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
