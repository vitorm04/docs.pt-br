---
title: Como usar e depurar a capacidade de descarregamento de assembly no .NET Core
description: Saiba como usar o AssemblyLoadContext de coleção para carregar e descarregar assemblies gerenciados e como depurar problemas que impedem o êxito do descarregamento.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: a3ba2c2809aedd0af03ec965089f8779c430a335
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68671241"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>Como usar e depurar a capacidade de descarregamento de assembly no .NET Core

No .NET Core 3.0 em diante, há suporte para a capacidade de carregar e, posteriormente, descarregar um conjunto de assemblies. No .NET Framework, os domínios de aplicativo personalizados foram usados para essa finalidade, mas o .NET Core só dá suporte a um único domínio de aplicativo padrão.

O .NET Core 3.0 e versões posteriores dão suporte à capacidade de descarregamento por meio de <xref:System.Runtime.Loader.AssemblyLoadContext>. Você pode carregar um conjunto de assemblies em um `AssemblyLoadContext` de coleção, executar métodos neles ou apenas inspecioná-los usando a reflexão e, por fim, descarregar o `AssemblyLoadContext`. Isso descarrega os assemblies carregados nesse `AssemblyLoadContext`.

Há uma diferença notável entre o descarregamento com `AssemblyLoadContext` e com o AppDomain. Com o AppDomain, o descarregamento é forçado. No momento do descarregamento, todos os threads em execução no AppDomain de destino são anulados, os objetos COM gerenciados criados no AppDomain de destino são destruídos etc. Com `AssemblyLoadContext`, o descarregamento é "cooperativo". A chamada do método <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> apenas inicia o descarregamento. O descarregamento é concluído depois que:

- Nenhum thread tem métodos dos assemblies carregados em `AssemblyLoadContext` nas pilhas de chamadas.
- Nenhum dos tipos dos assemblies carregados em `AssemblyLoadContext`, as instâncias desses tipos e os próprios assemblies fora de `AssemblyLoadContext` são referenciados por:
  - Referências fora do `AssemblyLoadContext`, exceto referências fracas (<xref:System.WeakReference> ou <xref:System.WeakReference%601>).
  - Identificadores GC fortes (<xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Normal> ou <xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Pinned>) dentro e fora de `AssemblyLoadContext`.

## <a name="using-collectible-assemblyloadcontext"></a>Como usar o AssemblyLoadContext de coleção

Esta seção contém um tutorial passo a passo detalhado que mostra uma maneira simples de carregar um aplicativo .NET Core em um `AssemblyLoadContext` de coleção, executar seu ponto de entrada e, em seguida, descarregá-lo. Encontre uma amostra completa em <https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading>.

### <a name="create-a-collectible-assemblyloadcontext"></a>Criar um AssemblyLoadContext de coleção

Você precisa derivar a classe de <xref:System.Runtime.Loader.AssemblyLoadContext> e sobrecarregar o método <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType>. Esse método resolve as referências para todos os assemblies que são dependências de assemblies carregados nesse `AssemblyLoadContext`.
O seguinte código é um exemplo do `AssemblyLoadContext` personalizado mais simples:

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

Como você pode ver, o método `Load` retorna `null`. Isso significa que todos os assemblies de dependência são carregados no contexto padrão e o novo contexto contém apenas os assemblies carregados explicitamente nele.

Caso deseje carregar algumas ou todas as dependências no `AssemblyLoadContext` também, use o `AssemblyDependencyResolver` no método `Load`. O `AssemblyDependencyResolver` resolve os nomes de assembly para caminhos absolutos de arquivo do assembly usando o arquivo *.deps.json* contido no diretório do assembly principal carregado no contexto e usando arquivos do assembly desse diretório.

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a>Usar um AssemblyLoadContext de coleção personalizado

Esta seção pressupõe que a versão mais simples do `TestAssemblyLoadContext` esteja sendo usada.

Crie uma instância do `AssemblyLoadContext` personalizado e carregue um assembly nele da seguinte maneira:

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

Para cada um dos assemblies referenciados pelo assembly carregado, o método `TestAssemblyLoadContext.Load` é chamado, de modo que o `TestAssemblyLoadContext` possa decidir o local em que obterá o assembly. Em nosso caso, ele retorna `null` para indicar que ele deve ser carregado no contexto padrão de localizações usadas pelo tempo de execução para carregar assemblies por padrão.

