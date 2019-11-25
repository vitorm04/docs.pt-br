---
title: Resolver carregamentos de assembly
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET Framework], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: edd398cd3e42e23301dcc992093d14d087754e76
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347248"
---
# <a name="resolve-assembly-loads"></a><span data-ttu-id="d0279-102">Resolver carregamentos de assembly</span><span class="sxs-lookup"><span data-stu-id="d0279-102">Resolve assembly loads</span></span>
<span data-ttu-id="d0279-103">.NET provides the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event for applications that require greater control over assembly loading.</span><span class="sxs-lookup"><span data-stu-id="d0279-103">.NET provides the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event for applications that require greater control over assembly loading.</span></span> <span data-ttu-id="d0279-104">Ao tratar esse evento, seu aplicativo pode carregar um assembly no contexto de carga de fora dos caminhos normais de investigação, selecionar qual das várias versões de assembly carregar, emitir um assembly dinâmico e retorná-lo, etc.</span><span class="sxs-lookup"><span data-stu-id="d0279-104">By handling this event, your application can load an assembly into the load context from outside the normal probing paths, select which of several assembly versions to load, emit a dynamic assembly and return it, and so on.</span></span> <span data-ttu-id="d0279-105">Este tópico fornece orientação para a manipulação do evento <xref:System.AppDomain.AssemblyResolve>.</span><span class="sxs-lookup"><span data-stu-id="d0279-105">This topic provides guidance for handling the <xref:System.AppDomain.AssemblyResolve> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0279-106">Para resolver carregamentos de assembly no contexto de somente reflexão, use o evento <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="d0279-106">For resolving assembly loads in the reflection-only context, use the <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> event instead.</span></span>  
  
## <a name="how-the-assemblyresolve-event-works"></a><span data-ttu-id="d0279-107">How the AssemblyResolve event works</span><span class="sxs-lookup"><span data-stu-id="d0279-107">How the AssemblyResolve event works</span></span>  
 <span data-ttu-id="d0279-108">Quando você registra um manipulador para o evento <xref:System.AppDomain.AssemblyResolve>, o manipulador é invocado sempre que o runtime falha ao se associar a um assembly por nome.</span><span class="sxs-lookup"><span data-stu-id="d0279-108">When you register a handler for the <xref:System.AppDomain.AssemblyResolve> event, the handler is invoked whenever the runtime fails to bind to an assembly by name.</span></span> <span data-ttu-id="d0279-109">Por exemplo, chamar os seguintes métodos usando o código do usuário pode fazer com que o evento <xref:System.AppDomain.AssemblyResolve> seja gerado:</span><span class="sxs-lookup"><span data-stu-id="d0279-109">For example, calling the following methods from user code can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised:</span></span>  
  
