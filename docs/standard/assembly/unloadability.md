---
title: Como usar e depurar a capacidade de descarregamento de assembly no .NET Core
description: Saiba como usar o AssemblyLoadContext de coleção para carregar e descarregar assemblies gerenciados e como depurar problemas que impedem o êxito do descarregamento.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 52cd864393342e2bc31f872b9d09cb484c2c8463
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972987"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="53a45-103">Como usar e depurar a capacidade de descarregamento de assembly no .NET Core</span><span class="sxs-lookup"><span data-stu-id="53a45-103">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="53a45-104">No .NET Core 3.0 em diante, há suporte para a capacidade de carregar e, posteriormente, descarregar um conjunto de assemblies.</span><span class="sxs-lookup"><span data-stu-id="53a45-104">Starting with .NET Core 3.0, the ability to load and later unload a set of assemblies is supported.</span></span> <span data-ttu-id="53a45-105">No .NET Framework, os domínios de aplicativo personalizados foram usados para essa finalidade, mas o .NET Core só dá suporte a um único domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="53a45-105">In .NET Framework, custom app domains were used for this purpose, but .NET Core only supports a single default app domain.</span></span>

<span data-ttu-id="53a45-106">O .NET Core 3.0 e versões posteriores dão suporte à capacidade de descarregamento por meio de <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="53a45-106">.NET Core 3.0 and later versions support unloadability through <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="53a45-107">Você pode carregar um conjunto de assemblies em um `AssemblyLoadContext` de coleção, executar métodos neles ou apenas inspecioná-los usando a reflexão e, por fim, descarregar o `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="53a45-107">You can load a set of assemblies into a collectible `AssemblyLoadContext`, execute methods in them or just inspect them using reflection, and finally unload the `AssemblyLoadContext`.</span></span> <span data-ttu-id="53a45-108">Isso descarrega os assemblies carregados nesse `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="53a45-108">That unloads the assemblies loaded into that `AssemblyLoadContext`.</span></span>

<span data-ttu-id="53a45-109">Há uma diferença notável entre o descarregamento com `AssemblyLoadContext` e com o AppDomain.</span><span class="sxs-lookup"><span data-stu-id="53a45-109">There's one noteworthy difference between the unloading using `AssemblyLoadContext` and using AppDomains.</span></span> <span data-ttu-id="53a45-110">Com o AppDomain, o descarregamento é forçado.</span><span class="sxs-lookup"><span data-stu-id="53a45-110">With AppDomains, the unloading is forced.</span></span> <span data-ttu-id="53a45-111">No momento do descarregamento, todos os threads em execução no AppDomain de destino são anulados, objetos COM gerenciados criados no AppDomain de destino são destruídos, etc. Com `AssemblyLoadContext`o, o descarregamento é "cooperativo".</span><span class="sxs-lookup"><span data-stu-id="53a45-111">At unload time, all threads running in the target AppDomain are aborted, managed COM objects created in the target AppDomain are destroyed, etc. With `AssemblyLoadContext`, the unload is "cooperative."</span></span> <span data-ttu-id="53a45-112">A chamada do método <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> apenas inicia o descarregamento.</span><span class="sxs-lookup"><span data-stu-id="53a45-112">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> method just initiates the unloading.</span></span> <span data-ttu-id="53a45-113">O descarregamento é concluído depois que:</span><span class="sxs-lookup"><span data-stu-id="53a45-113">The unloading finishes after:</span></span>

