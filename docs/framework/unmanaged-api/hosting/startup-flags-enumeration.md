---
title: Enumeração STARTUP_FLAGS
ms.date: 03/30/2017
api_name:
- STARTUP_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- STARTUP_FLAGS
helpviewer_keywords:
- STARTUP_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 4f043594-0c45-4bc6-988e-a6793f0d8d06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4680187de7318a6438bf6a5e6bd7c5f3acd05c2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43797840"
---
# <a name="startupflags-enumeration"></a><span data-ttu-id="b5972-102">Enumeração STARTUP_FLAGS</span><span class="sxs-lookup"><span data-stu-id="b5972-102">STARTUP_FLAGS Enumeration</span></span>
<span data-ttu-id="b5972-103">Contém valores que indicam o comportamento de inicialização do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b5972-103">Contains values that indicate the startup behavior of the common language runtime (CLR).</span></span> <span data-ttu-id="b5972-104">Por padrão, a coleta de lixo é não simultânea e somente a biblioteca de classe base é carregada para a área de domínio neutro.</span><span class="sxs-lookup"><span data-stu-id="b5972-104">By default, garbage collection is non-concurrent, and only the base class library is loaded into the domain-neutral area.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5972-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5972-105">Syntax</span></span>  
  
```  
typedef enum {  
    STARTUP_CONCURRENT_GC                         = 0x1,  
    STARTUP_LOADER_OPTIMIZATION_MASK              = 0x3<<1,  
    STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN     = 0x1<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN      = 0x2<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST = 0x3<<1,  
  
    STARTUP_LOADER_SAFEMODE                       = 0x10,  
    STARTUP_LOADER_SETPREFERENCE                  = 0x100,  
  
    STARTUP_SERVER_GC                             = 0x1000,  
    STARTUP_HOARD_GC_VM                           = 0x2000,  
  
    STARTUP_SINGLE_VERSION_HOSTING_INTERFACE      = 0x4000,  
    STARTUP_LEGACY_IMPERSONATION                  = 0x10000,  
    STARTUP_DISABLE_COMMITTHREADSTACK             = 0x20000,  
    STARTUP_ALWAYSFLOW_IMPERSONATION              = 0x40000,  
    STARTUP_TRIM_GC_COMMIT                        = 0x80000,  
  
    STARTUP_ETW                                   = 0x100000,  
    STARTUP_ARM                                   = 0x400000  
} STARTUP_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="b5972-106">Membros</span><span class="sxs-lookup"><span data-stu-id="b5972-106">Members</span></span>  
  
|<span data-ttu-id="b5972-107">Membro</span><span class="sxs-lookup"><span data-stu-id="b5972-107">Member</span></span>|<span data-ttu-id="b5972-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5972-108">Description</span></span>|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|<span data-ttu-id="b5972-109">Especifica que a coleta de lixo simultânea deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="b5972-109">Specifies that concurrent garbage collection should be used.</span></span> <span data-ttu-id="b5972-110">Se o chamador solicita a compilação do servidor e coleta de lixo simultânea em um computador de processador único, a compilação de estação de trabalho e a coleta de lixo não simultânea são executadas em vez disso.</span><span class="sxs-lookup"><span data-stu-id="b5972-110">If the caller asks for the server build and concurrent garbage collection on a single-processor machine, the workstation build and non-concurrent garbage collection are run instead.</span></span> <span data-ttu-id="b5972-111">**Observação:** coleta de lixo simultânea não é suportada em aplicativos que estão executando o WOW64 x86 emulator em sistemas de 64 bits que implementam a arquitetura Intel Itanium (chamada anteriormente de IA-64).</span><span class="sxs-lookup"><span data-stu-id="b5972-111">**Note:**  Concurrent garbage collection is not supported in applications that are running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="b5972-112">Para obter mais informações sobre como usar WOW64 em sistemas Windows de 64 bits, consulte [aplicativos de 32 bits em execução](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="b5972-112">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|<span data-ttu-id="b5972-113">Especifica que a otimização do carregador deverá ocorrer.</span><span class="sxs-lookup"><span data-stu-id="b5972-113">Specifies that loader optimization shall occur.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|<span data-ttu-id="b5972-114">Especifica que nenhum assembly é carregados como domínio neutro.</span><span class="sxs-lookup"><span data-stu-id="b5972-114">Specifies that no assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|<span data-ttu-id="b5972-115">Especifica que todos os assemblies são carregados como domínio neutro.</span><span class="sxs-lookup"><span data-stu-id="b5972-115">Specifies that all assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|<span data-ttu-id="b5972-116">Especifica que todos os assemblies de nome forte são carregados como domínio neutro.</span><span class="sxs-lookup"><span data-stu-id="b5972-116">Specifies that all strong-named assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_SAFEMODE`|<span data-ttu-id="b5972-117">Especifica que a política de versão CLR não será aplicada para a versão passada.</span><span class="sxs-lookup"><span data-stu-id="b5972-117">Specifies that CLR version policy will not be applied to the version passed in.</span></span> <span data-ttu-id="b5972-118">A versão exata especificada do CLR será carregada.</span><span class="sxs-lookup"><span data-stu-id="b5972-118">The exact version specified of the CLR will be loaded.</span></span> <span data-ttu-id="b5972-119">O shim não avalia a política para determinar a versão mais recente compatível.</span><span class="sxs-lookup"><span data-stu-id="b5972-119">The shim does not evaluate policy to determine the latest compatible version.</span></span>|  
|`STARTUP_LOADER_SETPREFERENCE`|<span data-ttu-id="b5972-120">Especifica que o tempo de execução preferencial será definido, mas na verdade não é iniciado.</span><span class="sxs-lookup"><span data-stu-id="b5972-120">Specifies that the preferred runtime will be set, but not actually started.</span></span>|  
|`STARTUP_SERVER_GC`|<span data-ttu-id="b5972-121">Especifica que a coleta de lixo do servidor será usada.</span><span class="sxs-lookup"><span data-stu-id="b5972-121">Specifies that the server garbage collection will be used.</span></span>|  
|`STARTUP_HOARD_GC_VM`|<span data-ttu-id="b5972-122">Especifica que a coleta de lixo manterá o endereço virtual usado.</span><span class="sxs-lookup"><span data-stu-id="b5972-122">Specifies that garbage collection will keep the virtual address used.</span></span>|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|<span data-ttu-id="b5972-123">Especifica que a combinação de uma interface de hospedagem não será permitida.</span><span class="sxs-lookup"><span data-stu-id="b5972-123">Specifies that mixing a hosting interface will not be allowed.</span></span>|  
|`STARTUP_LEGACY_IMPERSONATION`|<span data-ttu-id="b5972-124">Especifica a representação não deve fluir entre pontos assíncronos por padrão.</span><span class="sxs-lookup"><span data-stu-id="b5972-124">Specifies that impersonation should not flow across asynchronous points by default.</span></span>|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|<span data-ttu-id="b5972-125">Especifica que a pilha completa de threads não deve ser confirmada quando o thread for executado.</span><span class="sxs-lookup"><span data-stu-id="b5972-125">Specifies that the full thread stack should not be committed when the thread starts running.</span></span>|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|<span data-ttu-id="b5972-126">Especifica que as representações gerenciadas e as representações obtidas por meio da plataforma de invocação será flua entre pontos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="b5972-126">Specifies that managed impersonations and impersonations achieved through platform invoke will flow across asynchronous points.</span></span> <span data-ttu-id="b5972-127">Por padrão, somente as representações gerenciadas fluirão entre pontos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="b5972-127">By default, only managed impersonations will flow across asynchronous points.</span></span>|  
|`STARTUP_TRIM_GC_COMMIT`|<span data-ttu-id="b5972-128">Especifica que a coleta de lixo usará menos espaço comprometido quando a memória do sistema é insuficiente.</span><span class="sxs-lookup"><span data-stu-id="b5972-128">Specifies that garbage collection will use less committed space when system memory is low.</span></span> <span data-ttu-id="b5972-129">Ver `gcTrimCommitOnLowMemory` na [otimização para hospedagem na Web compartilhada](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="b5972-129">See `gcTrimCommitOnLowMemory` in [Optimization for Shared Web Hosting](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).</span></span>|  
|`STARTUP_ETW`|<span data-ttu-id="b5972-130">Especifica que o rastreamento de eventos para Windows (ETW) é habilitado para eventos do common language runtime.</span><span class="sxs-lookup"><span data-stu-id="b5972-130">Specifies that event tracing for Windows (ETW) is enabled for common language runtime events.</span></span> <span data-ttu-id="b5972-131">Começando com o Windows Vista, o rastreamento de eventos está sempre habilitado, portanto, esse sinalizador não tem nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="b5972-131">Beginning with Windows Vista, event tracing is always enabled, so this flag has no effect.</span></span> <span data-ttu-id="b5972-132">Ver [controlando o log do .NET Framework](../../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="b5972-132">See [Controlling .NET Framework Logging](../../../../docs/framework/performance/controlling-logging.md).</span></span>|  
|`STARTUP_ARM`|<span data-ttu-id="b5972-133">Especifica que o monitoramento de recursos de domínio do aplicativo está habilitado.</span><span class="sxs-lookup"><span data-stu-id="b5972-133">Specifies that application domain resource monitoring is enabled.</span></span> <span data-ttu-id="b5972-134">Consulte a <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> propriedade e [ \<appDomainResourceMonitoring > elemento](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span><span class="sxs-lookup"><span data-stu-id="b5972-134">See the <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> property and [\<appDomainResourceMonitoring> Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b5972-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5972-135">Requirements</span></span>  
 <span data-ttu-id="b5972-136">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5972-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5972-137">**Cabeçalho:** mscoree. H</span><span class="sxs-lookup"><span data-stu-id="b5972-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b5972-138">**Biblioteca:** mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b5972-138">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5972-139">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5972-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5972-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5972-140">See Also</span></span>  
 [<span data-ttu-id="b5972-141">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="b5972-141">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
