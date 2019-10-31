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
ms.openlocfilehash: 512009e053605e2018f1fcbafa422c1a36ddecc1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136900"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="37c95-102">Coclass CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="37c95-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="37c95-103">Fornece interfaces para gerenciar aplicativos que estão sendo executados pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="37c95-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37c95-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37c95-104">Syntax</span></span>  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="37c95-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="37c95-105">Interfaces</span></span>  
  
|<span data-ttu-id="37c95-106">Interface</span><span class="sxs-lookup"><span data-stu-id="37c95-106">Interface</span></span>|<span data-ttu-id="37c95-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="37c95-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="37c95-108">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="37c95-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="37c95-109">Fornece métodos para configurar o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="37c95-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="37c95-110">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="37c95-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="37c95-111">Fornece métodos que permitem que o host inicie e pare o Common Language Runtime explicitamente, para criar e configurar domínios de aplicativo, acessar o domínio padrão e enumerar todos os domínios em execução no processo.</span><span class="sxs-lookup"><span data-stu-id="37c95-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="37c95-112">Interface IDebuggerInfo</span><span class="sxs-lookup"><span data-stu-id="37c95-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="37c95-113">Fornece métodos para obter informações sobre o estado dos serviços de depuração.</span><span class="sxs-lookup"><span data-stu-id="37c95-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="37c95-114">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="37c95-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="37c95-115">Fornece métodos para obter informações sobre o sistema de coleta de lixo e para controlar alguns aspectos da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="37c95-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="37c95-116">IValidator</span><span class="sxs-lookup"><span data-stu-id="37c95-116">"IValidator"</span></span>|<span data-ttu-id="37c95-117">Fornece métodos para validação de imagens executáveis portáteis e relatórios detalhados de erros de validação.</span><span class="sxs-lookup"><span data-stu-id="37c95-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="37c95-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="37c95-118">Requirements</span></span>  
 <span data-ttu-id="37c95-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37c95-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37c95-120">**Cabeçalho:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="37c95-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="37c95-121">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="37c95-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37c95-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37c95-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37c95-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37c95-123">See also</span></span>

- [<span data-ttu-id="37c95-124">Coclasses de hospedagem</span><span class="sxs-lookup"><span data-stu-id="37c95-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
