---
title: Padrão de Dispose
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Dispose method
- class library design guidelines [.NET Framework], Dispose method
- class library design guidelines [.NET Framework], Finalize method
- customizing Dispose method name
- Finalize method
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdcb746ae2d8c2262b0cd0c6c9dcaababb12bd63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578983"
---
# <a name="dispose-pattern"></a><span data-ttu-id="fbdf1-102">Padrão de Dispose</span><span class="sxs-lookup"><span data-stu-id="fbdf1-102">Dispose Pattern</span></span>
<span data-ttu-id="fbdf1-103">Todos os programas adquirem um ou mais recursos do sistema, como memória, manipuladores de sistema ou conexões de banco de dados durante sua execução.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-103">All programs acquire one or more system resources, such as memory, system handles, or database connections, during the course of their execution.</span></span> <span data-ttu-id="fbdf1-104">Os desenvolvedores precisam ter cuidado ao usar esses recursos do sistema, porque eles devem ser liberados após ter sido adquiridas e usadas.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-104">Developers have to be careful when using such system resources, because they must be released after they have been acquired and used.</span></span>  
  
 <span data-ttu-id="fbdf1-105">O CLR fornece suporte para gerenciamento automático de memória.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-105">The CLR provides support for automatic memory management.</span></span> <span data-ttu-id="fbdf1-106">Memória gerenciada (memória alocada usando o operador c# `new`) não precisa ser explicitamente liberados.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-106">Managed memory (memory allocated using the C# operator `new`) does not need to be explicitly released.</span></span> <span data-ttu-id="fbdf1-107">Ele é liberado automaticamente pelo coletor de lixo (GC).</span><span class="sxs-lookup"><span data-stu-id="fbdf1-107">It is released automatically by the garbage collector (GC).</span></span> <span data-ttu-id="fbdf1-108">Isso libera os desenvolvedores da tarefa entediante e difícil de liberação de memória e tem sido um dos principais motivos para a produtividade sem precedentes proporcionada pelo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-108">This frees developers from the tedious and difficult task of releasing memory and has been one of the main reasons for the unprecedented productivity afforded by the .NET Framework.</span></span>  
  
 <span data-ttu-id="fbdf1-109">Infelizmente, a memória gerenciada é apenas um dos muitos tipos de recursos do sistema.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-109">Unfortunately, managed memory is just one of many types of system resources.</span></span> <span data-ttu-id="fbdf1-110">Recursos, além de memória gerenciada ainda precisam ser liberados explicitamente e são chamados de recursos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-110">Resources other than managed memory still need to be released explicitly and are referred to as unmanaged resources.</span></span> <span data-ttu-id="fbdf1-111">O GC especificamente não foi projetado para gerenciar esses recursos não gerenciados, o que significa que a responsabilidade de gerenciar recursos não gerenciados está nas mãos dos desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-111">The GC was specifically not designed to manage such unmanaged resources, which means that the responsibility for managing unmanaged resources lies in the hands of the developers.</span></span>  
  
 <span data-ttu-id="fbdf1-112">O CLR fornece ajuda ao liberar recursos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-112">The CLR provides some help in releasing unmanaged resources.</span></span> <span data-ttu-id="fbdf1-113"><xref:System.Object?displayProperty=nameWithType> declara um método virtual <xref:System.Object.Finalize%2A> (também chamado o finalizador) que é chamado pelo GC antes que a memória do objeto é recuperada pelo GC e pode ser substituída para liberar recursos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-113"><xref:System.Object?displayProperty=nameWithType> declares a virtual method <xref:System.Object.Finalize%2A> (also called the finalizer) that is called by the GC before the object’s memory is reclaimed by the GC and can be overridden to release unmanaged resources.</span></span> <span data-ttu-id="fbdf1-114">Tipos de substituem o finalizador são denominados finalizáveis tipos.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-114">Types that override the finalizer are referred to as finalizable types.</span></span>  
  
 <span data-ttu-id="fbdf1-115">Embora os finalizadores entrarão em vigor em alguns cenários de limpeza, eles têm duas desvantagens significativas:</span><span class="sxs-lookup"><span data-stu-id="fbdf1-115">Although finalizers are effective in some cleanup scenarios, they have two significant drawbacks:</span></span>  
  
-   <span data-ttu-id="fbdf1-116">O finalizador é chamado quando o GC detecta que um objeto é qualificado para a coleta.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-116">The finalizer is called when the GC detects that an object is eligible for collection.</span></span> <span data-ttu-id="fbdf1-117">Isso ocorre em um período indeterminado depois que o recurso não é mais necessária.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-117">This happens at some undetermined period of time after the resource is not needed anymore.</span></span> <span data-ttu-id="fbdf1-118">O atraso entre quando o desenvolvedor poderia ou deseja liberar o recurso e a hora quando o recurso, na verdade, é lançado pelo finalizador seria inaceitável em programas que adquirem vários recursos escassos (recursos que podem ser facilmente esgotados) ou em casos nos quais recursos são caros manter em uso (por exemplo, buffers de memória não gerenciada grande).</span><span class="sxs-lookup"><span data-stu-id="fbdf1-118">The delay between when the developer could or would like to release the resource and the time when the resource is actually released by the finalizer might be unacceptable in programs that acquire many scarce resources (resources that can be easily exhausted) or in cases in which resources are costly to keep in use (e.g., large unmanaged memory buffers).</span></span>  
  
-   <span data-ttu-id="fbdf1-119">Quando o CLR precisa chamar um finalizador, ele deve adiar a coleção de memória do objeto até que a próxima de ida e volta da coleta de lixo (os finalizadores executadas entre coleções).</span><span class="sxs-lookup"><span data-stu-id="fbdf1-119">When the CLR needs to call a finalizer, it must postpone collection of the object’s memory until the next round of garbage collection (the finalizers run between collections).</span></span> <span data-ttu-id="fbdf1-120">Isso significa que a memória do objeto (e todos os objetos que se refere a) não seja liberados para um período de tempo maior.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-120">This means that the object’s memory (and all objects it refers to) will not be released for a longer period of time.</span></span>  
  
 <span data-ttu-id="fbdf1-121">Portanto, depender exclusivamente finalizadores pode não ser apropriado em muitos cenários, quando é importante recuperar recursos não gerenciados assim que possível, ao lidar com recursos escassos ou em cenários de alto desempenho altamente no qual a sobrecarga adicional de GC de finalização é inaceitável.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-121">Therefore, relying exclusively on finalizers might not be appropriate in many scenarios when it is important to reclaim unmanaged resources as quickly as possible, when dealing with scarce resources, or in highly performant scenarios in which the added GC overhead of finalization is unacceptable.</span></span>  
  
 <span data-ttu-id="fbdf1-122">Fornece a estrutura de <xref:System.IDisposable?displayProperty=nameWithType> interface que deve ser implementada para fornecer ao desenvolvedor uma maneira manual para liberar recursos não gerenciados, assim que eles não são necessários.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-122">The Framework provides the <xref:System.IDisposable?displayProperty=nameWithType> interface that should be implemented to provide the developer a manual way to release unmanaged resources as soon as they are not needed.</span></span> <span data-ttu-id="fbdf1-123">Ele também fornece o <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> método que pode informar o GC um objeto manualmente foi descartado e não precisa ser finalizado, caso em que a memória do objeto pode ser recuperada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-123">It also provides the <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> method that can tell the GC that an object was manually disposed of and does not need to be finalized anymore, in which case the object’s memory can be reclaimed earlier.</span></span> <span data-ttu-id="fbdf1-124">Tipos que implementam o `IDisposable` interface são chamados de tipos descartáveis.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-124">Types that implement the `IDisposable` interface are referred to as disposable types.</span></span>  
  
 <span data-ttu-id="fbdf1-125">O padrão Dispose destina-se para padronizar o uso e a implementação de finalizadores e `IDisposable` interface.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-125">The Dispose Pattern is intended to standardize the usage and implementation of finalizers and the `IDisposable` interface.</span></span>  
  
 <span data-ttu-id="fbdf1-126">A principal motivação para o padrão é para reduzir a complexidade da implementação do <xref:System.Object.Finalize%2A> e <xref:System.IDisposable.Dispose%2A> métodos.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-126">The main motivation for the pattern is to reduce the complexity of the implementation of the <xref:System.Object.Finalize%2A> and the <xref:System.IDisposable.Dispose%2A> methods.</span></span> <span data-ttu-id="fbdf1-127">Reduz a complexidade do fato de que os métodos compartilham algumas, mas nem todos os caminhos de código (as diferenças são descritas posteriormente no capítulo).</span><span class="sxs-lookup"><span data-stu-id="fbdf1-127">The complexity stems from the fact that the methods share some but not all code paths (the differences are described later in the chapter).</span></span> <span data-ttu-id="fbdf1-128">Além disso, há razões históricas para alguns elementos do padrão relacionadas a evolução de suporte ao idioma para o gerenciamento de recursos determinística.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-128">In addition, there are historical reasons for some elements of the pattern related to the evolution of language support for deterministic resource management.</span></span>  
  
 <span data-ttu-id="fbdf1-129">**FAZER ✓** implementar o padrão de Dispose básico em tipos que contém instâncias de tipos descartáveis.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-129">**✓ DO** implement the Basic Dispose Pattern on types containing instances of disposable types.</span></span> <span data-ttu-id="fbdf1-130">Consulte o [padrão Dispose básico](#basic_pattern) seção para obter detalhes sobre o padrão básico.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-130">See the [Basic Dispose Pattern](#basic_pattern) section for details on the basic pattern.</span></span>  
  
 <span data-ttu-id="fbdf1-131">Se um tipo é responsável pelo tempo de vida de outros objetos descartáveis, os desenvolvedores precisam de uma maneira de descartá-los, muito.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-131">If a type is responsible for the lifetime of other disposable objects, developers need a way to dispose of them, too.</span></span> <span data-ttu-id="fbdf1-132">Usando o contêiner `Dispose` método é uma maneira conveniente para que isso aconteça.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-132">Using the container’s `Dispose` method is a convenient way to make this possible.</span></span>  
  
 <span data-ttu-id="fbdf1-133">**FAZER ✓** implementar o padrão de Dispose básico e fornecer um finalizador em tipos de recursos de retenção que precisam ser liberados explicitamente e que não tenham finalizadores.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-133">**✓ DO** implement the Basic Dispose Pattern and provide a finalizer on types holding resources that need to be freed explicitly and that do not have finalizers.</span></span>  
  
 <span data-ttu-id="fbdf1-134">Por exemplo, o padrão deve ser implementado em tipos de armazenamento de buffers de memória não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-134">For example, the pattern should be implemented on types storing unmanaged memory buffers.</span></span> <span data-ttu-id="fbdf1-135">O [tipos finalizáveis](#finalizable_types) seção discute as diretrizes relacionadas à implementação finalizadores.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-135">The [Finalizable Types](#finalizable_types) section discusses guidelines related to implementing finalizers.</span></span>  
  
 <span data-ttu-id="fbdf1-136">**✓ CONSIDERE** Implementando o padrão de Dispose básico em classes que se não mantém os recursos não gerenciados ou objetos descartáveis mas serão prováveis que os subtipos que fazer.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-136">**✓ CONSIDER** implementing the Basic Dispose Pattern on classes that themselves don’t hold unmanaged resources or disposable objects but are likely to have subtypes that do.</span></span>  
  
 <span data-ttu-id="fbdf1-137">Um ótimo exemplo disso é a <xref:System.IO.Stream?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-137">A great example of this is the <xref:System.IO.Stream?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="fbdf1-138">Embora seja uma classe base abstrata que não contêm todos os recursos, a maioria de suas subclasses fazer e por isso, ele implementa esse padrão.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-138">Although it is an abstract base class that doesn’t hold any resources, most of its subclasses do and because of this, it implements this pattern.</span></span>  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a><span data-ttu-id="fbdf1-139">Padrão Dispose básico</span><span class="sxs-lookup"><span data-stu-id="fbdf1-139">Basic Dispose Pattern</span></span>  
 <span data-ttu-id="fbdf1-140">A implementação básica do padrão envolve a implementação de `System.IDisposable` interface e declarando o `Dispose(bool)` método que implementa a lógica de limpeza todos os recursos para serem compartilhadas entre o `Dispose` método e o finalizador opcional.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-140">The basic implementation of the pattern involves implementing the `System.IDisposable` interface and declaring the `Dispose(bool)` method that implements all resource cleanup logic to be shared between the `Dispose` method and the optional finalizer.</span></span>  
  
 <span data-ttu-id="fbdf1-141">O exemplo a seguir mostra uma implementação simples do que o padrão básico:</span><span class="sxs-lookup"><span data-stu-id="fbdf1-141">The following example shows a simple implementation of the basic pattern:</span></span>  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder(){  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        if (disposing){  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="fbdf1-142">O parâmetro booliano `disposing` indica se o método foi chamado a partir de `IDisposable.Dispose` implementação ou o finalizador.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-142">The Boolean parameter `disposing` indicates whether the method was invoked from the `IDisposable.Dispose` implementation or from the finalizer.</span></span> <span data-ttu-id="fbdf1-143">O `Dispose(bool)` implementação deve verificar o parâmetro antes de acessar outros objetos de referência (por exemplo, o campo de recurso no exemplo anterior).</span><span class="sxs-lookup"><span data-stu-id="fbdf1-143">The `Dispose(bool)` implementation should check the parameter before accessing other reference objects (e.g., the resource field in the preceding sample).</span></span> <span data-ttu-id="fbdf1-144">Esses objetos só devem ser acessados quando o método é chamado da `IDisposable.Dispose` implementação (quando o `disposing` parâmetro for igual a true).</span><span class="sxs-lookup"><span data-stu-id="fbdf1-144">Such objects should only be accessed when the method is called from the `IDisposable.Dispose` implementation (when the `disposing` parameter is equal to true).</span></span> <span data-ttu-id="fbdf1-145">Se o método é invocado do finalizador (`disposing` é false), outros objetos não devem ser acessados.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-145">If the method is invoked from the finalizer (`disposing` is false), other objects should not be accessed.</span></span> <span data-ttu-id="fbdf1-146">O motivo é que os objetos são finalizados em uma ordem imprevisível e portanto eles ou qualquer uma de suas dependências, pode já ter finalizado.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-146">The reason is that objects are finalized in an unpredictable order and so they, or any of their dependencies, might already have been finalized.</span></span>  
  
 <span data-ttu-id="fbdf1-147">Além disso, esta seção se aplica a classes com uma base que não implementa o padrão Dispose.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-147">Also, this section applies to classes with a base that does not already implement the Dispose Pattern.</span></span> <span data-ttu-id="fbdf1-148">Se você estiver herdando de uma classe que já implementa o padrão, basta substituir a `Dispose(bool)` método para fornecer lógica de limpeza de recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-148">If you are inheriting from a class that already implements the pattern, simply override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="fbdf1-149">**FAZER ✓** declarar um `protected virtual void Dispose(bool disposing)` método centralizar toda a lógica relacionado à liberação de recursos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-149">**✓ DO** declare a `protected virtual void Dispose(bool disposing)` method to centralize all logic related to releasing unmanaged resources.</span></span>  
  
 <span data-ttu-id="fbdf1-150">Limpeza de todos os recursos deve ocorrer nesse método.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-150">All resource cleanup should occur in this method.</span></span> <span data-ttu-id="fbdf1-151">O método é chamado de ambos o finalizador e `IDisposable.Dispose` método.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-151">The method is called from both the finalizer and the `IDisposable.Dispose` method.</span></span> <span data-ttu-id="fbdf1-152">O parâmetro será false se o que está sendo chamado de dentro de um finalizador.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-152">The parameter will be false if being invoked from inside a finalizer.</span></span> <span data-ttu-id="fbdf1-153">Ele deve ser usado para garantir que qualquer código em execução durante a finalização não está acessando a outros objetos finalizáveis.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-153">It should be used to ensure any code running during finalization is not accessing other finalizable objects.</span></span> <span data-ttu-id="fbdf1-154">Detalhes de implementação de finalizadores são descritos na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-154">Details of implementing finalizers are described in the next section.</span></span>  
  
```  
protected virtual void Dispose(bool disposing){  
    if (disposing){  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 <span data-ttu-id="fbdf1-155">**FAZER ✓** implementar o `IDisposable` interface simplesmente chamando `Dispose(true)` seguido por `GC.SuppressFinalize(this)`.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-155">**✓ DO** implement the `IDisposable` interface by simply calling `Dispose(true)` followed by `GC.SuppressFinalize(this)`.</span></span>  
  
 <span data-ttu-id="fbdf1-156">A chamada para `SuppressFinalize` deve ocorrer somente se `Dispose(true)` for executado com êxito.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-156">The call to `SuppressFinalize` should only occur if `Dispose(true)` executes successfully.</span></span>  
  
```  
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 <span data-ttu-id="fbdf1-157">**X não** fazer o sem parâmetros `Dispose` método virtual.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-157">**X DO NOT** make the parameterless `Dispose` method virtual.</span></span>  
  
 <span data-ttu-id="fbdf1-158">O `Dispose(bool)` método é o que deve ser substituído por subclasses.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-158">The `Dispose(bool)` method is the one that should be overridden by subclasses.</span></span>  
  
```  
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
```  
  
 <span data-ttu-id="fbdf1-159">**X não** declarar qualquer sobrecargas do `Dispose` método diferente do `Dispose()` e `Dispose(bool)`.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-159">**X DO NOT** declare any overloads of the `Dispose` method other than `Dispose()` and `Dispose(bool)`.</span></span>  
  
 <span data-ttu-id="fbdf1-160">`Dispose` deve ser considerada uma palavra reservada para ajudar a codificar esse padrão e evitar confusão entre implementadores, usuários e compiladores.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-160">`Dispose` should be considered a reserved word to help codify this pattern and prevent confusion among implementers, users, and compilers.</span></span> <span data-ttu-id="fbdf1-161">Alguns idiomas podem optar por implementar esse padrão automaticamente em determinados tipos.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-161">Some languages might choose to automatically implement this pattern on certain types.</span></span>  
  
 <span data-ttu-id="fbdf1-162">**FAZER ✓** permitir a `Dispose(bool)` método a ser chamado mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-162">**✓ DO** allow the `Dispose(bool)` method to be called more than once.</span></span> <span data-ttu-id="fbdf1-163">O método pode optar por não fazer nada após a primeira chamada.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-163">The method might choose to do nothing after the first call.</span></span>  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 <span data-ttu-id="fbdf1-164">**X Evite** lançar uma exceção no `Dispose(bool)` exceto sob críticas situações em que o processo contendo está corrompido (vazamentos, estado compartilhado inconsistente, etc.).</span><span class="sxs-lookup"><span data-stu-id="fbdf1-164">**X AVOID** throwing an exception from within `Dispose(bool)` except under critical situations where the containing process has been corrupted (leaks, inconsistent shared state, etc.).</span></span>  
  
 <span data-ttu-id="fbdf1-165">Os usuários esperam que uma chamada para `Dispose` não gerará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-165">Users expect that a call to `Dispose` will not raise an exception.</span></span>  
  
 <span data-ttu-id="fbdf1-166">Se `Dispose` pode gerar uma exceção, a lógica de limpeza de bloco finally adicional não será executado.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-166">If `Dispose` could raise an exception, further finally-block cleanup logic will not execute.</span></span> <span data-ttu-id="fbdf1-167">Para contornar isso, o usuário teria que encapsulam cada chamada para `Dispose` (dentro do bloco finally!) em um bloco try, o que leva para manipuladores de limpeza muito complexos.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-167">To work around this, the user would need to wrap every call to `Dispose` (within the finally block!) in a try block, which leads to very complex cleanup handlers.</span></span> <span data-ttu-id="fbdf1-168">Se a execução de um `Dispose(bool disposing)` método, nunca lançar uma exceção se disposing é false.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-168">If executing a `Dispose(bool disposing)` method, never throw an exception if disposing is false.</span></span> <span data-ttu-id="fbdf1-169">Ao fazer isso, o processo será encerrado se a execução dentro de um contexto de finalizador.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-169">Doing so will terminate the process if executing inside a finalizer context.</span></span>  
  
 <span data-ttu-id="fbdf1-170">**FAZER ✓** lançar um <xref:System.ObjectDisposedException> de qualquer membro que não pode ser usado depois que o objeto foi descartado.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-170">**✓ DO** throw an <xref:System.ObjectDisposedException> from any member that cannot be used after the object has been disposed of.</span></span>  
  
```  
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething(){  
           if(disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
            ...  
    }  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 <span data-ttu-id="fbdf1-171">**✓ CONSIDERE** fornecendo método `Close()`, além de `Dispose()`, se fechar é terminologia padrão na área.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-171">**✓ CONSIDER** providing method `Close()`, in addition to the `Dispose()`, if close is standard terminology in the area.</span></span>  
  
 <span data-ttu-id="fbdf1-172">Ao fazer isso, é importante que você faça a `Close` implementação idêntica ao `Dispose` e considere implementar a `IDisposable.Dispose` método explicitamente.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-172">When doing so, it is important that you make the `Close` implementation identical to `Dispose` and consider implementing the `IDisposable.Dispose` method explicitly.</span></span>  
  
```  
public class Stream : IDisposable {  
    IDisposable.Dispose(){  
        Close();  
    }  
    public void Close(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## <a name="finalizable-types"></a><span data-ttu-id="fbdf1-173">Tipos finalizáveis</span><span class="sxs-lookup"><span data-stu-id="fbdf1-173">Finalizable Types</span></span>  
 <span data-ttu-id="fbdf1-174">Tipos finalizáveis são tipos que estendem o padrão básico de Dispose substituir o finalizador e fornecendo o caminho de código de finalização no `Dispose(bool)` método.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-174">Finalizable types are types that extend the Basic Dispose Pattern by overriding the finalizer and providing finalization code path in the `Dispose(bool)` method.</span></span>  
  
 <span data-ttu-id="fbdf1-175">Os finalizadores são notoriamente difíceis de implementar corretamente, principalmente porque você não pode fazer algumas suposições (normalmente válidas) sobre o estado do sistema durante sua execução.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-175">Finalizers are notoriously difficult to implement correctly, primarily because you cannot make certain (normally valid) assumptions about the state of the system during their execution.</span></span> <span data-ttu-id="fbdf1-176">As diretrizes a seguir devem ser levadas em consideração cuidadosa.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-176">The following guidelines should be taken into careful consideration.</span></span>  
  
 <span data-ttu-id="fbdf1-177">Observe que algumas das diretrizes se aplicam não apenas para o `Finalize` método, mas a qualquer código chamado a partir de um finalizador.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-177">Note that some of the guidelines apply not just to the `Finalize` method, but to any code called from a finalizer.</span></span> <span data-ttu-id="fbdf1-178">No caso de Dispose padrão básico definido anteriormente, isso significa que a lógica que é executado dentro `Dispose(bool disposing)` quando o `disposing` parâmetro for false.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-178">In the case of the Basic Dispose Pattern previously defined, this means logic that executes inside `Dispose(bool disposing)` when the `disposing` parameter is false.</span></span>  
  
 <span data-ttu-id="fbdf1-179">Se a classe base já é finalizável e implementa o padrão de Dispose básico, você não deve substituir `Finalize` novamente.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-179">If the base class already is finalizable and implements the Basic Dispose Pattern, you should not override `Finalize` again.</span></span> <span data-ttu-id="fbdf1-180">Você deve em vez disso, basta substituir a `Dispose(bool)` método para fornecer lógica de limpeza de recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-180">You should instead just override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="fbdf1-181">O código a seguir mostra um exemplo de um tipo finalizável:</span><span class="sxs-lookup"><span data-stu-id="fbdf1-181">The following code shows an example of a finalizable type:</span></span>  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder(){  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing){  
            ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing){ // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 <span data-ttu-id="fbdf1-182">**X Evite** fazer tipos finalizáveis.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-182">**X AVOID** making types finalizable.</span></span>  
  
 <span data-ttu-id="fbdf1-183">Considere cuidadosamente algum caso no qual você acha que é necessário um finalizador.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-183">Carefully consider any case in which you think a finalizer is needed.</span></span> <span data-ttu-id="fbdf1-184">Há um real custo associado com instâncias com finalizadores, do ponto de vista de complexidade de um desempenho e de código.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-184">There is a real cost associated with instances with finalizers, from both a performance and code complexity standpoint.</span></span> <span data-ttu-id="fbdf1-185">Preferir usar wrappers de recursos, como <xref:System.Runtime.InteropServices.SafeHandle> para encapsular recursos não gerenciados, sempre que possível, caso em que um finalizador é desnecessário porque o wrapper é responsável por sua própria limpeza de recursos.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-185">Prefer using resource wrappers such as <xref:System.Runtime.InteropServices.SafeHandle> to encapsulate unmanaged resources where possible, in which case a finalizer becomes unnecessary because the wrapper is responsible for its own resource cleanup.</span></span>  
  
 <span data-ttu-id="fbdf1-186">**X não** tornar os tipos de valor finalizáveis.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-186">**X DO NOT** make value types finalizable.</span></span>  
  
 <span data-ttu-id="fbdf1-187">Somente os tipos de referência, na verdade, obtenham finalizados pelo CLR, e, portanto, qualquer tentativa de colocar um finalizador em um tipo de valor será ignorada.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-187">Only reference types actually get finalized by the CLR, and thus any attempt to place a finalizer on a value type will be ignored.</span></span> <span data-ttu-id="fbdf1-188">O c# e C++ compiladores impõem essa regra.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-188">The C# and C++ compilers enforce this rule.</span></span>  
  
 <span data-ttu-id="fbdf1-189">**FAZER ✓** fazer um tipo finalizáveis se o tipo é responsável pela liberação de um recurso não gerenciado que não tem seu próprio finalizador.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-189">**✓ DO** make a type finalizable if the type is responsible for releasing an unmanaged resource that does not have its own finalizer.</span></span>  
  
 <span data-ttu-id="fbdf1-190">Ao implementar o finalizador, simplesmente chamar `Dispose(false)` e coloque a lógica de limpeza todos os recursos dentro de `Dispose(bool disposing)` método.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-190">When implementing the finalizer, simply call `Dispose(false)` and place all resource cleanup logic inside the `Dispose(bool disposing)` method.</span></span>  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        ...  
    }  
}  
```  
  
 <span data-ttu-id="fbdf1-191">**FAZER ✓** implementar o padrão de Dispose básico em cada tipo finalizável.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-191">**✓ DO** implement the Basic Dispose Pattern on every finalizable type.</span></span>  
  
 <span data-ttu-id="fbdf1-192">Isso fornece aos usuários do tipo um meio para executar explicitamente a limpeza determinística desses recursos mesmo para os quais o finalizador é responsável.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-192">This gives users of the type a means to explicitly perform deterministic cleanup of those same resources for which the finalizer is responsible.</span></span>  
  
 <span data-ttu-id="fbdf1-193">**X não** acessar quaisquer objetos finalizáveis no caminho de código do finalizador, porque não há risco significativo que eles serão já ter sido finalizados.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-193">**X DO NOT** access any finalizable objects in the finalizer code path, because there is significant risk that they will have already been finalized.</span></span>  
  
 <span data-ttu-id="fbdf1-194">Por exemplo, um objeto finalizável A que tem uma referência a outro objeto finalizável B confiável não é possível usar B do finalizador, ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-194">For example, a finalizable object A that has a reference to another finalizable object B cannot reliably use B in A’s finalizer, or vice versa.</span></span> <span data-ttu-id="fbdf1-195">Os finalizadores são chamados em uma ordem aleatória (com pouca uma garantia de ordenação fraca finalização crítico).</span><span class="sxs-lookup"><span data-stu-id="fbdf1-195">Finalizers are called in a random order (short of a weak ordering guarantee for critical finalization).</span></span>  
  
 <span data-ttu-id="fbdf1-196">Além disso, lembre-se de que os objetos armazenados em variáveis estáticas obter coletados em determinados pontos durante um descarregamento de domínio de aplicativo ou ao sair do processo.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-196">Also, be aware that objects stored in static variables will get collected at certain points during an application domain unload or while exiting the process.</span></span> <span data-ttu-id="fbdf1-197">Acessando uma variável estática que se refere a um objeto finalizável (ou chamar um método estático que pode usar os valores armazenados em variáveis estáticas) pode não ser seguro se <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> retorna true.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-197">Accessing a static variable that refers to a finalizable object (or calling a static method that might use values stored in static variables) might not be safe if <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> returns true.</span></span>  
  
 <span data-ttu-id="fbdf1-198">**FAZER ✓** fazer sua `Finalize` método protegido.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-198">**✓ DO** make your `Finalize` method protected.</span></span>  
  
 <span data-ttu-id="fbdf1-199">Os desenvolvedores do c#, C++ e VB.NET não precisa se preocupar com isso, porque os compiladores de ajudam a impor essa diretriz.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-199">C#, C++, and VB.NET developers do not need to worry about this, because the compilers help to enforce this guideline.</span></span>  
  
 <span data-ttu-id="fbdf1-200">**X não** escape permitem exceções da lógica finalizador, exceto para falhas críticas do sistema.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-200">**X DO NOT** let exceptions escape from the finalizer logic, except for system-critical failures.</span></span>  
  
 <span data-ttu-id="fbdf1-201">Se uma exceção é gerada a partir de um finalizador, o CLR desligará o processo inteiro (a partir do .NET Framework versão 2.0), impedindo que outros finalizadores executando e recursos do que está sendo liberado de forma controlada.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-201">If an exception is thrown from a finalizer, the CLR will shut down the entire process (as of .NET Framework version 2.0), preventing other finalizers from executing and resources from being released in a controlled manner.</span></span>  
  
 <span data-ttu-id="fbdf1-202">**✓ CONSIDERE** criando e usando um objeto finalizável crítico (um tipo com uma hierarquia de tipo que contém <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) para situações em que um finalizador absolutamente deve executar mesmo em caso de thread e os descarregamentos de domínio de aplicativo forçada será anulada.</span><span class="sxs-lookup"><span data-stu-id="fbdf1-202">**✓ CONSIDER** creating and using a critical finalizable object (a type with a type hierarchy that contains <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) for situations in which a finalizer absolutely must execute even in the face of forced application domain unloads and thread aborts.</span></span>  
  
 <span data-ttu-id="fbdf1-203">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="fbdf1-203">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="fbdf1-204">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="fbdf1-204">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbdf1-205">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbdf1-205">See Also</span></span>  
 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="fbdf1-206">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="fbdf1-206">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="fbdf1-207">Padrões comuns de Design</span><span class="sxs-lookup"><span data-stu-id="fbdf1-207">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 [<span data-ttu-id="fbdf1-208">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="fbdf1-208">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
