---
title: 'Tutorial: Criar um provedor de tipos (F #)'
description: 'Saiba como criar seus próprios provedores de tipos F # no F # 3.0 examinando vários provedores de tipo simples para ilustrar os conceitos básicos.'
ms.date: 05/16/2016
ms.openlocfilehash: 3c998377b2c3a408d536ef416f3799bf7f04b6bd
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44212315"
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="97303-103">Tutorial: Criar um provedor de tipo</span><span class="sxs-lookup"><span data-stu-id="97303-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="97303-104">O mecanismo de provedor de tipo em F # é uma parte significativa do seu suporte para programação rica de informações.</span><span class="sxs-lookup"><span data-stu-id="97303-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="97303-105">Este tutorial explica como criar seus próprios provedores de tipos ao guiá-lo através do desenvolvimento de vários provedores de tipo simples para ilustrar os conceitos básicos.</span><span class="sxs-lookup"><span data-stu-id="97303-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="97303-106">Para obter mais informações sobre o mecanismo de provedor de tipo em F #, consulte [provedores de tipos](index.md).</span><span class="sxs-lookup"><span data-stu-id="97303-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="97303-107">O ecossistema de F # contém uma variedade de provedores de tipos para serviços de dados corporativos e da Internet comumente usados.</span><span class="sxs-lookup"><span data-stu-id="97303-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="97303-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="97303-108">For example:</span></span>

