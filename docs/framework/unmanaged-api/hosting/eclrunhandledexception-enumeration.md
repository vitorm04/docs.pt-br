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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65910745aa6291f93fd42d8f99a0e84dc1e38fdd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686680"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="5a633-102">Enumeração EClrUnhandledException</span><span class="sxs-lookup"><span data-stu-id="5a633-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="5a633-103">Descreve as opções disponíveis para o gerenciamento de exceções que são sem tratamento no código do usuário.</span><span class="sxs-lookup"><span data-stu-id="5a633-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a633-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5a633-104">Syntax</span></span>  
  
```  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="5a633-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5a633-105">Members</span></span>  
  
|<span data-ttu-id="5a633-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5a633-106">Member</span></span>|<span data-ttu-id="5a633-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a633-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="5a633-108">Especifica que o comportamento padrão ocorre.</span><span class="sxs-lookup"><span data-stu-id="5a633-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="5a633-109">O processo é interrompido.</span><span class="sxs-lookup"><span data-stu-id="5a633-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="5a633-110">Especifica que o common language runtime (CLR) ignora as exceções sem tratamento e permite que o host determine nenhuma providência.</span><span class="sxs-lookup"><span data-stu-id="5a633-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a633-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="5a633-111">Remarks</span></span>  
 <span data-ttu-id="5a633-112">Para especificar que o CLR se comportam como nas versões anteriores, use o `eHostDeterminedPolicy` membro.</span><span class="sxs-lookup"><span data-stu-id="5a633-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a633-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5a633-113">Requirements</span></span>  
 <span data-ttu-id="5a633-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a633-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a633-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5a633-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5a633-116">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5a633-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a633-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a633-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a633-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a633-118">See also</span></span>
- [<span data-ttu-id="5a633-119">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="5a633-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="5a633-120">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="5a633-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="5a633-121">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="5a633-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="5a633-122">Método SetUnhandledExceptionPolicy</span><span class="sxs-lookup"><span data-stu-id="5a633-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="5a633-123">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="5a633-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="5a633-124">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="5a633-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
