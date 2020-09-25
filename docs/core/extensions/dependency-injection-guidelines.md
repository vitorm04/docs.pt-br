---
title: Diretrizes de injeção de dependência
description: Conheça várias diretrizes de injeção de dependência e práticas recomendadas para o desenvolvimento de aplicativos .NET.
author: IEvangelist
ms.author: dapine
ms.date: 09/23/2020
ms.topic: guide
ms.openlocfilehash: a8d52642b9217c7340db69494624d8ab85ea6c92
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247880"
---
# <a name="dependency-injection-guidelines"></a><span data-ttu-id="7143d-103">Diretrizes de injeção de dependência</span><span class="sxs-lookup"><span data-stu-id="7143d-103">Dependency injection guidelines</span></span>

<span data-ttu-id="7143d-104">Este artigo fornece diretrizes gerais e práticas recomendadas para implementar a injeção de dependência em aplicativos .NET.</span><span class="sxs-lookup"><span data-stu-id="7143d-104">This article provides general guidelines and best practices for implementing dependency injection in .NET applications.</span></span>

## <a name="design-services-for-dependency-injection"></a><span data-ttu-id="7143d-105">Projetar serviços para injeção de dependência</span><span class="sxs-lookup"><span data-stu-id="7143d-105">Design services for dependency injection</span></span>

<span data-ttu-id="7143d-106">Ao projetar serviços para injeção de dependência:</span><span class="sxs-lookup"><span data-stu-id="7143d-106">When designing services for dependency injection:</span></span>

- <span data-ttu-id="7143d-107">Evite classes e membros com estado e estáticos.</span><span class="sxs-lookup"><span data-stu-id="7143d-107">Avoid stateful, static classes and members.</span></span> <span data-ttu-id="7143d-108">Evite criar o estado global criando aplicativos para usar os serviços singleton.</span><span class="sxs-lookup"><span data-stu-id="7143d-108">Avoid creating global state by designing apps to use singleton services instead.</span></span>
- <span data-ttu-id="7143d-109">Evite a instanciação direta das classes dependentes em serviços.</span><span class="sxs-lookup"><span data-stu-id="7143d-109">Avoid direct instantiation of dependent classes within services.</span></span> <span data-ttu-id="7143d-110">A instanciação direta acopla o código a uma implementação específica.</span><span class="sxs-lookup"><span data-stu-id="7143d-110">Direct instantiation couples the code to a particular implementation.</span></span>
- <span data-ttu-id="7143d-111">Torne os serviços pequenos, bem fatorados e facilmente testados.</span><span class="sxs-lookup"><span data-stu-id="7143d-111">Make services small, well-factored, and easily tested.</span></span>

<span data-ttu-id="7143d-112">Se uma classe tiver muitas dependências injetadas, poderá ser um sinal de que a classe tem muitas responsabilidades e violará o [princípio de responsabilidade única (SRP)](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility).</span><span class="sxs-lookup"><span data-stu-id="7143d-112">If a class has many injected dependencies, it might be a sign that the class has too many responsibilities and violates the [Single Responsibility Principle (SRP)](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility).</span></span> <span data-ttu-id="7143d-113">Tente refatorar a classe movendo algumas de suas responsabilidades para novas classes.</span><span class="sxs-lookup"><span data-stu-id="7143d-113">Attempt to refactor the class by moving some of its responsibilities into new classes.</span></span>

### <a name="disposal-of-services"></a><span data-ttu-id="7143d-114">Descarte de serviços</span><span class="sxs-lookup"><span data-stu-id="7143d-114">Disposal of services</span></span>

<span data-ttu-id="7143d-115">O contêiner é responsável pela limpeza dos tipos que cria e chama <xref:System.IDisposable.Dispose%2A> em <xref:System.IDisposable> instâncias.</span><span class="sxs-lookup"><span data-stu-id="7143d-115">The container is responsible for cleanup of types it creates, and calls <xref:System.IDisposable.Dispose%2A> on <xref:System.IDisposable> instances.</span></span> <span data-ttu-id="7143d-116">Os serviços resolvidos do contêiner nunca devem ser descartados pelo desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="7143d-116">Services resolved from the container should never be disposed by the developer.</span></span> <span data-ttu-id="7143d-117">Se um tipo ou fábrica for registrado como um singleton, o contêiner descartará o singleton automaticamente.</span><span class="sxs-lookup"><span data-stu-id="7143d-117">If a type or factory is registered as a singleton, the container disposes the singleton automatically.</span></span>

