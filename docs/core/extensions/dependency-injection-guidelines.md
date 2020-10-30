---
title: Diretrizes de injeção de dependência
description: Conheça várias diretrizes de injeção de dependência e práticas recomendadas para o desenvolvimento de aplicativos .NET.
author: IEvangelist
ms.author: dapine
ms.date: 10/29/2020
ms.topic: guide
ms.openlocfilehash: 092fdc70bd5d6bae82c4c1da96db4d5ac08df452
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063163"
---
# <a name="dependency-injection-guidelines"></a><span data-ttu-id="a970d-103">Diretrizes de injeção de dependência</span><span class="sxs-lookup"><span data-stu-id="a970d-103">Dependency injection guidelines</span></span>

<span data-ttu-id="a970d-104">Este artigo fornece diretrizes gerais e práticas recomendadas para implementar a injeção de dependência em aplicativos .NET.</span><span class="sxs-lookup"><span data-stu-id="a970d-104">This article provides general guidelines and best practices for implementing dependency injection in .NET applications.</span></span>

## <a name="design-services-for-dependency-injection"></a><span data-ttu-id="a970d-105">Projetar serviços para injeção de dependência</span><span class="sxs-lookup"><span data-stu-id="a970d-105">Design services for dependency injection</span></span>

<span data-ttu-id="a970d-106">Ao projetar serviços para injeção de dependência:</span><span class="sxs-lookup"><span data-stu-id="a970d-106">When designing services for dependency injection:</span></span>

- <span data-ttu-id="a970d-107">Evite classes e membros com estado e estáticos.</span><span class="sxs-lookup"><span data-stu-id="a970d-107">Avoid stateful, static classes and members.</span></span> <span data-ttu-id="a970d-108">Evite criar o estado global criando aplicativos para usar os serviços singleton.</span><span class="sxs-lookup"><span data-stu-id="a970d-108">Avoid creating global state by designing apps to use singleton services instead.</span></span>
- <span data-ttu-id="a970d-109">Evite a instanciação direta das classes dependentes em serviços.</span><span class="sxs-lookup"><span data-stu-id="a970d-109">Avoid direct instantiation of dependent classes within services.</span></span> <span data-ttu-id="a970d-110">A instanciação direta acopla o código a uma implementação específica.</span><span class="sxs-lookup"><span data-stu-id="a970d-110">Direct instantiation couples the code to a particular implementation.</span></span>
- <span data-ttu-id="a970d-111">Torne os serviços pequenos, bem fatorados e facilmente testados.</span><span class="sxs-lookup"><span data-stu-id="a970d-111">Make services small, well-factored, and easily tested.</span></span>

<span data-ttu-id="a970d-112">Se uma classe tiver muitas dependências injetadas, poderá ser um sinal de que a classe tem muitas responsabilidades e violará o [princípio de responsabilidade única (SRP)](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility).</span><span class="sxs-lookup"><span data-stu-id="a970d-112">If a class has many injected dependencies, it might be a sign that the class has too many responsibilities and violates the [Single Responsibility Principle (SRP)](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility).</span></span> <span data-ttu-id="a970d-113">Tente refatorar a classe movendo algumas de suas responsabilidades para novas classes.</span><span class="sxs-lookup"><span data-stu-id="a970d-113">Attempt to refactor the class by moving some of its responsibilities into new classes.</span></span>

### <a name="disposal-of-services"></a><span data-ttu-id="a970d-114">Descarte de serviços</span><span class="sxs-lookup"><span data-stu-id="a970d-114">Disposal of services</span></span>

<span data-ttu-id="a970d-115">O contêiner é responsável pela limpeza dos tipos que cria e chama <xref:System.IDisposable.Dispose%2A> em <xref:System.IDisposable> instâncias.</span><span class="sxs-lookup"><span data-stu-id="a970d-115">The container is responsible for cleanup of types it creates, and calls <xref:System.IDisposable.Dispose%2A> on <xref:System.IDisposable> instances.</span></span> <span data-ttu-id="a970d-116">Os serviços resolvidos do contêiner nunca devem ser descartados pelo desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="a970d-116">Services resolved from the container should never be disposed by the developer.</span></span> <span data-ttu-id="a970d-117">Se um tipo ou fábrica for registrado como um singleton, o contêiner descartará o singleton automaticamente.</span><span class="sxs-lookup"><span data-stu-id="a970d-117">If a type or factory is registered as a singleton, the container disposes the singleton automatically.</span></span>

<span data-ttu-id="a970d-118">No exemplo a seguir, os serviços são criados pelo contêiner de serviço e descartados automaticamente:</span><span class="sxs-lookup"><span data-stu-id="a970d-118">In the following example, the services are created by the service container and disposed automatically:</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/TransientDisposable.cs":::

<span data-ttu-id="a970d-119">O descartável anterior deve ter um tempo de vida transitório.</span><span class="sxs-lookup"><span data-stu-id="a970d-119">The preceding disposable is intended to have a transient lifetime.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/ScopedDisposable.cs":::