- <span data-ttu-id="97303-109">[FSharp](https://fsharp.github.io/FSharp.Data/) inclui provedores de tipos de formatos de documentos JSON, XML, CSV e HTML.</span><span class="sxs-lookup"><span data-stu-id="97303-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="97303-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) fornece acesso fortemente tipado para bancos de dados SQL por meio de um mapeamento de objeto e o F # LINQ consultas em relação a essas fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="97303-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="97303-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) tem um conjunto de provedores de tipo para o tempo de compilação verificada incorporação do T-SQL em F #.</span><span class="sxs-lookup"><span data-stu-id="97303-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="97303-112">[Typeproviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) é um conjunto mais antigo de provedores de tipos para uso apenas com a programação do .NET Framework para acessar os serviços de dados SQL, Entity Framework, OData e WSDL.</span><span class="sxs-lookup"><span data-stu-id="97303-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="97303-113">Onde for necessário, você pode criar provedores de tipos personalizados, ou você pode fazer referência a provedores de tipos criados por outros usuários.</span><span class="sxs-lookup"><span data-stu-id="97303-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="97303-114">Por exemplo, sua organização pode ter um serviço de dados que fornece um grande e crescente número de conjuntos de dados nomeados, cada um com seu próprio esquema de dados estáveis.</span><span class="sxs-lookup"><span data-stu-id="97303-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="97303-115">Você pode criar um provedor de tipo que lê os esquemas e apresenta os conjuntos de dados atuais para o programador de uma forma fortemente tipada.</span><span class="sxs-lookup"><span data-stu-id="97303-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="97303-116">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="97303-116">Before You Start</span></span>

<span data-ttu-id="97303-117">O mecanismo de provedor de tipo é projetado principalmente para injetando dados estáveis e espaços de informações do serviço para a experiência de programação F #.</span><span class="sxs-lookup"><span data-stu-id="97303-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="97303-118">Esse mecanismo não foi projetado para injetar espaços informações cujo esquema é alterado durante a execução do programa de maneiras que sejam relevantes para a lógica do programa.</span><span class="sxs-lookup"><span data-stu-id="97303-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="97303-119">Além disso, o mecanismo não foi projetado para intraidioma metaprogramação, mesmo que esse domínio contém alguns usos válidos.</span><span class="sxs-lookup"><span data-stu-id="97303-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="97303-120">Você deve usar esse mecanismo somente quando necessário e, em que o desenvolvimento de um provedor de tipo produz o valor muito alto.</span><span class="sxs-lookup"><span data-stu-id="97303-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="97303-121">Você deve evitar escrever um provedor de tipo no qual um esquema não está disponível.</span><span class="sxs-lookup"><span data-stu-id="97303-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="97303-122">Da mesma forma, você deve evitar escrever um provedor de tipo, onde um comum (ou até mesmo um existente) biblioteca .NET seria suficiente.</span><span class="sxs-lookup"><span data-stu-id="97303-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="97303-123">Antes de começar, você pode fazer as perguntas a seguir:</span><span class="sxs-lookup"><span data-stu-id="97303-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="97303-124">Você tem um esquema para sua fonte de informações?</span><span class="sxs-lookup"><span data-stu-id="97303-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="97303-125">Nesse caso, o que é o mapeamento para o F # e sistema de tipos do .NET?</span><span class="sxs-lookup"><span data-stu-id="97303-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="97303-126">Você pode usar uma API (dinamicamente tipada) existente como ponto de partida para sua implementação?</span><span class="sxs-lookup"><span data-stu-id="97303-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="97303-127">Você e sua organização terá suficiente usos do provedor do tipo para tornar a escrevê-lo que vale a pena?</span><span class="sxs-lookup"><span data-stu-id="97303-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="97303-128">Uma biblioteca .NET normal atendem suas necessidades?</span><span class="sxs-lookup"><span data-stu-id="97303-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="97303-129">Quanto seu esquema será alterado?</span><span class="sxs-lookup"><span data-stu-id="97303-129">How much will your schema change?</span></span>

- <span data-ttu-id="97303-130">Ele será alterado durante a codificação?</span><span class="sxs-lookup"><span data-stu-id="97303-130">Will it change during coding?</span></span>

- <span data-ttu-id="97303-131">Ele será alterado entre as sessões de codificação?</span><span class="sxs-lookup"><span data-stu-id="97303-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="97303-132">Ele será alterado durante a execução do programa?</span><span class="sxs-lookup"><span data-stu-id="97303-132">Will it change during program execution?</span></span>

<span data-ttu-id="97303-133">Provedores de tipos são mais adequados para situações em que o esquema é estável no tempo de execução e durante o tempo de vida do código compilado.</span><span class="sxs-lookup"><span data-stu-id="97303-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>

## <a name="a-simple-type-provider"></a><span data-ttu-id="97303-134">Um provedor de tipo simples</span><span class="sxs-lookup"><span data-stu-id="97303-134">A Simple Type Provider</span></span>

<span data-ttu-id="97303-135">Este exemplo é Samples.HelloWorldTypeProvider, semelhante aos exemplos na `examples` diretório da [SDK do provedor de tipo F #](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span><span class="sxs-lookup"><span data-stu-id="97303-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="97303-136">O provedor torna disponível um "espaço de tipo" que contém 100 tipos apagados, como mostra o código usando a sintaxe de assinatura do F # e omitindo os detalhes para todos, exceto `Type1`.</span><span class="sxs-lookup"><span data-stu-id="97303-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="97303-137">Para obter mais informações sobre os tipos de apagados, consulte [detalhes sobre apagados fornecidos tipos](#details-about-erased-provided-types) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="97303-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

```fsharp
namespace Samples.HelloWorldTypeProvider

type Type1 =
    /// This is a static property.
    static member StaticProperty : string

    /// This constructor takes no arguments.
    new : unit -> Type1

    /// This constructor takes one argument.
    new : data:string -> Type1

    /// This is an instance property.
    member InstanceProperty : int

    /// This is an instance method.
    member InstanceMethod : x:int -> char

    nested type NestedType = 
        /// This is StaticProperty1 on NestedType.
        static member StaticProperty1 : string
        …
        /// This is StaticProperty100 on NestedType.
        static member StaticProperty100 : string

type Type2 =
…
…

type Type100 =
…
```

<span data-ttu-id="97303-138">Observe que o conjunto de tipos e membros fornecidos é conhecido estaticamente.</span><span class="sxs-lookup"><span data-stu-id="97303-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="97303-139">Este exemplo não aproveita a capacidade de provedores fornecem tipos que dependem de um esquema.</span><span class="sxs-lookup"><span data-stu-id="97303-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="97303-140">A implementação do provedor de tipo é descrita no código a seguir, e os detalhes são abordados nas seções posteriores deste tópico.</span><span class="sxs-lookup"><span data-stu-id="97303-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>

>[!WARNING]
<span data-ttu-id="97303-141">Pode haver diferenças entre esse código e os exemplos on-line.</span><span class="sxs-lookup"><span data-stu-id="97303-141">There may be differences between this code and the online samples.</span></span>

```fsharp
namespace Samples.FSharp.HelloWorldTypeProvider

open System
open System.Reflection
open ProviderImplementation.ProvidedTypes
open FSharp.Core.CompilerServices
open FSharp.Quotations

// This type defines the type provider. When compiled to a DLL, it can be added
// as a reference to an F# command-line compilation, script, or project.
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this = 

  // Inheriting from this type provides implementations of ITypeProvider 
  // in terms of the provided types below.
  inherit TypeProviderForNamespaces(config)

  let namespaceName = "Samples.HelloWorldTypeProvider"
  let thisAssembly = Assembly.GetExecutingAssembly()

  // Make one provided type, called TypeN.
  let makeOneProvidedType (n:int) = 
  …
  // Now generate 100 types
  let types = [ for i in 1 .. 100 -> makeOneProvidedType i ] 

  // And add them to the namespace
  do this.AddNamespace(namespaceName, types)

[<assembly:TypeProviderAssembly>] 
do()
```

<span data-ttu-id="97303-142">Para usar esse provedor, abra uma instância separada do Visual Studio, crie um script F # e, em seguida, adicione uma referência para o provedor do seu script usando #r como o código a seguir mostra:</span><span class="sxs-lookup"><span data-stu-id="97303-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

```fsharp
#r @".\bin\Debug\Samples.HelloWorldTypeProvider.dll"

let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")

let obj2 = Samples.HelloWorldTypeProvider.Type1("some other data")

obj1.InstanceProperty
obj2.InstanceProperty

[ for index in 0 .. obj1.InstanceProperty-1 -> obj1.InstanceMethod(index) ]
[ for index in 0 .. obj2.InstanceProperty-1 -> obj2.InstanceMethod(index) ]

let data1 = Samples.HelloWorldTypeProvider.Type1.NestedType.StaticProperty35
```

<span data-ttu-id="97303-143">Em seguida, procure os tipos no `Samples.HelloWorldTypeProvider` namespace que o provedor de tipos gerado.</span><span class="sxs-lookup"><span data-stu-id="97303-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="97303-144">Antes de recompilar o provedor, certifique-se de que você fechar todas as instâncias do Visual Studio e F # interativo que estiver usando a DLL do provedor.</span><span class="sxs-lookup"><span data-stu-id="97303-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="97303-145">Caso contrário, ocorrerá um erro de compilação porque a DLL de saída será bloqueada.</span><span class="sxs-lookup"><span data-stu-id="97303-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="97303-146">Para depurar este provedor usando as instruções print, fazer com que um script que expõe um problema com o provedor e, em seguida, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="97303-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```fsharp
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="97303-147">Para depurar este provedor usando o Visual Studio, abra o prompt de comando do Visual Studio com credenciais administrativas e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="97303-147">To debug this provider by using Visual Studio, open the Visual Studio command prompt with administrative credentials, and run the following command:</span></span>

```fsharp
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="97303-148">Como alternativa, abra o Visual Studio, abra o menu de depuração, escolha `Debug/Attach to process…`e anexar para outro `devenv` processo no qual você está editando o script.</span><span class="sxs-lookup"><span data-stu-id="97303-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="97303-149">Usando esse método, você pode direcionar mais facilmente a lógica específica no provedor de tipos digitando interativamente expressões na segunda instância (com suporte total ao IntelliSense e outros recursos).</span><span class="sxs-lookup"><span data-stu-id="97303-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="97303-150">Você pode desabilitar apenas meu código de depuração para identificar melhor os erros no código gerado.</span><span class="sxs-lookup"><span data-stu-id="97303-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="97303-151">Para obter informações sobre como habilitar ou desabilitar esse recurso, consulte [navegar pelo código com o depurador](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span><span class="sxs-lookup"><span data-stu-id="97303-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="97303-152">Além disso, você também pode definir exceções de primeira chance capturando abrindo o `Debug` menu e, em seguida, escolhendo `Exceptions` ou escolhendo as teclas Ctrl + Alt + E para abrir o `Exceptions` caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="97303-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="97303-153">Na caixa de diálogo, sob `Common Language Runtime Exceptions`, selecione o `Thrown` caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="97303-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>

### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="97303-154">Implementação do provedor de tipo</span><span class="sxs-lookup"><span data-stu-id="97303-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="97303-155">Esta seção explica as seções principais da implementação do provedor de tipo.</span><span class="sxs-lookup"><span data-stu-id="97303-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="97303-156">Primeiro, defina o tipo para o próprio provedor de tipo personalizado:</span><span class="sxs-lookup"><span data-stu-id="97303-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="97303-157">Esse tipo deve ser público e você deve marcá-la com o [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) para que o compilador reconheça o provedor de tipo quando um projeto separado do F # faz referência ao assembly que contém o tipo de atributo.</span><span class="sxs-lookup"><span data-stu-id="97303-157">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="97303-158">O *config* parâmetro é opcional e, se estiver presente, contém informações de configuração contextuais para a instância do provedor de tipo que o compilador F # cria.</span><span class="sxs-lookup"><span data-stu-id="97303-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="97303-159">Em seguida, você implementa o [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span><span class="sxs-lookup"><span data-stu-id="97303-159">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="97303-160">Nesse caso, você usa o `TypeProviderForNamespaces` tipo do `ProvidedTypes` API como um tipo base.</span><span class="sxs-lookup"><span data-stu-id="97303-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="97303-161">Esse tipo de auxiliar pode fornecer uma coleção finita de avidamente fornecida namespaces, diretamente, cada um deles contém um número finito de fixo, avidamente tipos.</span><span class="sxs-lookup"><span data-stu-id="97303-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="97303-162">Nesse contexto, o provedor *avidamente* gera tipos, mesmo se eles não são necessários ou usados.</span><span class="sxs-lookup"><span data-stu-id="97303-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="97303-163">Em seguida, definir valores particulares locais que especificam o namespace para os tipos fornecidos e localizar o assembly do provedor de tipo em si.</span><span class="sxs-lookup"><span data-stu-id="97303-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="97303-164">Esse assembly é usado posteriormente como o tipo de pai lógico dos tipos de apagados que são fornecidos.</span><span class="sxs-lookup"><span data-stu-id="97303-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="97303-165">Em seguida, crie uma função para fornecer cada um dos tipos Type1... Type100.</span><span class="sxs-lookup"><span data-stu-id="97303-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="97303-166">Essa função é explicada em mais detalhes mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="97303-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="97303-167">Em seguida, gere os 100 tipos fornecidos:</span><span class="sxs-lookup"><span data-stu-id="97303-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="97303-168">Em seguida, adicione os tipos como um namespace fornecido:</span><span class="sxs-lookup"><span data-stu-id="97303-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="97303-169">Finalmente, adicione um atributo de assembly que indica que você está criando uma DLL do provedor de tipo:</span><span class="sxs-lookup"><span data-stu-id="97303-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>] 
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="97303-170">Fornecendo um tipo e seus membros</span><span class="sxs-lookup"><span data-stu-id="97303-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="97303-171">O `makeOneProvidedType` função faz o trabalho real de fornecer um dos tipos.</span><span class="sxs-lookup"><span data-stu-id="97303-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) = 
…
```

<span data-ttu-id="97303-172">Esta etapa explica a implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="97303-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="97303-173">Primeiro, crie o tipo fornecido (por exemplo, Type1, quando n = 1 ou Type57, quando n = 57).</span><span class="sxs-lookup"><span data-stu-id="97303-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code, 
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="97303-174">Você deve observar os seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="97303-174">You should note the following points:</span></span>

- <span data-ttu-id="97303-175">Isso proporcionou tipo é apagado.</span><span class="sxs-lookup"><span data-stu-id="97303-175">This provided type is erased.</span></span>  <span data-ttu-id="97303-176">Porque você indica que o tipo base é `obj`, instâncias serão exibidos como valores do tipo [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) no código compilado.</span><span class="sxs-lookup"><span data-stu-id="97303-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="97303-177">Quando você especifica um tipo não aninhado, você deve especificar o assembly e namespace.</span><span class="sxs-lookup"><span data-stu-id="97303-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="97303-178">Para tipos apagados, o assembly deve ser o assembly do provedor de tipo em si.</span><span class="sxs-lookup"><span data-stu-id="97303-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="97303-179">Em seguida, adicione a documentação XML para o tipo.</span><span class="sxs-lookup"><span data-stu-id="97303-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="97303-180">Esta documentação está atrasada, ou seja, computados sob demanda se o compilador de host precisa dela.</span><span class="sxs-lookup"><span data-stu-id="97303-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="97303-181">Em seguida, você adicione uma propriedade estática fornecida para o tipo:</span><span class="sxs-lookup"><span data-stu-id="97303-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty", 
                                  propertyType = typeof<string>, 
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="97303-182">Obter esta propriedade será sempre avaliada como a cadeia de caracteres "Olá!".</span><span class="sxs-lookup"><span data-stu-id="97303-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="97303-183">O `GetterCode` para a propriedade usa uma cotação F #, que representa o código que o compilador de host gera para a obtenção da propriedade.</span><span class="sxs-lookup"><span data-stu-id="97303-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="97303-184">Para obter mais informações sobre cotações, consulte [citações de código (F #)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span><span class="sxs-lookup"><span data-stu-id="97303-184">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="97303-185">Adicione a documentação XML para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="97303-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="97303-186">Agora, anexe a propriedade fornecida para o tipo fornecido.</span><span class="sxs-lookup"><span data-stu-id="97303-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="97303-187">Você deve anexar o membro fornecido para apenas um tipo.</span><span class="sxs-lookup"><span data-stu-id="97303-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="97303-188">Caso contrário, o membro nunca poderão ser acessado.</span><span class="sxs-lookup"><span data-stu-id="97303-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="97303-189">Agora, crie um construtor fornecido que não usa nenhum parâmetro.</span><span class="sxs-lookup"><span data-stu-id="97303-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ], 
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="97303-190">O `InvokeCode` para o construtor retorna uma cotação F #, que representa o código que o compilador de host gera quando o construtor é chamado.</span><span class="sxs-lookup"><span data-stu-id="97303-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="97303-191">Por exemplo, você pode usar o seguinte construtor:</span><span class="sxs-lookup"><span data-stu-id="97303-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="97303-192">Uma instância do tipo fornecido será criada com dados subjacentes "Os dados do objeto".</span><span class="sxs-lookup"><span data-stu-id="97303-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="97303-193">O código entre aspas inclui uma conversão [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) porque esse tipo é a eliminação de Isso proporcionou tipo (conforme especificado quando você declarou que o tipo fornecido).</span><span class="sxs-lookup"><span data-stu-id="97303-193">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="97303-194">Adicionar a documentação XML para o construtor e adicione o construtor fornecido para o tipo fornecido:</span><span class="sxs-lookup"><span data-stu-id="97303-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="97303-195">Crie um segundo construtor fornecido que aceite um parâmetro:</span><span class="sxs-lookup"><span data-stu-id="97303-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 = 
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ], 
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="97303-196">O `InvokeCode` para o construtor retorna novamente uma cotação F #, que representa o código que o compilador de host gerado para uma chamada ao método.</span><span class="sxs-lookup"><span data-stu-id="97303-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="97303-197">Por exemplo, você pode usar o seguinte construtor:</span><span class="sxs-lookup"><span data-stu-id="97303-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="97303-198">Uma instância do tipo fornecido é criada com os dados subjacentes "dez".</span><span class="sxs-lookup"><span data-stu-id="97303-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="97303-199">Você talvez já notou que o `InvokeCode` função retorna uma cotação.</span><span class="sxs-lookup"><span data-stu-id="97303-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="97303-200">A entrada para essa função é uma lista de expressões, um por um parâmetro de construtor.</span><span class="sxs-lookup"><span data-stu-id="97303-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="97303-201">Nesse caso, uma expressão que representa o valor do parâmetro único está disponível em `args.[0]`.</span><span class="sxs-lookup"><span data-stu-id="97303-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="97303-202">O código para chamar o construtor força o valor de retorno para o tipo apagado `obj`.</span><span class="sxs-lookup"><span data-stu-id="97303-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="97303-203">Depois de adicionar o segundo construtor fornecido para o tipo, você pode criar uma propriedade de instância fornecida:</span><span class="sxs-lookup"><span data-stu-id="97303-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp = 
    ProvidedProperty(propertyName = "InstanceProperty", 
                     propertyType = typeof<int>, 
                     getterCode= (fun args -> 
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="97303-204">Obter esta propriedade retornará o comprimento da cadeia de caracteres, que é o objeto de representação.</span><span class="sxs-lookup"><span data-stu-id="97303-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="97303-205">O `GetterCode` propriedade retorna uma citação do F # que especifica o código que o compilador de host gera para obter a propriedade.</span><span class="sxs-lookup"><span data-stu-id="97303-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="97303-206">Como o `InvokeCode`, o `GetterCode` função retorna uma cotação.</span><span class="sxs-lookup"><span data-stu-id="97303-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="97303-207">O compilador de host chama essa função com uma lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="97303-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="97303-208">Nesse caso, os argumentos incluem apenas a única expressão que representa a instância na qual o getter está sendo chamado, que pode ser acessada usando `args.[0]`. A implementação de `GetterCode` une na cotação de resultado no tipo apagado `obj`, e uma conversão é usada para satisfazer o mecanismo do compilador para verificar os tipos que o objeto é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="97303-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="97303-209">A próxima parte do `makeOneProvidedType` fornece um método de instância com um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="97303-209">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

```fsharp
let instanceMeth = 
    ProvidedMethod(methodName = "InstanceMethod", 
                   parameters = [ProvidedParameter("x",typeof<int>)], 
                   returnType = typeof<char>, 
                   invokeCode = (fun args -> 
                       <@@ ((%%(args.[0]) : obj) :?> string).Chars(%%(args.[1]) : int) @@>))

instanceMeth.AddXmlDocDelayed(fun () -> "This is an instance method")
// Add the instance method to the type.
t.AddMember instanceMeth
```

<span data-ttu-id="97303-210">Por fim, crie um tipo aninhado que contém 100 propriedades aninhadas.</span><span class="sxs-lookup"><span data-stu-id="97303-210">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="97303-211">A criação deste aninhadas de tipo e suas propriedades estiver atrasada, ou seja, computados sob demanda.</span><span class="sxs-lookup"><span data-stu-id="97303-211">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

```fsharp
t.AddMembersDelayed(fun () -> 
  let nestedType = ProvidedTypeDefinition("NestedType", Some typeof<obj>)

  nestedType.AddMembersDelayed (fun () -> 
    let staticPropsInNestedType = 
      [ for i in 1 .. 100 do
          let valueOfTheProperty = "I am string "  + string i

          let p = 
            ProvidedProperty(propertyName = "StaticProperty" + string i, 
              propertyType = typeof<string>, 
              isStatic = true,
              getterCode= (fun args -> <@@ valueOfTheProperty @@>))

          p.AddXmlDocDelayed(fun () -> 
              sprintf "This is StaticProperty%d on NestedType" i)

          yield p ]

    staticPropsInNestedType)

  [nestedType])
```

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="97303-212">Detalhes sobre os tipos fornecidos apagados</span><span class="sxs-lookup"><span data-stu-id="97303-212">Details about Erased Provided Types</span></span>

<span data-ttu-id="97303-213">O exemplo nesta seção só fornece *apagados tipos fornecidos*, que são particularmente úteis nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="97303-213">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="97303-214">Quando você estiver escrevendo um provedor para um espaço de informações que contém somente dados e métodos.</span><span class="sxs-lookup"><span data-stu-id="97303-214">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="97303-215">Quando você estiver escrevendo um provedor de onde a semântica de tipo de tempo de execução precisa não é essencial para o uso prático do espaço de informações.</span><span class="sxs-lookup"><span data-stu-id="97303-215">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="97303-216">Quando você estiver escrevendo um provedor para um espaço de informações é tão grande e interconectados que não é tecnicamente possível gerar tipos reais do .NET para o espaço de informações.</span><span class="sxs-lookup"><span data-stu-id="97303-216">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="97303-217">Neste exemplo, cada um fornecido tipo for apagado para digitar `obj`, e todos os usos do tipo serão exibido como tipo `obj` no código compilado.</span><span class="sxs-lookup"><span data-stu-id="97303-217">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="97303-218">Na verdade, os objetos subjacentes nesses exemplos são cadeias de caracteres, mas o tipo será exibido como `System.Object` no .NET de código compilado.</span><span class="sxs-lookup"><span data-stu-id="97303-218">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="97303-219">Como com todos os usos de eliminação de tipo, você pode usar a conversão boxing explícita, conversão unboxing e de conversão subverter apagados tipos.</span><span class="sxs-lookup"><span data-stu-id="97303-219">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="97303-220">Nesse caso, uma exceção de conversão não é válida pode resultar quando o objeto é usado.</span><span class="sxs-lookup"><span data-stu-id="97303-220">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="97303-221">Um provedor de tempo de execução pode definir seu próprio tipo de representação privada para se proteger contra representações falsos.</span><span class="sxs-lookup"><span data-stu-id="97303-221">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="97303-222">Você não pode definir tipos apagados em F # em si.</span><span class="sxs-lookup"><span data-stu-id="97303-222">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="97303-223">Somente os tipos fornecidos podem ser apagados.</span><span class="sxs-lookup"><span data-stu-id="97303-223">Only provided types may be erased.</span></span> <span data-ttu-id="97303-224">Você deve compreender as ramificações, ambos os práticos e apagado tipos apagados para seu provedor de tipo ou um provedor que fornece semântica, usando um tipos.</span><span class="sxs-lookup"><span data-stu-id="97303-224">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="97303-225">Um tipo apagado não tem nenhum tipo .NET real.</span><span class="sxs-lookup"><span data-stu-id="97303-225">An erased type has no real .NET type.</span></span> <span data-ttu-id="97303-226">Portanto, não é possível fazer o reflexo preciso sobre o tipo e você pode subverter tipos apagados se você usar conversões de tempo de execução e outras técnicas que dependem de semântica de tipo de tempo de execução exato.</span><span class="sxs-lookup"><span data-stu-id="97303-226">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="97303-227">O Subversion dos tipos apagados frequentemente resulta em exceções de conversão de tipo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="97303-227">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>

### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="97303-228">Escolher representações para apagados tipos fornecidos</span><span class="sxs-lookup"><span data-stu-id="97303-228">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="97303-229">Para alguns usos de tipos fornecidos apagados, nenhuma representação é necessária.</span><span class="sxs-lookup"><span data-stu-id="97303-229">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="97303-230">Por exemplo, o apagados fornecido tipo pode conter somente propriedades estáticas e membros e nenhum construtor, e não há métodos ou propriedades retornaria uma instância do tipo.</span><span class="sxs-lookup"><span data-stu-id="97303-230">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="97303-231">Se você pode acessar instâncias de um apagados fornecido do tipo, você deve considerar as seguintes perguntas:</span><span class="sxs-lookup"><span data-stu-id="97303-231">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="97303-232">**O que é a eliminação de um tipo fornecido?**</span><span class="sxs-lookup"><span data-stu-id="97303-232">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="97303-233">A eliminação de um tipo fornecido é como o tipo é exibido no código compilado do .NET.</span><span class="sxs-lookup"><span data-stu-id="97303-233">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="97303-234">A remoção de um tipo de classe apagados fornecida é sempre o primeiro não apagados tipo base da cadeia de herança do tipo.</span><span class="sxs-lookup"><span data-stu-id="97303-234">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="97303-235">A remoção de um tipo de interface apagados fornecida é sempre `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="97303-235">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="97303-236">**Quais são as representações de um tipo fornecido?**</span><span class="sxs-lookup"><span data-stu-id="97303-236">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="97303-237">O conjunto de objetos possíveis para um apagados fornecido do tipo são chamados de suas representações.</span><span class="sxs-lookup"><span data-stu-id="97303-237">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="97303-238">O exemplo neste documento, as representações de todos os fornecidos a apagados tipos `Type1..Type100` sempre são objetos de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="97303-238">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="97303-239">Todas as representações de um tipo fornecido devem ser compatíveis com a eliminação de tipo fornecido.</span><span class="sxs-lookup"><span data-stu-id="97303-239">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="97303-240">(Caso contrário, o compilador F # fornecerá um erro para uso do provedor de tipos, ou será gerado um código .NET não verificável que não é válido.</span><span class="sxs-lookup"><span data-stu-id="97303-240">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="97303-241">Um provedor de tipo não é válido se ele retorna o código que fornece uma representação que não é válida.)</span><span class="sxs-lookup"><span data-stu-id="97303-241">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="97303-242">Você pode escolher uma representação para objetos fornecidos usando qualquer uma das abordagens a seguir, que são muito comuns:</span><span class="sxs-lookup"><span data-stu-id="97303-242">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="97303-243">Se você simplesmente fornece um wrapper fortemente tipado sobre um tipo .NET existente, geralmente faz sentido para seu tipo apagar a esse tipo, use instâncias desse tipo como representações, ou ambos.</span><span class="sxs-lookup"><span data-stu-id="97303-243">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="97303-244">Essa abordagem é apropriada quando a maioria dos métodos existentes nesse tipo ainda faz sentido ao usar a versão fortemente tipada.</span><span class="sxs-lookup"><span data-stu-id="97303-244">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="97303-245">Se você quiser criar uma API que difere significativamente, de qualquer API existente do .NET, faz sentido criar tipos de tempo de execução que serão a eliminação de tipo e representações para os tipos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="97303-245">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="97303-246">O exemplo neste documento usa cadeias de caracteres como representações dos objetos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="97303-246">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="97303-247">Com frequência, pode ser apropriado para usar outros objetos para representações.</span><span class="sxs-lookup"><span data-stu-id="97303-247">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="97303-248">Por exemplo, você pode usar um dicionário como um recipiente de propriedades:</span><span class="sxs-lookup"><span data-stu-id="97303-248">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="97303-249">Como alternativa, você pode definir um tipo em seu provedor de tipo que será usado em tempo de execução para formar a representação, juntamente com uma ou mais operações de tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="97303-249">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="97303-250">Membros fornecidos, em seguida, podem construir instâncias desse tipo de objeto:</span><span class="sxs-lookup"><span data-stu-id="97303-250">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="97303-251">Nesse caso, você pode (opcionalmente) usar esse tipo como a eliminação de tipo ao especificar esse tipo como o `baseType` ao construir o `ProvidedTypeDefinition`:</span><span class="sxs-lookup"><span data-stu-id="97303-251">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="97303-252">Principais lições</span><span class="sxs-lookup"><span data-stu-id="97303-252">Key Lessons</span></span>

<span data-ttu-id="97303-253">A seção anterior explicou como criar um provedor de tipo de apagamento simples que fornece uma variedade de tipos, propriedades e métodos.</span><span class="sxs-lookup"><span data-stu-id="97303-253">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="97303-254">Esta seção também explicou o conceito de eliminação de tipo, incluindo algumas das vantagens e desvantagens do fornecimento de tipos apagados de um provedor de tipo e discutido representações de tipos apagados.</span><span class="sxs-lookup"><span data-stu-id="97303-254">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>

## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="97303-255">Um provedor de tipo que usa parâmetros estáticos</span><span class="sxs-lookup"><span data-stu-id="97303-255">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="97303-256">A capacidade de parametrizar os provedores de tipos por dados estáticos permite muitos cenários interessantes, até mesmo em casos em que o provedor não precisa acessar os dados locais ou remotos.</span><span class="sxs-lookup"><span data-stu-id="97303-256">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="97303-257">Nesta seção, você aprenderá algumas técnicas básicas para reunir-se de que esse provedor.</span><span class="sxs-lookup"><span data-stu-id="97303-257">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>

### <a name="type-checked-regex-provider"></a><span data-ttu-id="97303-258">Tipo verificado provedor Regex</span><span class="sxs-lookup"><span data-stu-id="97303-258">Type Checked Regex Provider</span></span>

<span data-ttu-id="97303-259">Imagine que você deseja implementar um provedor de tipo para expressões regulares que encapsula o .NET <xref:System.Text.RegularExpressions.Regex> bibliotecas em uma interface que fornece as seguintes garantias de tempo de compilação:</span><span class="sxs-lookup"><span data-stu-id="97303-259">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="97303-260">Verificando se uma expressão regular é válida.</span><span class="sxs-lookup"><span data-stu-id="97303-260">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="97303-261">Fornecendo propriedades nomeadas em correspondências com base em quaisquer nomes de grupo na expressão regular.</span><span class="sxs-lookup"><span data-stu-id="97303-261">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="97303-262">Esta seção mostra como usar provedores de tipos para criar um `RegexTyped` de tipo que o padrão de expressão regular parametriza para fornecer esses benefícios.</span><span class="sxs-lookup"><span data-stu-id="97303-262">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="97303-263">O compilador relatará um erro se o padrão fornecido não é válido e o provedor de tipos pode extrair os grupos do padrão para que você pode acessá-los por meio de propriedades em correspondências nomeadas.</span><span class="sxs-lookup"><span data-stu-id="97303-263">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="97303-264">Quando você cria um provedor de tipos, você deve considerar deve ser a aparência de sua API exposta aos usuários finais e como esse design se traduzirá em código .NET.</span><span class="sxs-lookup"><span data-stu-id="97303-264">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="97303-265">O exemplo a seguir mostra como usar uma API desse tipo para obter os componentes do código de área:</span><span class="sxs-lookup"><span data-stu-id="97303-265">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="97303-266">O exemplo a seguir mostra como o provedor de tipo traduz essas chamadas:</span><span class="sxs-lookup"><span data-stu-id="97303-266">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="97303-267">Observe os seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="97303-267">Note the following points:</span></span>

- <span data-ttu-id="97303-268">O tipo padrão de Regex representa com parâmetros `RegexTyped` tipo.</span><span class="sxs-lookup"><span data-stu-id="97303-268">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="97303-269">O `RegexTyped` construtor resulta em uma chamada para o construtor de Regex, passando o argumento de tipo estático para o padrão.</span><span class="sxs-lookup"><span data-stu-id="97303-269">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="97303-270">Os resultados do `Match` método são representados pelo padrão <xref:System.Text.RegularExpressions.Match> tipo.</span><span class="sxs-lookup"><span data-stu-id="97303-270">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="97303-271">Cada grupo nomeado resulta em uma propriedade fornecida e acessar a propriedade resulta em um uso de um indexador em uma correspondência `Groups` coleção.</span><span class="sxs-lookup"><span data-stu-id="97303-271">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="97303-272">O código a seguir é o núcleo da lógica para implementar esse provedor, e este exemplo omite a adição de todos os membros para o tipo fornecido.</span><span class="sxs-lookup"><span data-stu-id="97303-272">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="97303-273">Para obter informações sobre cada membro adicionado, consulte a seção apropriada mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="97303-273">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="97303-274">Para o código completo, baixe o exemplo do [pacote de exemplo do F # 3.0](https://fsharp3sample.codeplex.com) no site da Codeplex.</span><span class="sxs-lookup"><span data-stu-id="97303-274">For the full code, download the sample from the [F# 3.0 Sample Pack](https://fsharp3sample.codeplex.com) on the Codeplex website.</span></span>

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams, 
        instantiationFunction=(fun typeName parameterValues ->

          match parameterValues with 
          | [| :? string as pattern|] -> 

            // Create an instance of the regular expression. 
            //
            // This will fail with System.ArgumentException if the regular expression is not valid. 
            // The exception will escape the type provider and be reported in client code.
            let r = System.Text.RegularExpressions.Regex(pattern)            

            // Declare the typed regex provided type.
            // The type erasure of this type is 'obj', even though the representation will always be a Regex
            // This, combined with hiding the object methods, makes the IntelliSense experience simpler.
            let ty = 
              ProvidedTypeDefinition(
                thisAssembly, 
                rootNamespace, 
                typeName, 
                baseType = Some baseTy)

            ...

            ty
          | _ -> failwith "unexpected parameter values")) 

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

<span data-ttu-id="97303-275">Observe os seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="97303-275">Note the following points:</span></span>

- <span data-ttu-id="97303-276">O provedor de tipo leva dois parâmetros estáticos: o `pattern`, que é obrigatório e o `options`, quais são opcionais (porque um valor padrão é fornecido).</span><span class="sxs-lookup"><span data-stu-id="97303-276">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="97303-277">Depois que os argumentos estáticos são fornecidos, você cria uma instância da expressão regular.</span><span class="sxs-lookup"><span data-stu-id="97303-277">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="97303-278">Esta instância lançará uma exceção se a expressão regular está malformada e esse erro será relatado para os usuários.</span><span class="sxs-lookup"><span data-stu-id="97303-278">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="97303-279">Dentro de `DefineStaticParameters` retorno de chamada, você define o tipo que será retornado depois que os argumentos são fornecidos.</span><span class="sxs-lookup"><span data-stu-id="97303-279">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="97303-280">Esse código define `HideObjectMethods` como true para que a experiência de IntelliSense permanecerá simplificada.</span><span class="sxs-lookup"><span data-stu-id="97303-280">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="97303-281">Esse atributo faz com que o `Equals`, `GetHashCode`, `Finalize`, e `GetType` membros a serem suprimidos nas listas de IntelliSense para um objeto fornecido.</span><span class="sxs-lookup"><span data-stu-id="97303-281">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="97303-282">Você usa `obj` como o tipo base do método, mas você usará um `Regex` objeto como a representação de tempo de execução desse tipo, como a exemplo a seguir mostra.</span><span class="sxs-lookup"><span data-stu-id="97303-282">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="97303-283">A chamada para o `Regex` construtor lança um <xref:System.ArgumentException> quando uma expressão regular não é válida.</span><span class="sxs-lookup"><span data-stu-id="97303-283">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="97303-284">O compilador captura essa exceção e relata uma mensagem de erro para o usuário em tempo de compilação ou no editor do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="97303-284">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="97303-285">Essa exceção permite que as expressões regulares a ser validado sem executar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="97303-285">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="97303-286">O tipo definido acima ainda não está útil porque ele não contém todos os métodos significativos ou propriedades.</span><span class="sxs-lookup"><span data-stu-id="97303-286">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="97303-287">Primeiro, adicione um estático `IsMatch` método:</span><span class="sxs-lookup"><span data-stu-id="97303-287">First, add a static `IsMatch` method:</span></span>

```fsharp
let isMatch = 
    ProvidedMethod(
        methodName = "IsMatch", 
        parameters = [ProvidedParameter("input", typeof<string>)], 
        returnType = typeof<bool>, 
        isStatic = true,
        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>) 

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string." 
ty.AddMember isMatch
```

<span data-ttu-id="97303-288">O código anterior define um método `IsMatch`, que usa uma cadeia de caracteres como entrada e retorna um `bool`.</span><span class="sxs-lookup"><span data-stu-id="97303-288">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="97303-289">A única parte difícil é o uso do `args` argumento dentro de `InvokeCode` definição.</span><span class="sxs-lookup"><span data-stu-id="97303-289">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="97303-290">Neste exemplo, `args` é uma lista de cotações que representa os argumentos para esse método.</span><span class="sxs-lookup"><span data-stu-id="97303-290">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="97303-291">Se o método é um método de instância, o primeiro argumento representa o `this` argumento.</span><span class="sxs-lookup"><span data-stu-id="97303-291">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="97303-292">No entanto, para um método estático, os argumentos são apenas os argumentos explícitos ao método.</span><span class="sxs-lookup"><span data-stu-id="97303-292">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="97303-293">Observe que o tipo do valor entre aspas deve corresponder ao tipo de retorno especificado (nesse caso, `bool`).</span><span class="sxs-lookup"><span data-stu-id="97303-293">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="97303-294">Observe também que esse código usa o `AddXmlDoc` método para certificar-se de que o método fornecido também possui documentação útil que você pode fornecer por meio do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="97303-294">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="97303-295">Em seguida, adicione um método de correspondência de instância.</span><span class="sxs-lookup"><span data-stu-id="97303-295">Next, add an instance Match method.</span></span> <span data-ttu-id="97303-296">No entanto, esse método deve retornar um valor de fornecido `Match` tipo de forma que os grupos podem ser acessados de uma maneira fortemente tipada.</span><span class="sxs-lookup"><span data-stu-id="97303-296">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="97303-297">Portanto, você deve primeiramente declarar o `Match` tipo.</span><span class="sxs-lookup"><span data-stu-id="97303-297">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="97303-298">Porque esse tipo depende do padrão que foi fornecido como um argumento estático, esse tipo deve ser aninhado dentro da definição de tipo parametrizado:</span><span class="sxs-lookup"><span data-stu-id="97303-298">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy = 
    ProvidedTypeDefinition(
        "MatchType", 
        baseType = Some baseTy, 
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="97303-299">Você, em seguida, adicione uma propriedade para o tipo de correspondência para cada grupo.</span><span class="sxs-lookup"><span data-stu-id="97303-299">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="97303-300">Em tempo de execução, uma correspondência é representada como uma <xref:System.Text.RegularExpressions.Match> de valor, portanto, as aspas que define a propriedade devem usar o <xref:System.Text.RegularExpressions.Match.Groups> indexado de propriedade para obter o grupo relevante.</span><span class="sxs-lookup"><span data-stu-id="97303-300">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

```fsharp
for group in r.GetGroupNames() do
    // Ignore the group named 0, which represents all input.
    if group <> "0" then
    let prop = 
      ProvidedProperty(
        propertyName = group, 
        propertyType = typeof<Group>, 
        getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
        prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
    matchTy.AddMember prop
```

<span data-ttu-id="97303-301">Novamente, observe que você está adicionando documentação XML a propriedade fornecida.</span><span class="sxs-lookup"><span data-stu-id="97303-301">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="97303-302">Observe também que uma propriedade pode ser lidos se um `GetterCode` função é fornecida, e a propriedade pode ser escrita se um `SetterCode` função for fornecida, portanto, a propriedade resultante é somente leitura.</span><span class="sxs-lookup"><span data-stu-id="97303-302">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="97303-303">Agora você pode criar um método de instância que retorna um valor deste `Match` tipo:</span><span class="sxs-lookup"><span data-stu-id="97303-303">Now you can create an instance method that returns a value of this `Match` type:</span></span>

```fsharp
let matchMethod = 
    ProvidedMethod(
        methodName = "Match", 
        parameters = [ProvidedParameter("input", typeof<string>)], 
        returnType = matchTy, 
        invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)

matchMeth.AddXmlDoc "Searches the specified input string for the first ocurrence of this regular expression" 

ty.AddMember matchMeth
```

<span data-ttu-id="97303-304">Porque você está criando um método de instância `args.[0]` representa o `RegexTyped` instância na qual o método está sendo chamado, e `args.[1]` é o argumento de entrada.</span><span class="sxs-lookup"><span data-stu-id="97303-304">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="97303-305">Por fim, fornece um construtor para que a instância do tipo fornecido pode ser criada.</span><span class="sxs-lookup"><span data-stu-id="97303-305">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor = 
    ProvidedConstructor(
        parameters = [], 
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="97303-306">O construtor simplesmente apaga à criação de uma instância de Regex do .NET standard, que é convertida novamente para um objeto porque `obj` é a eliminação de tipo fornecido.</span><span class="sxs-lookup"><span data-stu-id="97303-306">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="97303-307">Com essa alteração, o exemplo de uso de API que especificou anteriormente no tópico funciona conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="97303-307">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="97303-308">O código a seguir é concluída e final:</span><span class="sxs-lookup"><span data-stu-id="97303-308">The following code is complete and final:</span></span>

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types.
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams, 
        instantiationFunction=(fun typeName parameterValues ->

            match parameterValues with 
            | [| :? string as pattern|] -> 

                // Create an instance of the regular expression. 

                let r = System.Text.RegularExpressions.Regex(pattern)            

                // Declare the typed regex provided type.

                let ty = 
                    ProvidedTypeDefinition(
                        thisAssembly, 
                        rootNamespace, 
                        typeName, 
                        baseType = Some baseTy)

                ty.AddXmlDoc "A strongly typed interface to the regular expression '%s'"

                // Provide strongly typed version of Regex.IsMatch static method.
                let isMatch = 
                    ProvidedMethod(
                        methodName = "IsMatch", 
                        parameters = [ProvidedParameter("input", typeof<string>)], 
                        returnType = typeof<bool>, 
                        isStatic = true,
                        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>) 

                isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string"

                ty.AddMember isMatch

                // Provided type for matches
                // Again, erase to obj even though the representation will always be a Match
                let matchTy = 
                    ProvidedTypeDefinition(
                        "MatchType", 
                        baseType = Some baseTy, 
                        hideObjectMethods = true)

                // Nest the match type within parameterized Regex type.
                ty.AddMember matchTy

                // Add group properties to match type
                for group in r.GetGroupNames() do
                    // Ignore the group named 0, which represents all input.
                    if group <> "0" then
                        let prop = 
                          ProvidedProperty(
                            propertyName = group, 
                            propertyType = typeof<Group>, 
                            getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
                        prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
                        matchTy.AddMember(prop)

                // Provide strongly typed version of Regex.Match instance method.
                let matchMeth = 
                  ProvidedMethod(
                    methodName = "Match", 
                    parameters = [ProvidedParameter("input", typeof<string>)], 
                    returnType = matchTy, 
                    invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
                matchMeth.AddXmlDoc "Searches the specified input string for the first occurence of this regular expression"

                ty.AddMember matchMeth

                // Declare a constructor.
                let ctor = 
                  ProvidedConstructor(
                    parameters = [], 
                    invokeCode = fun args -> <@@ Regex(pattern) :> obj @@>)

                // Add documentation to the constructor.
                ctor.AddXmlDoc "Initializes a regular expression instance"

                ty.AddMember ctor

                ty
            | _ -> failwith "unexpected parameter values")) 

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

### <a name="key-lessons"></a><span data-ttu-id="97303-309">Principais lições</span><span class="sxs-lookup"><span data-stu-id="97303-309">Key Lessons</span></span>

<span data-ttu-id="97303-310">Esta seção explicou como criar um provedor de tipos que opera em seus parâmetros estáticos.</span><span class="sxs-lookup"><span data-stu-id="97303-310">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="97303-311">O provedor verifica o parâmetro static e fornece operações com base em seu valor.</span><span class="sxs-lookup"><span data-stu-id="97303-311">The provider checks the static parameter and provides operations based on its value.</span></span>

## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="97303-312">Um provedor de tipo que é apoiado por dados locais</span><span class="sxs-lookup"><span data-stu-id="97303-312">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="97303-313">Com frequência, convém provedores de tipos para apresentar as APIs com base em não apenas parâmetros estáticos, mas também informações de sistemas locais ou remotos.</span><span class="sxs-lookup"><span data-stu-id="97303-313">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="97303-314">Esta seção discute os provedores de tipos se baseiam em dados locais, como arquivos de dados local.</span><span class="sxs-lookup"><span data-stu-id="97303-314">This section discusses type providers that are based on local data, such as local data files.</span></span>

### <a name="simple-csv-file-provider"></a><span data-ttu-id="97303-315">Provedor de arquivo CSV simples</span><span class="sxs-lookup"><span data-stu-id="97303-315">Simple CSV File Provider</span></span>

<span data-ttu-id="97303-316">Como um exemplo simples, considere um provedor de tipos para acessar dados científicos; dados no formato de valor separados por vírgulas (CSV).</span><span class="sxs-lookup"><span data-stu-id="97303-316">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="97303-317">Esta seção pressupõe que os arquivos CSV contêm uma linha de cabeçalho seguida pelos dados de ponto flutuante, como mostra a tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="97303-317">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>

|<span data-ttu-id="97303-318">Distância (medidor)</span><span class="sxs-lookup"><span data-stu-id="97303-318">Distance (meter)</span></span>|<span data-ttu-id="97303-319">Tempo (segundos)</span><span class="sxs-lookup"><span data-stu-id="97303-319">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="97303-320">50.0</span><span class="sxs-lookup"><span data-stu-id="97303-320">50.0</span></span>|<span data-ttu-id="97303-321">3.7</span><span class="sxs-lookup"><span data-stu-id="97303-321">3.7</span></span>|
|<span data-ttu-id="97303-322">100.0</span><span class="sxs-lookup"><span data-stu-id="97303-322">100.0</span></span>|<span data-ttu-id="97303-323">5.2</span><span class="sxs-lookup"><span data-stu-id="97303-323">5.2</span></span>|
|<span data-ttu-id="97303-324">150.0</span><span class="sxs-lookup"><span data-stu-id="97303-324">150.0</span></span>|<span data-ttu-id="97303-325">6.4</span><span class="sxs-lookup"><span data-stu-id="97303-325">6.4</span></span>|

<span data-ttu-id="97303-326">Esta seção mostra como fornecer um tipo que você pode usar para obter linhas com um `Distance` propriedade do tipo `float<meter>` e uma `Time` propriedade do tipo `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="97303-326">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="97303-327">Para simplificar, as seguintes suposições são feitas:</span><span class="sxs-lookup"><span data-stu-id="97303-327">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="97303-328">Nomes de cabeçalho são menos de unidade ou têm o formato "Nome (unidade)" e não contêm vírgulas.</span><span class="sxs-lookup"><span data-stu-id="97303-328">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="97303-329">As unidades são todas as unidades de Systeme internacional (SI) como o [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames módulo (F #)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) módulo define.</span><span class="sxs-lookup"><span data-stu-id="97303-329">Units are all Systeme International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="97303-330">As unidades são tudo simples (por exemplo, medidor) em vez de compostos (por exemplo, medidor/segundo).</span><span class="sxs-lookup"><span data-stu-id="97303-330">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="97303-331">Todas as colunas contêm dados de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="97303-331">All columns contain floating point data.</span></span>

<span data-ttu-id="97303-332">Um provedor mais completo seria solte essas restrições.</span><span class="sxs-lookup"><span data-stu-id="97303-332">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="97303-333">Novamente, a primeira etapa é considerar como a API deve ser.</span><span class="sxs-lookup"><span data-stu-id="97303-333">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="97303-334">Dado um `info.csv` arquivo com o conteúdo da tabela anterior (em formato separado por vírgula), os usuários do provedor devem ser capazes de gravar o código semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="97303-334">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="97303-335">Nesse caso, o compilador deve converter essas chamadas em algo semelhante ao seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="97303-335">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="97303-336">A tradução ideal exigirá o provedor de tipo para definir um real `CsvFile` tipo no assembly do provedor de tipo.</span><span class="sxs-lookup"><span data-stu-id="97303-336">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="97303-337">Provedores de tipos geralmente dependem de alguns tipos auxiliares e métodos para encapsular a lógica importante.</span><span class="sxs-lookup"><span data-stu-id="97303-337">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="97303-338">Como as medidas são apagadas em tempo de execução, você pode usar um `float[]` como o tipo apagado para uma linha.</span><span class="sxs-lookup"><span data-stu-id="97303-338">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="97303-339">O compilador tratará colunas diferentes têm tipos diferentes de medida.</span><span class="sxs-lookup"><span data-stu-id="97303-339">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="97303-340">Por exemplo, a primeira coluna em nosso exemplo tem o tipo `float<meter>`, e o segundo tem `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="97303-340">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="97303-341">No entanto, a representação apagada pode permanecer bastante simple.</span><span class="sxs-lookup"><span data-stu-id="97303-341">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="97303-342">O código a seguir mostra o núcleo da implementação.</span><span class="sxs-lookup"><span data-stu-id="97303-342">The following code shows the core of the implementation.</span></span>

```fsharp
// Simple type wrapping CSV data
type CsvFile(filename) =
    // Cache the sequence of all data lines (all lines but the first)
    let data = 
        seq { for line in File.ReadAllLines(filename) |> Seq.skip 1 do
                 yield line.Split(',') |> Array.map float }
        |> Seq.cache
    member __.Data = data

[<TypeProvider>]
type public MiniCsvProvider(cfg:TypeProviderConfig) as this =
    inherit TypeProviderForNamespaces(cfg)

    // Get the assembly and namespace used to house the provided types.
    let asm = System.Reflection.Assembly.GetExecutingAssembly()
    let ns = "Samples.FSharp.MiniCsvProvider"

    // Create the main provided type.
    let csvTy = ProvidedTypeDefinition(asm, ns, "MiniCsv", Some(typeof<obj>))

    // Parameterize the type by the file to use as a template.
    let filename = ProvidedStaticParameter("filename", typeof<string>)
    do csvTy.DefineStaticParameters([filename], fun tyName [| :? string as filename |] ->
    
        // Resolve the filename relative to the resolution folder.
        let resolvedFilename = Path.Combine(cfg.ResolutionFolder, filename)

        // Get the first line from the file.
        let headerLine = File.ReadLines(resolvedFilename) |> Seq.head

        // Define a provided type for each row, erasing to a float[].
        let rowTy = ProvidedTypeDefinition("Row", Some(typeof<float[]>))

        // Extract header names from the file, splitting on commas.
        // use Regex matching to get the position in the row at which the field occurs
        let headers = Regex.Matches(headerLine, "[^,]+")

        // Add one property per CSV field.
        for i in 0 .. headers.Count - 1 do
            let headerText = headers.[i].Value

            // Try to decompose this header into a name and unit.
            let fieldName, fieldTy =
                let m = Regex.Match(headerText, @"(?<field>.+) \((?<unit>.+)\)")
                if m.Success then

                    let unitName = m.Groups.["unit"].Value
                    let units = ProvidedMeasureBuilder.Default.SI unitName
                    m.Groups.["field"].Value, ProvidedMeasureBuilder.Default.AnnotateType(typeof<float>,[units])

                else
                    // no units, just treat it as a normal float
                    headerText, typeof<float>

            let prop = 
                ProvidedProperty(fieldName, fieldTy, 
                    getterCode = fun [row] -> <@@ (%%row:float[]).[i] @@>)

            // Add metadata that defines the property's location in the referenced file.
            prop.AddDefinitionLocation(1, headers.[i].Index + 1, filename)
            rowTy.AddMember(prop) 

        // Define the provided type, erasing to CsvFile.
        let ty = ProvidedTypeDefinition(asm, ns, tyName, Some(typeof<CsvFile>))

        // Add a parameterless constructor that loads the file that was used to define the schema.
        let ctor0 = 
            ProvidedConstructor([], 
                invokeCode = fun [] -> <@@ CsvFile(resolvedFilename) @@>)
        ty.AddMember ctor0

        // Add a constructor that takes the file name to load.
        let ctor1 = ProvidedConstructor([ProvidedParameter("filename", typeof<string>)], 
            invokeCode = fun [filename] -> <@@ CsvFile(%%filename) @@>)
        ty.AddMember ctor1

        // Add a more strongly typed Data property, which uses the existing property at runtime.
        let prop = 
            ProvidedProperty("Data", typedefof<seq<_>>.MakeGenericType(rowTy), 
                getterCode = fun [csvFile] -> <@@ (%%csvFile:CsvFile).Data @@>)
        ty.AddMember prop

        // Add the row type as a nested type.
        ty.AddMember rowTy
        ty)

    // Add the type to the namespace.
    do this.AddNamespace(ns, [csvTy])
```

<span data-ttu-id="97303-343">Observe os seguintes pontos sobre a implementação:</span><span class="sxs-lookup"><span data-stu-id="97303-343">Note the following points about the implementation:</span></span>

- <span data-ttu-id="97303-344">Construtores sobrecarregados permitem que o arquivo original ou um que tenha um esquema idêntico a serem lidos.</span><span class="sxs-lookup"><span data-stu-id="97303-344">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="97303-345">Esse padrão é comum quando você escrever um provedor de tipo para fontes de dados local ou remoto e esse padrão permite que um arquivo local a ser usado como modelo para dados remotos.</span><span class="sxs-lookup"><span data-stu-id="97303-345">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="97303-346">Você pode usar o [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) valor que é passado para o construtor de tipo de provedor para resolver nomes de arquivo relativos.</span><span class="sxs-lookup"><span data-stu-id="97303-346">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="97303-347">Você pode usar o `AddDefinitionLocation` método para definir o local das propriedades fornecidas.</span><span class="sxs-lookup"><span data-stu-id="97303-347">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="97303-348">Portanto, se você usar `Go To Definition` em uma propriedade fornecida, o arquivo CSV será aberto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="97303-348">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="97303-349">Você pode usar o `ProvidedMeasureBuilder` digite para pesquisar as unidades de SI e para gerar o relevantes `float<_>` tipos.</span><span class="sxs-lookup"><span data-stu-id="97303-349">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="97303-350">Principais lições</span><span class="sxs-lookup"><span data-stu-id="97303-350">Key Lessons</span></span>

<span data-ttu-id="97303-351">Esta seção explicou como criar um provedor de tipo para uma fonte de dados local com um esquema simples que está contido na fonte de dados em si.</span><span class="sxs-lookup"><span data-stu-id="97303-351">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>

## <a name="going-further"></a><span data-ttu-id="97303-352">Indo mais além</span><span class="sxs-lookup"><span data-stu-id="97303-352">Going Further</span></span>

<span data-ttu-id="97303-353">As seções a seguir incluem sugestões para estudar em mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="97303-353">The following sections include suggestions for further study.</span></span>

### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="97303-354">Examinar o código compilado para tipos apagados</span><span class="sxs-lookup"><span data-stu-id="97303-354">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="97303-355">Para dar uma ideia de como o uso do provedor de tipo corresponde ao código que é emitido, examine a seguinte função usando o `HelloWorldTypeProvider` que é usado no início deste tópico.</span><span class="sxs-lookup"><span data-stu-id="97303-355">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () = 
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="97303-356">Aqui está uma imagem do código descompilado usando ildasm.exe resultante:</span><span class="sxs-lookup"><span data-stu-id="97303-356">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

```
.class public abstract auto ansi sealed Module1
extends [mscorlib]System.Object
{
.custom instance void [FSharp.Core]Microsoft.FSharp.Core.CompilationMappingAtt
ribute::.ctor(valuetype [FSharp.Core]Microsoft.FSharp.Core.SourceConstructFlags)
= ( 01 00 07 00 00 00 00 00 )
.method public static int32  function1() cil managed
{
// Code size       24 (0x18)
.maxstack  3
.locals init ([0] object obj1)
IL_0000:  nop
IL_0001:  ldstr      "some data"
IL_0006:  unbox.any  [mscorlib]System.Object
IL_000b:  stloc.0
IL_000c:  ldloc.0
IL_000d:  call       !!0 [FSharp.Core_2]Microsoft.FSharp.Core.LanguagePrimit
ives/IntrinsicFunctions::UnboxGeneric<string>(object)
IL_0012:  callvirt   instance int32 [mscorlib_3]System.String::get_Length()
IL_0017:  ret
} // end of method Module1::function1

} // end of class Module1
```

<span data-ttu-id="97303-357">Como mostra o exemplo, todos os menções do tipo `Type1` e o `InstanceProperty` propriedade foram apagados, deixando apenas as operações nos tipos de tempo de execução envolvidos.</span><span class="sxs-lookup"><span data-stu-id="97303-357">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>

### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="97303-358">Design e convenções de nomenclatura para provedores de tipos</span><span class="sxs-lookup"><span data-stu-id="97303-358">Design and Naming Conventions for Type Providers</span></span>

<span data-ttu-id="97303-359">Observe as convenções a seguir ao criar provedores de tipos.</span><span class="sxs-lookup"><span data-stu-id="97303-359">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="97303-360">**Provedores para protocolos de conectividade** em geral, nomes de provedor a maioria das DLLs para protocolos de conectividade de dados e o serviço, como conexões do OData ou SQL, devem terminar com `TypeProvider` ou `TypeProviders`.</span><span class="sxs-lookup"><span data-stu-id="97303-360">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="97303-361">Por exemplo, use um nome DLL que se parece com a cadeia de caracteres a seguir:</span><span class="sxs-lookup"><span data-stu-id="97303-361">For example, use a DLL name that resembles the following string:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.dll
```

<span data-ttu-id="97303-362">Certifique-se de que seus tipos fornecidos são membros do namespace correspondente e indicam o protocolo de conectividade que você tiver implementado:</span><span class="sxs-lookup"><span data-stu-id="97303-362">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="97303-363">**Provedores de utilitário para codificação geral**.</span><span class="sxs-lookup"><span data-stu-id="97303-363">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="97303-364">Para um provedor de tipo de utilitário, como para expressões regulares, o provedor de tipo pode ser parte de uma biblioteca de base, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="97303-364">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
  #r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="97303-365">Nesse caso, o tipo fornecido apareceria em um ponto apropriado de acordo com as convenções normais de design do .NET:</span><span class="sxs-lookup"><span data-stu-id="97303-365">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped
  
  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="97303-366">**Fontes de dados singleton**.</span><span class="sxs-lookup"><span data-stu-id="97303-366">**Singleton Data Sources**.</span></span> <span data-ttu-id="97303-367">Alguns provedores de tipos se conectar a uma fonte de dados dedicado e fornecem apenas os dados.</span><span class="sxs-lookup"><span data-stu-id="97303-367">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="97303-368">Nesse caso, você deve descartar o `TypeProvider` sufixo e use normais convenções de nomenclatura do .NET:</span><span class="sxs-lookup"><span data-stu-id="97303-368">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"
  
let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="97303-369">Para obter mais informações, consulte o `GetConnection` projetar convenção que é descrita posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="97303-369">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>

### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="97303-370">Padrões de design para provedores de tipos</span><span class="sxs-lookup"><span data-stu-id="97303-370">Design Patterns for Type Providers</span></span>

<span data-ttu-id="97303-371">As seções a seguir descrevem padrões de design, que você pode usar ao criar provedores de tipos.</span><span class="sxs-lookup"><span data-stu-id="97303-371">The following sections describe design patterns you can use when authoring type providers.</span></span>

#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="97303-372">O padrão de Design GetConnection</span><span class="sxs-lookup"><span data-stu-id="97303-372">The GetConnection Design Pattern</span></span>

<span data-ttu-id="97303-373">A maioria dos provedores de tipo deve ser escrito para usar o `GetConnection` padrão que é usado pelos provedores de tipo em FSharp.Data.TypeProviders.dll, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="97303-373">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="97303-374">Provedores de tipos com suporte pelos serviços e dados remotos</span><span class="sxs-lookup"><span data-stu-id="97303-374">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="97303-375">Antes de criar um provedor de tipo que é apoiado por serviços e dados remotos, você deve considerar uma variedade de problemas inerentes à programação conectada.</span><span class="sxs-lookup"><span data-stu-id="97303-375">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="97303-376">Esses problemas incluem as seguintes considerações:</span><span class="sxs-lookup"><span data-stu-id="97303-376">These issues include the following considerations:</span></span>

- <span data-ttu-id="97303-377">mapeamento de esquema</span><span class="sxs-lookup"><span data-stu-id="97303-377">schema mapping</span></span>

- <span data-ttu-id="97303-378">alocação e a invalidação na presença de alteração de esquema</span><span class="sxs-lookup"><span data-stu-id="97303-378">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="97303-379">cache de esquemas</span><span class="sxs-lookup"><span data-stu-id="97303-379">schema caching</span></span>

- <span data-ttu-id="97303-380">implementações assíncronas de operações de acesso de dados</span><span class="sxs-lookup"><span data-stu-id="97303-380">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="97303-381">suporte a consultas, incluindo consultas LINQ</span><span class="sxs-lookup"><span data-stu-id="97303-381">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="97303-382">autenticação e credenciais</span><span class="sxs-lookup"><span data-stu-id="97303-382">credentials and authentication</span></span>

<span data-ttu-id="97303-383">Este tópico não explorar ainda mais esses problemas.</span><span class="sxs-lookup"><span data-stu-id="97303-383">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="97303-384">Técnicas de criação adicionais</span><span class="sxs-lookup"><span data-stu-id="97303-384">Additional Authoring Techniques</span></span>

<span data-ttu-id="97303-385">Quando você escrever seus próprios provedores de tipos, você talvez queira usar as seguintes técnicas adicionais.</span><span class="sxs-lookup"><span data-stu-id="97303-385">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="97303-386">Criação de tipos e membros sob demanda</span><span class="sxs-lookup"><span data-stu-id="97303-386">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="97303-387">A API ProvidedType adiou a versões do AddMember.</span><span class="sxs-lookup"><span data-stu-id="97303-387">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="97303-388">Essas versões são usadas para criar espaços de demanda de tipos.</span><span class="sxs-lookup"><span data-stu-id="97303-388">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="97303-389">Fornecendo instanciações de tipo genérico e tipos de matriz</span><span class="sxs-lookup"><span data-stu-id="97303-389">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="97303-390">Tornar membros fornecidos (cujas assinaturas incluem tipos de matriz e tipos byref instanciações de tipos genéricos) usando o vetor perpendicular `MakeArrayType`, `MakePointerType`, e `MakeGenericType` em qualquer instância do <xref:System.Type>, incluindo `ProvidedTypeDefinitions`.</span><span class="sxs-lookup"><span data-stu-id="97303-390">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="97303-391">Em alguns casos você talvez precise usar o auxiliar em `ProvidedTypeBuilder.MakeGenericType`.</span><span class="sxs-lookup"><span data-stu-id="97303-391">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="97303-392">Consulte a [documentação do SDK do provedor de tipo](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="97303-392">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="97303-393">Fornecendo a unidade de medida anotações</span><span class="sxs-lookup"><span data-stu-id="97303-393">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="97303-394">A API ProvidedTypes fornece auxiliares para fornecer anotações de medida.</span><span class="sxs-lookup"><span data-stu-id="97303-394">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="97303-395">Por exemplo, para fornecer o tipo `float<kg>`, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="97303-395">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="97303-396">Para fornecer o tipo `Nullable<decimal<kg/m^2>>`, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="97303-396">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="97303-397">Acessando recursos do projeto Local ou Local de Script</span><span class="sxs-lookup"><span data-stu-id="97303-397">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="97303-398">Cada instância de um provedor de tipo pode ser fornecida um `TypeProviderConfig` valor durante a construção.</span><span class="sxs-lookup"><span data-stu-id="97303-398">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="97303-399">Esse valor contém a pasta"Resolução" para o provedor (ou seja, a pasta de projeto para a compilação ou o diretório que contém um script), a lista de assemblies referenciados e outras informações.</span><span class="sxs-lookup"><span data-stu-id="97303-399">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="97303-400">Invalidação</span><span class="sxs-lookup"><span data-stu-id="97303-400">Invalidation</span></span>

<span data-ttu-id="97303-401">Provedores podem gerar sinais de invalidação para notificar o serviço de linguagem F # que as suposições de esquema podem ter sido alterado.</span><span class="sxs-lookup"><span data-stu-id="97303-401">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="97303-402">Quando ocorre a invalidação, um typecheck é refeito se o provedor está sendo hospedado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="97303-402">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="97303-403">Esse sinal será ignorada quando o provedor estiver hospedado em F # interativo ou pelo compilador F # (fsc.exe).</span><span class="sxs-lookup"><span data-stu-id="97303-403">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="97303-404">Armazenar em cache informações de esquema</span><span class="sxs-lookup"><span data-stu-id="97303-404">Caching Schema Information</span></span>

<span data-ttu-id="97303-405">Provedores devem armazenar em cache geralmente acesso às informações de esquema.</span><span class="sxs-lookup"><span data-stu-id="97303-405">Providers must often cache access to schema information.</span></span> <span data-ttu-id="97303-406">Os dados armazenados em cache devem ser armazenados usando um nome de arquivo que é fornecido como um parâmetro estático ou como dados de usuário.</span><span class="sxs-lookup"><span data-stu-id="97303-406">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="97303-407">Um exemplo de cache de esquema é o `LocalSchemaFile` os provedores de tipo no parâmetro o `FSharp.Data.TypeProviders` assembly.</span><span class="sxs-lookup"><span data-stu-id="97303-407">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="97303-408">Na implementação desses provedores, esse parâmetro estático instrui o provedor de tipo para usar as informações de esquema no arquivo local especificado em vez de acessar a fonte de dados pela rede.</span><span class="sxs-lookup"><span data-stu-id="97303-408">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="97303-409">Para usar as informações de esquema em cache, você também deve definir o parâmetro static `ForceUpdate` para `false`.</span><span class="sxs-lookup"><span data-stu-id="97303-409">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="97303-410">Você pode usar uma técnica semelhante para habilitar o acesso de dados online e offline.</span><span class="sxs-lookup"><span data-stu-id="97303-410">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="97303-411">Assembly de suporte</span><span class="sxs-lookup"><span data-stu-id="97303-411">Backing Assembly</span></span>

<span data-ttu-id="97303-412">Quando você compila um `.dll` ou `.exe` arquivo, o arquivo. dll de suporte para tipos gerados está vinculada estaticamente o assembly resultante.</span><span class="sxs-lookup"><span data-stu-id="97303-412">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="97303-413">Esse link é criado, copiando as definições de tipo de linguagem intermediária (IL) e todos os recursos gerenciados do conjunto de backup no assembly final.</span><span class="sxs-lookup"><span data-stu-id="97303-413">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="97303-414">Ao usar o F # interativo, o arquivo. dll de backup não sejam copiado e em vez disso, é carregado diretamente ao processo de F # interativo.</span><span class="sxs-lookup"><span data-stu-id="97303-414">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="97303-415">Exceções e diagnóstico de provedores de tipos</span><span class="sxs-lookup"><span data-stu-id="97303-415">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="97303-416">Todos os usos de todos os membros de tipos fornecidos podem lançar exceções.</span><span class="sxs-lookup"><span data-stu-id="97303-416">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="97303-417">Em todos os casos, se um provedor de tipos gera uma exceção, o compilador de host atributos o erro para um provedor de tipo específico.</span><span class="sxs-lookup"><span data-stu-id="97303-417">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="97303-418">Tipo de provedor exceções nunca deve resultar em erros internos do compilador.</span><span class="sxs-lookup"><span data-stu-id="97303-418">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="97303-419">Provedores de tipos não podem relatar avisos.</span><span class="sxs-lookup"><span data-stu-id="97303-419">Type providers can't report warnings.</span></span>

- <span data-ttu-id="97303-420">Quando um provedor de tipo é hospedado no compilador F #, um ambiente de desenvolvimento em F # ou F # interativo, todas as exceções do provedor são capturadas.</span><span class="sxs-lookup"><span data-stu-id="97303-420">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="97303-421">A propriedade de mensagem sempre é o texto de erro e nenhum rastreamento de pilha é exibida.</span><span class="sxs-lookup"><span data-stu-id="97303-421">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="97303-422">Se você pretende lançar uma exceção, você pode lançar os exemplos a seguir: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="97303-422">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="97303-423">Fornecimento de tipos gerados</span><span class="sxs-lookup"><span data-stu-id="97303-423">Providing Generated Types</span></span>

<span data-ttu-id="97303-424">Até agora, este documento explicou como fornecer tipos apagados.</span><span class="sxs-lookup"><span data-stu-id="97303-424">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="97303-425">Você também pode usar o mecanismo de provedor de tipo em F # para fornecer tipos gerados, que são adicionados como definições de tipo real do .NET no programa dos usuários.</span><span class="sxs-lookup"><span data-stu-id="97303-425">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="97303-426">Você deve se referir a gerado tipos fornecidos por meio de uma definição de tipo.</span><span class="sxs-lookup"><span data-stu-id="97303-426">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders 

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="97303-427">O código do auxiliar de 0,2 ProvidedTypes que faz parte da versão 3.0 do F # tem somente suporte limitado para fornecer tipos gerados.</span><span class="sxs-lookup"><span data-stu-id="97303-427">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="97303-428">As instruções a seguir devem ser verdadeiras para uma definição de tipo gerado:</span><span class="sxs-lookup"><span data-stu-id="97303-428">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="97303-429">`isErased` deve ser definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="97303-429">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="97303-430">O tipo gerado deve ser adicionado a um recentemente construído `ProvidedAssembly()`, que representa um contêiner para fragmentos de código gerado.</span><span class="sxs-lookup"><span data-stu-id="97303-430">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="97303-431">O provedor deve ter um assembly que tem um arquivo. dll do .NET de backup real com um arquivo. dll correspondente no disco.</span><span class="sxs-lookup"><span data-stu-id="97303-431">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>

## <a name="rules-and-limitations"></a><span data-ttu-id="97303-432">Regras e limitações</span><span class="sxs-lookup"><span data-stu-id="97303-432">Rules and Limitations</span></span>

<span data-ttu-id="97303-433">Quando você escrever provedores de tipos, tenha as seguintes regras e limitações em mente.</span><span class="sxs-lookup"><span data-stu-id="97303-433">When you write type providers, keep the following rules and limitations in mind.</span></span>

### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="97303-434">Tipos fornecidos devem ser acessíveis</span><span class="sxs-lookup"><span data-stu-id="97303-434">Provided types must be reachable</span></span>

<span data-ttu-id="97303-435">Todos fornecidos tipos devem ser acessíveis a partir de tipos não aninhadas.</span><span class="sxs-lookup"><span data-stu-id="97303-435">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="97303-436">Os tipos aninhados não são fornecidos na chamada para o `TypeProviderForNamespaces` construtor ou uma chamada para `AddNamespace`.</span><span class="sxs-lookup"><span data-stu-id="97303-436">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="97303-437">Por exemplo, se o provedor fornece um tipo `StaticClass.P : T`, você deve garantir que T é um tipo não aninhado ou aninhados em um.</span><span class="sxs-lookup"><span data-stu-id="97303-437">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="97303-438">Por exemplo, alguns provedores têm uma classe estática, como `DataTypes` que contêm esses `T1, T2, T3, ...` tipos.</span><span class="sxs-lookup"><span data-stu-id="97303-438">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="97303-439">Caso contrário, o erro afirma que uma referência ao tipo T em um assembly foi encontrada, mas não foi possível encontrar o tipo nesse assembly.</span><span class="sxs-lookup"><span data-stu-id="97303-439">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="97303-440">Se esse erro aparecer, verifique se todos os seus subtipos podem ser acessados entre os tipos de provedor.</span><span class="sxs-lookup"><span data-stu-id="97303-440">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="97303-441">Observação: Essas `T1, T2, T3...` tipos são chamados da *em interrupções* tipos.</span><span class="sxs-lookup"><span data-stu-id="97303-441">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="97303-442">Lembre-se de colocá-los em um namespace acessível ou um tipo de pai.</span><span class="sxs-lookup"><span data-stu-id="97303-442">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="97303-443">Limitações do mecanismo de provedor de tipo</span><span class="sxs-lookup"><span data-stu-id="97303-443">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="97303-444">O mecanismo de provedor de tipo em F # tem as seguintes limitações:</span><span class="sxs-lookup"><span data-stu-id="97303-444">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="97303-445">A infraestrutura subjacente para provedores de tipos em F # não oferece suporte fornecido genérico tipos ou fornecidos métodos genéricos.</span><span class="sxs-lookup"><span data-stu-id="97303-445">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="97303-446">O mecanismo não dá suporte a tipos aninhados com parâmetros estáticos.</span><span class="sxs-lookup"><span data-stu-id="97303-446">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="97303-447">Dicas de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="97303-447">Development Tips</span></span>

<span data-ttu-id="97303-448">Você pode achar as seguintes dicas úteis durante o processo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="97303-448">You might find the following tips helpful during the development process.</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="97303-449">Executar duas instâncias do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="97303-449">Run Two Instances of Visual Studio</span></span>

<span data-ttu-id="97303-450">Você pode desenvolver o provedor de tipo em uma instância e testar o provedor nos outros porque o IDE de teste tem um bloqueio no arquivo. dll que impede que o provedor de tipo que está sendo recriado.</span><span class="sxs-lookup"><span data-stu-id="97303-450">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="97303-451">Portanto, você deve fechar a segunda instância do Visual Studio enquanto o provedor é criado na primeira instância e, em seguida, você deverá reabri-la a segunda instância depois que o provedor é compilado.</span><span class="sxs-lookup"><span data-stu-id="97303-451">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="97303-452">Provedores de tipos de depuração por meio de invocações de fsc.exe</span><span class="sxs-lookup"><span data-stu-id="97303-452">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="97303-453">Você pode invocar provedores de tipos, usando as seguintes ferramentas:</span><span class="sxs-lookup"><span data-stu-id="97303-453">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="97303-454">FSC.exe (compilador de linha de comando do F #)</span><span class="sxs-lookup"><span data-stu-id="97303-454">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="97303-455">FSI.exe (compilador do F # interativo)</span><span class="sxs-lookup"><span data-stu-id="97303-455">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="97303-456">devenv.exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="97303-456">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="97303-457">Muitas vezes você pode depurar provedores de tipos com mais facilidade usando fsc.exe em um arquivo de script de teste (por exemplo, script.fsx).</span><span class="sxs-lookup"><span data-stu-id="97303-457">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="97303-458">Você pode iniciar um depurador em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="97303-458">You can launch a debugger from a command prompt.</span></span>

```
  devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="97303-459">Você pode usar o log de impressão para stdout.</span><span class="sxs-lookup"><span data-stu-id="97303-459">You can use print-to-stdout logging.</span></span>

## <a name="see-also"></a><span data-ttu-id="97303-460">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97303-460">See also</span></span>

- [<span data-ttu-id="97303-461">Provedores de Tipos</span><span class="sxs-lookup"><span data-stu-id="97303-461">Type Providers</span></span>](index.md)
- [<span data-ttu-id="97303-462">O SDK do provedor de tipo</span><span class="sxs-lookup"><span data-stu-id="97303-462">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