<span data-ttu-id="7143d-118">No exemplo a seguir, os serviços são criados pelo contêiner de serviço e descartados automaticamente:</span><span class="sxs-lookup"><span data-stu-id="7143d-118">In the following example, the services are created by the service container and disposed automatically:</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/TransientDisposable.cs":::

:::code language="csharp" source="snippets/configuration/console-di-disposable/ScopedDisposable.cs":::

:::code language="csharp" source="snippets/configuration/console-di-disposable/SingletonDisposable.cs":::

:::code language="csharp" source="snippets/configuration/console-di-disposable/Program.cs" range="1-21,41-60":::

<span data-ttu-id="7143d-119">O console de depuração mostra a seguinte saída de exemplo após a execução:</span><span class="sxs-lookup"><span data-stu-id="7143d-119">The debug console shows the following sample output after running:</span></span>

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

### <a name="services-not-created-by-the-service-container"></a><span data-ttu-id="7143d-120">Serviços não criados pelo contêiner de serviço</span><span class="sxs-lookup"><span data-stu-id="7143d-120">Services not created by the service container</span></span>

<span data-ttu-id="7143d-121">Considere o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="7143d-121">Consider the following code:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddSingleton(new ExampleService());

    // ...
}
```

<span data-ttu-id="7143d-122">No código anterior:</span><span class="sxs-lookup"><span data-stu-id="7143d-122">In the preceding code:</span></span>

- <span data-ttu-id="7143d-123">A `ExampleService` instância **não** é criada pelo contêiner de serviço.</span><span class="sxs-lookup"><span data-stu-id="7143d-123">The `ExampleService` instance is **not** created by the service container.</span></span>
- <span data-ttu-id="7143d-124">A estrutura não **descarta os** serviços automaticamente.</span><span class="sxs-lookup"><span data-stu-id="7143d-124">The framework does **not** dispose of the services automatically.</span></span>
- <span data-ttu-id="7143d-125">O desenvolvedor é responsável por descartar os serviços.</span><span class="sxs-lookup"><span data-stu-id="7143d-125">The developer is responsible for disposing the services.</span></span>

### <a name="idisposable-guidance-for-transient-and-shared-instances"></a><span data-ttu-id="7143d-126">Diretrizes de IDisposable para instâncias transitórias e compartilhadas</span><span class="sxs-lookup"><span data-stu-id="7143d-126">IDisposable guidance for Transient and shared instances</span></span>

#### <a name="transient-limited-lifetime"></a><span data-ttu-id="7143d-127">Tempo de vida transitório, limitado</span><span class="sxs-lookup"><span data-stu-id="7143d-127">Transient, limited lifetime</span></span>

<span data-ttu-id="7143d-128">**Cenário**</span><span class="sxs-lookup"><span data-stu-id="7143d-128">**Scenario**</span></span>

<span data-ttu-id="7143d-129">O aplicativo requer uma <xref:System.IDisposable> instância com um tempo de vida transitório para qualquer um dos seguintes cenários:</span><span class="sxs-lookup"><span data-stu-id="7143d-129">The app requires an <xref:System.IDisposable> instance with a transient lifetime for either of the following scenarios:</span></span>

- <span data-ttu-id="7143d-130">A instância é resolvida no escopo raiz (contêiner raiz).</span><span class="sxs-lookup"><span data-stu-id="7143d-130">The instance is resolved in the root scope (root container).</span></span>
- <span data-ttu-id="7143d-131">A instância deve ser descartada antes do término do escopo.</span><span class="sxs-lookup"><span data-stu-id="7143d-131">The instance should be disposed before the scope ends.</span></span>

<span data-ttu-id="7143d-132">**Solução**</span><span class="sxs-lookup"><span data-stu-id="7143d-132">**Solution**</span></span>

<span data-ttu-id="7143d-133">Use o padrão de fábrica para criar uma instância fora do escopo pai.</span><span class="sxs-lookup"><span data-stu-id="7143d-133">Use the factory pattern to create an instance outside of the parent scope.</span></span> <span data-ttu-id="7143d-134">Nessa situação, o aplicativo geralmente teria um `Create` método que chamasse o construtor do tipo final diretamente.</span><span class="sxs-lookup"><span data-stu-id="7143d-134">In this situation, the app would generally have a `Create` method that calls the final type's constructor directly.</span></span> <span data-ttu-id="7143d-135">Se o tipo final tiver outras dependências, a fábrica poderá:</span><span class="sxs-lookup"><span data-stu-id="7143d-135">If the final type has other dependencies, the factory can:</span></span>

- <span data-ttu-id="7143d-136">Receber um <xref:System.IServiceProvider> em seu construtor.</span><span class="sxs-lookup"><span data-stu-id="7143d-136">Receive an <xref:System.IServiceProvider> in its constructor.</span></span>
- <span data-ttu-id="7143d-137">Use <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType> para instanciar a instância fora do contêiner, ao usar o contêiner para suas dependências.</span><span class="sxs-lookup"><span data-stu-id="7143d-137">Use <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType> to instantiate the instance outside of the container, while using the container for its dependencies.</span></span>

#### <a name="shared-instance-limited-lifetime"></a><span data-ttu-id="7143d-138">Instância compartilhada, tempo de vida limitado</span><span class="sxs-lookup"><span data-stu-id="7143d-138">Shared instance, limited lifetime</span></span>

<span data-ttu-id="7143d-139">**Cenário**</span><span class="sxs-lookup"><span data-stu-id="7143d-139">**Scenario**</span></span>

<span data-ttu-id="7143d-140">O aplicativo requer uma <xref:System.IDisposable> instância compartilhada em vários serviços, mas a <xref:System.IDisposable> instância deve ter um tempo de vida limitado.</span><span class="sxs-lookup"><span data-stu-id="7143d-140">The app requires a shared <xref:System.IDisposable> instance across multiple services, but the <xref:System.IDisposable> instance should have a limited lifetime.</span></span>

<span data-ttu-id="7143d-141">**Solução**</span><span class="sxs-lookup"><span data-stu-id="7143d-141">**Solution**</span></span>

<span data-ttu-id="7143d-142">Registre a instância com um tempo de vida de escopo.</span><span class="sxs-lookup"><span data-stu-id="7143d-142">Register the instance with a scoped lifetime.</span></span> <span data-ttu-id="7143d-143">Use <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType> para criar um novo <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> .</span><span class="sxs-lookup"><span data-stu-id="7143d-143">Use <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType> to create a new <xref:Microsoft.Extensions.DependencyInjection.IServiceScope>.</span></span> <span data-ttu-id="7143d-144">Use o escopo <xref:System.IServiceProvider> para obter os serviços necessários.</span><span class="sxs-lookup"><span data-stu-id="7143d-144">Use the scope's <xref:System.IServiceProvider> to get required services.</span></span> <span data-ttu-id="7143d-145">Descarte o escopo quando ele não for mais necessário.</span><span class="sxs-lookup"><span data-stu-id="7143d-145">Dispose the scope when it's no longer needed.</span></span>

#### <a name="general-idisposable-guidelines"></a><span data-ttu-id="7143d-146">`IDisposable`Diretrizes gerais</span><span class="sxs-lookup"><span data-stu-id="7143d-146">General `IDisposable` guidelines</span></span>

- <span data-ttu-id="7143d-147">Não registre <xref:System.IDisposable> instâncias com um tempo de vida transitório.</span><span class="sxs-lookup"><span data-stu-id="7143d-147">Don't register <xref:System.IDisposable> instances with a transient lifetime.</span></span> <span data-ttu-id="7143d-148">Em vez disso, use o padrão de fábrica.</span><span class="sxs-lookup"><span data-stu-id="7143d-148">Use the factory pattern instead.</span></span>
- <span data-ttu-id="7143d-149">Não resolva <xref:System.IDisposable> instâncias com um tempo de vida transitório ou com escopo definido no escopo raiz.</span><span class="sxs-lookup"><span data-stu-id="7143d-149">Don't resolve <xref:System.IDisposable> instances with a transient or scoped lifetime in the root scope.</span></span> <span data-ttu-id="7143d-150">A única exceção a isso é se o aplicativo cria/recria e descarta <xref:System.IServiceProvider> , mas esse não é um padrão ideal.</span><span class="sxs-lookup"><span data-stu-id="7143d-150">The only exception to this is if the app creates/recreates and disposes <xref:System.IServiceProvider>, but this isn't an ideal pattern.</span></span>
- <span data-ttu-id="7143d-151">O recebimento de uma <xref:System.IDisposable> dependência por meio de di não exige que o receptor se implemente <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="7143d-151">Receiving an <xref:System.IDisposable> dependency via DI doesn't require that the receiver implement <xref:System.IDisposable> itself.</span></span> <span data-ttu-id="7143d-152">O receptor da <xref:System.IDisposable> dependência não deve chamar <xref:System.IDisposable.Dispose%2A> essa dependência.</span><span class="sxs-lookup"><span data-stu-id="7143d-152">The receiver of the <xref:System.IDisposable> dependency shouldn't call <xref:System.IDisposable.Dispose%2A> on that dependency.</span></span>
- <span data-ttu-id="7143d-153">Use escopos para controlar os tempos de vida dos serviços.</span><span class="sxs-lookup"><span data-stu-id="7143d-153">Use scopes to control the lifetimes of services.</span></span> <span data-ttu-id="7143d-154">Os escopos não são hierárquicos e não há nenhuma conexão especial entre escopos.</span><span class="sxs-lookup"><span data-stu-id="7143d-154">Scopes aren't hierarchical, and there's no special connection among scopes.</span></span>

<span data-ttu-id="7143d-155">Para obter mais informações sobre a limpeza de recursos, consulte [implementar um método Dispose](../../standard/garbage-collection/implementing-dispose.md)</span><span class="sxs-lookup"><span data-stu-id="7143d-155">For more information on resource cleanup, see [Implement a Dispose method](../../standard/garbage-collection/implementing-dispose.md)</span></span>

## <a name="default-service-container-replacement"></a><span data-ttu-id="7143d-156">Substituição do contêiner de serviço padrão</span><span class="sxs-lookup"><span data-stu-id="7143d-156">Default service container replacement</span></span>

<span data-ttu-id="7143d-157">O contêiner de serviço interno foi projetado para atender às necessidades da estrutura e da maioria dos aplicativos de consumidor.</span><span class="sxs-lookup"><span data-stu-id="7143d-157">The built-in service container is designed to serve the needs of the framework and most consumer apps.</span></span> <span data-ttu-id="7143d-158">É recomendável usar o contêiner interno, a menos que você precise de um recurso específico ao qual ele não ofereça suporte, como:</span><span class="sxs-lookup"><span data-stu-id="7143d-158">We recommend using the built-in container unless you need a specific feature that it doesn't support, such as:</span></span>

- <span data-ttu-id="7143d-159">Injeção de propriedade</span><span class="sxs-lookup"><span data-stu-id="7143d-159">Property injection</span></span>
- <span data-ttu-id="7143d-160">Injeção com base no nome</span><span class="sxs-lookup"><span data-stu-id="7143d-160">Injection based on name</span></span>
- <span data-ttu-id="7143d-161">Contêineres filho</span><span class="sxs-lookup"><span data-stu-id="7143d-161">Child containers</span></span>
- <span data-ttu-id="7143d-162">Gerenciamento de tempo de vida personalizado</span><span class="sxs-lookup"><span data-stu-id="7143d-162">Custom lifetime management</span></span>
- <span data-ttu-id="7143d-163">Suporte de `Func<T>` para inicialização lenta</span><span class="sxs-lookup"><span data-stu-id="7143d-163">`Func<T>` support for lazy initialization</span></span>
- <span data-ttu-id="7143d-164">Registro baseado em Convenção</span><span class="sxs-lookup"><span data-stu-id="7143d-164">Convention-based registration</span></span>

<span data-ttu-id="7143d-165">Os seguintes contêineres de terceiros podem ser usados com aplicativos ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="7143d-165">The following third-party containers can be used with ASP.NET Core apps:</span></span>

- [<span data-ttu-id="7143d-166">Autofac</span><span class="sxs-lookup"><span data-stu-id="7143d-166">Autofac</span></span>](https://autofac.readthedocs.io/en/latest/integration/aspnetcore.html)
- [<span data-ttu-id="7143d-167">DryIoc</span><span class="sxs-lookup"><span data-stu-id="7143d-167">DryIoc</span></span>](https://www.nuget.org/packages/DryIoc.Microsoft.DependencyInjection)
- [<span data-ttu-id="7143d-168">Grace</span><span class="sxs-lookup"><span data-stu-id="7143d-168">Grace</span></span>](https://www.nuget.org/packages/Grace.DependencyInjection.Extensions)
- [<span data-ttu-id="7143d-169">LightInject</span><span class="sxs-lookup"><span data-stu-id="7143d-169">LightInject</span></span>](https://github.com/seesharper/LightInject.Microsoft.DependencyInjection)
- [<span data-ttu-id="7143d-170">Lamar</span><span class="sxs-lookup"><span data-stu-id="7143d-170">Lamar</span></span>](https://jasperfx.github.io/lamar/)
- [<span data-ttu-id="7143d-171">Stashbox</span><span class="sxs-lookup"><span data-stu-id="7143d-171">Stashbox</span></span>](https://github.com/z4kn4fein/stashbox-extensions-dependencyinjection)
- [<span data-ttu-id="7143d-172">Unity</span><span class="sxs-lookup"><span data-stu-id="7143d-172">Unity</span></span>](https://www.nuget.org/packages/Unity.Microsoft.DependencyInjection)

## <a name="thread-safety"></a><span data-ttu-id="7143d-173">Acesso thread-safe</span><span class="sxs-lookup"><span data-stu-id="7143d-173">Thread safety</span></span>

<span data-ttu-id="7143d-174">Crie serviços singleton thread-safe.</span><span class="sxs-lookup"><span data-stu-id="7143d-174">Create thread-safe singleton services.</span></span> <span data-ttu-id="7143d-175">Se um serviço singleton tiver uma dependência em um serviço transitório, o serviço transitório também poderá exigir a segurança do thread dependendo de como ele é usado pelo singleton.</span><span class="sxs-lookup"><span data-stu-id="7143d-175">If a singleton service has a dependency on a transient service, the transient service may also require thread safety depending on how it's used by the singleton.</span></span>

<span data-ttu-id="7143d-176">O método de fábrica de um único serviço, como o segundo argumento para [addsingleton \<TService> (IServiceCollection, Func \<IServiceProvider,TService> )](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A), não precisa ser thread-safe.</span><span class="sxs-lookup"><span data-stu-id="7143d-176">The factory method of single service, such as the second argument to [AddSingleton\<TService>(IServiceCollection, Func\<IServiceProvider,TService>)](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A), doesn't need to be thread-safe.</span></span> <span data-ttu-id="7143d-177">Como um construtor de tipo ( `static` ), é garantido que ele seja chamado apenas uma vez por um único thread.</span><span class="sxs-lookup"><span data-stu-id="7143d-177">Like a type (`static`) constructor, it's guaranteed to be called only once by a single thread.</span></span>

## <a name="recommendations"></a><span data-ttu-id="7143d-178">Recomendações</span><span class="sxs-lookup"><span data-stu-id="7143d-178">Recommendations</span></span>

- <span data-ttu-id="7143d-179">`async/await` e a `Task` resolução de serviço baseada não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="7143d-179">`async/await` and `Task` based service resolution isn't supported.</span></span> <span data-ttu-id="7143d-180">Como o C# não dá suporte a construtores assíncronos, use métodos assíncronos após a resolução síncrona do serviço.</span><span class="sxs-lookup"><span data-stu-id="7143d-180">Because C# doesn't support asynchronous constructors, use asynchronous methods after synchronously resolving the service.</span></span>
- <span data-ttu-id="7143d-181">Evite armazenar dados e a configuração diretamente no contêiner do serviço.</span><span class="sxs-lookup"><span data-stu-id="7143d-181">Avoid storing data and configuration directly in the service container.</span></span> <span data-ttu-id="7143d-182">Por exemplo, o carrinho de compras de um usuário normalmente não deve ser adicionado ao contêiner do serviço.</span><span class="sxs-lookup"><span data-stu-id="7143d-182">For example, a user's shopping cart shouldn't typically be added to the service container.</span></span> <span data-ttu-id="7143d-183">A configuração deve usar o padrão de opções.</span><span class="sxs-lookup"><span data-stu-id="7143d-183">Configuration should use the options pattern.</span></span> <span data-ttu-id="7143d-184">Da mesma forma, evite objetos de "portador de dados" que existem somente para permitir o acesso a outro objeto.</span><span class="sxs-lookup"><span data-stu-id="7143d-184">Similarly, avoid "data holder" objects that only exist to allow access to another object.</span></span> <span data-ttu-id="7143d-185">É melhor solicitar o item real por meio da DI.</span><span class="sxs-lookup"><span data-stu-id="7143d-185">It's better to request the actual item via DI.</span></span>
- <span data-ttu-id="7143d-186">Evite o acesso estático aos serviços.</span><span class="sxs-lookup"><span data-stu-id="7143d-186">Avoid static access to services.</span></span> <span data-ttu-id="7143d-187">Por exemplo, evite capturar [IApplicationBuilder. ApplicationServices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) como um campo ou propriedade estática para uso em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="7143d-187">For example, avoid capturing [IApplicationBuilder.ApplicationServices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) as a static field or property for use elsewhere.</span></span>
- <span data-ttu-id="7143d-188">Mantenha as fábricas de injeção rápida e síncrona.</span><span class="sxs-lookup"><span data-stu-id="7143d-188">Keep DI factories fast and synchronous.</span></span>
- <span data-ttu-id="7143d-189">Evite usar o *padrão do localizador de serviço*.</span><span class="sxs-lookup"><span data-stu-id="7143d-189">Avoid using the *service locator pattern*.</span></span> <span data-ttu-id="7143d-190">Por exemplo, não invoque <xref:System.IServiceProvider.GetService%2A> para obter uma instância de serviço quando for possível usar a DI.</span><span class="sxs-lookup"><span data-stu-id="7143d-190">For example, don't invoke <xref:System.IServiceProvider.GetService%2A> to obtain a service instance when you can use DI instead.</span></span>
- <span data-ttu-id="7143d-191">Outra variação de localizador de serviço a ser evitada é injetar um alocador que resolve as dependências em runtime.</span><span class="sxs-lookup"><span data-stu-id="7143d-191">Another service locator variation to avoid is injecting a factory that resolves dependencies at runtime.</span></span> <span data-ttu-id="7143d-192">Essas duas práticas misturam estratégias de [inversão de controle](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion).</span><span class="sxs-lookup"><span data-stu-id="7143d-192">Both of these practices mix [Inversion of Control](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion) strategies.</span></span>
- <span data-ttu-id="7143d-193">Evite chamadas para <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> no `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="7143d-193">Avoid calls to <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> in `ConfigureServices`.</span></span> <span data-ttu-id="7143d-194">Chamar `BuildServiceProvider` normalmente acontece quando o desenvolvedor deseja resolver um serviço no `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="7143d-194">Calling `BuildServiceProvider` typically happens when the developer wants to resolve a service in `ConfigureServices`.</span></span>
- <span data-ttu-id="7143d-195">Serviços inposados transitórios são capturados pelo contêiner para descarte.</span><span class="sxs-lookup"><span data-stu-id="7143d-195">Disposable transient services are captured by the container for disposal.</span></span> <span data-ttu-id="7143d-196">Isso pode transformar em um vazamento de memória se resolvido do contêiner de nível superior.</span><span class="sxs-lookup"><span data-stu-id="7143d-196">This can turn into a memory leak if resolved from the top-level container.</span></span>
- <span data-ttu-id="7143d-197">Habilite a validação de escopo para certificar-se de que o aplicativo não tem singletons que capturam serviços com escopo.</span><span class="sxs-lookup"><span data-stu-id="7143d-197">Enable scope validation to make sure the app doesn't have singletons that capture scoped services.</span></span> <span data-ttu-id="7143d-198">Para obter mais informações, confira [Validação de escopo](dependency-injection.md#scope-validation).</span><span class="sxs-lookup"><span data-stu-id="7143d-198">For more information, see [Scope validation](dependency-injection.md#scope-validation).</span></span>

<span data-ttu-id="7143d-199">Como todos os conjuntos de recomendações, talvez você encontre situações em que é necessário ignorar uma recomendação.</span><span class="sxs-lookup"><span data-stu-id="7143d-199">Like all sets of recommendations, you may encounter situations where ignoring a recommendation is required.</span></span> <span data-ttu-id="7143d-200">As exceções são raras, principalmente os casos especiais dentro da própria estrutura.</span><span class="sxs-lookup"><span data-stu-id="7143d-200">Exceptions are rare, mostly special cases within the framework itself.</span></span>

<span data-ttu-id="7143d-201">A DI é uma *alternativa* aos padrões de acesso a objeto estático/global.</span><span class="sxs-lookup"><span data-stu-id="7143d-201">DI is an *alternative* to static/global object access patterns.</span></span> <span data-ttu-id="7143d-202">Talvez você não obtenha os benefícios da DI se combiná-lo com o acesso a objeto estático.</span><span class="sxs-lookup"><span data-stu-id="7143d-202">You may not be able to realize the benefits of DI if you mix it with static object access.</span></span>

## <a name="see-also"></a><span data-ttu-id="7143d-203">Confira também</span><span class="sxs-lookup"><span data-stu-id="7143d-203">See also</span></span>

- [<span data-ttu-id="7143d-204">Injeção de dependência no .NET</span><span class="sxs-lookup"><span data-stu-id="7143d-204">Dependency injection in .NET</span></span>](dependency-injection.md)
