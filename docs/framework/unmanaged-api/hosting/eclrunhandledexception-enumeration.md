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
ms.openlocfilehash: ba0c2ea7733f098b7fac95f51b5eb16d083174e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779371"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="dbbff-102">Enumeração EClrUnhandledException</span><span class="sxs-lookup"><span data-stu-id="dbbff-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="dbbff-103">Descreve as opções disponíveis para o gerenciamento de exceções que são sem tratamento no código do usuário.</span><span class="sxs-lookup"><span data-stu-id="dbbff-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbbff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dbbff-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="dbbff-105">Membros</span><span class="sxs-lookup"><span data-stu-id="dbbff-105">Members</span></span>  
  
|<span data-ttu-id="dbbff-106">Membro</span><span class="sxs-lookup"><span data-stu-id="dbbff-106">Member</span></span>|<span data-ttu-id="dbbff-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="dbbff-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="dbbff-108">Especifica que o comportamento padrão ocorre.</span><span class="sxs-lookup"><span data-stu-id="dbbff-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="dbbff-109">O processo é interrompido.</span><span class="sxs-lookup"><span data-stu-id="dbbff-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="dbbff-110">Especifica que o common language runtime (CLR) ignora as exceções sem tratamento e permite que o host determine nenhuma providência.</span><span class="sxs-lookup"><span data-stu-id="dbbff-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbbff-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="dbbff-111">Remarks</span></span>  
 <span data-ttu-id="dbbff-112">Para especificar que o CLR se comportam como nas versões anteriores, use o `eHostDeterminedPolicy` membro.</span><span class="sxs-lookup"><span data-stu-id="dbbff-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbbff-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dbbff-113">Requirements</span></span>  
 <span data-ttu-id="dbbff-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbbff-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbbff-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dbbff-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dbbff-116">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dbbff-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbbff-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbbff-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbbff-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbbff-118">See also</span></span>

- [<span data-ttu-id="dbbff-119">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="dbbff-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="dbbff-120">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="dbbff-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="dbbff-121">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="dbbff-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="dbbff-122">Método SetUnhandledExceptionPolicy</span><span class="sxs-lookup"><span data-stu-id="dbbff-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="dbbff-123">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="dbbff-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="dbbff-124">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="dbbff-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
