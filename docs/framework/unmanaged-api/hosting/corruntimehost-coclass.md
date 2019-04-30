---
title: Coclass CorRuntimeHost
ms.date: 03/30/2017
api_name:
- CorRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRuntimeHost
helpviewer_keywords:
- CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2143fc13db1757ac2fa8a9c5a43f104a0c519ca0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985823"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="50056-102">Coclass CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="50056-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="50056-103">Fornece interfaces para gerenciar aplicativos que estão sendo executados pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="50056-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50056-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="50056-104">Syntax</span></span>  
  
```  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="50056-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="50056-105">Interfaces</span></span>  
  
|<span data-ttu-id="50056-106">Interface</span><span class="sxs-lookup"><span data-stu-id="50056-106">Interface</span></span>|<span data-ttu-id="50056-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="50056-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="50056-108">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="50056-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="50056-109">Fornece métodos para configurar o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="50056-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="50056-110">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="50056-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="50056-111">Fornece métodos que permitem que o host iniciar e parar o common language runtime explicitamente, para criar e configurar domínios do aplicativo, para acessar o domínio padrão e para enumerar todos os domínios em execução no processo.</span><span class="sxs-lookup"><span data-stu-id="50056-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="50056-112">Interface IDebuggerInfo</span><span class="sxs-lookup"><span data-stu-id="50056-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="50056-113">Fornece métodos para obter informações sobre o estado dos serviços de depuração.</span><span class="sxs-lookup"><span data-stu-id="50056-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="50056-114">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="50056-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="50056-115">Fornece métodos para obter informações sobre o sistema de coleta de lixo e para controlar alguns aspectos da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="50056-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="50056-116">"IValidator"</span><span class="sxs-lookup"><span data-stu-id="50056-116">"IValidator"</span></span>|<span data-ttu-id="50056-117">Fornece métodos para validação de imagens executáveis portáteis e relatórios detalhados de erros de validação.</span><span class="sxs-lookup"><span data-stu-id="50056-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="50056-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="50056-118">Requirements</span></span>  
 <span data-ttu-id="50056-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50056-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50056-120">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="50056-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="50056-121">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="50056-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50056-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50056-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50056-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50056-123">See also</span></span>

- [<span data-ttu-id="50056-124">Coclasses de hospedagem</span><span class="sxs-lookup"><span data-stu-id="50056-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
