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
ms.openlocfilehash: 7c81a39acee31986421c810e2814a4f7e6c4d970
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597522"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="faa11-102">Coclass CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="faa11-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="faa11-103">Fornece interfaces para gerenciar aplicativos que estão sendo executados pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="faa11-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faa11-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="faa11-104">Syntax</span></span>  
  
```  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="faa11-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="faa11-105">Interfaces</span></span>  
  
|<span data-ttu-id="faa11-106">Interface</span><span class="sxs-lookup"><span data-stu-id="faa11-106">Interface</span></span>|<span data-ttu-id="faa11-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="faa11-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="faa11-108">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="faa11-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="faa11-109">Fornece métodos para configurar o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="faa11-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="faa11-110">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="faa11-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="faa11-111">Fornece métodos que permitem que o host iniciar e parar o common language runtime explicitamente, para criar e configurar domínios do aplicativo, para acessar o domínio padrão e para enumerar todos os domínios em execução no processo.</span><span class="sxs-lookup"><span data-stu-id="faa11-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="faa11-112">Interface IDebuggerInfo</span><span class="sxs-lookup"><span data-stu-id="faa11-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="faa11-113">Fornece métodos para obter informações sobre o estado dos serviços de depuração.</span><span class="sxs-lookup"><span data-stu-id="faa11-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="faa11-114">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="faa11-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="faa11-115">Fornece métodos para obter informações sobre o sistema de coleta de lixo e para controlar alguns aspectos da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="faa11-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="faa11-116">"IValidator"</span><span class="sxs-lookup"><span data-stu-id="faa11-116">"IValidator"</span></span>|<span data-ttu-id="faa11-117">Fornece métodos para validação de imagens executáveis portáteis e relatórios detalhados de erros de validação.</span><span class="sxs-lookup"><span data-stu-id="faa11-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="faa11-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="faa11-118">Requirements</span></span>  
 <span data-ttu-id="faa11-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faa11-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faa11-120">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="faa11-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="faa11-121">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="faa11-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="faa11-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faa11-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faa11-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="faa11-123">See also</span></span>
- [<span data-ttu-id="faa11-124">Coclasses de hospedagem</span><span class="sxs-lookup"><span data-stu-id="faa11-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
