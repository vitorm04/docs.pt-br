---
title: Coclass CLRRuntimeHost
ms.date: 03/30/2017
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bae2d134c412023d0f126453b5285662d994c78
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789591"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="ba4e1-102">Coclass CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="ba4e1-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="ba4e1-103">Fornece interfaces para gerenciar a execução de código em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ba4e1-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba4e1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba4e1-104">Syntax</span></span>  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="ba4e1-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="ba4e1-105">Interfaces</span></span>  
  
|<span data-ttu-id="ba4e1-106">Interface</span><span class="sxs-lookup"><span data-stu-id="ba4e1-106">Interface</span></span>|<span data-ttu-id="ba4e1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba4e1-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="ba4e1-108">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="ba4e1-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="ba4e1-109">Fornece métodos para controlar a execução de aplicativos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ba4e1-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="ba4e1-110">Interface ICLRValidator</span><span class="sxs-lookup"><span data-stu-id="ba4e1-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="ba4e1-111">Fornece métodos para a validação de imagens executáveis portáteis e relatórios detalhados de erros de validação.</span><span class="sxs-lookup"><span data-stu-id="ba4e1-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ba4e1-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ba4e1-112">Requirements</span></span>  
 <span data-ttu-id="ba4e1-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba4e1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba4e1-114">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="ba4e1-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="ba4e1-115">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ba4e1-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba4e1-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba4e1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba4e1-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba4e1-117">See also</span></span>

- [<span data-ttu-id="ba4e1-118">Coclasses de hospedagem</span><span class="sxs-lookup"><span data-stu-id="ba4e1-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
