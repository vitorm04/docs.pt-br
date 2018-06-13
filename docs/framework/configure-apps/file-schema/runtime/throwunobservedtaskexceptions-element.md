---
title: '&lt;ThrowUnobservedTaskExceptions&gt; elemento'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f72bedbaaf0b15ade7ff6b7b8c3edcdfd3fda6d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749420"
---
# <a name="ltthrowunobservedtaskexceptionsgt-element"></a><span data-ttu-id="31f8b-102">&lt;ThrowUnobservedTaskExceptions&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="31f8b-102">&lt;ThrowUnobservedTaskExceptions&gt; Element</span></span>
<span data-ttu-id="31f8b-103">Especifica se as exceções de tarefas sem tratamento devem encerrar um processo em execução.</span><span class="sxs-lookup"><span data-stu-id="31f8b-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
 <span data-ttu-id="31f8b-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="31f8b-104">\<configuration></span></span>  
<span data-ttu-id="31f8b-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="31f8b-105">\<runtime></span></span>  
<span data-ttu-id="31f8b-106">\<ThrowUnobservedTaskExceptions ></span><span class="sxs-lookup"><span data-stu-id="31f8b-106">\<ThrowUnobservedTaskExceptions></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31f8b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31f8b-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31f8b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="31f8b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="31f8b-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="31f8b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31f8b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="31f8b-110">Attributes</span></span>  
  
|<span data-ttu-id="31f8b-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="31f8b-111">Attribute</span></span>|<span data-ttu-id="31f8b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="31f8b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="31f8b-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="31f8b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="31f8b-114">Especifica se as exceções de tarefa não manipulada devem encerrar o processo em execução.</span><span class="sxs-lookup"><span data-stu-id="31f8b-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="31f8b-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="31f8b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="31f8b-116">Valor</span><span class="sxs-lookup"><span data-stu-id="31f8b-116">Value</span></span>|<span data-ttu-id="31f8b-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="31f8b-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="31f8b-118">Não encerra o processo em execução para uma exceção sem tratamento de tarefa.</span><span class="sxs-lookup"><span data-stu-id="31f8b-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="31f8b-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="31f8b-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="31f8b-120">Encerra o processo em execução para uma exceção sem tratamento de tarefa.</span><span class="sxs-lookup"><span data-stu-id="31f8b-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31f8b-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="31f8b-121">Child Elements</span></span>  
 <span data-ttu-id="31f8b-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="31f8b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="31f8b-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="31f8b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="31f8b-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="31f8b-124">Element</span></span>|<span data-ttu-id="31f8b-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="31f8b-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="31f8b-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="31f8b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="31f8b-127">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="31f8b-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="31f8b-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="31f8b-128">Remarks</span></span>  
 <span data-ttu-id="31f8b-129">Se uma exceção que é associada com um <xref:System.Threading.Tasks.Task> não está presente, não há nenhum <xref:System.Threading.Tasks.Task.Wait%2A> operação, o pai não está anexada e o <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> propriedade não foi lido a exceção de tarefa é considerada a ser observada.</span><span class="sxs-lookup"><span data-stu-id="31f8b-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="31f8b-130">No [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], por padrão, se um <xref:System.Threading.Tasks.Task> que tem um observada exceção é coletado como lixo, o finalizador lança uma exceção e encerra o processo.</span><span class="sxs-lookup"><span data-stu-id="31f8b-130">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="31f8b-131">O encerramento do processo é determinado pelo tempo de coleta de lixo e finalização.</span><span class="sxs-lookup"><span data-stu-id="31f8b-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="31f8b-132">Para tornar mais fácil para os desenvolvedores a gravar código assíncrono baseado em tarefas, o [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] altera esse comportamento padrão para exceções observadas.</span><span class="sxs-lookup"><span data-stu-id="31f8b-132">To make it easier for developers to write asynchronous code based on tasks, the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="31f8b-133">Observada exceções ainda farão com que o <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> evento ser gerado, mas por padrão, o processo não terminar.</span><span class="sxs-lookup"><span data-stu-id="31f8b-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="31f8b-134">Em vez disso, a exceção será ignorada após o evento é gerado, independentemente se um manipulador de eventos observa a exceção.</span><span class="sxs-lookup"><span data-stu-id="31f8b-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="31f8b-135">No [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], você pode usar o [ \<ThrowUnobservedTaskExceptions > elemento](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) em um arquivo de configuração do aplicativo para habilitar o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] comportamento de gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="31f8b-135">In the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], you can use the [\<ThrowUnobservedTaskExceptions> element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) in an application configuration file to enable the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="31f8b-136">Você também pode especificar o comportamento de exceção em uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="31f8b-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
-   <span data-ttu-id="31f8b-137">Definindo a variável de ambiente `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span><span class="sxs-lookup"><span data-stu-id="31f8b-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
-   <span data-ttu-id="31f8b-138">Definindo o Registro DWORD valor ThrowUnobservedTaskExceptions = 1 no HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Chave de NETFramework.</span><span class="sxs-lookup"><span data-stu-id="31f8b-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31f8b-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="31f8b-139">Example</span></span>  
 <span data-ttu-id="31f8b-140">O exemplo a seguir mostra como habilitar a gerar exceções em tarefas usando um arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="31f8b-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="31f8b-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="31f8b-141">Example</span></span>  
 <span data-ttu-id="31f8b-142">O exemplo a seguir demonstra como uma exceção não observada é gerada de uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="31f8b-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="31f8b-143">O código deve ser executado como um programa lançado funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="31f8b-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="31f8b-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31f8b-144">See Also</span></span>  
 [<span data-ttu-id="31f8b-145">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="31f8b-145">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="31f8b-146">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="31f8b-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
