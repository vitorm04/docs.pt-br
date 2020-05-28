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
ms.openlocfilehash: b4694efffa0a3dd6fed1f97fc2359c5eb335d440
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006409"
---
# <a name="startup_flags-enumeration"></a><span data-ttu-id="88369-102">Enumeração STARTUP_FLAGS</span><span class="sxs-lookup"><span data-stu-id="88369-102">STARTUP_FLAGS Enumeration</span></span>
<span data-ttu-id="88369-103">Contém valores que indicam o comportamento de inicialização do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="88369-103">Contains values that indicate the startup behavior of the common language runtime (CLR).</span></span> <span data-ttu-id="88369-104">Por padrão, a coleta de lixo não é simultânea e somente a biblioteca de classes base é carregada na área de domínio neutro.</span><span class="sxs-lookup"><span data-stu-id="88369-104">By default, garbage collection is non-concurrent, and only the base class library is loaded into the domain-neutral area.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88369-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88369-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="88369-106">Membros</span><span class="sxs-lookup"><span data-stu-id="88369-106">Members</span></span>  
  
|<span data-ttu-id="88369-107">Membro</span><span class="sxs-lookup"><span data-stu-id="88369-107">Member</span></span>|<span data-ttu-id="88369-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="88369-108">Description</span></span>|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|<span data-ttu-id="88369-109">Especifica que a coleta de lixo simultânea deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="88369-109">Specifies that concurrent garbage collection should be used.</span></span> <span data-ttu-id="88369-110">Se o chamador solicitar a compilação do servidor e a coleta de lixo simultânea em um computador com um único processador, a compilação da estação de trabalho e a coleta de lixo não simultânea serão executadas em vez disso.</span><span class="sxs-lookup"><span data-stu-id="88369-110">If the caller asks for the server build and concurrent garbage collection on a single-processor machine, the workstation build and non-concurrent garbage collection are run instead.</span></span> <span data-ttu-id="88369-111">**Observação:**  Não há suporte para a coleta de lixo simultânea em aplicativos que executam o emulador x86 WOW64 em sistemas de 64 bits que implementam a arquitetura Intel Itanium (anteriormente chamada IA-64).</span><span class="sxs-lookup"><span data-stu-id="88369-111">**Note:**  Concurrent garbage collection is not supported in applications that are running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="88369-112">Para obter mais informações sobre como usar o WOW64 em sistemas Windows de 64 bits, consulte [executando aplicativos de 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="88369-112">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|<span data-ttu-id="88369-113">Especifica que a otimização do carregador deve ocorrer.</span><span class="sxs-lookup"><span data-stu-id="88369-113">Specifies that loader optimization shall occur.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|<span data-ttu-id="88369-114">Especifica que nenhum assembly é carregado como domínio neutro.</span><span class="sxs-lookup"><span data-stu-id="88369-114">Specifies that no assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|<span data-ttu-id="88369-115">Especifica que todos os assemblies são carregados como domínio neutro.</span><span class="sxs-lookup"><span data-stu-id="88369-115">Specifies that all assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|<span data-ttu-id="88369-116">Especifica que todos os assemblies de nome forte são carregados como domínio neutro.</span><span class="sxs-lookup"><span data-stu-id="88369-116">Specifies that all strong-named assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_SAFEMODE`|<span data-ttu-id="88369-117">Especifica que a política de versão do CLR não será aplicada à versão passada.</span><span class="sxs-lookup"><span data-stu-id="88369-117">Specifies that CLR version policy will not be applied to the version passed in.</span></span> <span data-ttu-id="88369-118">A versão exata especificada do CLR será carregada.</span><span class="sxs-lookup"><span data-stu-id="88369-118">The exact version specified of the CLR will be loaded.</span></span> <span data-ttu-id="88369-119">O Shim não avalia a política para determinar a versão mais recente compatível.</span><span class="sxs-lookup"><span data-stu-id="88369-119">The shim does not evaluate policy to determine the latest compatible version.</span></span>|  
|`STARTUP_LOADER_SETPREFERENCE`|<span data-ttu-id="88369-120">Especifica que o tempo de execução preferencial será definido, mas não iniciado de fato.</span><span class="sxs-lookup"><span data-stu-id="88369-120">Specifies that the preferred runtime will be set, but not actually started.</span></span>|  
|`STARTUP_SERVER_GC`|<span data-ttu-id="88369-121">Especifica que a coleta de lixo do servidor será usada.</span><span class="sxs-lookup"><span data-stu-id="88369-121">Specifies that the server garbage collection will be used.</span></span>|  
|`STARTUP_HOARD_GC_VM`|<span data-ttu-id="88369-122">Especifica que a coleta de lixo manterá o endereço virtual usado.</span><span class="sxs-lookup"><span data-stu-id="88369-122">Specifies that garbage collection will keep the virtual address used.</span></span>|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|<span data-ttu-id="88369-123">Especifica que a combinação de uma interface de hospedagem não será permitida.</span><span class="sxs-lookup"><span data-stu-id="88369-123">Specifies that mixing a hosting interface will not be allowed.</span></span>|  
|`STARTUP_LEGACY_IMPERSONATION`|<span data-ttu-id="88369-124">Especifica que a representação não deve fluir entre pontos assíncronos por padrão.</span><span class="sxs-lookup"><span data-stu-id="88369-124">Specifies that impersonation should not flow across asynchronous points by default.</span></span>|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|<span data-ttu-id="88369-125">Especifica que a pilha de threads completa não deve ser confirmada quando o thread inicia a execução.</span><span class="sxs-lookup"><span data-stu-id="88369-125">Specifies that the full thread stack should not be committed when the thread starts running.</span></span>|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|<span data-ttu-id="88369-126">Especifica que as impessoas gerenciadas e as impessoas obtidas por meio da invocação de plataforma fluirão entre pontos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="88369-126">Specifies that managed impersonations and impersonations achieved through platform invoke will flow across asynchronous points.</span></span> <span data-ttu-id="88369-127">Por padrão, somente as impessoas gerenciadas serão fluidas entre pontos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="88369-127">By default, only managed impersonations will flow across asynchronous points.</span></span>|  
|`STARTUP_TRIM_GC_COMMIT`|<span data-ttu-id="88369-128">Especifica que a coleta de lixo usará menos espaço confirmado quando a memória do sistema estiver baixa.</span><span class="sxs-lookup"><span data-stu-id="88369-128">Specifies that garbage collection will use less committed space when system memory is low.</span></span> <span data-ttu-id="88369-129">Consulte `gcTrimCommitOnLowMemory` em [otimização para hospedagem na Web compartilhada](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="88369-129">See `gcTrimCommitOnLowMemory` in [Optimization for Shared Web Hosting](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md).</span></span>|  
|`STARTUP_ETW`|<span data-ttu-id="88369-130">Especifica que o ETW (rastreamento de eventos para Windows) está habilitado para eventos de Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="88369-130">Specifies that event tracing for Windows (ETW) is enabled for common language runtime events.</span></span> <span data-ttu-id="88369-131">A partir do Windows Vista, o rastreamento de eventos está sempre habilitado, portanto, esse sinalizador não tem nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="88369-131">Beginning with Windows Vista, event tracing is always enabled, so this flag has no effect.</span></span> <span data-ttu-id="88369-132">Consulte [controlando o log de .NET Framework](../../performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="88369-132">See [Controlling .NET Framework Logging](../../performance/controlling-logging.md).</span></span>|  
|`STARTUP_ARM`|<span data-ttu-id="88369-133">Especifica que o monitoramento de recursos de domínio de aplicativo está habilitado.</span><span class="sxs-lookup"><span data-stu-id="88369-133">Specifies that application domain resource monitoring is enabled.</span></span> <span data-ttu-id="88369-134">Consulte a <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> propriedade e o [ \<appDomainResourceMonitoring> elemento](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span><span class="sxs-lookup"><span data-stu-id="88369-134">See the <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> property and [\<appDomainResourceMonitoring> Element](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="88369-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88369-135">Requirements</span></span>  
 <span data-ttu-id="88369-136">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88369-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88369-137">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="88369-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="88369-138">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="88369-138">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88369-139">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88369-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88369-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="88369-140">See also</span></span>

- [<span data-ttu-id="88369-141">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="88369-141">Hosting Enumerations</span></span>](hosting-enumerations.md)