- <span data-ttu-id="53a45-114">Nenhum thread tem métodos dos assemblies carregados em `AssemblyLoadContext` nas pilhas de chamadas.</span><span class="sxs-lookup"><span data-stu-id="53a45-114">No threads have methods from the assemblies loaded into the `AssemblyLoadContext` on their call stacks.</span></span>
- <span data-ttu-id="53a45-115">Nenhum dos tipos dos assemblies carregados em `AssemblyLoadContext`, as instâncias desses tipos e os próprios assemblies fora de `AssemblyLoadContext` são referenciados por:</span><span class="sxs-lookup"><span data-stu-id="53a45-115">None of the types from the assemblies loaded into the `AssemblyLoadContext`, instances of those types and the assemblies themselves outside of the `AssemblyLoadContext` are referenced by:</span></span>
  - <span data-ttu-id="53a45-116">Referências fora do `AssemblyLoadContext`, exceto referências fracas (<xref:System.WeakReference> ou <xref:System.WeakReference%601>).</span><span class="sxs-lookup"><span data-stu-id="53a45-116">References outside of the `AssemblyLoadContext`, except of weak references (<xref:System.WeakReference> or <xref:System.WeakReference%601>).</span></span>
  - <span data-ttu-id="53a45-117">Identificadores GC fortes (<xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Normal></span><span class="sxs-lookup"><span data-stu-id="53a45-117">Strong GC handles (<xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Normal></span></span> <span data-ttu-id="53a45-118">ou <xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Pinned>) dentro e fora de `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="53a45-118">or <xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Pinned>) from both inside and outside of the `AssemblyLoadContext`.</span></span>

## <a name="use-collectible-assemblyloadcontext"></a><span data-ttu-id="53a45-119">Usar AssemblyLoadContext de coleção</span><span class="sxs-lookup"><span data-stu-id="53a45-119">Use collectible AssemblyLoadContext</span></span>

<span data-ttu-id="53a45-120">Esta seção contém um tutorial passo a passo detalhado que mostra uma maneira simples de carregar um aplicativo .NET Core em um `AssemblyLoadContext` de coleção, executar seu ponto de entrada e, em seguida, descarregá-lo.</span><span class="sxs-lookup"><span data-stu-id="53a45-120">This section contains a detailed step-by-step tutorial that shows a simple way to load a .NET Core application into a collectible `AssemblyLoadContext`, execute its entry point, and then unload it.</span></span> <span data-ttu-id="53a45-121">Você pode encontrar um exemplo completo em [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading).</span><span class="sxs-lookup"><span data-stu-id="53a45-121">You can find a complete sample at [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading).</span></span>

### <a name="create-a-collectible-assemblyloadcontext"></a><span data-ttu-id="53a45-122">Criar um AssemblyLoadContext de coleção</span><span class="sxs-lookup"><span data-stu-id="53a45-122">Create a collectible AssemblyLoadContext</span></span>

<span data-ttu-id="53a45-123">Você precisa derivar a classe de <xref:System.Runtime.Loader.AssemblyLoadContext> e sobrecarregar o método <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="53a45-123">You need to derive your class from the <xref:System.Runtime.Loader.AssemblyLoadContext> and overload its <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="53a45-124">Esse método resolve as referências para todos os assemblies que são dependências de assemblies carregados nesse `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="53a45-124">That method resolves references to all assemblies that are dependencies of assemblies loaded into that `AssemblyLoadContext`.</span></span>
<span data-ttu-id="53a45-125">O seguinte código é um exemplo do `AssemblyLoadContext` personalizado mais simples:</span><span class="sxs-lookup"><span data-stu-id="53a45-125">The following code is an example of the simplest custom `AssemblyLoadContext`:</span></span>

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

<span data-ttu-id="53a45-126">Como você pode ver, o método `Load` retorna `null`.</span><span class="sxs-lookup"><span data-stu-id="53a45-126">As you can see, the `Load` method returns `null`.</span></span> <span data-ttu-id="53a45-127">Isso significa que todos os assemblies de dependência são carregados no contexto padrão e o novo contexto contém apenas os assemblies carregados explicitamente nele.</span><span class="sxs-lookup"><span data-stu-id="53a45-127">That means that all the dependency assemblies are loaded into the default context, and the new context contains only the assemblies explicitly loaded into it.</span></span>

<span data-ttu-id="53a45-128">Caso deseje carregar algumas ou todas as dependências no `AssemblyLoadContext` também, use o `AssemblyDependencyResolver` no método `Load`.</span><span class="sxs-lookup"><span data-stu-id="53a45-128">If you want to load some or all of the dependencies into the `AssemblyLoadContext` too, you can use the `AssemblyDependencyResolver` in the `Load` method.</span></span> <span data-ttu-id="53a45-129">O `AssemblyDependencyResolver` resolve os nomes de assembly para caminhos absolutos de arquivo do assembly usando o arquivo *.deps.json* contido no diretório do assembly principal carregado no contexto e usando arquivos do assembly desse diretório.</span><span class="sxs-lookup"><span data-stu-id="53a45-129">The `AssemblyDependencyResolver` resolves the assembly names to absolute assembly file paths using the *.deps.json* file contained in the directory of the main assembly loaded into the context and using assembly files in that directory.</span></span>

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a><span data-ttu-id="53a45-130">Usar um AssemblyLoadContext de coleção personalizado</span><span class="sxs-lookup"><span data-stu-id="53a45-130">Use a custom collectible AssemblyLoadContext</span></span>

<span data-ttu-id="53a45-131">Esta seção pressupõe que a versão mais simples do `TestAssemblyLoadContext` esteja sendo usada.</span><span class="sxs-lookup"><span data-stu-id="53a45-131">This section assumes the simpler version of the `TestAssemblyLoadContext` is being used.</span></span>

<span data-ttu-id="53a45-132">Crie uma instância do `AssemblyLoadContext` personalizado e carregue um assembly nele da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="53a45-132">You can create an instance of the custom `AssemblyLoadContext` and load an assembly into it as follows:</span></span>

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

<span data-ttu-id="53a45-133">Para cada um dos assemblies referenciados pelo assembly carregado, o método `TestAssemblyLoadContext.Load` é chamado, de modo que o `TestAssemblyLoadContext` possa decidir o local em que obterá o assembly.</span><span class="sxs-lookup"><span data-stu-id="53a45-133">For each of the assemblies referenced by the loaded assembly, the `TestAssemblyLoadContext.Load` method is called so that the `TestAssemblyLoadContext` can decide where to get the assembly from.</span></span> <span data-ttu-id="53a45-134">Em nosso caso, ele retorna `null` para indicar que ele deve ser carregado no contexto padrão de localizações usadas pelo tempo de execução para carregar assemblies por padrão.</span><span class="sxs-lookup"><span data-stu-id="53a45-134">In our case, it returns `null` to indicate that it should be loaded into the default context from locations that the runtime uses to load assemblies by default.</span></span>

<span data-ttu-id="53a45-135">Agora que um assembly foi carregado, você pode executar um método nele.</span><span class="sxs-lookup"><span data-stu-id="53a45-135">Now that an assembly was loaded, you can execute a method from it.</span></span> <span data-ttu-id="53a45-136">Execute o método `Main`:</span><span class="sxs-lookup"><span data-stu-id="53a45-136">Run the `Main` method:</span></span>

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

<span data-ttu-id="53a45-137">Depois que o método `Main` for retornado, você poderá iniciar o descarregamento chamando o método `Unload` no `AssemblyLoadContext` personalizado ou se livrar da referência existente ao `AssemblyLoadContext`:</span><span class="sxs-lookup"><span data-stu-id="53a45-137">After the `Main` method returns, you can initiate unloading by either calling the `Unload` method on the custom `AssemblyLoadContext` or getting rid of the reference you have to the `AssemblyLoadContext`:</span></span>

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

<span data-ttu-id="53a45-138">Isso é suficiente para descarregar o assembly de teste.</span><span class="sxs-lookup"><span data-stu-id="53a45-138">This is sufficient to unload the test assembly.</span></span> <span data-ttu-id="53a45-139">Na verdade, vamos colocar tudo isso em um método separado que não pode ser embutido para garantir que `TestAssemblyLoadContext`, `Assembly` e `MethodInfo` (o `Assembly.EntryPoint`) não possam ser mantidos ativos por referências de slot de pilha (locais introduzidos reais ou em JIT).</span><span class="sxs-lookup"><span data-stu-id="53a45-139">Let's actually put all of this into a separate non-inlineable method to ensure that the `TestAssemblyLoadContext`, `Assembly`, and `MethodInfo` (the `Assembly.EntryPoint`) can't be kept alive by stack slot references (real- or JIT-introduced locals).</span></span> <span data-ttu-id="53a45-140">Isso pode manter o `TestAssemblyLoadContext` ativo e impedir o descarregamento.</span><span class="sxs-lookup"><span data-stu-id="53a45-140">That could keep the `TestAssemblyLoadContext` alive and prevent the unload.</span></span>

<span data-ttu-id="53a45-141">Além disso, retorne uma referência fraca ao `AssemblyLoadContext`, de modo que você possa usá-la posteriormente para detectar a conclusão do descarregamento.</span><span class="sxs-lookup"><span data-stu-id="53a45-141">Also, return a weak reference to the `AssemblyLoadContext` so that you can use it later to detect unload completion.</span></span>

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

<span data-ttu-id="53a45-142">Agora você pode executar essa função para carregar, executar e descarregar o assembly.</span><span class="sxs-lookup"><span data-stu-id="53a45-142">Now you can run this function to load, execute, and unload the assembly.</span></span>

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

<span data-ttu-id="53a45-143">No entanto, o descarregamento não é concluído imediatamente.</span><span class="sxs-lookup"><span data-stu-id="53a45-143">However, the unload doesn't complete immediately.</span></span> <span data-ttu-id="53a45-144">Como mencionado anteriormente, ele depende do GC para coletar todos os objetos do assembly de teste.</span><span class="sxs-lookup"><span data-stu-id="53a45-144">As previously mentioned, it relies on the GC to collect all the objects from the test assembly.</span></span> <span data-ttu-id="53a45-145">Em muitos casos, não é necessário aguardar a conclusão do descarregamento.</span><span class="sxs-lookup"><span data-stu-id="53a45-145">In many cases, it isn't necessary to wait for the unload completion.</span></span> <span data-ttu-id="53a45-146">No entanto, há casos em que é útil saber que o descarregamento foi concluído.</span><span class="sxs-lookup"><span data-stu-id="53a45-146">However, there are cases where it's useful to know that the unload has finished.</span></span> <span data-ttu-id="53a45-147">Por exemplo, talvez você deseje excluir o arquivo do assembly que foi carregado no `AssemblyLoadContext` personalizado do disco.</span><span class="sxs-lookup"><span data-stu-id="53a45-147">For example, you may want to delete the assembly file that was loaded into the custom `AssemblyLoadContext` from disk.</span></span> <span data-ttu-id="53a45-148">Nesse caso, o snippet de código a seguir pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="53a45-148">In such a case, the following code snippet can be used.</span></span> <span data-ttu-id="53a45-149">Ele dispara um GC e aguarda os finalizadores pendentes em um loop até a referência fraca ao `AssemblyLoadContext` personalizado ser definida como `null`, indicando que o objeto de destino foi coletado.</span><span class="sxs-lookup"><span data-stu-id="53a45-149">It triggers a GC and waits for pending finalizers in a loop until the weak reference to the custom `AssemblyLoadContext` is set to `null`, indicating the target object was collected.</span></span> <span data-ttu-id="53a45-150">Observe que, na maioria dos casos, apenas uma passagem pelo loop é necessária.</span><span class="sxs-lookup"><span data-stu-id="53a45-150">Note that in most cases, just one pass through the loop is required.</span></span> <span data-ttu-id="53a45-151">No entanto, para casos mais complexos em que os objetos criados pelo código em execução no `AssemblyLoadContext` têm finalizadores, mais passagens podem ser necessárias.</span><span class="sxs-lookup"><span data-stu-id="53a45-151">However, for more complex cases where objects created by the code running in the `AssemblyLoadContext` have finalizers, more passes may be needed.</span></span>

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a><span data-ttu-id="53a45-152">O evento de descarregamento</span><span class="sxs-lookup"><span data-stu-id="53a45-152">The Unloading event</span></span>

<span data-ttu-id="53a45-153">Em alguns casos, poderá ser necessário que o código carregado em um `AssemblyLoadContext` personalizado execute alguma limpeza quando o descarregamento for iniciado.</span><span class="sxs-lookup"><span data-stu-id="53a45-153">In some cases, it may be necessary for the code loaded into a custom `AssemblyLoadContext` to perform some cleanup when the unloading is initiated.</span></span> <span data-ttu-id="53a45-154">Por exemplo, pode ser necessário interromper os threads, limpar alguns identificadores GC fortes etc. O evento `Unloading` pode ser usado nesses casos.</span><span class="sxs-lookup"><span data-stu-id="53a45-154">For example, it may need to stop threads, clean up some strong GC handles, etc. The `Unloading` event can be used in such cases.</span></span> <span data-ttu-id="53a45-155">Um manipulador que executa a limpeza necessária pode ser conectado a esse evento.</span><span class="sxs-lookup"><span data-stu-id="53a45-155">A handler that performs the necessary cleanup can be hooked to this event.</span></span>

### <a name="troubleshoot-unloadability-issues"></a><span data-ttu-id="53a45-156">Solução de problemas de capacidade de descarregamento</span><span class="sxs-lookup"><span data-stu-id="53a45-156">Troubleshoot unloadability issues</span></span>

<span data-ttu-id="53a45-157">Devido à natureza cooperativa do descarregamento, é fácil esquecer as referências mantendo os itens em um `AssemblyLoadContext` de coleção ativos e impedindo o descarregamento.</span><span class="sxs-lookup"><span data-stu-id="53a45-157">Due to the cooperative nature of the unloading, it's easy to forget about references keeping the stuff in a collectible `AssemblyLoadContext` alive and preventing unload.</span></span> <span data-ttu-id="53a45-158">Este é um resumo dos itens (alguns deles não óbvios) que podem conter as referências:</span><span class="sxs-lookup"><span data-stu-id="53a45-158">Here is a summary of things (some of them non-obvious) that can hold the references:</span></span>

- <span data-ttu-id="53a45-159">Referências regulares mantidas fora do `AssemblyLoadContext` de coleção, armazenadas em um slot de pilha ou em um registro de processador (locais de método, criados explicitamente pelo código do usuário ou implicitamente pelo JIT), uma variável estática ou um identificador GC forte/de fixação e apontando transitivamente para:</span><span class="sxs-lookup"><span data-stu-id="53a45-159">Regular references held from outside of the collectible `AssemblyLoadContext`, stored in a stack slot or a processor register (method locals, either explicitly created by the user code or implicitly by the JIT), a static variable or a strong / pinning GC handle, and transitively pointing to:</span></span>
  - <span data-ttu-id="53a45-160">Um assembly carregado no `AssemblyLoadContext` de coleção.</span><span class="sxs-lookup"><span data-stu-id="53a45-160">An assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
  - <span data-ttu-id="53a45-161">Um tipo desse assembly.</span><span class="sxs-lookup"><span data-stu-id="53a45-161">A type from such an assembly.</span></span>
  - <span data-ttu-id="53a45-162">Uma instância de um tipo desse assembly.</span><span class="sxs-lookup"><span data-stu-id="53a45-162">An instance of a type from such an assembly.</span></span>
- <span data-ttu-id="53a45-163">Threads executando um código de um assembly carregado no `AssemblyLoadContext` de coleção.</span><span class="sxs-lookup"><span data-stu-id="53a45-163">Threads running code from an assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="53a45-164">Instâncias de tipos `AssemblyLoadContext` personalizados que não são de coleção criados dentro do `AssemblyLoadContext` de coleção</span><span class="sxs-lookup"><span data-stu-id="53a45-164">Instances of custom non-collectible `AssemblyLoadContext` types created inside of the collectible `AssemblyLoadContext`</span></span>
- <span data-ttu-id="53a45-165">Instâncias <xref:System.Threading.RegisteredWaitHandle> pendentes com retornos de chamada definidos como métodos no `AssemblyLoadContext` personalizado</span><span class="sxs-lookup"><span data-stu-id="53a45-165">Pending <xref:System.Threading.RegisteredWaitHandle> instances with callbacks set to methods in the custom `AssemblyLoadContext`</span></span>

<span data-ttu-id="53a45-166">Dicas para localizar o slot de pilha/o registro de processador fazendo rooting de um objeto:</span><span class="sxs-lookup"><span data-stu-id="53a45-166">Hints to find stack slot / processor register rooting an object:</span></span>

- <span data-ttu-id="53a45-167">Passar os resultados da chamada de função diretamente para outra função pode criar uma raiz, embora não haja nenhuma variável local criada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="53a45-167">Passing function call results directly to another function may create a root even though there is no user-created local variable.</span></span>
- <span data-ttu-id="53a45-168">Se uma referência a um objeto estivesse disponível em qualquer ponto em um método, o JIT poderia ter decidido manter a referência em um slot de pilha/um registro do processador pelo tempo desejado na função atual.</span><span class="sxs-lookup"><span data-stu-id="53a45-168">If a reference to an object was available at any point in a method, the JIT might have decided to keep the reference in a stack slot / processor register for as long as it wants in the current function.</span></span>

## <a name="debug-unloading-issues"></a><span data-ttu-id="53a45-169">Depurar problemas de descarregamento</span><span class="sxs-lookup"><span data-stu-id="53a45-169">Debug unloading issues</span></span>

<span data-ttu-id="53a45-170">Problemas de depuração com o descarregamento podem ser entediantes.</span><span class="sxs-lookup"><span data-stu-id="53a45-170">Debugging issues with unloading can be tedious.</span></span> <span data-ttu-id="53a45-171">Você pode enfrentar situações em que não sabe o que pode estar mantendo `AssemblyLoadContext` um ativo, mas o descarregamento falha.</span><span class="sxs-lookup"><span data-stu-id="53a45-171">You can get into situations where you don't know what can be holding an `AssemblyLoadContext` alive, but the unload fails.</span></span>
<span data-ttu-id="53a45-172">A melhor arma para ajudar com isso é o WinDbg (LLDB no UNIX) com o plug-in do SOS.</span><span class="sxs-lookup"><span data-stu-id="53a45-172">The best weapon to help with that is WinDbg (LLDB on Unix) with the SOS plugin.</span></span> <span data-ttu-id="53a45-173">Você precisa encontrar o que está mantendo um `LoaderAllocator` ativo pertencente ao `AssemblyLoadContext` específico.</span><span class="sxs-lookup"><span data-stu-id="53a45-173">You need to find what's keeping a `LoaderAllocator` belonging to the specific `AssemblyLoadContext` alive.</span></span>
<span data-ttu-id="53a45-174">Esse plug-in permite que você examine os objetos de heap do GC, suas hierarquias e raízes.</span><span class="sxs-lookup"><span data-stu-id="53a45-174">This plugin allows you to look at GC heap objects, their hierarchies, and roots.</span></span>
<span data-ttu-id="53a45-175">Para carregar o plug-in no depurador, insira o seguinte comando na linha de comando do depurador:</span><span class="sxs-lookup"><span data-stu-id="53a45-175">To load the plugin into the debugger, enter the following command in the debugger command line:</span></span>

<span data-ttu-id="53a45-176">No WinDbg (parece que o WinDbg faz isso automaticamente ao executar a interrupção no aplicativo .NET Core):</span><span class="sxs-lookup"><span data-stu-id="53a45-176">In WinDbg (it seems WinDbg does that automatically when breaking into .NET Core application):</span></span>

```console
.loadby sos coreclr
```

<span data-ttu-id="53a45-177">No LLDB:</span><span class="sxs-lookup"><span data-stu-id="53a45-177">In LLDB:</span></span>

```console
plugin load /path/to/libsosplugin.so
```

<span data-ttu-id="53a45-178">Vamos tentar depurar um programa de exemplo que tem problemas com o descarregamento.</span><span class="sxs-lookup"><span data-stu-id="53a45-178">Let's try to debug an example program that has problems with unloading.</span></span> <span data-ttu-id="53a45-179">O código-fonte está incluído abaixo.</span><span class="sxs-lookup"><span data-stu-id="53a45-179">Source code is included below.</span></span> <span data-ttu-id="53a45-180">Quando você o executa no WinDbg, o programa interrompe o depurador logo após a tentativa de verificar o êxito do descarregamento.</span><span class="sxs-lookup"><span data-stu-id="53a45-180">When you run it under WinDbg, the program breaks into the debugger right after attempting to check for the unload success.</span></span> <span data-ttu-id="53a45-181">Em seguida, você poderá começar a procurar os culpados.</span><span class="sxs-lookup"><span data-stu-id="53a45-181">You can then start looking for the culprits.</span></span>

<span data-ttu-id="53a45-182">Observe que se você fizer a depuração usando o LLDB no UNIX, os comandos do SOS nos exemplos a seguir não serão precedidos pelo `!`.</span><span class="sxs-lookup"><span data-stu-id="53a45-182">Note that if you debug using LLDB on Unix, the SOS commands in the following examples don't have the `!` in front of them.</span></span>

```console
!dumpheap -type LoaderAllocator
```

<span data-ttu-id="53a45-183">Esse comando despeja todos os objetos com um nome de tipo que contém `LoaderAllocator` que estão no heap do GC.</span><span class="sxs-lookup"><span data-stu-id="53a45-183">This command dumps all objects with a type name containing `LoaderAllocator` that are in the GC heap.</span></span> <span data-ttu-id="53a45-184">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="53a45-184">Here is an example:</span></span>

```console
         Address               MT     Size
000002b78000ce40 00007ffadc93a288       48     
000002b78000ceb0 00007ffadc93a218       24     

Statistics:
              MT    Count    TotalSize Class Name
00007ffadc93a218        1           24 System.Reflection.LoaderAllocatorScout
00007ffadc93a288        1           48 System.Reflection.LoaderAllocator
Total 2 objects
```

<span data-ttu-id="53a45-185">Na parte "Estatísticas:" abaixo, verifique `MT` (`MethodTable`) pertencente ao `System.Reflection.LoaderAllocator`, que é o objeto sobre o qual nos preocupamos.</span><span class="sxs-lookup"><span data-stu-id="53a45-185">In the "Statistics:" part below, check the `MT` (`MethodTable`) belonging to the `System.Reflection.LoaderAllocator`, which is the object we care about.</span></span> <span data-ttu-id="53a45-186">Em seguida, na lista no início, localize a entrada com `MT` correspondente a aquela e obtenha o endereço do próprio objeto.</span><span class="sxs-lookup"><span data-stu-id="53a45-186">Then in the list at the beginning, find the entry with `MT` matching that one and get the address of the object itself.</span></span> <span data-ttu-id="53a45-187">Em nosso caso, ela é "000002b78000ce40"</span><span class="sxs-lookup"><span data-stu-id="53a45-187">In our case, it is "000002b78000ce40"</span></span>

<span data-ttu-id="53a45-188">Agora que sabemos o endereço do objeto `LoaderAllocator`, podemos usar outro comando para encontrar suas raízes do GC</span><span class="sxs-lookup"><span data-stu-id="53a45-188">Now that we know the address of the `LoaderAllocator` object, we can use another command to find its GC roots</span></span>

```console
!gcroot -all 0x000002b78000ce40 
```

<span data-ttu-id="53a45-189">Esse comando despeja a cadeia de referências de objeto que leva à instância `LoaderAllocator`.</span><span class="sxs-lookup"><span data-stu-id="53a45-189">This command dumps the chain of object references that lead to the `LoaderAllocator` instance.</span></span> <span data-ttu-id="53a45-190">A lista começa com a raiz, que é a entidade que mantém o `LoaderAllocator` ativo e, portanto, é o cerne do problema que você está depurando.</span><span class="sxs-lookup"><span data-stu-id="53a45-190">The list starts with the root, which is the entity that keeps our `LoaderAllocator` alive and thus is the core of the problem you're debugging.</span></span> <span data-ttu-id="53a45-191">A raiz pode ser um slot de pilha, um registro de processador, um identificador GC ou uma variável estática.</span><span class="sxs-lookup"><span data-stu-id="53a45-191">The root can be a stack slot, a processor register, a GC handle, or a static variable.</span></span>

<span data-ttu-id="53a45-192">Este é um exemplo da saída do comando `gcroot`:</span><span class="sxs-lookup"><span data-stu-id="53a45-192">Here is an example of the output of the `gcroot` command:</span></span>

```console
Thread 4ac:
    000000cf9499dd20 00007ffa7d0236bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
        rbp-20: 000000cf9499dd90
            ->  000002b78000d328 System.Reflection.RuntimeMethodInfo
            ->  000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
            ->  000002b78000d1d0 System.RuntimeType
            ->  000002b78000ce40 System.Reflection.LoaderAllocator

HandleTable:
    000002b7f8a81198 (strong handle)
    -> 000002b78000d948 test.Test
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

    000002b7f8a815f8 (pinned handle)
    -> 000002b790001038 System.Object[]
    -> 000002b78000d390 example.TestInfo
    -> 000002b78000d328 System.Reflection.RuntimeMethodInfo
    -> 000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
    -> 000002b78000d1d0 System.RuntimeType
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

Found 3 roots.
```

<span data-ttu-id="53a45-193">Agora você precisa descobrir o local em que a raiz se encontra para corrigi-la.</span><span class="sxs-lookup"><span data-stu-id="53a45-193">Now you need to figure out where the root is located so you can fix it.</span></span> <span data-ttu-id="53a45-194">O caso mais fácil é quando a raiz é um slot de pilha ou um registro de processador.</span><span class="sxs-lookup"><span data-stu-id="53a45-194">The easiest case is when the root is a stack slot or a processor register.</span></span> <span data-ttu-id="53a45-195">Nesse caso, o `gcroot` mostra o nome da função cujo quadro contém a raiz e o thread que executa essa função.</span><span class="sxs-lookup"><span data-stu-id="53a45-195">In that case, the `gcroot` shows you the name of the function whose frame contains the root and the thread executing that function.</span></span> <span data-ttu-id="53a45-196">O caso difícil é quando a raiz é uma variável estática ou um identificador GC.</span><span class="sxs-lookup"><span data-stu-id="53a45-196">The difficult case is when the root is a static variable or a GC handle.</span></span> 

<span data-ttu-id="53a45-197">No exemplo anterior, a primeira raiz é um local do tipo `System.Reflection.RuntimeMethodInfo` armazenado no quadro da função `example.Program.Main(System.String[])` no endereço `rbp-20` (`rbp` é o registro de processador `rbp` e -20 é um deslocamento hexadecimal desse registro).</span><span class="sxs-lookup"><span data-stu-id="53a45-197">In the previous example, the first root is a local of type `System.Reflection.RuntimeMethodInfo` stored in the frame of the function `example.Program.Main(System.String[])` at address `rbp-20` (`rbp` is the processor register `rbp` and -20 is a hexadecimal offset from that register).</span></span>

<span data-ttu-id="53a45-198">A segunda raiz é um `GCHandle` normal (forte) que contém uma referência a uma instância da classe `test.Test`.</span><span class="sxs-lookup"><span data-stu-id="53a45-198">The second root is a normal (strong) `GCHandle` that holds a reference to an instance of the `test.Test` class.</span></span> 

<span data-ttu-id="53a45-199">A terceira raiz é um `GCHandle` fixo.</span><span class="sxs-lookup"><span data-stu-id="53a45-199">The third root is a pinned `GCHandle`.</span></span> <span data-ttu-id="53a45-200">Essa é, na verdade, uma variável estática.</span><span class="sxs-lookup"><span data-stu-id="53a45-200">This one is actually a static variable.</span></span> <span data-ttu-id="53a45-201">A má notícia é que não há como identificar isso.</span><span class="sxs-lookup"><span data-stu-id="53a45-201">Unfortunately, there is no way to tell.</span></span> <span data-ttu-id="53a45-202">Os estáticos para tipos de referência são armazenados em uma matriz de objeto gerenciado em estruturas de tempo de execução internas.</span><span class="sxs-lookup"><span data-stu-id="53a45-202">Statics for reference types are stored in a managed object array in internal runtime structures.</span></span>

<span data-ttu-id="53a45-203">Outro caso que pode impedir o descarregamento de um `AssemblyLoadContext` é quando um thread tem um quadro de um método de um assembly carregado no `AssemblyLoadContext` em sua pilha.</span><span class="sxs-lookup"><span data-stu-id="53a45-203">Another case that can prevent unloading of an `AssemblyLoadContext` is when a thread has a frame of a method from an assembly loaded into the `AssemblyLoadContext` on its stack.</span></span> <span data-ttu-id="53a45-204">Você pode verificar isso despejando pilhas de chamadas gerenciadas de todos os threads:</span><span class="sxs-lookup"><span data-stu-id="53a45-204">You can check that by dumping managed call stacks of all threads:</span></span>

```console
~*e !clrstack
```

<span data-ttu-id="53a45-205">O comando significa "aplicar a todos os threads o comando `!clrstack`".</span><span class="sxs-lookup"><span data-stu-id="53a45-205">The command means "apply to all threads the `!clrstack` command".</span></span> <span data-ttu-id="53a45-206">Veja a seguir a saída desse comando para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="53a45-206">The following is the output of that command for the example.</span></span> <span data-ttu-id="53a45-207">A má notícia é que o LLDB no UNIX não tem nenhuma maneira de aplicar um comando a todos os threads; portanto, você precisará recorrer à alternância manual de threads e repetição do comando `clrstack`.</span><span class="sxs-lookup"><span data-stu-id="53a45-207">Unfortunately, LLDB on Unix doesn't have any way to apply a command to all threads, so you'll need to resort to manually switching threads and repeating the `clrstack` command.</span></span>
<span data-ttu-id="53a45-208">Ignore todos os threads em que o depurador indica "Não é possível percorrer a pilha gerenciada".</span><span class="sxs-lookup"><span data-stu-id="53a45-208">Ignore all threads where the debugger says "Unable to walk the managed stack."</span></span>

```console
OS Thread Id: 0x6ba8 (0)
        Child SP               IP Call Site
0000001fc697d5c8 00007ffb50d9de12 [HelperMethodFrame: 0000001fc697d5c8] System.Diagnostics.Debugger.BreakInternal()
0000001fc697d6d0 00007ffa864765fa System.Diagnostics.Debugger.Break()
0000001fc697d700 00007ffa864736bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
0000001fc697d998 00007ffae5fdc1e3 [GCFrame: 0000001fc697d998] 
0000001fc697df28 00007ffae5fdc1e3 [GCFrame: 0000001fc697df28] 
OS Thread Id: 0x2ae4 (1)
Unable to walk the managed stack. The current thread is likely not a 
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x61a4 (2)
Unable to walk the managed stack. The current thread is likely not a 
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x7fdc (3)
Unable to walk the managed stack. The current thread is likely not a 
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5390 (4)
Unable to walk the managed stack. The current thread is likely not a 
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5ec8 (5)
        Child SP               IP Call Site
0000001fc70ff6e0 00007ffb5437f6e4 [DebuggerU2MCatchHandlerFrame: 0000001fc70ff6e0] 
OS Thread Id: 0x4624 (6)
        Child SP               IP Call Site
GetFrameContext failed: 1
0000000000000000 0000000000000000 
OS Thread Id: 0x60bc (7)
        Child SP               IP Call Site
0000001fc727f158 00007ffb5437fce4 [HelperMethodFrame: 0000001fc727f158] System.Threading.Thread.SleepInternal(Int32)
0000001fc727f260 00007ffb37ea7c2b System.Threading.Thread.Sleep(Int32)
0000001fc727f290 00007ffa865005b3 test.Program.ThreadProc() [E:\unloadability\test\Program.cs @ 17]
0000001fc727f2c0 00007ffb37ea6a5b System.Threading.Thread.ThreadMain_ThreadStart()
0000001fc727f2f0 00007ffadbc4cbe3 System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object)
0000001fc727f568 00007ffae5fdc1e3 [GCFrame: 0000001fc727f568] 
0000001fc727f7f0 00007ffae5fdc1e3 [DebuggerU2MCatchHandlerFrame: 0000001fc727f7f0] 

```

<span data-ttu-id="53a45-209">Como você pode ver, o último thread tem `test.Program.ThreadProc()`.</span><span class="sxs-lookup"><span data-stu-id="53a45-209">As you can see, the last thread has `test.Program.ThreadProc()`.</span></span> <span data-ttu-id="53a45-210">Essa é uma função do assembly carregado no `AssemblyLoadContext` e, portanto, mantém o `AssemblyLoadContext` ativo.</span><span class="sxs-lookup"><span data-stu-id="53a45-210">This is a function from the assembly loaded into the `AssemblyLoadContext`, and so it keeps the `AssemblyLoadContext` alive.</span></span>

## <a name="example-source-with-unloadability-issues"></a><span data-ttu-id="53a45-211">Origem de exemplo com problemas de capacidade de descarregamento</span><span class="sxs-lookup"><span data-stu-id="53a45-211">Example source with unloadability issues</span></span>

<span data-ttu-id="53a45-212">O código a seguir é usado no exemplo de depuração anterior.</span><span class="sxs-lookup"><span data-stu-id="53a45-212">The following code is used in the previous debugging example.</span></span>

### <a name="main-testing-program"></a><span data-ttu-id="53a45-213">Programa de teste principal</span><span class="sxs-lookup"><span data-stu-id="53a45-213">Main testing program</span></span>

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a><span data-ttu-id="53a45-214">Programa carregado no TestAssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="53a45-214">Program loaded into the TestAssemblyLoadContext</span></span>

<span data-ttu-id="53a45-215">O código a seguir representa o *Test. dll* passado para `ExecuteAndUnload` o método no programa de teste principal.</span><span class="sxs-lookup"><span data-stu-id="53a45-215">The following code represents the *test.dll* passed to the `ExecuteAndUnload` method in the main testing program.</span></span>

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