<span data-ttu-id="a970d-120">O descartável anterior tem como objetivo ter um tempo de vida de escopo.</span><span class="sxs-lookup"><span data-stu-id="a970d-120">The preceding disposable is intended to have a scoped lifetime.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/SingletonDisposable.cs":::

<span data-ttu-id="a970d-121">O descartável anterior deve ter um tempo de vida singleton.</span><span class="sxs-lookup"><span data-stu-id="a970d-121">The preceding disposable is intended to have a singleton lifetime.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/Program.cs" range="1-21,41-60" highlight="":::

<span data-ttu-id="a970d-122">O console de depuração mostra a seguinte saída de exemplo após a execução:</span><span class="sxs-lookup"><span data-stu-id="a970d-122">The debug console shows the following sample output after running:</span></span>

```console
Scope 1...
ScopedDisposable.Dispose()
TransientDisposable.Dispose()

Scope 2...
ScopedDisposable.Dispose()
TransientDisposable.Dispose()

info: Microsoft.Hosting.Lifetime[0]
      Application started.Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
     Hosting environment: Production
info: Microsoft.Hosting.Lifetime[0]
     Content root path: .\configuration\console-di-disposable\bin\Debug\net5.0
info: Microsoft.Hosting.Lifetime[0]
     Application is shutting down...
SingletonDisposable.Dispose()
```

### <a name="services-not-created-by-the-service-container"></a><span data-ttu-id="a970d-123">Serviços não criados pelo contêiner de serviço</span><span class="sxs-lookup"><span data-stu-id="a970d-123">Services not created by the service container</span></span>

