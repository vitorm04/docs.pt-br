---
title: Elemento <ThrowUnobservedTaskExceptions>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
ms.openlocfilehash: 012c2e70e66015bc317606a7eea07812b5df26e7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183917"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="c6729-102">Elemento \<ThrowUnobservedTaskExceptions></span><span class="sxs-lookup"><span data-stu-id="c6729-102">\<ThrowUnobservedTaskExceptions> Element</span></span>

<span data-ttu-id="c6729-103">Especifica se as exceções de tarefas sem tratamento devem encerrar um processo em execução.</span><span class="sxs-lookup"><span data-stu-id="c6729-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**  
  
## <a name="syntax"></a><span data-ttu-id="c6729-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6729-104">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6729-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c6729-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c6729-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c6729-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6729-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="c6729-107">Attributes</span></span>  
  
|<span data-ttu-id="c6729-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="c6729-108">Attribute</span></span>|<span data-ttu-id="c6729-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6729-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c6729-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="c6729-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="c6729-111">Especifica se exceções de tarefas sem tratamento devem encerrar o processo em execução.</span><span class="sxs-lookup"><span data-stu-id="c6729-111">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c6729-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="c6729-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="c6729-113">Valor</span><span class="sxs-lookup"><span data-stu-id="c6729-113">Value</span></span>|<span data-ttu-id="c6729-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6729-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="c6729-115">Não encerra o processo em execução para uma exceção de tarefa sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="c6729-115">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="c6729-116">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="c6729-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="c6729-117">Encerra o processo em execução para uma exceção de tarefa sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="c6729-117">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6729-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c6729-118">Child Elements</span></span>  

 <span data-ttu-id="c6729-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c6729-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6729-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c6729-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c6729-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="c6729-121">Element</span></span>|<span data-ttu-id="c6729-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6729-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c6729-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c6729-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c6729-124">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="c6729-124">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="c6729-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="c6729-125">Remarks</span></span>  

 <span data-ttu-id="c6729-126">Se uma exceção associada a um <xref:System.Threading.Tasks.Task> não tiver sido observada, não há nenhuma <xref:System.Threading.Tasks.Task.Wait%2A> operação, o pai não está anexado e a <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> propriedade não foi lida, a exceção da tarefa é considerada não observada.</span><span class="sxs-lookup"><span data-stu-id="c6729-126">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="c6729-127">No .NET Framework 4, por padrão, se um <xref:System.Threading.Tasks.Task> que tem uma exceção não observada for lixo coletado, o finalizador lançará uma exceção e encerrará o processo.</span><span class="sxs-lookup"><span data-stu-id="c6729-127">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="c6729-128">O encerramento do processo é determinado pelo tempo de coleta e finalização de lixo.</span><span class="sxs-lookup"><span data-stu-id="c6729-128">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="c6729-129">Para facilitar para os desenvolvedores a gravação de código assíncrono com base nas tarefas, o .NET Framework 4,5 altera esse comportamento padrão para exceções não observadas.</span><span class="sxs-lookup"><span data-stu-id="c6729-129">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="c6729-130">Exceções não observadas ainda fazem com que o <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> evento seja gerado, mas por padrão, o processo não é encerrado.</span><span class="sxs-lookup"><span data-stu-id="c6729-130">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="c6729-131">Em vez disso, a exceção é ignorada depois que o evento é gerado, independentemente se um manipulador de eventos observa a exceção.</span><span class="sxs-lookup"><span data-stu-id="c6729-131">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="c6729-132">No .NET Framework 4,5, você pode usar o [ \<ThrowUnobservedTaskExceptions> elemento](throwunobservedtaskexceptions-element.md) em um arquivo de configuração de aplicativo para habilitar o comportamento de .NET Framework 4 do lançamento de uma exceção.</span><span class="sxs-lookup"><span data-stu-id="c6729-132">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="c6729-133">Você também pode especificar o comportamento da exceção de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="c6729-133">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="c6729-134">Definindo a variável de ambiente `COMPlus_ThrowUnobservedTaskExceptions` ( `set COMPlus_ThrowUnobservedTaskExceptions=1` ).</span><span class="sxs-lookup"><span data-stu-id="c6729-134">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="c6729-135">Definindo o valor DWORD do registro ThrowUnobservedTaskExceptions = 1 no HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . Chave NETFramework.</span><span class="sxs-lookup"><span data-stu-id="c6729-135">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6729-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c6729-136">Example</span></span>  

 <span data-ttu-id="c6729-137">O exemplo a seguir mostra como habilitar o lançamento de exceções em tarefas usando um arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c6729-137">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="c6729-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c6729-138">Example</span></span>  

 <span data-ttu-id="c6729-139">O exemplo a seguir demonstra como uma exceção não observada é gerada de uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="c6729-139">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="c6729-140">O código deve ser executado como um programa liberado para funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="c6729-140">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c6729-141">Veja também</span><span class="sxs-lookup"><span data-stu-id="c6729-141">See also</span></span>

- [<span data-ttu-id="c6729-142">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="c6729-142">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c6729-143">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="c6729-143">Configuration File Schema</span></span>](../index.md)