Agora que um assembly foi carregado, você pode executar um método nele. Execute o método `Main`:

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

Depois que o método `Main` for retornado, você poderá iniciar o descarregamento chamando o método `Unload` no `AssemblyLoadContext` personalizado ou se livrar da referência existente ao `AssemblyLoadContext`:

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

Isso é suficiente para descarregar o assembly de teste. Na verdade, vamos colocar tudo isso em um método separado que não pode ser embutido para garantir que `TestAssemblyLoadContext`, `Assembly` e `MethodInfo` (o `Assembly.EntryPoint`) não possam ser mantidos ativos por referências de slot de pilha (locais introduzidos reais ou em JIT). Isso pode manter o `TestAssemblyLoadContext` ativo e impedir o descarregamento.

Além disso, retorne uma referência fraca ao `AssemblyLoadContext`, de modo que você possa usá-la posteriormente para detectar a conclusão do descarregamento.

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

Agora você pode executar essa função para carregar, executar e descarregar o assembly.

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

No entanto, o descarregamento não é concluído imediatamente. Como mencionado anteriormente, ele depende do GC para coletar todos os objetos do assembly de teste. Em muitos casos, não é necessário aguardar a conclusão do descarregamento. No entanto, há casos em que é útil saber que o descarregamento foi concluído. Por exemplo, talvez você deseje excluir o arquivo do assembly que foi carregado no `AssemblyLoadContext` personalizado do disco. Nesse caso, o snippet de código a seguir pode ser usado. Ele dispara um GC e aguarda os finalizadores pendentes em um loop até a referência fraca ao `AssemblyLoadContext` personalizado ser definida como `null`, indicando que o objeto de destino foi coletado. Observe que, na maioria dos casos, apenas uma passagem pelo loop é necessária. No entanto, para casos mais complexos em que os objetos criados pelo código em execução no `AssemblyLoadContext` têm finalizadores, mais passagens podem ser necessárias.

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a>O evento de descarregamento

Em alguns casos, poderá ser necessário que o código carregado em um `AssemblyLoadContext` personalizado execute alguma limpeza quando o descarregamento for iniciado. Por exemplo, pode ser necessário interromper os threads, limpar alguns identificadores GC fortes etc. O evento `Unloading` pode ser usado nesses casos. Um manipulador que executa a limpeza necessária pode ser conectado a esse evento.

### <a name="troubleshoot-unloadability-issues"></a>Solução de problemas de capacidade de descarregamento

Devido à natureza cooperativa do descarregamento, é fácil esquecer as referências mantendo os itens em um `AssemblyLoadContext` de coleção ativos e impedindo o descarregamento. Este é um resumo dos itens (alguns deles não óbvios) que podem conter as referências:

- Referências regulares mantidas fora do `AssemblyLoadContext` de coleção, armazenadas em um slot de pilha ou em um registro de processador (locais de método, criados explicitamente pelo código do usuário ou implicitamente pelo JIT), uma variável estática ou um identificador GC forte/de fixação e apontando transitivamente para:
  - Um assembly carregado no `AssemblyLoadContext` de coleção.
  - Um tipo desse assembly.
  - Uma instância de um tipo desse assembly.
- Threads executando um código de um assembly carregado no `AssemblyLoadContext` de coleção.
- Instâncias de tipos `AssemblyLoadContext` personalizados que não são de coleção criados dentro do `AssemblyLoadContext` de coleção
- Instâncias <xref:System.Threading.RegisteredWaitHandle> pendentes com retornos de chamada definidos como métodos no `AssemblyLoadContext` personalizado

Dicas para localizar o slot de pilha/o registro de processador fazendo rooting de um objeto:

- Passar os resultados da chamada de função diretamente para outra função pode criar uma raiz, embora não haja nenhuma variável local criada pelo usuário.
- Se uma referência a um objeto estivesse disponível em qualquer ponto em um método, o JIT poderia ter decidido manter a referência em um slot de pilha/um registro do processador pelo tempo desejado na função atual.

## <a name="debug-unloading-issues"></a>Depurar problemas de descarregamento

Problemas de depuração com o descarregamento podem ser entediantes. Você pode enfrentar situações em que não sabe o que pode estar mantendo `AssemblyLoadContext` um ativo, mas o descarregamento falha.
A melhor arma para ajudar com isso é o WinDbg (LLDB no UNIX) com o plug-in do SOS. Você precisa encontrar o que está mantendo um `LoaderAllocator` ativo pertencente ao `AssemblyLoadContext` específico.
Esse plug-in permite que você examine os objetos de heap do GC, suas hierarquias e raízes.
Para carregar o plug-in no depurador, insira o seguinte comando na linha de comando do depurador:

