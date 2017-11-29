---
title: Coclass CLRRuntimeHost
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRRuntimeHost Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CLRRuntimeHost
helpviewer_keywords: CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 372b2466baaa76ba47a6710447d93f9fa6bb967f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="62f29-102">Coclass CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="62f29-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="62f29-103">Fornece interfaces para gerenciar a execução de código em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="62f29-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62f29-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="62f29-104">Syntax</span></span>  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="62f29-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="62f29-105">Interfaces</span></span>  
  
|<span data-ttu-id="62f29-106">Interface</span><span class="sxs-lookup"><span data-stu-id="62f29-106">Interface</span></span>|<span data-ttu-id="62f29-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="62f29-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="62f29-108">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="62f29-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="62f29-109">Fornece métodos para controlar a execução de aplicativos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="62f29-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="62f29-110">Interface ICLRValidator</span><span class="sxs-lookup"><span data-stu-id="62f29-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="62f29-111">Fornece métodos para validação de imagens executáveis portáteis e os relatórios detalhados de erros de validação.</span><span class="sxs-lookup"><span data-stu-id="62f29-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62f29-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="62f29-112">Requirements</span></span>  
 <span data-ttu-id="62f29-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62f29-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62f29-114">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="62f29-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="62f29-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="62f29-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62f29-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62f29-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f29-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62f29-117">See Also</span></span>  
 [<span data-ttu-id="62f29-118">Coclasses de hospedagem</span><span class="sxs-lookup"><span data-stu-id="62f29-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