<span data-ttu-id="a970d-124">Considere o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="a970d-124">Consider the following code:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddSingleton(new ExampleService());

    // ...
}
```

<span data-ttu-id="a970d-125">No código anterior:</span><span class="sxs-lookup"><span data-stu-id="a970d-125">In the preceding code:</span></span>

- <span data-ttu-id="a970d-126">A `ExampleService` instância **não** é criada pelo contêiner de serviço.</span><span class="sxs-lookup"><span data-stu-id="a970d-126">The `ExampleService` instance is **not** created by the service container.</span></span>
- <span data-ttu-id="a970d-127">A estrutura não **descarta os** serviços automaticamente.</span><span class="sxs-lookup"><span data-stu-id="a970d-127">The framework does **not** dispose of the services automatically.</span></span>
- <span data-ttu-id="a970d-128">O desenvolvedor é responsável por descartar os serviços.</span><span class="sxs-lookup"><span data-stu-id="a970d-128">The developer is responsible for disposing the services.</span></span>

### <a name="idisposable-guidance-for-transient-and-shared-instances"></a><span data-ttu-id="a970d-129">Diretrizes de IDisposable para instâncias transitórias e compartilhadas</span><span class="sxs-lookup"><span data-stu-id="a970d-129">IDisposable guidance for Transient and shared instances</span></span>

#### <a name="transient-limited-lifetime"></a><span data-ttu-id="a970d-130">Tempo de vida transitório, limitado</span><span class="sxs-lookup"><span data-stu-id="a970d-130">Transient, limited lifetime</span></span>

<span data-ttu-id="a970d-131">**Cenário**</span><span class="sxs-lookup"><span data-stu-id="a970d-131">**Scenario**</span></span>

<span data-ttu-id="a970d-132">O aplicativo requer uma <xref:System.IDisposable> instância com um tempo de vida transitório para qualquer um dos seguintes cenários:</span><span class="sxs-lookup"><span data-stu-id="a970d-132">The app requires an <xref:System.IDisposable> instance with a transient lifetime for either of the following scenarios:</span></span>

- <span data-ttu-id="a970d-133">A instância é resolvida no escopo raiz (contêiner raiz).</span><span class="sxs-lookup"><span data-stu-id="a970d-133">The instance is resolved in the root scope (root container).</span></span>
- <span data-ttu-id="a970d-134">A instância deve ser descartada antes do término do escopo.</span><span class="sxs-lookup"><span data-stu-id="a970d-134">The instance should be disposed before the scope ends.</span></span>

<span data-ttu-id="a970d-135">**Solução**</span><span class="sxs-lookup"><span data-stu-id="a970d-135">**Solution**</span></span>

<span data-ttu-id="a970d-136">Use o padrão de fábrica para criar uma instância fora do escopo pai.</span><span class="sxs-lookup"><span data-stu-id="a970d-136">Use the factory pattern to create an instance outside of the parent scope.</span></span> <span data-ttu-id="a970d-137">Nessa situação, o aplicativo geralmente teria um `Create` método que chamasse o construtor do tipo final diretamente.</span><span class="sxs-lookup"><span data-stu-id="a970d-137">In this situation, the app would generally have a `Create` method that calls the final type's constructor directly.</span></span> <span data-ttu-id="a970d-138">Se o tipo final tiver outras dependências, a fábrica poderá:</span><span class="sxs-lookup"><span data-stu-id="a970d-138">If the final type has other dependencies, the factory can:</span></span>

- <span data-ttu-id="a970d-139">Receber um <xref:System.IServiceProvider> em seu construtor.</span><span class="sxs-lookup"><span data-stu-id="a970d-139">Receive an <xref:System.IServiceProvider> in its constructor.</span></span>
- <span data-ttu-id="a970d-140">Use <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType> para instanciar a instância fora do contêiner, ao usar o contêiner para suas dependências.</span><span class="sxs-lookup"><span data-stu-id="a970d-140">Use <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType> to instantiate the instance outside of the container, while using the container for its dependencies.</span></span>

#### <a name="shared-instance-limited-lifetime"></a><span data-ttu-id="a970d-141">Instância compartilhada, tempo de vida limitado</span><span class="sxs-lookup"><span data-stu-id="a970d-141">Shared instance, limited lifetime</span></span>

<span data-ttu-id="a970d-142">**Cenário**</span><span class="sxs-lookup"><span data-stu-id="a970d-142">**Scenario**</span></span>

<span data-ttu-id="a970d-143">O aplicativo requer uma <xref:System.IDisposable> instância compartilhada em vários serviços, mas a <xref:System.IDisposable> instância deve ter um tempo de vida limitado.</span><span class="sxs-lookup"><span data-stu-id="a970d-143">The app requires a shared <xref:System.IDisposable> instance across multiple services, but the <xref:System.IDisposable> instance should have a limited lifetime.</span></span>

<span data-ttu-id="a970d-144">**Solução**</span><span class="sxs-lookup"><span data-stu-id="a970d-144">**Solution**</span></span>

<span data-ttu-id="a970d-145">Registre a instância com um tempo de vida de escopo.</span><span class="sxs-lookup"><span data-stu-id="a970d-145">Register the instance with a scoped lifetime.</span></span> <span data-ttu-id="a970d-146">Use <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType> para criar um novo <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> .</span><span class="sxs-lookup"><span data-stu-id="a970d-146">Use <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType> to create a new <xref:Microsoft.Extensions.DependencyInjection.IServiceScope>.</span></span> <span data-ttu-id="a970d-147">Use o escopo <xref:System.IServiceProvider> para obter os serviços necessários.</span><span class="sxs-lookup"><span data-stu-id="a970d-147">Use the scope's <xref:System.IServiceProvider> to get required services.</span></span> <span data-ttu-id="a970d-148">Descarte o escopo quando ele não for mais necessário.</span><span class="sxs-lookup"><span data-stu-id="a970d-148">Dispose the scope when it's no longer needed.</span></span>

#### <a name="general-idisposable-guidelines"></a><span data-ttu-id="a970d-149">`IDisposable`Diretrizes gerais</span><span class="sxs-lookup"><span data-stu-id="a970d-149">General `IDisposable` guidelines</span></span>

- <span data-ttu-id="a970d-150">Não registre <xref:System.IDisposable> instâncias com um tempo de vida transitório.</span><span class="sxs-lookup"><span data-stu-id="a970d-150">Don't register <xref:System.IDisposable> instances with a transient lifetime.</span></span> <span data-ttu-id="a970d-151">Em vez disso, use o padrão de fábrica.</span><span class="sxs-lookup"><span data-stu-id="a970d-151">Use the factory pattern instead.</span></span>
- <span data-ttu-id="a970d-152">Não resolva <xref:System.IDisposable> instâncias com um tempo de vida transitório ou com escopo definido no escopo raiz.</span><span class="sxs-lookup"><span data-stu-id="a970d-152">Don't resolve <xref:System.IDisposable> instances with a transient or scoped lifetime in the root scope.</span></span> <span data-ttu-id="a970d-153">A única exceção a isso é se o aplicativo cria/recria e descarta <xref:System.IServiceProvider> , mas esse não é um padrão ideal.</span><span class="sxs-lookup"><span data-stu-id="a970d-153">The only exception to this is if the app creates/recreates and disposes <xref:System.IServiceProvider>, but this isn't an ideal pattern.</span></span>
- <span data-ttu-id="a970d-154">O recebimento de uma <xref:System.IDisposable> dependência por meio de di não exige que o receptor se implemente <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="a970d-154">Receiving an <xref:System.IDisposable> dependency via DI doesn't require that the receiver implement <xref:System.IDisposable> itself.</span></span> <span data-ttu-id="a970d-155">O receptor da <xref:System.IDisposable> dependência não deve chamar <xref:System.IDisposable.Dispose%2A> essa dependência.</span><span class="sxs-lookup"><span data-stu-id="a970d-155">The receiver of the <xref:System.IDisposable> dependency shouldn't call <xref:System.IDisposable.Dispose%2A> on that dependency.</span></span>
- <span data-ttu-id="a970d-156">Use escopos para controlar os tempos de vida dos serviços.</span><span class="sxs-lookup"><span data-stu-id="a970d-156">Use scopes to control the lifetimes of services.</span></span> <span data-ttu-id="a970d-157">Os escopos não são hierárquicos e não há nenhuma conexão especial entre escopos.</span><span class="sxs-lookup"><span data-stu-id="a970d-157">Scopes aren't hierarchical, and there's no special connection among scopes.</span></span>

<span data-ttu-id="a970d-158">Para obter mais informações sobre a limpeza de recursos, consulte [implementar um `Dispose` método](../../standard/garbage-collection/implementing-dispose.md)ou [implementar um `DisposeAsync` método](../../standard/garbage-collection/implementing-disposeasync.md).</span><span class="sxs-lookup"><span data-stu-id="a970d-158">For more information on resource cleanup, see [Implement a `Dispose` method](../../standard/garbage-collection/implementing-dispose.md), or [Implement a `DisposeAsync` method](../../standard/garbage-collection/implementing-disposeasync.md).</span></span> <span data-ttu-id="a970d-159">Além disso, considere os [Serviços transitórios descartáveis capturados pelo](#disposable-transient-services-captured-by-container) cenário de contêiner, pois ele se relaciona com a limpeza de recursos.</span><span class="sxs-lookup"><span data-stu-id="a970d-159">Additionally, consider the [Disposable transient services captured by container](#disposable-transient-services-captured-by-container) scenario as it relates to resource cleanup.</span></span>

## <a name="default-service-container-replacement"></a><span data-ttu-id="a970d-160">Substituição do contêiner de serviço padrão</span><span class="sxs-lookup"><span data-stu-id="a970d-160">Default service container replacement</span></span>

<span data-ttu-id="a970d-161">O contêiner de serviço interno foi projetado para atender às necessidades da estrutura e da maioria dos aplicativos de consumidor.</span><span class="sxs-lookup"><span data-stu-id="a970d-161">The built-in service container is designed to serve the needs of the framework and most consumer apps.</span></span> <span data-ttu-id="a970d-162">É recomendável usar o contêiner interno, a menos que você precise de um recurso específico ao qual ele não ofereça suporte, como:</span><span class="sxs-lookup"><span data-stu-id="a970d-162">We recommend using the built-in container unless you need a specific feature that it doesn't support, such as:</span></span>

- <span data-ttu-id="a970d-163">Injeção de propriedade</span><span class="sxs-lookup"><span data-stu-id="a970d-163">Property injection</span></span>
- <span data-ttu-id="a970d-164">Injeção com base no nome</span><span class="sxs-lookup"><span data-stu-id="a970d-164">Injection based on name</span></span>
- <span data-ttu-id="a970d-165">Contêineres filho</span><span class="sxs-lookup"><span data-stu-id="a970d-165">Child containers</span></span>
- <span data-ttu-id="a970d-166">Gerenciamento de tempo de vida personalizado</span><span class="sxs-lookup"><span data-stu-id="a970d-166">Custom lifetime management</span></span>
- <span data-ttu-id="a970d-167">Suporte de `Func<T>` para inicialização lenta</span><span class="sxs-lookup"><span data-stu-id="a970d-167">`Func<T>` support for lazy initialization</span></span>
- <span data-ttu-id="a970d-168">Registro baseado em Convenção</span><span class="sxs-lookup"><span data-stu-id="a970d-168">Convention-based registration</span></span>

<span data-ttu-id="a970d-169">Os seguintes contêineres de terceiros podem ser usados com aplicativos ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="a970d-169">The following third-party containers can be used with ASP.NET Core apps:</span></span>

- [<span data-ttu-id="a970d-170">Autofac</span><span class="sxs-lookup"><span data-stu-id="a970d-170">Autofac</span></span>](https://autofac.readthedocs.io/en/latest/integration/aspnetcore.html)
- [<span data-ttu-id="a970d-171">DryIoc</span><span class="sxs-lookup"><span data-stu-id="a970d-171">DryIoc</span></span>](https://www.nuget.org/packages/DryIoc.Microsoft.DependencyInjection)
- [<span data-ttu-id="a970d-172">Grace</span><span class="sxs-lookup"><span data-stu-id="a970d-172">Grace</span></span>](https://www.nuget.org/packages/Grace.DependencyInjection.Extensions)
- [<span data-ttu-id="a970d-173">LightInject</span><span class="sxs-lookup"><span data-stu-id="a970d-173">LightInject</span></span>](https://github.com/seesharper/LightInject.Microsoft.DependencyInjection)
- [<span data-ttu-id="a970d-174">Lamar</span><span class="sxs-lookup"><span data-stu-id="a970d-174">Lamar</span></span>](https://jasperfx.github.io/lamar/)
- [<span data-ttu-id="a970d-175">Stashbox</span><span class="sxs-lookup"><span data-stu-id="a970d-175">Stashbox</span></span>](https://github.com/z4kn4fein/stashbox-extensions-dependencyinjection)
- [<span data-ttu-id="a970d-176">Unity</span><span class="sxs-lookup"><span data-stu-id="a970d-176">Unity</span></span>](https://www.nuget.org/packages/Unity.Microsoft.DependencyInjection)

## <a name="thread-safety"></a><span data-ttu-id="a970d-177">Acesso thread-safe</span><span class="sxs-lookup"><span data-stu-id="a970d-177">Thread safety</span></span>

<span data-ttu-id="a970d-178">Crie serviços singleton thread-safe.</span><span class="sxs-lookup"><span data-stu-id="a970d-178">Create thread-safe singleton services.</span></span> <span data-ttu-id="a970d-179">Se um serviço singleton tiver uma dependência em um serviço transitório, o serviço transitório também poderá exigir a segurança do thread dependendo de como ele é usado pelo singleton.</span><span class="sxs-lookup"><span data-stu-id="a970d-179">If a singleton service has a dependency on a transient service, the transient service may also require thread safety depending on how it's used by the singleton.</span></span>

<span data-ttu-id="a970d-180">O método de fábrica de um único serviço, como o segundo argumento para [addsingleton \<TService> (IServiceCollection, Func \<IServiceProvider,TService> )](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A), não precisa ser thread-safe.</span><span class="sxs-lookup"><span data-stu-id="a970d-180">The factory method of single service, such as the second argument to [AddSingleton\<TService>(IServiceCollection, Func\<IServiceProvider,TService>)](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A), doesn't need to be thread-safe.</span></span> <span data-ttu-id="a970d-181">Como um construtor de tipo ( `static` ), é garantido que ele seja chamado apenas uma vez por um único thread.</span><span class="sxs-lookup"><span data-stu-id="a970d-181">Like a type (`static`) constructor, it's guaranteed to be called only once by a single thread.</span></span>

## <a name="recommendations"></a><span data-ttu-id="a970d-182">Recomendações</span><span class="sxs-lookup"><span data-stu-id="a970d-182">Recommendations</span></span>

- <span data-ttu-id="a970d-183">`async/await` e a `Task` resolução de serviço baseada não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="a970d-183">`async/await` and `Task` based service resolution isn't supported.</span></span> <span data-ttu-id="a970d-184">Como o C# não dá suporte a construtores assíncronos, use métodos assíncronos após a resolução síncrona do serviço.</span><span class="sxs-lookup"><span data-stu-id="a970d-184">Because C# doesn't support asynchronous constructors, use asynchronous methods after synchronously resolving the service.</span></span>
- <span data-ttu-id="a970d-185">Evite armazenar dados e a configuração diretamente no contêiner do serviço.</span><span class="sxs-lookup"><span data-stu-id="a970d-185">Avoid storing data and configuration directly in the service container.</span></span> <span data-ttu-id="a970d-186">Por exemplo, o carrinho de compras de um usuário normalmente não deve ser adicionado ao contêiner do serviço.</span><span class="sxs-lookup"><span data-stu-id="a970d-186">For example, a user's shopping cart shouldn't typically be added to the service container.</span></span> <span data-ttu-id="a970d-187">A configuração deve usar o padrão de opções.</span><span class="sxs-lookup"><span data-stu-id="a970d-187">Configuration should use the options pattern.</span></span> <span data-ttu-id="a970d-188">Da mesma forma, evite objetos de "portador de dados" que existem somente para permitir o acesso a outro objeto.</span><span class="sxs-lookup"><span data-stu-id="a970d-188">Similarly, avoid "data holder" objects that only exist to allow access to another object.</span></span> <span data-ttu-id="a970d-189">É melhor solicitar o item real por meio da DI.</span><span class="sxs-lookup"><span data-stu-id="a970d-189">It's better to request the actual item via DI.</span></span>
- <span data-ttu-id="a970d-190">Evite o acesso estático aos serviços.</span><span class="sxs-lookup"><span data-stu-id="a970d-190">Avoid static access to services.</span></span> <span data-ttu-id="a970d-191">Por exemplo, evite capturar [IApplicationBuilder. ApplicationServices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) como um campo ou propriedade estática para uso em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="a970d-191">For example, avoid capturing [IApplicationBuilder.ApplicationServices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) as a static field or property for use elsewhere.</span></span>
- <span data-ttu-id="a970d-192">Mantenha as [fábricas de injeção](#async-di-factories-can-cause-deadlocks) rápida e síncrona.</span><span class="sxs-lookup"><span data-stu-id="a970d-192">Keep [DI factories](#async-di-factories-can-cause-deadlocks) fast and synchronous.</span></span>
- <span data-ttu-id="a970d-193">Evite usar o [*padrão de localizador de serviço*](#scoped-service-as-singleton).</span><span class="sxs-lookup"><span data-stu-id="a970d-193">Avoid using the [*service locator pattern*](#scoped-service-as-singleton).</span></span> <span data-ttu-id="a970d-194">Por exemplo, não invoque <xref:System.IServiceProvider.GetService%2A> para obter uma instância de serviço quando for possível usar a DI.</span><span class="sxs-lookup"><span data-stu-id="a970d-194">For example, don't invoke <xref:System.IServiceProvider.GetService%2A> to obtain a service instance when you can use DI instead.</span></span>
- <span data-ttu-id="a970d-195">Outra variação de localizador de serviço a ser evitada é injetar um alocador que resolve as dependências em runtime.</span><span class="sxs-lookup"><span data-stu-id="a970d-195">Another service locator variation to avoid is injecting a factory that resolves dependencies at runtime.</span></span> <span data-ttu-id="a970d-196">Essas duas práticas misturam estratégias de [inversão de controle](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion).</span><span class="sxs-lookup"><span data-stu-id="a970d-196">Both of these practices mix [Inversion of Control](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion) strategies.</span></span>
- <span data-ttu-id="a970d-197">Evite chamadas para <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> no `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="a970d-197">Avoid calls to <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> in `ConfigureServices`.</span></span> <span data-ttu-id="a970d-198">Chamar `BuildServiceProvider` normalmente acontece quando o desenvolvedor deseja resolver um serviço no `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="a970d-198">Calling `BuildServiceProvider` typically happens when the developer wants to resolve a service in `ConfigureServices`.</span></span>
- <span data-ttu-id="a970d-199">[Serviços Inposados transitórios são capturados](#disposable-transient-services-captured-by-container) pelo contêiner para descarte.</span><span class="sxs-lookup"><span data-stu-id="a970d-199">[Disposable transient services are captured](#disposable-transient-services-captured-by-container) by the container for disposal.</span></span> <span data-ttu-id="a970d-200">Isso pode transformar em um vazamento de memória se resolvido do contêiner de nível superior.</span><span class="sxs-lookup"><span data-stu-id="a970d-200">This can turn into a memory leak if resolved from the top-level container.</span></span>
- <span data-ttu-id="a970d-201">Habilite a validação de escopo para certificar-se de que o aplicativo não tem singletons que capturam serviços com escopo.</span><span class="sxs-lookup"><span data-stu-id="a970d-201">Enable scope validation to make sure the app doesn't have singletons that capture scoped services.</span></span> <span data-ttu-id="a970d-202">Para obter mais informações, confira [Validação de escopo](dependency-injection.md#scope-validation).</span><span class="sxs-lookup"><span data-stu-id="a970d-202">For more information, see [Scope validation](dependency-injection.md#scope-validation).</span></span>

<span data-ttu-id="a970d-203">Como todos os conjuntos de recomendações, talvez você encontre situações em que é necessário ignorar uma recomendação.</span><span class="sxs-lookup"><span data-stu-id="a970d-203">Like all sets of recommendations, you may encounter situations where ignoring a recommendation is required.</span></span> <span data-ttu-id="a970d-204">As exceções são raras, principalmente os casos especiais dentro da própria estrutura.</span><span class="sxs-lookup"><span data-stu-id="a970d-204">Exceptions are rare, mostly special cases within the framework itself.</span></span>

<span data-ttu-id="a970d-205">A DI é uma *alternativa* aos padrões de acesso a objeto estático/global.</span><span class="sxs-lookup"><span data-stu-id="a970d-205">DI is an *alternative* to static/global object access patterns.</span></span> <span data-ttu-id="a970d-206">Talvez você não obtenha os benefícios da DI se combiná-lo com o acesso a objeto estático.</span><span class="sxs-lookup"><span data-stu-id="a970d-206">You may not be able to realize the benefits of DI if you mix it with static object access.</span></span>

## <a name="example-anti-patterns"></a><span data-ttu-id="a970d-207">Antipadrões de exemplo</span><span class="sxs-lookup"><span data-stu-id="a970d-207">Example anti-patterns</span></span>

<span data-ttu-id="a970d-208">Além das diretrizes neste artigo, há vários antipadrões *que você **deve** evitar* .</span><span class="sxs-lookup"><span data-stu-id="a970d-208">In addition to the guidelines in this article, there are several anti-patterns *you **should** avoid* .</span></span> <span data-ttu-id="a970d-209">Alguns desses antipadrões são aprender a desenvolver os tempos de execução em si.</span><span class="sxs-lookup"><span data-stu-id="a970d-209">Some of these anti-patterns are learnings from developing the runtimes themselves.</span></span>

> [!WARNING]
> <span data-ttu-id="a970d-210">Esses são antipadrões de exemplo, *não copiam* o código, *não usam esses* padrões e evitam esses padrões com todos os custos.</span><span class="sxs-lookup"><span data-stu-id="a970d-210">These are example anti-patterns, *do not* copy the code, *do not* use these patterns, and avoid these patterns at all costs.</span></span>

### <a name="disposable-transient-services-captured-by-container"></a><span data-ttu-id="a970d-211">Serviços transitórios descartáveis capturados pelo contêiner</span><span class="sxs-lookup"><span data-stu-id="a970d-211">Disposable transient services captured by container</span></span>

<span data-ttu-id="a970d-212">Quando você registra serviços *transitórios* que implementam <xref:System.IDisposable> , por padrão, o contêiner di manterá essas referências e não delas <xref:System.IDisposable.Dispose> até que o aplicativo pare.</span><span class="sxs-lookup"><span data-stu-id="a970d-212">When you register *Transient* services that implement <xref:System.IDisposable>, by default the DI container will hold onto these references, and not <xref:System.IDisposable.Dispose> of them until the application stops.</span></span> <span data-ttu-id="a970d-213">Isso pode transformar em um vazamento de memória se resolvido no contêiner de nível.</span><span class="sxs-lookup"><span data-stu-id="a970d-213">This can turn into a memory leak if resolved from the level container.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="18-30":::

<span data-ttu-id="a970d-214">No antipadrão anterior, 1.000 `ExampleDisposable` objetos são instanciados e com raiz.</span><span class="sxs-lookup"><span data-stu-id="a970d-214">In the preceding anti-pattern, 1,000 `ExampleDisposable` objects are instantiated and rooted.</span></span> <span data-ttu-id="a970d-215">Eles não serão descartados até que a `serviceProvider` instância seja descartada.</span><span class="sxs-lookup"><span data-stu-id="a970d-215">They will not be disposed of until the `serviceProvider` instance is disposed.</span></span>

<span data-ttu-id="a970d-216">Para obter mais informações sobre como depurar vazamentos de memória, consulte [depurar um vazamento de memória no .net](../diagnostics/debug-memory-leak.md).</span><span class="sxs-lookup"><span data-stu-id="a970d-216">For more information on debugging memory leaks, see [Debug a memory leak in .NET](../diagnostics/debug-memory-leak.md).</span></span>

### <a name="async-di-factories-can-cause-deadlocks"></a><span data-ttu-id="a970d-217">Fábricas de DI assíncronas podem causar deadlocks</span><span class="sxs-lookup"><span data-stu-id="a970d-217">Async DI factories can cause deadlocks</span></span>

<span data-ttu-id="a970d-218">O termo "fábricas de DI" refere-se aos métodos de sobrecarga que existem ao chamar `Add{LIFETIME}` .</span><span class="sxs-lookup"><span data-stu-id="a970d-218">The term "DI factories" refers to the overload methods that exist when calling `Add{LIFETIME}`.</span></span> <span data-ttu-id="a970d-219">Há sobrecargas aceitando um `Func<IServiceProvider, T>` onde `T` o serviço está sendo registrado e o parâmetro é nomeado `implementationFactory` .</span><span class="sxs-lookup"><span data-stu-id="a970d-219">There are overloads accepting a `Func<IServiceProvider, T>` where `T` is the service being registered, and the parameter is named `implementationFactory`.</span></span> <span data-ttu-id="a970d-220">O `implementationFactory` pode ser fornecido como uma expressão lambda, uma função local ou um método.</span><span class="sxs-lookup"><span data-stu-id="a970d-220">The `implementationFactory` can be provided as a lambda expression, local function, or method.</span></span> <span data-ttu-id="a970d-221">Se a fábrica for assíncrona, e você usar <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> , isso gerará um deadlock.</span><span class="sxs-lookup"><span data-stu-id="a970d-221">If the factory is asynchronous, and you use <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType>, this will cause a deadlock.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="32-45" highlight="4-8":::

<span data-ttu-id="a970d-222">No código anterior, o recebe `implementationFactory` uma expressão lambda em que o corpo chama <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> um método de `Task<Bar>` retorno.</span><span class="sxs-lookup"><span data-stu-id="a970d-222">In the preceding code, the `implementationFactory` is given a lambda expression where the body calls <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> on a `Task<Bar>` returning method.</span></span> <span data-ttu-id="a970d-223">Isso ***causa um deadlock*** .</span><span class="sxs-lookup"><span data-stu-id="a970d-223">This ***causes a deadlock*** .</span></span> <span data-ttu-id="a970d-224">O `GetBarAsync` método simplesmente emula uma operação de trabalho assíncrona com <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> e, em seguida, chama <xref:Microsoft.Extensions.DependencyInjection.ServiceProviderServiceExtensions.GetRequiredService%60%601(System.IServiceProvider)> .</span><span class="sxs-lookup"><span data-stu-id="a970d-224">The `GetBarAsync` method simply emulates an asynchronous work operation with <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType>, and then calls <xref:Microsoft.Extensions.DependencyInjection.ServiceProviderServiceExtensions.GetRequiredService%60%601(System.IServiceProvider)>.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="47-53":::

<span data-ttu-id="a970d-225">Para obter mais informações sobre diretrizes assíncronas, consulte [programação assíncrona: informações importantes e conselhos](../../csharp/async.md#important-info-and-advice).</span><span class="sxs-lookup"><span data-stu-id="a970d-225">For more information on asynchronous guidance, see [Asynchronous programming: Important info and advice](../../csharp/async.md#important-info-and-advice).</span></span> <span data-ttu-id="a970d-226">Para obter mais informações sobre depuração de deadlocks, consulte [depurar um deadlock no .net](../diagnostics/debug-deadlock.md).</span><span class="sxs-lookup"><span data-stu-id="a970d-226">For more information debugging deadlocks, see [Debug a deadlock in .NET](../diagnostics/debug-deadlock.md).</span></span>

<span data-ttu-id="a970d-227">Quando você estiver executando esse antipadrão e o deadlock ocorrer, poderá exibir os dois threads aguardando a janela de pilhas paralelas do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a970d-227">When you're running this anti-pattern and the deadlock occurs, you can view the two threads waiting from Visual Studio's Parallel Stacks window.</span></span> <span data-ttu-id="a970d-228">Para obter mais informações, consulte [exibir threads e tarefas na janela pilhas paralelas](/visualstudio/debugger/using-the-parallel-stacks-window).</span><span class="sxs-lookup"><span data-stu-id="a970d-228">For more information, see [View threads and tasks in the Parallel Stacks window](/visualstudio/debugger/using-the-parallel-stacks-window).</span></span>

### <a name="captive-dependency"></a><span data-ttu-id="a970d-229">Dependência cativo</span><span class="sxs-lookup"><span data-stu-id="a970d-229">Captive dependency</span></span>

<span data-ttu-id="a970d-230">O termo ["dependência cativo"](https://blog.ploeh.dk/2014/06/02/captive-dependency) foi cunhado por [Mark Seeman](https://blog.ploeh.dk/about)e refere-se à configuração incorreta de tempos de vida do serviço, em que um serviço de vida maior tem um serviço de vida mais curto cativo.</span><span class="sxs-lookup"><span data-stu-id="a970d-230">The term ["captive dependency"](https://blog.ploeh.dk/2014/06/02/captive-dependency) was coined by [Mark Seeman](https://blog.ploeh.dk/about), and refers to the misconfiguration of service lifetimes, where a longer-lived service holds a shorter-lived service captive.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="55-65":::

<span data-ttu-id="a970d-231">No código anterior, `Foo` é registrado como um singleton e `Bar` tem o escopo, que na superfície parece válido.</span><span class="sxs-lookup"><span data-stu-id="a970d-231">In the preceding code, `Foo` is registered as a singleton and `Bar` is scoped - which on the surface seems valid.</span></span> <span data-ttu-id="a970d-232">No entanto, considere a implementação de `Foo` .</span><span class="sxs-lookup"><span data-stu-id="a970d-232">However, consider the implementation of `Foo`.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Foo.cs" highlight="5":::

<span data-ttu-id="a970d-233">O `Foo` objeto requer um `Bar` objeto e, como `Foo` é um singleton e `Bar` tem o escopo definido, essa é uma configuração incorreta.</span><span class="sxs-lookup"><span data-stu-id="a970d-233">The `Foo` object requires a `Bar` object, and since `Foo` is a singleton, and `Bar` is scoped - this is a misconfiguration.</span></span> <span data-ttu-id="a970d-234">Como está, `Foo` ela só seria instanciada uma vez e seria mantida `Bar` por seu tempo de vida, o que é mais longo do que o tempo de vida do escopo pretendido de `Bar` .</span><span class="sxs-lookup"><span data-stu-id="a970d-234">As is, `Foo` would only be instantiated once, and it would hold onto `Bar` for its lifetime, which is longer than the intended scoped lifetime of `Bar`.</span></span> <span data-ttu-id="a970d-235">Você deve considerar a validação de escopos, passando `validateScopes: true` para o <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Boolean)> .</span><span class="sxs-lookup"><span data-stu-id="a970d-235">You should consider validating scopes, by passing `validateScopes: true` to the <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Boolean)>.</span></span> <span data-ttu-id="a970d-236">Ao validar os escopos, você receberá um <xref:System.InvalidOperationException> com uma mensagem semelhante a "não é possível consumir o serviço no escopo ' bar ' do singleton ' foo '.".</span><span class="sxs-lookup"><span data-stu-id="a970d-236">When you validate the scopes, you'd get an <xref:System.InvalidOperationException> with a message similar to "Cannot consume scoped service 'Bar' from singleton 'Foo'.".</span></span>

<span data-ttu-id="a970d-237">Para obter mais informações, confira [Validação de escopo](dependency-injection.md#scope-validation).</span><span class="sxs-lookup"><span data-stu-id="a970d-237">For more information, see [Scope validation](dependency-injection.md#scope-validation).</span></span>

### <a name="scoped-service-as-singleton"></a><span data-ttu-id="a970d-238">Serviço com escopo como singleton</span><span class="sxs-lookup"><span data-stu-id="a970d-238">Scoped service as singleton</span></span>

<span data-ttu-id="a970d-239">Ao usar serviços com escopo, se você não estiver criando um escopo ou dentro de um escopo existente, o serviço se tornará um singleton.</span><span class="sxs-lookup"><span data-stu-id="a970d-239">When using scoped services, if you're not creating a scope or within an existing scope - the service becomes a singleton.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="68-82" highlight="13-14":::

<span data-ttu-id="a970d-240">No código anterior, `Bar` é recuperado em um <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> , que está correto.</span><span class="sxs-lookup"><span data-stu-id="a970d-240">In the preceding code, `Bar` is retrieved within an <xref:Microsoft.Extensions.DependencyInjection.IServiceScope>, which is correct.</span></span> <span data-ttu-id="a970d-241">O antipadrão é a recuperação de `Bar` fora do escopo, e a variável é nomeada `avoid` para mostrar qual exemplo de recuperação está incorreto.</span><span class="sxs-lookup"><span data-stu-id="a970d-241">The anti-pattern is the retrieval of `Bar` outside of the scope, and the variable is named `avoid` to show which example retrieval is incorrect.</span></span>

## <a name="see-also"></a><span data-ttu-id="a970d-242">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a970d-242">See also</span></span>

- [<span data-ttu-id="a970d-243">Injeção de dependência no .NET</span><span class="sxs-lookup"><span data-stu-id="a970d-243">Dependency injection in .NET</span></span>](dependency-injection.md)
- [<span data-ttu-id="a970d-244">Tutorial: usar injeção de dependência no .NET</span><span class="sxs-lookup"><span data-stu-id="a970d-244">Tutorial: Use dependency injection in .NET</span></span>](dependency-injection-usage.md)
