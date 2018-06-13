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
ms.openlocfilehash: bc1d3ffc34cd74d68bf10cb677b68f0a75bb7c67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444224"
---
# <a name="startupflags-enumeration"></a><span data-ttu-id="43834-102">Enumeração STARTUP_FLAGS</span><span class="sxs-lookup"><span data-stu-id="43834-102">STARTUP_FLAGS Enumeration</span></span>
<span data-ttu-id="43834-103">Contém valores que indicam o comportamento de inicialização do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="43834-103">Contains values that indicate the startup behavior of the common language runtime (CLR).</span></span> <span data-ttu-id="43834-104">Por padrão, a coleta de lixo é não simultânea e somente é carregar a biblioteca de classe base para a área de um domínio neutro.</span><span class="sxs-lookup"><span data-stu-id="43834-104">By default, garbage collection is non-concurrent, and only the base class library is loaded into the domain-neutral area.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43834-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43834-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="43834-106">Membros</span><span class="sxs-lookup"><span data-stu-id="43834-106">Members</span></span>  
  
|<span data-ttu-id="43834-107">Membro</span><span class="sxs-lookup"><span data-stu-id="43834-107">Member</span></span>|<span data-ttu-id="43834-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="43834-108">Description</span></span>|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|<span data-ttu-id="43834-109">Especifica que a coleta de lixo simultânea deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="43834-109">Specifies that concurrent garbage collection should be used.</span></span> <span data-ttu-id="43834-110">Se o chamador solicita a criação do servidor e a coleta de lixo simultânea em um computador com processador único, a criação de estação de trabalho e a coleta de lixo não simultânea são executados em vez disso.</span><span class="sxs-lookup"><span data-stu-id="43834-110">If the caller asks for the server build and concurrent garbage collection on a single-processor machine, the workstation build and non-concurrent garbage collection are run instead.</span></span> <span data-ttu-id="43834-111">**Observação:** não há suporte para a coleta de lixo simultânea em aplicativos que estão executando o WOW64 x86 emulador em sistemas de 64 bits que implementam a arquitetura Intel Itanium (anteriormente chamado de IA-64).</span><span class="sxs-lookup"><span data-stu-id="43834-111">**Note:**  Concurrent garbage collection is not supported in applications that are running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="43834-112">Para obter mais informações sobre como usar o WOW64 em sistemas de 64 bits do Windows, consulte [aplicativos em execução de 32 bits](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span><span class="sxs-lookup"><span data-stu-id="43834-112">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|<span data-ttu-id="43834-113">Especifica que otimização carregador deve ocorrer.</span><span class="sxs-lookup"><span data-stu-id="43834-113">Specifies that loader optimization shall occur.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|<span data-ttu-id="43834-114">Especifica que nenhum assembly é carregados como domínios neutros.</span><span class="sxs-lookup"><span data-stu-id="43834-114">Specifies that no assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|<span data-ttu-id="43834-115">Especifica que todos os assemblies são carregados como domínios neutros.</span><span class="sxs-lookup"><span data-stu-id="43834-115">Specifies that all assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|<span data-ttu-id="43834-116">Especifica que todos os assemblies de nomes fortes são carregados como domínios neutros.</span><span class="sxs-lookup"><span data-stu-id="43834-116">Specifies that all strong-named assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_SAFEMODE`|<span data-ttu-id="43834-117">Especifica que diretiva de versão do CLR não será aplicada para a versão passada.</span><span class="sxs-lookup"><span data-stu-id="43834-117">Specifies that CLR version policy will not be applied to the version passed in.</span></span> <span data-ttu-id="43834-118">A versão exata especificada do CLR será carregada.</span><span class="sxs-lookup"><span data-stu-id="43834-118">The exact version specified of the CLR will be loaded.</span></span> <span data-ttu-id="43834-119">A correção não avalia a política para determinar a versão compatível mais recente.</span><span class="sxs-lookup"><span data-stu-id="43834-119">The shim does not evaluate policy to determine the latest compatible version.</span></span>|  
|`STARTUP_LOADER_SETPREFERENCE`|<span data-ttu-id="43834-120">Especifica que o tempo de execução preferencial será definido, mas na verdade não iniciado.</span><span class="sxs-lookup"><span data-stu-id="43834-120">Specifies that the preferred runtime will be set, but not actually started.</span></span>|  
|`STARTUP_SERVER_GC`|<span data-ttu-id="43834-121">Especifica que a coleta de lixo do servidor será usada.</span><span class="sxs-lookup"><span data-stu-id="43834-121">Specifies that the server garbage collection will be used.</span></span>|  
|`STARTUP_HOARD_GC_VM`|<span data-ttu-id="43834-122">Especifica que a coleta de lixo manterá o endereço virtual usado.</span><span class="sxs-lookup"><span data-stu-id="43834-122">Specifies that garbage collection will keep the virtual address used.</span></span>|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|<span data-ttu-id="43834-123">Especifica que a combinação de uma interface de hospedagem não será permitida.</span><span class="sxs-lookup"><span data-stu-id="43834-123">Specifies that mixing a hosting interface will not be allowed.</span></span>|  
|`STARTUP_LEGACY_IMPERSONATION`|<span data-ttu-id="43834-124">Especifica a representação não deve fluir pelos pontos assíncronos por padrão.</span><span class="sxs-lookup"><span data-stu-id="43834-124">Specifies that impersonation should not flow across asynchronous points by default.</span></span>|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|<span data-ttu-id="43834-125">Especifica que a pilha do thread total não deve ser confirmada quando o thread é iniciado.</span><span class="sxs-lookup"><span data-stu-id="43834-125">Specifies that the full thread stack should not be committed when the thread starts running.</span></span>|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|<span data-ttu-id="43834-126">Especifica que a invocação de representações gerenciadas e representações obtidas por meio de plataforma será fluxo pelos pontos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="43834-126">Specifies that managed impersonations and impersonations achieved through platform invoke will flow across asynchronous points.</span></span> <span data-ttu-id="43834-127">Por padrão, somente as representações gerenciadas fluirá pelos pontos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="43834-127">By default, only managed impersonations will flow across asynchronous points.</span></span>|  
|`STARTUP_TRIM_GC_COMMIT`|<span data-ttu-id="43834-128">Especifica que a coleta de lixo usará espaço menor confirmado quando a memória do sistema é insuficiente.</span><span class="sxs-lookup"><span data-stu-id="43834-128">Specifies that garbage collection will use less committed space when system memory is low.</span></span> <span data-ttu-id="43834-129">Consulte `gcTrimCommitOnLowMemory` na [otimização da hospedagem Web compartilhada](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="43834-129">See `gcTrimCommitOnLowMemory` in [Optimization for Shared Web Hosting](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).</span></span>|  
|`STARTUP_ETW`|<span data-ttu-id="43834-130">Especifica que o rastreamento de eventos para Windows (ETW) está habilitado para eventos de tempo de execução de linguagem comum.</span><span class="sxs-lookup"><span data-stu-id="43834-130">Specifies that event tracing for Windows (ETW) is enabled for common language runtime events.</span></span> <span data-ttu-id="43834-131">Começando com o Windows Vista, o rastreamento de eventos está sempre habilitado, portanto esse sinalizador não tem nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="43834-131">Beginning with Windows Vista, event tracing is always enabled, so this flag has no effect.</span></span> <span data-ttu-id="43834-132">Consulte [controlando o log do .NET Framework](../../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="43834-132">See [Controlling .NET Framework Logging](../../../../docs/framework/performance/controlling-logging.md).</span></span>|  
|`STARTUP_ARM`|<span data-ttu-id="43834-133">Especifica que o monitoramento de recursos do domínio de aplicativo está habilitado.</span><span class="sxs-lookup"><span data-stu-id="43834-133">Specifies that application domain resource monitoring is enabled.</span></span> <span data-ttu-id="43834-134">Consulte o <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> propriedade e [ \<appDomainResourceMonitoring > elemento](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span><span class="sxs-lookup"><span data-stu-id="43834-134">See the <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> property and [\<appDomainResourceMonitoring> Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="43834-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="43834-135">Requirements</span></span>  
 <span data-ttu-id="43834-136">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43834-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43834-137">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="43834-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43834-138">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="43834-138">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43834-139">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43834-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43834-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43834-140">See Also</span></span>  
 [<span data-ttu-id="43834-141">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="43834-141">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
