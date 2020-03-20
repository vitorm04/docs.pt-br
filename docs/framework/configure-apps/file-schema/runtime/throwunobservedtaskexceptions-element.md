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
ms.openlocfilehash: de5a686bcbd88fc52173b488103f033575623d62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153809"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="5deb7-102">\<ThrowUnobservedTaskExceptions> Element</span><span class="sxs-lookup"><span data-stu-id="5deb7-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="5deb7-103">Especifica se as exceções de tarefas sem tratamento devem encerrar um processo em execução.</span><span class="sxs-lookup"><span data-stu-id="5deb7-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
<span data-ttu-id="5deb7-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5deb7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5deb7-105">&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="5deb7-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="5deb7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**</span><span class="sxs-lookup"><span data-stu-id="5deb7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5deb7-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5deb7-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5deb7-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5deb7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5deb7-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5deb7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5deb7-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="5deb7-110">Attributes</span></span>  
  
|<span data-ttu-id="5deb7-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="5deb7-111">Attribute</span></span>|<span data-ttu-id="5deb7-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5deb7-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5deb7-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="5deb7-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5deb7-114">Especifica se as exceções de tarefa não tratadas devem encerrar o processo de execução.</span><span class="sxs-lookup"><span data-stu-id="5deb7-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5deb7-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="5deb7-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5deb7-116">Valor</span><span class="sxs-lookup"><span data-stu-id="5deb7-116">Value</span></span>|<span data-ttu-id="5deb7-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="5deb7-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5deb7-118">Não encerra o processo de execução para uma exceção de tarefa não tratada.</span><span class="sxs-lookup"><span data-stu-id="5deb7-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="5deb7-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="5deb7-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="5deb7-120">Encerra o processo de execução para uma exceção de tarefa não tratada.</span><span class="sxs-lookup"><span data-stu-id="5deb7-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5deb7-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5deb7-121">Child Elements</span></span>  
 <span data-ttu-id="5deb7-122">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5deb7-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5deb7-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5deb7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5deb7-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="5deb7-124">Element</span></span>|<span data-ttu-id="5deb7-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="5deb7-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5deb7-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5deb7-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5deb7-127">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="5deb7-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="5deb7-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="5deb7-128">Remarks</span></span>  
 <span data-ttu-id="5deb7-129">Se uma exceção associada <xref:System.Threading.Tasks.Task> a um não foi <xref:System.Threading.Tasks.Task.Wait%2A> observada, não há operação, o <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> pai não está anexado, e a propriedade não foi lida, a exceção da tarefa é considerada não observada.</span><span class="sxs-lookup"><span data-stu-id="5deb7-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="5deb7-130">No Quadro .NET 4, por <xref:System.Threading.Tasks.Task> padrão, se um que tem uma exceção não observada for o lixo coletado, o finalizador lança uma exceção e encerra o processo.</span><span class="sxs-lookup"><span data-stu-id="5deb7-130">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="5deb7-131">O término do processo é determinado pelo calendário de coleta e finalização do lixo.</span><span class="sxs-lookup"><span data-stu-id="5deb7-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="5deb7-132">Para facilitar a gravação de código assíncrono com base em tarefas, o .NET Framework 4.5 altera esse comportamento padrão para exceções não observadas.</span><span class="sxs-lookup"><span data-stu-id="5deb7-132">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="5deb7-133">Exceções não observadas <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> ainda fazem com que o evento seja levantado, mas por padrão, o processo não termina.</span><span class="sxs-lookup"><span data-stu-id="5deb7-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="5deb7-134">Em vez disso, a exceção é ignorada após o evento ser levantado, independentemente de um manipulador de eventos observar a exceção.</span><span class="sxs-lookup"><span data-stu-id="5deb7-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="5deb7-135">No .NET Framework 4.5, você pode usar o [ \<elemento ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md) em um arquivo de configuração de aplicativo para habilitar o comportamento do .NET Framework 4 de lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="5deb7-135">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="5deb7-136">Você também pode especificar o comportamento de exceção de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="5deb7-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="5deb7-137">Definindo a `COMPlus_ThrowUnobservedTaskExceptions` variável`set COMPlus_ThrowUnobservedTaskExceptions=1`ambiente ( ).</span><span class="sxs-lookup"><span data-stu-id="5deb7-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="5deb7-138">Ao definir o valor do Registro DWORD ThrowUnobservedTaskExceptions\\= 1 no HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft . Tecla NETFramework.</span><span class="sxs-lookup"><span data-stu-id="5deb7-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5deb7-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5deb7-139">Example</span></span>  
 <span data-ttu-id="5deb7-140">O exemplo a seguir mostra como ativar o lançamento de exceções em tarefas usando um arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5deb7-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="5deb7-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5deb7-141">Example</span></span>  
 <span data-ttu-id="5deb7-142">O exemplo a seguir demonstra como uma exceção não observada é lançada de uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="5deb7-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="5deb7-143">O código deve ser executado como um programa liberado para funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="5deb7-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5deb7-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="5deb7-144">See also</span></span>

- [<span data-ttu-id="5deb7-145">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="5deb7-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5deb7-146">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="5deb7-146">Configuration File Schema</span></span>](../index.md)
