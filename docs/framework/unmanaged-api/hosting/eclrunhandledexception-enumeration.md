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
ms.workload: dotnet
ms.openlocfilehash: a8fcc9254499724d94153c445943fdaf78d12a10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="64b3b-102">Enumeração EClrUnhandledException</span><span class="sxs-lookup"><span data-stu-id="64b3b-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="64b3b-103">Descreve as opções disponíveis para o gerenciamento de exceções que são sem tratamento no código do usuário.</span><span class="sxs-lookup"><span data-stu-id="64b3b-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64b3b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64b3b-104">Syntax</span></span>  
  
```  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="64b3b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="64b3b-105">Members</span></span>  
  
|<span data-ttu-id="64b3b-106">Membro</span><span class="sxs-lookup"><span data-stu-id="64b3b-106">Member</span></span>|<span data-ttu-id="64b3b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="64b3b-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="64b3b-108">Especifica que o comportamento padrão ocorre.</span><span class="sxs-lookup"><span data-stu-id="64b3b-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="64b3b-109">O processo é interrompido.</span><span class="sxs-lookup"><span data-stu-id="64b3b-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="64b3b-110">Especifica que o common language runtime (CLR) ignora exceções sem tratamento e permite que o host determine nenhuma outra ação.</span><span class="sxs-lookup"><span data-stu-id="64b3b-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64b3b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="64b3b-111">Remarks</span></span>  
 <span data-ttu-id="64b3b-112">Para especificar que o CLR se comportam como nas versões anteriores, use o `eHostDeterminedPolicy` membro.</span><span class="sxs-lookup"><span data-stu-id="64b3b-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64b3b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="64b3b-113">Requirements</span></span>  
 <span data-ttu-id="64b3b-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64b3b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64b3b-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="64b3b-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="64b3b-116">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="64b3b-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64b3b-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64b3b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64b3b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64b3b-118">See Also</span></span>  
 [<span data-ttu-id="64b3b-119">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="64b3b-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="64b3b-120">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="64b3b-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="64b3b-121">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="64b3b-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="64b3b-122">Método SetUnhandledExceptionPolicy</span><span class="sxs-lookup"><span data-stu-id="64b3b-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)  
 [<span data-ttu-id="64b3b-123">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="64b3b-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="64b3b-124">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="64b3b-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