No WinDbg (parece que o WinDbg faz isso automaticamente ao executar a interrupção no aplicativo .NET Core):

```console
.loadby sos coreclr
```

No LLDB:

```console
plugin load /path/to/libsosplugin.so
```

Vamos tentar depurar um programa de exemplo que tem problemas com o descarregamento. O código-fonte está incluído abaixo. Quando você o executa no WinDbg, o programa interrompe o depurador logo após a tentativa de verificar o êxito do descarregamento. Em seguida, você poderá começar a procurar os culpados.

Observe que se você fizer a depuração usando o LLDB no UNIX, os comandos do SOS nos exemplos a seguir não serão precedidos pelo `!`.

```console
!dumpheap -type LoaderAllocator
```

Esse comando despeja todos os objetos com um nome de tipo que contém `LoaderAllocator` que estão no heap do GC. Veja um exemplo:

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

Na parte "Estatísticas:" abaixo, verifique `MT` (`MethodTable`) pertencente ao `System.Reflection.LoaderAllocator`, que é o objeto sobre o qual nos preocupamos. Em seguida, na lista no início, localize a entrada com `MT` correspondente a aquela e obtenha o endereço do próprio objeto. Em nosso caso, ela é "000002b78000ce40"

Agora que sabemos o endereço do objeto `LoaderAllocator`, podemos usar outro comando para encontrar suas raízes do GC

```console
!gcroot -all 0x000002b78000ce40 
```

Esse comando despeja a cadeia de referências de objeto que leva à instância `LoaderAllocator`. A lista começa com a raiz, que é a entidade que mantém o `LoaderAllocator` ativo e, portanto, é o cerne do problema que você está depurando. A raiz pode ser um slot de pilha, um registro de processador, um identificador GC ou uma variável estática.

Este é um exemplo da saída do comando `gcroot`:

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

Agora você precisa descobrir o local em que a raiz se encontra para corrigi-la. O caso mais fácil é quando a raiz é um slot de pilha ou um registro de processador. Nesse caso, o `gcroot` mostra o nome da função cujo quadro contém a raiz e o thread que executa essa função. O caso difícil é quando a raiz é uma variável estática ou um identificador GC. 

No exemplo anterior, a primeira raiz é um local do tipo `System.Reflection.RuntimeMethodInfo` armazenado no quadro da função `example.Program.Main(System.String[])` no endereço `rbp-20` (`rbp` é o registro de processador `rbp` e -20 é um deslocamento hexadecimal desse registro).

A segunda raiz é um `GCHandle` normal (forte) que contém uma referência a uma instância da classe `test.Test`. 

A terceira raiz é um `GCHandle` fixo. Essa é, na verdade, uma variável estática. A má notícia é que não há como identificar isso. Os estáticos para tipos de referência são armazenados em uma matriz de objeto gerenciado em estruturas de tempo de execução internas.

Outro caso que pode impedir o descarregamento de um `AssemblyLoadContext` é quando um thread tem um quadro de um método de um assembly carregado no `AssemblyLoadContext` em sua pilha. Você pode verificar isso despejando pilhas de chamadas gerenciadas de todos os threads:

```console
~*e !clrstack
```

O comando significa "aplicar a todos os threads o comando `!clrstack`". Veja a seguir a saída desse comando para o exemplo. A má notícia é que o LLDB no UNIX não tem nenhuma maneira de aplicar um comando a todos os threads; portanto, você precisará recorrer à alternância manual de threads e repetição do comando `clrstack`.
Ignore todos os threads em que o depurador indica "Não é possível percorrer a pilha gerenciada".

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

Como você pode ver, o último thread tem `test.Program.ThreadProc()`. Essa é uma função do assembly carregado no `AssemblyLoadContext` e, portanto, mantém o `AssemblyLoadContext` ativo.

## <a name="example-source-with-unloadability-issues"></a>Origem de exemplo com problemas de capacidade de descarregamento

O código a seguir é usado no exemplo de depuração anterior.

### <a name="main-testing-program"></a>Programa de teste principal

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a>Programa carregado no TestAssemblyLoadContext

O código a seguir representa a `test.dll` passada para o método `ExecuteAndUnload` no programa de teste principal.

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
