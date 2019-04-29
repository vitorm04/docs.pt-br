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
ms.openlocfilehash: 7e5fb3ab1d2dedb220fd4a486409512414233021
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795961"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="b7d41-102">Enumeração EClrUnhandledException</span><span class="sxs-lookup"><span data-stu-id="b7d41-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="b7d41-103">Descreve as opções disponíveis para o gerenciamento de exceções que são sem tratamento no código do usuário.</span><span class="sxs-lookup"><span data-stu-id="b7d41-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7d41-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7d41-104">Syntax</span></span>  
  
```  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="b7d41-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b7d41-105">Members</span></span>  
  
|<span data-ttu-id="b7d41-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b7d41-106">Member</span></span>|<span data-ttu-id="b7d41-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7d41-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="b7d41-108">Especifica que o comportamento padrão ocorre.</span><span class="sxs-lookup"><span data-stu-id="b7d41-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="b7d41-109">O processo é interrompido.</span><span class="sxs-lookup"><span data-stu-id="b7d41-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="b7d41-110">Especifica que o common language runtime (CLR) ignora as exceções sem tratamento e permite que o host determine nenhuma providência.</span><span class="sxs-lookup"><span data-stu-id="b7d41-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7d41-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7d41-111">Remarks</span></span>  
 <span data-ttu-id="b7d41-112">Para especificar que o CLR se comportam como nas versões anteriores, use o `eHostDeterminedPolicy` membro.</span><span class="sxs-lookup"><span data-stu-id="b7d41-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7d41-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7d41-113">Requirements</span></span>  
 <span data-ttu-id="b7d41-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7d41-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7d41-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b7d41-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b7d41-116">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b7d41-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7d41-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7d41-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7d41-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7d41-118">See also</span></span>

- [<span data-ttu-id="b7d41-119">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="b7d41-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="b7d41-120">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="b7d41-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="b7d41-121">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="b7d41-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="b7d41-122">Método SetUnhandledExceptionPolicy</span><span class="sxs-lookup"><span data-stu-id="b7d41-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="b7d41-123">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="b7d41-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="b7d41-124">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="b7d41-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