- <span data-ttu-id="d0279-110">Uma sobrecarga de método <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> ou uma sobrecarga de método <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> cujo primeiro argumento é uma cadeia de caracteres que representa o nome de exibição do assembly a ser carregado (ou seja, a cadeia de caracteres retornada pela propriedade <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="d0279-110">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is a string that represents the display name of the assembly to load (that is, the string returned by the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property).</span></span>  
  
- <span data-ttu-id="d0279-111">Uma sobrecarga de método <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> ou uma sobrecarga de método <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> cujo primeiro argumento é um objeto <xref:System.Reflection.AssemblyName> que identifica o assembly a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="d0279-111">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is an <xref:System.Reflection.AssemblyName> object that identifies the assembly to load.</span></span>  
  
- <span data-ttu-id="d0279-112">Uma sobrecarga de método <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d0279-112">An <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> method overload.</span></span>  
  
- <span data-ttu-id="d0279-113">Uma sobrecarga de método <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> ou <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> que cria uma instância de um objeto em outro domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d0279-113">An <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> method overload that instantiates an object in another application domain.</span></span>  
  
### <a name="what-the-event-handler-does"></a><span data-ttu-id="d0279-114">What the event handler does</span><span class="sxs-lookup"><span data-stu-id="d0279-114">What the event handler does</span></span>  
 <span data-ttu-id="d0279-115">O manipulador do evento <xref:System.AppDomain.AssemblyResolve> recebe o nome de exibição do assembly a ser carregado na propriedade <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d0279-115">The handler for the <xref:System.AppDomain.AssemblyResolve> event receives the display name of the assembly to be loaded, in the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="d0279-116">If the handler does not recognize the assembly name, it returns `null` (C#), `Nothing` (Visual Basic), or `nullptr` (Visual C++).</span><span class="sxs-lookup"><span data-stu-id="d0279-116">If the handler does not recognize the assembly name, it returns `null` (C#), `Nothing` (Visual Basic), or `nullptr` (Visual C++).</span></span>  
  
 <span data-ttu-id="d0279-117">Se o manipulador reconhecer o nome do assembly, ele poderá carregar e retornar um assembly que atende à solicitação.</span><span class="sxs-lookup"><span data-stu-id="d0279-117">If the handler recognizes the assembly name, it can load and return an assembly that satisfies the request.</span></span> <span data-ttu-id="d0279-118">A lista a seguir descreve alguns cenários de exemplo.</span><span class="sxs-lookup"><span data-stu-id="d0279-118">The following list describes some sample scenarios.</span></span>  
  
- <span data-ttu-id="d0279-119">Se o manipulador conhecer o local de uma versão do assembly, ele poderá carregar o assembly usando o método <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> ou <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> e poderá retornar o assembly carregado se tiver êxito.</span><span class="sxs-lookup"><span data-stu-id="d0279-119">If the handler knows the location of a version of the assembly, it can load the assembly by using the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> method, and can return the loaded assembly if successful.</span></span>  
  
- <span data-ttu-id="d0279-120">Se o manipulador tiver acesso a um banco de dados de assemblies armazenados como matrizes de bytes, ele poderá carregar uma matriz de bytes usando uma das sobrecargas do método <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> que usa uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="d0279-120">If the handler has access to a database of assemblies stored as byte arrays, it can load a byte array by using one of the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that take a byte array.</span></span>  
  
- <span data-ttu-id="d0279-121">O manipulador pode gerar um assembly dinâmico e retorná-lo.</span><span class="sxs-lookup"><span data-stu-id="d0279-121">The handler can generate a dynamic assembly and return it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0279-122">O manipulador deve carregar o assembly no contexto de origem de carga, no contexto de carregamento ou sem contexto. Se o manipulador carregar o assembly no contexto de somente reflexão usando o método <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> ou o <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType>, a tentativa de carregamento que gerou o evento <xref:System.AppDomain.AssemblyResolve> falhará.</span><span class="sxs-lookup"><span data-stu-id="d0279-122">The handler must load the assembly into the load-from context, into the load context, or without context.If the handler loads the assembly into the reflection-only context by using the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> method, the load attempt that raised the <xref:System.AppDomain.AssemblyResolve> event fails.</span></span>  
  
 <span data-ttu-id="d0279-123">É responsabilidade do manipulador de eventos retornar um assembly adequado.</span><span class="sxs-lookup"><span data-stu-id="d0279-123">It is the responsibility of the event handler to return a suitable assembly.</span></span> <span data-ttu-id="d0279-124">O manipulador pode analisar o nome de exibição do assembly solicitado passando o valor da propriedade <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> para o construtor <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="d0279-124">The handler can parse the display name of the requested assembly by passing the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property value to the <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> constructor.</span></span> <span data-ttu-id="d0279-125">A partir do .NET Framework 4, o manipulador pode usar a propriedade <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> para determinar se a solicitação atual é uma dependência de outro assembly.</span><span class="sxs-lookup"><span data-stu-id="d0279-125">Beginning with the .NET Framework 4, the handler can use the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property to determine whether the current request is a dependency of another assembly.</span></span> <span data-ttu-id="d0279-126">Essas informações podem ajudar a identificar um assembly que atenderá à dependência.</span><span class="sxs-lookup"><span data-stu-id="d0279-126">This information can help identify an assembly that will satisfy the dependency.</span></span>  
  
 <span data-ttu-id="d0279-127">O manipulador de eventos pode retornar uma versão diferente do assembly do que a versão que foi solicitada.</span><span class="sxs-lookup"><span data-stu-id="d0279-127">The event handler can return a different version of the assembly than the version that was requested.</span></span>  
  
 <span data-ttu-id="d0279-128">Na maioria dos casos, o assembly que é retornado pelo manipulador aparece no contexto de carga, independentemente do contexto em que o manipulador o carrega.</span><span class="sxs-lookup"><span data-stu-id="d0279-128">In most cases, the assembly that is returned by the handler appears in the load context, regardless of the context the handler loads it into.</span></span> <span data-ttu-id="d0279-129">Por exemplo, se o manipulador usar o método <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> para carregar um assembly no contexto de origem de carga, o assembly aparecerá no contexto de carga quando o manipulador o retornar.</span><span class="sxs-lookup"><span data-stu-id="d0279-129">For example, if the handler uses the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method to load an assembly into the load-from context, the assembly appears in the load context when the handler returns it.</span></span> <span data-ttu-id="d0279-130">No entanto, no seguinte caso, o assembly aparece sem contexto quando o manipulador o retorna:</span><span class="sxs-lookup"><span data-stu-id="d0279-130">However, in the following case the assembly appears without context when the handler returns it:</span></span>  
  
- <span data-ttu-id="d0279-131">O manipulador carrega um assembly sem contexto.</span><span class="sxs-lookup"><span data-stu-id="d0279-131">The handler loads an assembly without context.</span></span>  
  
- <span data-ttu-id="d0279-132">A propriedade <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> não é nula.</span><span class="sxs-lookup"><span data-stu-id="d0279-132">The <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property is not null.</span></span>  
  
- <span data-ttu-id="d0279-133">O assembly solicitante (ou seja, o assembly que é retornado pela propriedade <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType>) foi carregado sem contexto.</span><span class="sxs-lookup"><span data-stu-id="d0279-133">The requesting assembly (that is, the assembly that is returned by the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property) was loaded without context.</span></span>  
  
 <span data-ttu-id="d0279-134">Para obter informações sobre os contextos, consulte a sobrecarga de método <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d0279-134">For information about contexts, see the <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> method overload.</span></span>  
  
 <span data-ttu-id="d0279-135">Várias versões do mesmo assembly podem ser carregadas no mesmo domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d0279-135">Multiple versions of the same assembly can be loaded into the same application domain.</span></span> <span data-ttu-id="d0279-136">Essa prática não é recomendada, pois ela pode levar a problemas de atribuição de tipo.</span><span class="sxs-lookup"><span data-stu-id="d0279-136">This practice is not recommended, because it can lead to type assignment problems.</span></span> <span data-ttu-id="d0279-137">See [Best practices for assembly loading](../../framework/deployment/best-practices-for-assembly-loading.md).</span><span class="sxs-lookup"><span data-stu-id="d0279-137">See [Best practices for assembly loading](../../framework/deployment/best-practices-for-assembly-loading.md).</span></span>  
  
### <a name="what-the-event-handler-should-not-do"></a><span data-ttu-id="d0279-138">What the event handler should not do</span><span class="sxs-lookup"><span data-stu-id="d0279-138">What the event handler should not do</span></span>  
<span data-ttu-id="d0279-139">A regra principal para tratamento do evento <xref:System.AppDomain.AssemblyResolve> é que você não deve tentar retornar um assembly que não reconhece.</span><span class="sxs-lookup"><span data-stu-id="d0279-139">The primary rule for handling the <xref:System.AppDomain.AssemblyResolve> event is that you should not try to return an assembly you do not recognize.</span></span> <span data-ttu-id="d0279-140">Ao escrever o manipulador, você deve saber quais assemblies podem fazer com que o evento seja acionado.</span><span class="sxs-lookup"><span data-stu-id="d0279-140">When you write the handler, you should know which assemblies might cause the event to be raised.</span></span> <span data-ttu-id="d0279-141">O manipulador deve retornar nulo para outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="d0279-141">Your handler should return null for other assemblies.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="d0279-142">Começando com o .NET Framework 4, o evento <xref:System.AppDomain.AssemblyResolve> é gerado para assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="d0279-142">Beginning with the .NET Framework 4, the <xref:System.AppDomain.AssemblyResolve> event is raised for satellite assemblies.</span></span> <span data-ttu-id="d0279-143">Essa alteração afeta um manipulador de eventos que foi escrito para uma versão anterior do .NET Framework, se o manipulador tenta resolver todas as solicitações de carga do assembly.</span><span class="sxs-lookup"><span data-stu-id="d0279-143">This change affects an event handler that was written for an earlier version of the .NET Framework, if the handler tries to resolve all assembly load requests.</span></span> <span data-ttu-id="d0279-144">Os manipuladores de eventos que ignoram assemblies que eles não reconhecem não são afetados por essa alteração: eles retornam nulo, e os mecanismos normais de fallback são seguidos.</span><span class="sxs-lookup"><span data-stu-id="d0279-144">Event handlers that ignore assemblies they do not recognize are not affected by this change: They return null, and normal fallback mechanisms are followed.</span></span>  

<span data-ttu-id="d0279-145">Ao carregar um assembly, o manipulador de eventos não deve usar nenhuma das sobrecargas de método <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> ou <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> que possam fazer com que o evento <xref:System.AppDomain.AssemblyResolve> seja gerado recursivamente, pois isso poderia levar a um excedente de pilha.</span><span class="sxs-lookup"><span data-stu-id="d0279-145">When loading an assembly, the event handler must not use any of the <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised recursively, because this can lead to a stack overflow.</span></span> <span data-ttu-id="d0279-146">(See the list provided earlier in this topic.) This happens even if you provide exception handling for the load request, because no exception is thrown until all event handlers have returned.</span><span class="sxs-lookup"><span data-stu-id="d0279-146">(See the list provided earlier in this topic.) This happens even if you provide exception handling for the load request, because no exception is thrown until all event handlers have returned.</span></span> <span data-ttu-id="d0279-147">Desse modo, o seguinte código resultará em um excedente de pilha se `MyAssembly` não for encontrado:</span><span class="sxs-lookup"><span data-stu-id="d0279-147">Thus, the following code results in a stack overflow if `MyAssembly` is not found:</span></span>  

```cpp
using namespace System;
using namespace System::Reflection;

ref class Example
{
internal:
    static Assembly^ MyHandler(Object^ source, ResolveEventArgs^ e) 
    {
        Console::WriteLine("Resolving {0}", e->Name);
        return Assembly::Load(e->Name);
    }
};

void main()
{
    AppDomain^ ad = AppDomain::CreateDomain("Test");
    ad->AssemblyResolve += gcnew ResolveEventHandler(&Example::MyHandler);

    try
    {
        Object^ obj = ad->CreateInstanceAndUnwrap(
            "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
            "MyType");
    } 
    catch (Exception^ ex)
    {
        Console::WriteLine(ex->Message);
    }
}

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
 */
```

```csharp
using System;
using System.Reflection;

class BadExample
{
    static void Main()
    {
        AppDomain ad = AppDomain.CreateDomain("Test");
        ad.AssemblyResolve += MyHandler;

        try
        {
            object obj = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType");
        } 
        catch (Exception ex)
        {
            Console.WriteLine(ex.Message);
        }
    }

    static Assembly MyHandler(object source, ResolveEventArgs e) 
    {
        Console.WriteLine("Resolving {0}", e.Name);
        return Assembly.Load(e.Name);
    }
} 

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
 */
```

```vb
Imports System.Reflection

Class BadExample

    Shared Sub Main()
    
        Dim ad As AppDomain = AppDomain.CreateDomain("Test")
        AddHandler ad.AssemblyResolve, AddressOf MyHandler

        Try
            Dim obj As object = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType")
        Catch ex As Exception
            Console.WriteLine(ex.Message)
        End Try
    End Sub

    Shared Function MyHandler(ByVal source As Object, _
                              ByVal e As ResolveEventArgs) As Assembly
        Console.WriteLine("Resolving {0}", e.Name)
        Return Assembly.Load(e.Name)
    End Function
End Class

' This example produces output similar to the following:
'
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'...
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'
'Process is terminated due to StackOverflowException.
```

## <a name="see-also"></a><span data-ttu-id="d0279-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0279-148">See also</span></span>

- [<span data-ttu-id="d0279-149">Best practices for assembly loading</span><span class="sxs-lookup"><span data-stu-id="d0279-149">Best practices for assembly loading</span></span>](../../framework/deployment/best-practices-for-assembly-loading.md)
- [<span data-ttu-id="d0279-150">Use application domains</span><span class="sxs-lookup"><span data-stu-id="d0279-150">Use application domains</span></span>](../../framework/app-domains/use.md)
