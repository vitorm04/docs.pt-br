---
title: "Referência de API não gerenciada"
ms.custom: 
ms.date: 11/06/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- runtime, unmanaged APIs
- common language runtime, unmanaged APIs
- native API reference [.NET Framework]
- unmanaged API reference [.NET Framework]
ms.assetid: 9aa000ee-c04c-492c-ae4f-83ecdf4fdbbe
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9836d8d02bb81fc19a5b3a1714e32fcefeb8791d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="unmanaged-api-reference"></a><span data-ttu-id="4ff56-102">Referência de API não gerenciada</span><span class="sxs-lookup"><span data-stu-id="4ff56-102">Unmanaged API Reference</span></span>
<span data-ttu-id="4ff56-103">Esta seção inclui informações sobre APIs não gerenciadas que podem ser usadas por aplicativos relacionados a código gerenciado, como hosts de tempo de execução, compiladores, desmontadores, ofuscadores, depuradores e criadores de perfis.</span><span class="sxs-lookup"><span data-stu-id="4ff56-103">This section includes information on unmanaged APIs that can be used by managed-code-related applications, such as runtime hosts, compilers, disassemblers, obfuscators, debuggers, and profilers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4ff56-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="4ff56-104">In This Section</span></span>  
 [<span data-ttu-id="4ff56-105">Tipos de dados comuns</span><span class="sxs-lookup"><span data-stu-id="4ff56-105">Common Data Types</span></span>](../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)  
 <span data-ttu-id="4ff56-106">Lista os tipos de dados comuns que são usados, especialmente na criação de perfis não gerenciados e APIs de depuração.</span><span class="sxs-lookup"><span data-stu-id="4ff56-106">Lists the common data types that are used, particularly in the unmanaged profiling and debugging APIs.</span></span>  
  
 [<span data-ttu-id="4ff56-107">ALink</span><span class="sxs-lookup"><span data-stu-id="4ff56-107">ALink</span></span>](../../../docs/framework/unmanaged-api/alink/index.md)  
 <span data-ttu-id="4ff56-108">Descreve a API ALink, que oferece suporte à criação de assemblies do .NET Framework e módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="4ff56-108">Describes the ALink API, which supports the creation of .NET Framework assemblies and unbound modules.</span></span>  
  
 [<span data-ttu-id="4ff56-109">Authenticode</span><span class="sxs-lookup"><span data-stu-id="4ff56-109">Authenticode</span></span>](../../../docs/framework/unmanaged-api/authenticode/index.md)  
 <span data-ttu-id="4ff56-110">Oferece suporte à criação de licença Authenticode XrML e módulo de verificação.</span><span class="sxs-lookup"><span data-stu-id="4ff56-110">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
 [<span data-ttu-id="4ff56-111">Constantes</span><span class="sxs-lookup"><span data-stu-id="4ff56-111">Constants</span></span>](../../../docs/framework/unmanaged-api/constants-unmanaged-api-reference.md)  
 <span data-ttu-id="4ff56-112">Descreve as constantes que são definidas em CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="4ff56-112">Describes the constants that are defined in CorSym.idl.</span></span>  
  
 [<span data-ttu-id="4ff56-113">Atributos de Interface personalizada</span><span class="sxs-lookup"><span data-stu-id="4ff56-113">Custom Interface Attributes</span></span>](http://msdn.microsoft.com/en-us/940952f9-46ad-4a1a-920f-118dc0bdcd9f)  
 <span data-ttu-id="4ff56-114">Descreve os atributos de interface personalizada do COM (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="4ff56-114">Describes component object model (COM) custom interface attributes.</span></span>  
  
 [<span data-ttu-id="4ff56-115">Depuração</span><span class="sxs-lookup"><span data-stu-id="4ff56-115">Debugging</span></span>](../../../docs/framework/unmanaged-api/debugging/index.md)  
 <span data-ttu-id="4ff56-116">Descreve a API de depuração, que permite a um depurador depurar código que é executado no ambiente de tempo de execução de linguagem comum (CLR).</span><span class="sxs-lookup"><span data-stu-id="4ff56-116">Describes the debugging API, which enables a debugger to debug code that runs in the common language runtime (CLR) environment.</span></span>  
  
 [<span data-ttu-id="4ff56-117">Repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="4ff56-117">Diagnostics Symbol Store</span></span>](../../../docs/framework/unmanaged-api/diagnostics/index.md)  
 <span data-ttu-id="4ff56-118">Descreve a API de armazenamento de código de diagnóstico, que permite a um compilador gerar informações de símbolo para uso por um depurador.</span><span class="sxs-lookup"><span data-stu-id="4ff56-118">Describes the diagnostics symbol store API, which enables a compiler to generate symbol information for use by a debugger.</span></span>  
  
 [<span data-ttu-id="4ff56-119">Fusão</span><span class="sxs-lookup"><span data-stu-id="4ff56-119">Fusion</span></span>](../../../docs/framework/unmanaged-api/fusion/index.md)  
 <span data-ttu-id="4ff56-120">Descreve a API de fusão, que permite a um host de tempo de execução acessar as propriedades dos recursos de um aplicativo para localizar as versões corretas desses recursos para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4ff56-120">Describes the fusion API, which enables a runtime host to access the properties of an application's resources in order to locate the correct versions of those resources for the application.</span></span>  
  
 [<span data-ttu-id="4ff56-121">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="4ff56-121">Hosting</span></span>](../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="4ff56-122">Descreve a API de hospedagem, que permite a hosts não gerenciados integrar o CLR em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4ff56-122">Describes the hosting API, which enables unmanaged hosts to integrate the CLR into their applications.</span></span>  
  
 [<span data-ttu-id="4ff56-123">Metadados</span><span class="sxs-lookup"><span data-stu-id="4ff56-123">Metadata</span></span>](../../../docs/framework/unmanaged-api/metadata/index.md)  
 <span data-ttu-id="4ff56-124">Descreve a API de metadados, que permite a um cliente, como um compilador, gerar ou acessar os metadados de um componente sem os tipos serem carregados pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="4ff56-124">Describes the metadata API, which enables a client such as a compiler to generate or access a component's metadata without the types being loaded by the CLR.</span></span>  
  
 [<span data-ttu-id="4ff56-125">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="4ff56-125">Profiling</span></span>](../../../docs/framework/unmanaged-api/profiling/index.md)  
 <span data-ttu-id="4ff56-126">Descreve a API de criação de perfis, que permite a um criador de perfis monitorar a execução de um programa pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="4ff56-126">Describes the profiling API, which enables a profiler to monitor a program's execution by the CLR.</span></span>  
  
 [<span data-ttu-id="4ff56-127">Nomenclatura forte</span><span class="sxs-lookup"><span data-stu-id="4ff56-127">Strong Naming</span></span>](../../../docs/framework/unmanaged-api/strong-naming/index.md)  
 <span data-ttu-id="4ff56-128">Descreve a API de nomenclatura forte, que permite a um cliente administrar assinatura de nome forte para assemblies.</span><span class="sxs-lookup"><span data-stu-id="4ff56-128">Describes the strong naming API, which enables a client to administer strong name signing for assemblies.</span></span>  

 [<span data-ttu-id="4ff56-129">WMI e contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="4ff56-129">WMI and Performance Counters</span></span>](wmi/index.md)  
 <span data-ttu-id="4ff56-130">Descreve as APIs que envolvem chamadas para bibliotecas do Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="4ff56-130">Describes the APIs that wrap calls to Windows Management Instrumentation (WMI) libraries.</span></span>
  
 [<span data-ttu-id="4ff56-131">Funções auxiliares do Tlbexp</span><span class="sxs-lookup"><span data-stu-id="4ff56-131">Tlbexp Helper Functions</span></span>](../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="4ff56-132">Descreve as duas funções auxiliares e a interface usada pelo Exportador da Biblioteca de Tipos (Tlbexp.exe) durante o processo de conversão de assembly para biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="4ff56-132">Describes the two helper functions and interface used by the Type Library Exporter (Tlbexp.exe) during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4ff56-133">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="4ff56-133">Related Sections</span></span>  
 [<span data-ttu-id="4ff56-134">Guia de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="4ff56-134">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
  
 [<span data-ttu-id="4ff56-135">Leitura avançada para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4ff56-135">Advanced Reading for the .NET Framework</span></span>](http://msdn.microsoft.com/en-us/faae8083-fecb-4514-b133-b0a5a32a7c3c)
