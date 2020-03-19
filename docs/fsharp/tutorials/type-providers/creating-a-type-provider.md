---
title: 'Tutorial: Crie um provedor de tipos'
description: Aprenda a criar seus próprios provedores do tipo F# em F# 3.0 examinando vários provedores de tipo simples para ilustrar os conceitos básicos.
ms.date: 11/04/2019
ms.openlocfilehash: 3b8145d4c2d8bf96b6dcf66de02e9f2d83927d74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186117"
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="e3df4-103">Tutorial: Crie um provedor de tipos</span><span class="sxs-lookup"><span data-stu-id="e3df4-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="e3df4-104">O mecanismo do provedor de tipo em F# é uma parte significativa de seu suporte para programação rica em informações.</span><span class="sxs-lookup"><span data-stu-id="e3df4-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="e3df4-105">Este tutorial explica como criar seus próprios provedores de tipo, guiando você através do desenvolvimento de vários provedores de tipo simples para ilustrar os conceitos básicos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="e3df4-106">Para obter mais informações sobre o mecanismo do provedor de tipo em F#, consulte [Provedores de tipo](index.md).</span><span class="sxs-lookup"><span data-stu-id="e3df4-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="e3df4-107">O ecossistema F# contém uma gama de provedores de tipo para serviços de dados corporativos e de Internet comumente usados.</span><span class="sxs-lookup"><span data-stu-id="e3df4-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="e3df4-108">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="e3df4-108">For example:</span></span>

- <span data-ttu-id="e3df4-109">[O FSharp.Data](https://fsharp.github.io/FSharp.Data/) inclui provedores de tipo para formatos de documentos JSON, XML, CSV e HTML.</span><span class="sxs-lookup"><span data-stu-id="e3df4-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="e3df4-110">[O SQLProvider](https://fsprojects.github.io/SQLProvider/) fornece acesso fortemente digitado a bancos de dados SQL por meio de um mapeamento de objetos e consultas F# LINQ contra essas fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="e3df4-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="e3df4-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) tem um conjunto de provedores de tipo para incorporação verificada por tempo de compilação do T-SQL em F#.</span><span class="sxs-lookup"><span data-stu-id="e3df4-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="e3df4-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) é um conjunto mais antigo de provedores de tipo para uso apenas com programação .NET Framework para acessar serviços de dados SQL, Entity Framework, OData e WSDL.</span><span class="sxs-lookup"><span data-stu-id="e3df4-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="e3df4-113">Quando necessário, você pode criar provedores de tipo personalizados, ou pode referenciar provedores de tipo que outros criaram.</span><span class="sxs-lookup"><span data-stu-id="e3df4-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="e3df4-114">Por exemplo, sua organização pode ter um serviço de dados que fornece um grande e crescente número de conjuntos de dados nomeados, cada um com seu próprio esquema de dados estáveis.</span><span class="sxs-lookup"><span data-stu-id="e3df4-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="e3df4-115">Você pode criar um provedor de tipo que lê os esquemas e apresenta os conjuntos de dados atuais para o programador de forma fortemente digitada.</span><span class="sxs-lookup"><span data-stu-id="e3df4-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="e3df4-116">Antes de iniciar</span><span class="sxs-lookup"><span data-stu-id="e3df4-116">Before You Start</span></span>

<span data-ttu-id="e3df4-117">O mecanismo do provedor de tipo foi projetado principalmente para injetar dados estáveis e espaços de informações de serviço na experiência de programação F#.</span><span class="sxs-lookup"><span data-stu-id="e3df4-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="e3df4-118">Este mecanismo não foi projetado para injetar espaços de informação cujo esquema muda durante a execução do programa de maneiras relevantes para a lógica do programa.</span><span class="sxs-lookup"><span data-stu-id="e3df4-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="e3df4-119">Além disso, o mecanismo não foi projetado para meta-programação intra-linguagem, embora esse domínio contenha alguns usos válidos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="e3df4-120">Você deve usar este mecanismo apenas quando necessário e onde o desenvolvimento de um provedor de tipo produz um valor muito alto.</span><span class="sxs-lookup"><span data-stu-id="e3df4-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="e3df4-121">Você deve evitar escrever um provedor de tipo onde um esquema não está disponível.</span><span class="sxs-lookup"><span data-stu-id="e3df4-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="e3df4-122">Da mesma forma, você deve evitar escrever um provedor de tipo onde uma biblioteca .NET ordinária (ou mesmo existente) seria suficiente.</span><span class="sxs-lookup"><span data-stu-id="e3df4-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="e3df4-123">Antes de começar, você pode fazer as seguintes perguntas:</span><span class="sxs-lookup"><span data-stu-id="e3df4-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="e3df4-124">Você tem um esquema para sua fonte de informação?</span><span class="sxs-lookup"><span data-stu-id="e3df4-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="e3df4-125">Se assim for, qual é o mapeamento no sistema do tipo F# e .NET?</span><span class="sxs-lookup"><span data-stu-id="e3df4-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="e3df4-126">Você pode usar uma API (digitada dinamicamente) como ponto de partida para sua implementação?</span><span class="sxs-lookup"><span data-stu-id="e3df4-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="e3df4-127">Você e sua organização terão usos suficientes do provedor do tipo para fazer com que a escrita valha a pena?</span><span class="sxs-lookup"><span data-stu-id="e3df4-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="e3df4-128">Uma biblioteca normal .NET atenderia às suas necessidades?</span><span class="sxs-lookup"><span data-stu-id="e3df4-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="e3df4-129">Quanto seu esquema mudará?</span><span class="sxs-lookup"><span data-stu-id="e3df4-129">How much will your schema change?</span></span>

- <span data-ttu-id="e3df4-130">Mudará durante a codificação?</span><span class="sxs-lookup"><span data-stu-id="e3df4-130">Will it change during coding?</span></span>

- <span data-ttu-id="e3df4-131">Mudará entre as sessões de codificação?</span><span class="sxs-lookup"><span data-stu-id="e3df4-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="e3df4-132">Mudará durante a execução do programa?</span><span class="sxs-lookup"><span data-stu-id="e3df4-132">Will it change during program execution?</span></span>

<span data-ttu-id="e3df4-133">Os provedores de tipos são mais adequados para situações em que o esquema é estável em tempo de execução e durante a vida útil do código compilado.</span><span class="sxs-lookup"><span data-stu-id="e3df4-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>

## <a name="a-simple-type-provider"></a><span data-ttu-id="e3df4-134">Um provedor de tipo simples</span><span class="sxs-lookup"><span data-stu-id="e3df4-134">A Simple Type Provider</span></span>

<span data-ttu-id="e3df4-135">Esta amostra é Samples.HelloWorldTypeProvider, semelhante `examples` às amostras no diretório do Provedor de [Tipo F# SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span><span class="sxs-lookup"><span data-stu-id="e3df4-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="e3df4-136">O provedor disponibiliza um "espaço de tipo" que contém 100 tipos apagados, como mostra o código a `Type1`seguir usando a sintaxe de assinatura F# e omitindo os detalhes para todos, exceto .</span><span class="sxs-lookup"><span data-stu-id="e3df4-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="e3df4-137">Para obter mais informações sobre tipos apagados, consulte [detalhes sobre tipos fornecidos apagados](#details-about-erased-provided-types) mais tarde neste tópico.</span><span class="sxs-lookup"><span data-stu-id="e3df4-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

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

<span data-ttu-id="e3df4-138">Observe que o conjunto de tipos e membros fornecidos é sabia estáticamente.</span><span class="sxs-lookup"><span data-stu-id="e3df4-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="e3df4-139">Este exemplo não aproveita a capacidade dos provedores de fornecer tipos que dependem de um esquema.</span><span class="sxs-lookup"><span data-stu-id="e3df4-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="e3df4-140">A implementação do provedor de tipo é descrita no código a seguir, e os detalhes são cobertos em seções posteriores deste tópico.</span><span class="sxs-lookup"><span data-stu-id="e3df4-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>

> [!WARNING]
> <span data-ttu-id="e3df4-141">Pode haver diferenças entre este código e as amostras online.</span><span class="sxs-lookup"><span data-stu-id="e3df4-141">There may be differences between this code and the online samples.</span></span>

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

<span data-ttu-id="e3df4-142">Para usar este provedor, abra uma instância separada do Visual Studio, crie um script F# e adicione uma referência ao provedor do seu script usando #r como o seguinte código mostra:</span><span class="sxs-lookup"><span data-stu-id="e3df4-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

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

<span data-ttu-id="e3df4-143">Em seguida, procure `Samples.HelloWorldTypeProvider` os tipos o namespace que o provedor de tipo gerou.</span><span class="sxs-lookup"><span data-stu-id="e3df4-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="e3df4-144">Antes de recompilar o provedor, certifique-se de que você fechou todas as instâncias do Visual Studio e F# Interactive que estão usando o provedor DLL.</span><span class="sxs-lookup"><span data-stu-id="e3df4-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="e3df4-145">Caso contrário, um erro de compilação ocorrerá porque a DLL de saída será bloqueada.</span><span class="sxs-lookup"><span data-stu-id="e3df4-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="e3df4-146">Para depurar este provedor usando instruções de impressão, faça um script que exponha um problema com o provedor e use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="e3df4-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="e3df4-147">Para depurar este provedor usando o Visual Studio, abra o Prompt de comando do desenvolvedor para o Visual Studio com credenciais administrativas e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e3df4-147">To debug this provider by using Visual Studio, open the Developer Command Prompt for Visual Studio with administrative credentials, and run the following command:</span></span>

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="e3df4-148">Como alternativa, abra o Visual Studio, abra `Debug/Attach to process…`o menu `devenv` Debug, escolha e anexe a outro processo onde você está editando seu script.</span><span class="sxs-lookup"><span data-stu-id="e3df4-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="e3df4-149">Usando este método, você pode direcionar mais facilmente a lógica específica no provedor de tipos digitando expressões interativamente na segunda instância (com intelliSense completo e outros recursos).</span><span class="sxs-lookup"><span data-stu-id="e3df4-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="e3df4-150">Você pode desativar a depuração do Just My Code para identificar melhor os erros no código gerado.</span><span class="sxs-lookup"><span data-stu-id="e3df4-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="e3df4-151">Para obter informações sobre como ativar ou desativar esse recurso, consulte [Navegando através de Código com o Depurador](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span><span class="sxs-lookup"><span data-stu-id="e3df4-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="e3df4-152">Além disso, você também pode definir a `Debug` captura de `Exceptions` exceção de primeira chance abrindo o `Exceptions` menu e, em seguida, escolhendo ou escolhendo as teclas Ctrl+Alt+E para abrir a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="e3df4-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="e3df4-153">Nessa caixa de `Common Language Runtime Exceptions`diálogo, `Thrown` em , selecione a caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="e3df4-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>

### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="e3df4-154">Implementação do Provedor de Tipo</span><span class="sxs-lookup"><span data-stu-id="e3df4-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="e3df4-155">Esta seção orienta você através das principais seções da implementação do provedor de tipo.</span><span class="sxs-lookup"><span data-stu-id="e3df4-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="e3df4-156">Primeiro, você define o tipo para o próprio provedor de tipo personalizado:</span><span class="sxs-lookup"><span data-stu-id="e3df4-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="e3df4-157">Esse tipo deve ser público, e você deve marcá-lo com o atributo [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) para que o compilador reconheça o provedor de tipos quando um projeto F# separado fizer referência ao conjunto que contém o tipo.</span><span class="sxs-lookup"><span data-stu-id="e3df4-157">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="e3df4-158">O parâmetro *de configuração* é opcional e, se presente, contém informações de configuração contextuais para a instância do provedor de tipo que o compilador F# cria.</span><span class="sxs-lookup"><span data-stu-id="e3df4-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="e3df4-159">Em seguida, você implementa a interface [ITypeProvider.](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f)</span><span class="sxs-lookup"><span data-stu-id="e3df4-159">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="e3df4-160">Neste caso, você `TypeProviderForNamespaces` usa o `ProvidedTypes` tipo da API como um tipo de base.</span><span class="sxs-lookup"><span data-stu-id="e3df4-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="e3df4-161">Este tipo de ajudante pode fornecer uma coleção finita de espaços de nome ansiosamente fornecidos, cada um dos quais contém diretamente um número finito de tipos fixos e ansiosamente fornecidos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="e3df4-162">Nesse contexto, o provedor gera *ansiosamente* tipos, mesmo que não sejam necessários ou usados.</span><span class="sxs-lookup"><span data-stu-id="e3df4-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="e3df4-163">Em seguida, defina valores privados locais que especifiquem o namespace para os tipos fornecidos e encontre o próprio conjunto do provedor de tipos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="e3df4-164">Este conjunto é usado mais tarde como o tipo lógico dos tipos apagados que são fornecidos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="e3df4-165">Em seguida, crie uma função para fornecer cada um dos tipos Tipo1... Tipo100.</span><span class="sxs-lookup"><span data-stu-id="e3df4-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="e3df4-166">Esta função é explicada com mais detalhes mais tarde neste tópico.</span><span class="sxs-lookup"><span data-stu-id="e3df4-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="e3df4-167">Em seguida, gere os 100 tipos fornecidos:</span><span class="sxs-lookup"><span data-stu-id="e3df4-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="e3df4-168">Em seguida, adicione os tipos como um namespace fornecido:</span><span class="sxs-lookup"><span data-stu-id="e3df4-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="e3df4-169">Finalmente, adicione um atributo de montagem que indique que você está criando um provedor de tipo DLL:</span><span class="sxs-lookup"><span data-stu-id="e3df4-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="e3df4-170">fornecendo um tipo e seus membros</span><span class="sxs-lookup"><span data-stu-id="e3df4-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="e3df4-171">A `makeOneProvidedType` função faz o trabalho real de fornecer um dos tipos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) =
…
```

<span data-ttu-id="e3df4-172">Esta etapa explica a implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="e3df4-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="e3df4-173">Primeiro, crie o tipo fornecido (por exemplo, Tipo1, quando n = 1, ou Type57, quando n = 57).</span><span class="sxs-lookup"><span data-stu-id="e3df4-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="e3df4-174">Você deve observar os seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="e3df4-174">You should note the following points:</span></span>

- <span data-ttu-id="e3df4-175">Este tipo fornecido é apagado.</span><span class="sxs-lookup"><span data-stu-id="e3df4-175">This provided type is erased.</span></span>  <span data-ttu-id="e3df4-176">Como você indica que `obj`o tipo base é , as instâncias aparecerão como valores do tipo [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) em código compilado.</span><span class="sxs-lookup"><span data-stu-id="e3df4-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="e3df4-177">Quando você especificar um tipo não aninhado, você deve especificar o conjunto e o namespace.</span><span class="sxs-lookup"><span data-stu-id="e3df4-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="e3df4-178">Para tipos apagados, o conjunto deve ser o próprio conjunto do provedor do tipo.</span><span class="sxs-lookup"><span data-stu-id="e3df4-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="e3df4-179">Em seguida, adicione a documentação XML ao tipo.</span><span class="sxs-lookup"><span data-stu-id="e3df4-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="e3df4-180">Esta documentação está atrasada, ou seja, calculada demanda se o compilador host precisar.</span><span class="sxs-lookup"><span data-stu-id="e3df4-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="e3df4-181">Em seguida, você adiciona uma propriedade estática fornecida ao tipo:</span><span class="sxs-lookup"><span data-stu-id="e3df4-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="e3df4-182">Conseguir essa propriedade sempre avaliará a string "Hello!".</span><span class="sxs-lookup"><span data-stu-id="e3df4-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="e3df4-183">O `GetterCode` para a propriedade usa uma cotação F#, que representa o código que o compilador host gera para obter a propriedade.</span><span class="sxs-lookup"><span data-stu-id="e3df4-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="e3df4-184">Para obter mais informações sobre cotações, consulte [Cotações de Código (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span><span class="sxs-lookup"><span data-stu-id="e3df4-184">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="e3df4-185">Adicione a documentação XML à propriedade.</span><span class="sxs-lookup"><span data-stu-id="e3df4-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="e3df4-186">Agora anexar a propriedade fornecida ao tipo fornecido.</span><span class="sxs-lookup"><span data-stu-id="e3df4-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="e3df4-187">Você deve anexar um membro fornecido a um e apenas um tipo.</span><span class="sxs-lookup"><span data-stu-id="e3df4-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="e3df4-188">Caso contrário, o membro nunca será acessível.</span><span class="sxs-lookup"><span data-stu-id="e3df4-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="e3df4-189">Agora crie um construtor fornecido que não tome parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e3df4-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="e3df4-190">O `InvokeCode` para o construtor retorna uma cotação F#, que representa o código que o compilador host gera quando o construtor é chamado.</span><span class="sxs-lookup"><span data-stu-id="e3df4-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="e3df4-191">Por exemplo, você pode usar o seguinte construtor:</span><span class="sxs-lookup"><span data-stu-id="e3df4-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="e3df4-192">Uma instância do tipo fornecido será criada com dados subjacentes "Os dados do objeto".</span><span class="sxs-lookup"><span data-stu-id="e3df4-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="e3df4-193">O código citado inclui uma conversão para [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) porque esse tipo é o apagamento deste tipo fornecido (como você especificou quando declarou o tipo fornecido).</span><span class="sxs-lookup"><span data-stu-id="e3df4-193">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="e3df4-194">Adicione a documentação XML ao construtor e adicione o construtor fornecido ao tipo fornecido:</span><span class="sxs-lookup"><span data-stu-id="e3df4-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="e3df4-195">Crie um segundo construtor fornecido que leve um parâmetro:</span><span class="sxs-lookup"><span data-stu-id="e3df4-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="e3df4-196">O `InvokeCode` para o construtor retorna novamente uma cotação F#, que representa o código que o compilador host gerou para uma chamada para o método.</span><span class="sxs-lookup"><span data-stu-id="e3df4-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="e3df4-197">Por exemplo, você pode usar o seguinte construtor:</span><span class="sxs-lookup"><span data-stu-id="e3df4-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="e3df4-198">Uma instância do tipo fornecido é criada com dados subjacentes "dez".</span><span class="sxs-lookup"><span data-stu-id="e3df4-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="e3df4-199">Você já deve ter `InvokeCode` notado que a função retorna uma cotação.</span><span class="sxs-lookup"><span data-stu-id="e3df4-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="e3df4-200">A entrada para esta função é uma lista de expressões, uma por parâmetro de construtor.</span><span class="sxs-lookup"><span data-stu-id="e3df4-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="e3df4-201">Neste caso, uma expressão que representa o valor `args.[0]`único do parâmetro está disponível em .</span><span class="sxs-lookup"><span data-stu-id="e3df4-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="e3df4-202">O código de uma chamada para o construtor coece o `obj`valor de retorno para o tipo apagado .</span><span class="sxs-lookup"><span data-stu-id="e3df4-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="e3df4-203">Depois de adicionar o segundo construtor fornecido ao tipo, você cria uma propriedade de instância fornecida:</span><span class="sxs-lookup"><span data-stu-id="e3df4-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="e3df4-204">Obter esta propriedade retornará o comprimento da string, que é o objeto de representação.</span><span class="sxs-lookup"><span data-stu-id="e3df4-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="e3df4-205">A `GetterCode` propriedade retorna uma cotação F# que especifica o código que o compilador host gera para obter a propriedade.</span><span class="sxs-lookup"><span data-stu-id="e3df4-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="e3df4-206">Como, `InvokeCode` `GetterCode` a função retorna uma cotação.</span><span class="sxs-lookup"><span data-stu-id="e3df4-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="e3df4-207">O compilador host chama essa função com uma lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="e3df4-208">Neste caso, os argumentos incluem apenas a expressão única que representa a instância sobre a `args.[0]`qual o getter está sendo chamado, que você pode acessar usando .</span><span class="sxs-lookup"><span data-stu-id="e3df4-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.</span></span> <span data-ttu-id="e3df4-209">A implementação de `GetterCode` então emenda na cotação de `obj`resultados no tipo apagado , e um molde é usado para satisfazer o mecanismo do compilador para verificar tipos de que o objeto é uma string.</span><span class="sxs-lookup"><span data-stu-id="e3df4-209">The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="e3df4-210">A próxima `makeOneProvidedType` parte fornece um método de ocorrência com um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e3df4-210">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

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

<span data-ttu-id="e3df4-211">Finalmente, crie um tipo aninhado que contenha 100 propriedades aninhadas.</span><span class="sxs-lookup"><span data-stu-id="e3df4-211">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="e3df4-212">A criação desse tipo aninhado e suas propriedades está atrasada, ou seja, computada demanda.</span><span class="sxs-lookup"><span data-stu-id="e3df4-212">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

```fsharp
t.AddMembersDelayed(fun () ->
  let nestedType = ProvidedTypeDefinition("NestedType", Some typeof<obj>)

  nestedType.AddMembersDelayed (fun () ->
    let staticPropsInNestedType =
      [
          for i in 1 .. 100 ->
              let valueOfTheProperty = "I am string "  + string i

              let p =
                ProvidedProperty(propertyName = "StaticProperty" + string i,
                  propertyType = typeof<string>,
                  isStatic = true,
                  getterCode= (fun args -> <@@ valueOfTheProperty @@>))

              p.AddXmlDocDelayed(fun () ->
                  sprintf "This is StaticProperty%d on NestedType" i)

              p
      ]

    staticPropsInNestedType)

  [nestedType])
```

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="e3df4-213">Detalhes sobre tipos fornecidos apagados</span><span class="sxs-lookup"><span data-stu-id="e3df4-213">Details about Erased Provided Types</span></span>

<span data-ttu-id="e3df4-214">O exemplo nesta seção fornece apenas *tipos apagados fornecidos,* que são particularmente úteis nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="e3df4-214">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="e3df4-215">Quando você está escrevendo um provedor para um espaço de informação que contém apenas dados e métodos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-215">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="e3df4-216">Quando você está escrevendo um provedor onde a semântica precisa do tipo runtime não é crítica para o uso prático do espaço de informação.</span><span class="sxs-lookup"><span data-stu-id="e3df4-216">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="e3df4-217">Quando você está escrevendo um provedor para um espaço de informação tão grande e interconectado que não é tecnicamente viável gerar tipos .NET reais para o espaço de informação.</span><span class="sxs-lookup"><span data-stu-id="e3df4-217">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="e3df4-218">Neste exemplo, cada tipo fornecido é apagado `obj`para digitar , e todos `obj` os usos do tipo aparecerão como tipo em código compilado.</span><span class="sxs-lookup"><span data-stu-id="e3df4-218">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="e3df4-219">Na verdade, os objetos subjacentes nesses exemplos são strings, mas o tipo aparecerá como `System.Object` em código compilado .NET.</span><span class="sxs-lookup"><span data-stu-id="e3df4-219">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="e3df4-220">Como em todos os usos de apagamento de tipo, você pode usar boxe explícito, unboxing e elenco para subverter tipos apagados.</span><span class="sxs-lookup"><span data-stu-id="e3df4-220">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="e3df4-221">Neste caso, uma exceção de elenco que não é válida pode resultar quando o objeto é usado.</span><span class="sxs-lookup"><span data-stu-id="e3df4-221">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="e3df4-222">Um tempo de execução do provedor pode definir seu próprio tipo de representação privada para ajudar a proteger contra falsas representações.</span><span class="sxs-lookup"><span data-stu-id="e3df4-222">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="e3df4-223">Você não pode definir tipos apagados em f# em si.</span><span class="sxs-lookup"><span data-stu-id="e3df4-223">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="e3df4-224">Somente os tipos fornecidos podem ser apagados.</span><span class="sxs-lookup"><span data-stu-id="e3df4-224">Only provided types may be erased.</span></span> <span data-ttu-id="e3df4-225">Você deve entender as ramificações, tanto práticas quanto semânticas, de usar tipos apagados para o seu provedor de tipo ou um provedor que fornece tipos apagados.</span><span class="sxs-lookup"><span data-stu-id="e3df4-225">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="e3df4-226">Um tipo apagado não tem nenhum tipo real .NET.</span><span class="sxs-lookup"><span data-stu-id="e3df4-226">An erased type has no real .NET type.</span></span> <span data-ttu-id="e3df4-227">Portanto, você não pode fazer uma reflexão precisa sobre o tipo, e você pode subverter tipos apagados se você usar moldes de tempo de execução e outras técnicas que dependem de semântica exata do tipo de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e3df4-227">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="e3df4-228">A subversão de tipos apagados frequentemente resulta em exceções de elenco de tipo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e3df4-228">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>

### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="e3df4-229">Escolhendo representações para tipos fornecidos apagados</span><span class="sxs-lookup"><span data-stu-id="e3df4-229">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="e3df4-230">Para alguns usos de tipos apagados fornecidos, nenhuma representação é necessária.</span><span class="sxs-lookup"><span data-stu-id="e3df4-230">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="e3df4-231">Por exemplo, o tipo apagado fornecido pode conter apenas propriedades estáticas e membros e sem construtores, e nenhum método ou propriedades retornaria uma instância do tipo.</span><span class="sxs-lookup"><span data-stu-id="e3df4-231">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="e3df4-232">Se você pode alcançar instâncias de um tipo fornecido apagado, você deve considerar as seguintes perguntas:</span><span class="sxs-lookup"><span data-stu-id="e3df4-232">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="e3df4-233">**Qual é o apagamento de um tipo fornecido?**</span><span class="sxs-lookup"><span data-stu-id="e3df4-233">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="e3df4-234">A eliminação de um tipo fornecido é como o tipo aparece no código .NET compilado.</span><span class="sxs-lookup"><span data-stu-id="e3df4-234">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="e3df4-235">O apagamento de um tipo de classe apagado fornecido é sempre o primeiro tipo de base não apagado na cadeia de herança do tipo.</span><span class="sxs-lookup"><span data-stu-id="e3df4-235">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="e3df4-236">O apagamento de um tipo de interface `System.Object`aserdestejada fornecido é sempre .</span><span class="sxs-lookup"><span data-stu-id="e3df4-236">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="e3df4-237">**Quais são as representações de um tipo fornecido?**</span><span class="sxs-lookup"><span data-stu-id="e3df4-237">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="e3df4-238">O conjunto de possíveis objetos para um tipo apagado é chamado de suas representações.</span><span class="sxs-lookup"><span data-stu-id="e3df4-238">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="e3df4-239">No exemplo deste documento, as representações de todos os `Type1..Type100` tipos apagados fornecidos são sempre objetos de cadeia.</span><span class="sxs-lookup"><span data-stu-id="e3df4-239">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="e3df4-240">Todas as representações de um tipo fornecido devem ser compatíveis com a eliminação do tipo fornecido.</span><span class="sxs-lookup"><span data-stu-id="e3df4-240">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="e3df4-241">(Caso contrário, o compilador F# dará um erro para o uso do provedor de tipo ou o código .NET não verificável que não é válido será gerado.</span><span class="sxs-lookup"><span data-stu-id="e3df4-241">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="e3df4-242">Um provedor de tipo não é válido se ele retornar código que dá uma representação que não é válida.)</span><span class="sxs-lookup"><span data-stu-id="e3df4-242">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="e3df4-243">Você pode escolher uma representação para objetos fornecidos usando qualquer uma das seguintes abordagens, ambas muito comuns:</span><span class="sxs-lookup"><span data-stu-id="e3df4-243">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="e3df4-244">Se você está simplesmente fornecendo um invólucro fortemente digitado sobre um tipo .NET existente, muitas vezes faz sentido para o seu tipo apagar para esse tipo, usar instâncias desse tipo como representações, ou ambos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-244">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="e3df4-245">Esta abordagem é apropriada quando a maioria dos métodos existentes nesse tipo ainda fazem sentido ao usar a versão fortemente digitada.</span><span class="sxs-lookup"><span data-stu-id="e3df4-245">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="e3df4-246">Se você quiser criar uma API que difere significativamente de qualquer API .NET existente, faz sentido criar tipos de tempo de execução que serão o apagamento do tipo e representações para os tipos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-246">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="e3df4-247">O exemplo neste documento usa strings como representações de objetos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-247">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="e3df4-248">Frequentemente, pode ser apropriado usar outros objetos para representações.</span><span class="sxs-lookup"><span data-stu-id="e3df4-248">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="e3df4-249">Por exemplo, você pode usar um dicionário como saco de propriedades:</span><span class="sxs-lookup"><span data-stu-id="e3df4-249">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="e3df4-250">Como alternativa, você pode definir um tipo no provedor de tipo que será usado em tempo de execução para formar a representação, juntamente com uma ou mais operações em tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="e3df4-250">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="e3df4-251">Desde que os membros possam construir instâncias desse tipo de objeto:</span><span class="sxs-lookup"><span data-stu-id="e3df4-251">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="e3df4-252">Neste caso, você pode (opcionalmente) usar esse tipo como apagamento `baseType` de tipo `ProvidedTypeDefinition`especificando este tipo como o ao construir o :</span><span class="sxs-lookup"><span data-stu-id="e3df4-252">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="e3df4-253">Lições-chave</span><span class="sxs-lookup"><span data-stu-id="e3df4-253">Key Lessons</span></span>

<span data-ttu-id="e3df4-254">A seção anterior explicou como criar um provedor de tipo de apagamento simples que fornece uma variedade de tipos, propriedades e métodos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-254">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="e3df4-255">Esta seção também explicou o conceito de eliminação de tipos, incluindo algumas das vantagens e desvantagens de fornecer tipos apagados de um provedor de tipo, e discutiu representações de tipos apagados.</span><span class="sxs-lookup"><span data-stu-id="e3df4-255">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>

## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="e3df4-256">Um provedor de tipo que usa parâmetros estáticos</span><span class="sxs-lookup"><span data-stu-id="e3df4-256">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="e3df4-257">A capacidade de parametrizar provedores de tipos por dados estáticos permite muitos cenários interessantes, mesmo nos casos em que o provedor não precisa acessar nenhum dado local ou remoto.</span><span class="sxs-lookup"><span data-stu-id="e3df4-257">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="e3df4-258">Nesta seção, você aprenderá algumas técnicas básicas para montar tal provedor.</span><span class="sxs-lookup"><span data-stu-id="e3df4-258">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>

### <a name="type-checked-regex-provider"></a><span data-ttu-id="e3df4-259">Provedor Regex verificado de tipo</span><span class="sxs-lookup"><span data-stu-id="e3df4-259">Type Checked Regex Provider</span></span>

<span data-ttu-id="e3df4-260">Imagine que você deseja implementar um provedor de tipo para <xref:System.Text.RegularExpressions.Regex> expressões regulares que envolva as bibliotecas .NET em uma interface que fornece as seguintes garantias de tempo de compilação:</span><span class="sxs-lookup"><span data-stu-id="e3df4-260">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="e3df4-261">Verificando se uma expressão regular é válida.</span><span class="sxs-lookup"><span data-stu-id="e3df4-261">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="e3df4-262">Fornecendo propriedades nomeadas em correspondências baseadas em nomes de grupo na expressão regular.</span><span class="sxs-lookup"><span data-stu-id="e3df4-262">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="e3df4-263">Esta seção mostra como usar provedores de tipo para criar um `RegexTyped` tipo que o padrão de expressão regular parametriza para fornecer esses benefícios.</span><span class="sxs-lookup"><span data-stu-id="e3df4-263">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="e3df4-264">O compilador relatará um erro se o padrão fornecido não for válido, e o provedor de tipo pode extrair os grupos do padrão para que você possa acessá-los usando propriedades nomeadas em correspondências.</span><span class="sxs-lookup"><span data-stu-id="e3df4-264">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="e3df4-265">Quando você projeta um provedor de tipo, você deve considerar como sua API exposta deve parecer para usuários finais e como esse design se traduzirá em código .NET.</span><span class="sxs-lookup"><span data-stu-id="e3df4-265">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="e3df4-266">O exemplo a seguir mostra como usar tal API para obter os componentes do código de área:</span><span class="sxs-lookup"><span data-stu-id="e3df4-266">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="e3df4-267">O exemplo a seguir mostra como o provedor de tipos traduz essas chamadas:</span><span class="sxs-lookup"><span data-stu-id="e3df4-267">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="e3df4-268">Observe os seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="e3df4-268">Note the following points:</span></span>

- <span data-ttu-id="e3df4-269">O tipo Regex padrão representa `RegexTyped` o tipo parametrizado.</span><span class="sxs-lookup"><span data-stu-id="e3df4-269">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="e3df4-270">O `RegexTyped` construtor resulta em uma chamada para o construtor Regex, passando no argumento do tipo estático para o padrão.</span><span class="sxs-lookup"><span data-stu-id="e3df4-270">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="e3df4-271">Os resultados `Match` do método são <xref:System.Text.RegularExpressions.Match> representados pelo tipo padrão.</span><span class="sxs-lookup"><span data-stu-id="e3df4-271">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="e3df4-272">Cada grupo nomeado resulta em uma propriedade fornecida, e acessar a propriedade resulta `Groups` no uso de um indexador na coleção de uma partida.</span><span class="sxs-lookup"><span data-stu-id="e3df4-272">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="e3df4-273">O código a seguir é o núcleo da lógica para implementar tal provedor, e este exemplo omite a adição de todos os membros ao tipo fornecido.</span><span class="sxs-lookup"><span data-stu-id="e3df4-273">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="e3df4-274">Para obter informações sobre cada membro adicionado, consulte a seção apropriada mais tarde neste tópico.</span><span class="sxs-lookup"><span data-stu-id="e3df4-274">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="e3df4-275">Para obter o código completo, baixe a amostra do [F# 3.0 Sample Pack](https://archive.codeplex.com/?p=fsharp3sample) no site do CodePlex.</span><span class="sxs-lookup"><span data-stu-id="e3df4-275">For the full code, download the sample from the [F# 3.0 Sample Pack](https://archive.codeplex.com/?p=fsharp3sample) on the CodePlex website.</span></span>

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

<span data-ttu-id="e3df4-276">Observe os seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="e3df4-276">Note the following points:</span></span>

- <span data-ttu-id="e3df4-277">O provedor de tipos tem `pattern`dois parâmetros estáticos: o , que é obrigatório, e o `options`, que são opcionais (porque um valor padrão é fornecido).</span><span class="sxs-lookup"><span data-stu-id="e3df4-277">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="e3df4-278">Depois que os argumentos estáticos são fornecidos, você cria uma instância da expressão regular.</span><span class="sxs-lookup"><span data-stu-id="e3df4-278">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="e3df4-279">Esta instância abrirá uma exceção se o Regex estiver mal formado e esse erro será relatado aos usuários.</span><span class="sxs-lookup"><span data-stu-id="e3df4-279">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="e3df4-280">Dentro `DefineStaticParameters` do retorno de chamada, você define o tipo que será devolvido após o fornecimento dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-280">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="e3df4-281">Este código `HideObjectMethods` define-se como verdadeiro para que a experiência do IntelliSense permaneça simplificada.</span><span class="sxs-lookup"><span data-stu-id="e3df4-281">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="e3df4-282">Esse atributo `Equals` `GetHashCode`faz `Finalize`com `GetType` que os membros sejam suprimidos das listas do IntelliSense para um objeto fornecido.</span><span class="sxs-lookup"><span data-stu-id="e3df4-282">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="e3df4-283">Você `obj` usa como o tipo base do método, `Regex` mas você usará um objeto como a representação em tempo de execução deste tipo, como mostra o próximo exemplo.</span><span class="sxs-lookup"><span data-stu-id="e3df4-283">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="e3df4-284">A chamada `Regex` para o <xref:System.ArgumentException> construtor joga um quando uma expressão regular não é válida.</span><span class="sxs-lookup"><span data-stu-id="e3df4-284">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="e3df4-285">O compilador captura essa exceção e relata uma mensagem de erro para o usuário na hora da compilação ou no editor do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e3df4-285">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="e3df4-286">Essa exceção permite que expressões regulares sejam validadas sem executar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3df4-286">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="e3df4-287">O tipo definido acima ainda não é útil porque não contém nenhum método ou propriedades significativas.</span><span class="sxs-lookup"><span data-stu-id="e3df4-287">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="e3df4-288">Primeiro, adicione `IsMatch` um método estático:</span><span class="sxs-lookup"><span data-stu-id="e3df4-288">First, add a static `IsMatch` method:</span></span>

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

<span data-ttu-id="e3df4-289">O código anterior define `IsMatch`um método , que toma `bool`uma seqüência como entrada e retorna a .</span><span class="sxs-lookup"><span data-stu-id="e3df4-289">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="e3df4-290">A única parte complicada é `args` o uso `InvokeCode` do argumento dentro da definição.</span><span class="sxs-lookup"><span data-stu-id="e3df4-290">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="e3df4-291">Neste exemplo, `args` há uma lista de citações que representa os argumentos para este método.</span><span class="sxs-lookup"><span data-stu-id="e3df4-291">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="e3df4-292">Se o método é um método de `this` instância, o primeiro argumento representa o argumento.</span><span class="sxs-lookup"><span data-stu-id="e3df4-292">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="e3df4-293">No entanto, para um método estático, os argumentos são todos apenas os argumentos explícitos para o método.</span><span class="sxs-lookup"><span data-stu-id="e3df4-293">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="e3df4-294">Observe que o tipo do valor citado deve corresponder ao tipo `bool`de retorno especificado (neste caso, ).</span><span class="sxs-lookup"><span data-stu-id="e3df4-294">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="e3df4-295">Observe também que este `AddXmlDoc` código usa o método para garantir que o método fornecido também tenha documentação útil, que você pode fornecer através do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="e3df4-295">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="e3df4-296">Em seguida, adicione um método de correspondência de ocorrência.</span><span class="sxs-lookup"><span data-stu-id="e3df4-296">Next, add an instance Match method.</span></span> <span data-ttu-id="e3df4-297">No entanto, este método deve `Match` retornar um valor de um tipo fornecido para que os grupos possam ser acessados de forma fortemente digitada.</span><span class="sxs-lookup"><span data-stu-id="e3df4-297">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="e3df4-298">Assim, primeiro você `Match` declara o tipo.</span><span class="sxs-lookup"><span data-stu-id="e3df4-298">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="e3df4-299">Como esse tipo depende do padrão fornecido como argumento estático, esse tipo deve ser aninhado dentro da definição de tipo parametrizado:</span><span class="sxs-lookup"><span data-stu-id="e3df4-299">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="e3df4-300">Em seguida, adicione uma propriedade ao tipo Match para cada grupo.</span><span class="sxs-lookup"><span data-stu-id="e3df4-300">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="e3df4-301">Em tempo de execução, <xref:System.Text.RegularExpressions.Match> uma partida é representada como um valor, <xref:System.Text.RegularExpressions.Match.Groups> de modo que a cotação que define a propriedade deve usar a propriedade indexada para obter o grupo relevante.</span><span class="sxs-lookup"><span data-stu-id="e3df4-301">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

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

<span data-ttu-id="e3df4-302">Novamente, observe que você está adicionando a documentação XML à propriedade fornecida.</span><span class="sxs-lookup"><span data-stu-id="e3df4-302">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="e3df4-303">Observe também que uma propriedade `GetterCode` pode ser lida se uma função for `SetterCode` fornecida, e a propriedade pode ser escrita se uma função for fornecida, de modo que a propriedade resultante seja apenas lida.</span><span class="sxs-lookup"><span data-stu-id="e3df4-303">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="e3df4-304">Agora você pode criar um método de `Match` instância que retorna um valor desse tipo:</span><span class="sxs-lookup"><span data-stu-id="e3df4-304">Now you can create an instance method that returns a value of this `Match` type:</span></span>

```fsharp
let matchMethod =
    ProvidedMethod(
        methodName = "Match",
        parameters = [ProvidedParameter("input", typeof<string>)],
        returnType = matchTy,
        invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)

matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

ty.AddMember matchMeth
```

<span data-ttu-id="e3df4-305">Porque você está criando `args.[0]` um método `RegexTyped` de instância, representa a `args.[1]` instância na qual o método está sendo chamado, e é o argumento de entrada.</span><span class="sxs-lookup"><span data-stu-id="e3df4-305">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="e3df4-306">Finalmente, forneça um construtor para que instâncias do tipo fornecido possam ser criadas.</span><span class="sxs-lookup"><span data-stu-id="e3df4-306">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="e3df4-307">O construtor simplesmente apaga para a criação de uma instância padrão .NET Regex, que é novamente encaixotada em um objeto porque `obj` é o apagamento do tipo fornecido.</span><span class="sxs-lookup"><span data-stu-id="e3df4-307">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="e3df4-308">Com essa mudança, o uso da API amostra que especificava anteriormente no tópico funciona conforme esperado.</span><span class="sxs-lookup"><span data-stu-id="e3df4-308">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="e3df4-309">O seguinte código é completo e final:</span><span class="sxs-lookup"><span data-stu-id="e3df4-309">The following code is complete and final:</span></span>

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
                matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

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

### <a name="key-lessons"></a><span data-ttu-id="e3df4-310">Lições-chave</span><span class="sxs-lookup"><span data-stu-id="e3df4-310">Key Lessons</span></span>

<span data-ttu-id="e3df4-311">Esta seção explicou como criar um provedor de tipo que opera em seus parâmetros estáticos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-311">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="e3df4-312">O provedor verifica o parâmetro estático e fornece operações com base em seu valor.</span><span class="sxs-lookup"><span data-stu-id="e3df4-312">The provider checks the static parameter and provides operations based on its value.</span></span>

## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="e3df4-313">Um provedor de tipo que é apoiado por dados locais</span><span class="sxs-lookup"><span data-stu-id="e3df4-313">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="e3df4-314">Frequentemente, você pode querer que os provedores de tipos apresentem APIs com base não apenas em parâmetros estáticos, mas também em informações de sistemas locais ou remotos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-314">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="e3df4-315">Esta seção discute provedores de tipo que são baseados em dados locais, como arquivos de dados locais.</span><span class="sxs-lookup"><span data-stu-id="e3df4-315">This section discusses type providers that are based on local data, such as local data files.</span></span>

### <a name="simple-csv-file-provider"></a><span data-ttu-id="e3df4-316">Provedor de arquivos CSV simples</span><span class="sxs-lookup"><span data-stu-id="e3df4-316">Simple CSV File Provider</span></span>

<span data-ttu-id="e3df4-317">Como exemplo simples, considere um provedor de tipo para acessar dados científicos no formato CSV (Comma Separated Value).</span><span class="sxs-lookup"><span data-stu-id="e3df4-317">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="e3df4-318">Esta seção assume que os arquivos CSV contêm uma linha de cabeçalho seguida de dados de ponto flutuante, como ilustra a tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="e3df4-318">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>

|<span data-ttu-id="e3df4-319">Distância (medidor)</span><span class="sxs-lookup"><span data-stu-id="e3df4-319">Distance (meter)</span></span>|<span data-ttu-id="e3df4-320">Tempo (segundo)</span><span class="sxs-lookup"><span data-stu-id="e3df4-320">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="e3df4-321">50.0</span><span class="sxs-lookup"><span data-stu-id="e3df4-321">50.0</span></span>|<span data-ttu-id="e3df4-322">3.7</span><span class="sxs-lookup"><span data-stu-id="e3df4-322">3.7</span></span>|
|<span data-ttu-id="e3df4-323">100.0</span><span class="sxs-lookup"><span data-stu-id="e3df4-323">100.0</span></span>|<span data-ttu-id="e3df4-324">5.2</span><span class="sxs-lookup"><span data-stu-id="e3df4-324">5.2</span></span>|
|<span data-ttu-id="e3df4-325">150.0</span><span class="sxs-lookup"><span data-stu-id="e3df4-325">150.0</span></span>|<span data-ttu-id="e3df4-326">6.4</span><span class="sxs-lookup"><span data-stu-id="e3df4-326">6.4</span></span>|

<span data-ttu-id="e3df4-327">Esta seção mostra como fornecer um tipo que você `Distance` pode `float<meter>` usar `Time` para obter `float<second>`linhas com uma propriedade de tipo e uma propriedade do tipo .</span><span class="sxs-lookup"><span data-stu-id="e3df4-327">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="e3df4-328">Para simplificar, são feitas as seguintes suposições:</span><span class="sxs-lookup"><span data-stu-id="e3df4-328">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="e3df4-329">Os nomes de cabeçalho são sem unidade ou têm o formulário "Nome (unidade)" e não contêm commas.</span><span class="sxs-lookup"><span data-stu-id="e3df4-329">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="e3df4-330">As unidades são todas unidades do System International (SI) como define o módulo [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#).](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b)</span><span class="sxs-lookup"><span data-stu-id="e3df4-330">Units are all System International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="e3df4-331">As unidades são todas simples (por exemplo, medidor) em vez de compostas (por exemplo, medidor/segundo).</span><span class="sxs-lookup"><span data-stu-id="e3df4-331">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="e3df4-332">Todas as colunas contêm dados de pontos flutuantes.</span><span class="sxs-lookup"><span data-stu-id="e3df4-332">All columns contain floating point data.</span></span>

<span data-ttu-id="e3df4-333">Um provedor mais completo afrouxaria essas restrições.</span><span class="sxs-lookup"><span data-stu-id="e3df4-333">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="e3df4-334">Novamente, o primeiro passo é considerar como a API deve ficar.</span><span class="sxs-lookup"><span data-stu-id="e3df4-334">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="e3df4-335">Dado `info.csv` um arquivo com o conteúdo da tabela anterior (em formato separado por comma), os usuários do provedor devem ser capazes de escrever código que se assemelha ao seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="e3df4-335">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="e3df4-336">Neste caso, o compilador deve converter essas chamadas em algo como o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="e3df4-336">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="e3df4-337">A tradução ideal exigirá que o `CsvFile` provedor de tipos defina um tipo real na montagem do provedor do tipo.</span><span class="sxs-lookup"><span data-stu-id="e3df4-337">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="e3df4-338">Os provedores de tipos geralmente dependem de alguns tipos e métodos auxiliares para envolver uma lógica importante.</span><span class="sxs-lookup"><span data-stu-id="e3df4-338">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="e3df4-339">Como as medidas são apagadas em tempo `float[]` de execução, você pode usar um tipo agravado para uma linha.</span><span class="sxs-lookup"><span data-stu-id="e3df4-339">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="e3df4-340">O compilador tratará diferentes colunas como tendo diferentes tipos de medidas.</span><span class="sxs-lookup"><span data-stu-id="e3df4-340">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="e3df4-341">Por exemplo, a primeira coluna `float<meter>`em nosso exemplo `float<second>`tem tipo , e a segunda tem .</span><span class="sxs-lookup"><span data-stu-id="e3df4-341">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="e3df4-342">No entanto, a representação apagada pode permanecer bastante simples.</span><span class="sxs-lookup"><span data-stu-id="e3df4-342">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="e3df4-343">O código a seguir mostra o núcleo da implementação.</span><span class="sxs-lookup"><span data-stu-id="e3df4-343">The following code shows the core of the implementation.</span></span>

```fsharp
// Simple type wrapping CSV data
type CsvFile(filename) =
    // Cache the sequence of all data lines (all lines but the first)
    let data =
        seq {
            for line in File.ReadAllLines(filename) |> Seq.skip 1 ->
                line.Split(',') |> Array.map float
        }
        |> Seq.cache
    member _.Data = data

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

<span data-ttu-id="e3df4-344">Observe os seguintes pontos sobre a implementação:</span><span class="sxs-lookup"><span data-stu-id="e3df4-344">Note the following points about the implementation:</span></span>

- <span data-ttu-id="e3df4-345">Os construtores sobrecarregados permitem que o arquivo original ou um que tenha um esquema idêntico seja lido.</span><span class="sxs-lookup"><span data-stu-id="e3df4-345">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="e3df4-346">Esse padrão é comum quando você escreve um provedor de tipo para fontes de dados locais ou remotas, e esse padrão permite que um arquivo local seja usado como modelo para dados remotos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-346">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="e3df4-347">Você pode usar o valor [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) que é passado para o construtor do provedor de tipos para resolver nomes de arquivos relativos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-347">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="e3df4-348">Você pode `AddDefinitionLocation` usar o método para definir a localização das propriedades fornecidas.</span><span class="sxs-lookup"><span data-stu-id="e3df4-348">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="e3df4-349">Portanto, se você `Go To Definition` usar em uma propriedade fornecida, o arquivo CSV será aberto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e3df4-349">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="e3df4-350">Você pode `ProvidedMeasureBuilder` usar o tipo para procurar as unidades `float<_>` SI e gerar os tipos relevantes.</span><span class="sxs-lookup"><span data-stu-id="e3df4-350">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="e3df4-351">Lições-chave</span><span class="sxs-lookup"><span data-stu-id="e3df4-351">Key Lessons</span></span>

<span data-ttu-id="e3df4-352">Esta seção explicou como criar um provedor de tipo para uma fonte de dados local com um esquema simples que está contido na própria fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="e3df4-352">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>

## <a name="going-further"></a><span data-ttu-id="e3df4-353">Aprofundamento</span><span class="sxs-lookup"><span data-stu-id="e3df4-353">Going Further</span></span>

<span data-ttu-id="e3df4-354">As seções a seguir incluem sugestões para um estudo mais aprofundado.</span><span class="sxs-lookup"><span data-stu-id="e3df4-354">The following sections include suggestions for further study.</span></span>

### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="e3df4-355">Uma olhada no código compilado para tipos apagados</span><span class="sxs-lookup"><span data-stu-id="e3df4-355">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="e3df4-356">Para dar uma ideia de como o uso do provedor de tipo corresponde ao código emitido, `HelloWorldTypeProvider` consulte a seguinte função usando o que é usado anteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="e3df4-356">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="e3df4-357">Aqui está uma imagem do código resultante descompilado usando ildasm.exe:</span><span class="sxs-lookup"><span data-stu-id="e3df4-357">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

```il
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

<span data-ttu-id="e3df4-358">Como o exemplo mostra, todas `Type1` as `InstanceProperty` menções do tipo e da propriedade foram apagadas, deixando apenas operações nos tipos de tempo de execução envolvidos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-358">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>

### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="e3df4-359">Convenções de Design e Nomeação para Provedores de Tipos</span><span class="sxs-lookup"><span data-stu-id="e3df4-359">Design and Naming Conventions for Type Providers</span></span>

<span data-ttu-id="e3df4-360">Observe as seguintes convenções ao criar provedores de tipos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-360">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="e3df4-361">**Provedores de Protocolos de Conectividade** Em geral, os nomes da maioria dos DLLs do provedor para protocolos de conectividade de `TypeProvider` `TypeProviders`dados e serviços, como conexões OData ou SQL, devem terminar em ou .</span><span class="sxs-lookup"><span data-stu-id="e3df4-361">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="e3df4-362">Por exemplo, use um nome DLL que se assemelhe à seguinte seqüência de string:</span><span class="sxs-lookup"><span data-stu-id="e3df4-362">For example, use a DLL name that resembles the following string:</span></span>

`Fabrikam.Management.BasicTypeProviders.dll`

<span data-ttu-id="e3df4-363">Certifique-se de que seus tipos fornecidos são membros do namespace correspondente e indique o protocolo de conectividade que você implementou:</span><span class="sxs-lookup"><span data-stu-id="e3df4-363">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="e3df4-364">**Provedores de utilidades para codificação geral**.</span><span class="sxs-lookup"><span data-stu-id="e3df4-364">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="e3df4-365">Para um provedor de tipo de utilidade como o de expressões regulares, o provedor de tipo pode fazer parte de uma biblioteca base, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e3df4-365">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="e3df4-366">Neste caso, o tipo fornecido apareceria em um ponto apropriado de acordo com as convenções normais de design .NET:</span><span class="sxs-lookup"><span data-stu-id="e3df4-366">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="e3df4-367">**Fontes de dados de Singleton**.</span><span class="sxs-lookup"><span data-stu-id="e3df4-367">**Singleton Data Sources**.</span></span> <span data-ttu-id="e3df4-368">Alguns provedores de tipo se conectam a uma única fonte de dados dedicada e fornecem apenas dados.</span><span class="sxs-lookup"><span data-stu-id="e3df4-368">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="e3df4-369">Neste caso, você deve `TypeProvider` soltar o sufixo e usar convenções normais para nomear .NET:</span><span class="sxs-lookup"><span data-stu-id="e3df4-369">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="e3df4-370">Para obter mais `GetConnection` informações, consulte a convenção de design descrita mais tarde neste tópico.</span><span class="sxs-lookup"><span data-stu-id="e3df4-370">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>

### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="e3df4-371">Padrões de design para provedores de tipos</span><span class="sxs-lookup"><span data-stu-id="e3df4-371">Design Patterns for Type Providers</span></span>

<span data-ttu-id="e3df4-372">As seções a seguir descrevem padrões de design que você pode usar ao criar provedores de tipos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-372">The following sections describe design patterns you can use when authoring type providers.</span></span>

#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="e3df4-373">O padrão de design getconnection</span><span class="sxs-lookup"><span data-stu-id="e3df4-373">The GetConnection Design Pattern</span></span>

<span data-ttu-id="e3df4-374">A maioria dos provedores `GetConnection` de tipos deve ser escrita para usar o padrão usado pelos provedores de tipo em FSharp.Data.TypeProviders.dll, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e3df4-374">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="e3df4-375">Provedores de tipo apoiados por dados e serviços remotos</span><span class="sxs-lookup"><span data-stu-id="e3df4-375">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="e3df4-376">Antes de criar um provedor de tipo que seja apoiado por dados e serviços remotos, você deve considerar uma série de problemas que são inerentes à programação conectada.</span><span class="sxs-lookup"><span data-stu-id="e3df4-376">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="e3df4-377">Essas questões incluem as seguintes considerações:</span><span class="sxs-lookup"><span data-stu-id="e3df4-377">These issues include the following considerations:</span></span>

- <span data-ttu-id="e3df4-378">mapeamento esquema</span><span class="sxs-lookup"><span data-stu-id="e3df4-378">schema mapping</span></span>

- <span data-ttu-id="e3df4-379">vida e invalidação na presença de mudança de esquema</span><span class="sxs-lookup"><span data-stu-id="e3df4-379">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="e3df4-380">cache esquema</span><span class="sxs-lookup"><span data-stu-id="e3df4-380">schema caching</span></span>

- <span data-ttu-id="e3df4-381">implementações assíncronas de operações de acesso a dados</span><span class="sxs-lookup"><span data-stu-id="e3df4-381">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="e3df4-382">suporte a consultas, incluindo consultas LINQ</span><span class="sxs-lookup"><span data-stu-id="e3df4-382">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="e3df4-383">credenciais e autenticação</span><span class="sxs-lookup"><span data-stu-id="e3df4-383">credentials and authentication</span></span>

<span data-ttu-id="e3df4-384">Este tópico não explora mais essas questões.</span><span class="sxs-lookup"><span data-stu-id="e3df4-384">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="e3df4-385">Técnicas adicionais de autoria</span><span class="sxs-lookup"><span data-stu-id="e3df4-385">Additional Authoring Techniques</span></span>

<span data-ttu-id="e3df4-386">Quando você escreve seus próprios provedores de tipo, você pode querer usar as seguintes técnicas adicionais.</span><span class="sxs-lookup"><span data-stu-id="e3df4-386">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="e3df4-387">Criando tipos e membros demanda</span><span class="sxs-lookup"><span data-stu-id="e3df4-387">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="e3df4-388">A API ProvidedType tem versões atrasadas do AddMember.</span><span class="sxs-lookup"><span data-stu-id="e3df4-388">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="e3df4-389">Essas versões são usadas para criar espaços demanda de tipos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-389">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="e3df4-390">Fornecendo tipos de array e instanciações genéricas do tipo</span><span class="sxs-lookup"><span data-stu-id="e3df4-390">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="e3df4-391">Você faz membros fornecidos (cujas assinaturas incluem tipos de matriz, tipos de byref `MakePointerType`e `MakeGenericType` instanciações de tipos genéricos) usando o normal <xref:System.Type> `MakeArrayType`, e em qualquer instância de , incluindo `ProvidedTypeDefinitions`.</span><span class="sxs-lookup"><span data-stu-id="e3df4-391">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="e3df4-392">Em alguns casos, você pode `ProvidedTypeBuilder.MakeGenericType`ter que usar o ajudante em .</span><span class="sxs-lookup"><span data-stu-id="e3df4-392">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="e3df4-393">Consulte a [documentação do Provedor de Tipo SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="e3df4-393">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="e3df4-394">Fornecendo Anotações de Unidade de Medida</span><span class="sxs-lookup"><span data-stu-id="e3df4-394">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="e3df4-395">A API ProvidedTypes fornece ajuda para fornecer anotações de medida.</span><span class="sxs-lookup"><span data-stu-id="e3df4-395">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="e3df4-396">Por exemplo, para `float<kg>`fornecer o tipo, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="e3df4-396">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="e3df4-397">Para fornecer `Nullable<decimal<kg/m^2>>`o tipo, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="e3df4-397">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="e3df4-398">Acessando recursos locais de projeto ou script</span><span class="sxs-lookup"><span data-stu-id="e3df4-398">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="e3df4-399">Cada instância de um provedor `TypeProviderConfig` de tipo pode receber um valor durante a construção.</span><span class="sxs-lookup"><span data-stu-id="e3df4-399">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="e3df4-400">Este valor contém a "pasta de resolução" para o provedor (ou seja, a pasta do projeto para a compilação ou o diretório que contém um script), a lista de conjuntos referenciados e outras informações.</span><span class="sxs-lookup"><span data-stu-id="e3df4-400">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="e3df4-401">Invalidação</span><span class="sxs-lookup"><span data-stu-id="e3df4-401">Invalidation</span></span>

<span data-ttu-id="e3df4-402">Os provedores podem levantar sinais de invalidação para notificar o serviço de idioma F# de que as suposições do esquema podem ter mudado.</span><span class="sxs-lookup"><span data-stu-id="e3df4-402">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="e3df4-403">Quando ocorre a invalidação, uma verificação de tipo é refeita se o provedor estiver hospedado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e3df4-403">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="e3df4-404">Esse sinal será ignorado quando o provedor estiver hospedado no F# Interactive ou no F# Compiler (fsc.exe).</span><span class="sxs-lookup"><span data-stu-id="e3df4-404">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="e3df4-405">Informações sobre esquemas de cache</span><span class="sxs-lookup"><span data-stu-id="e3df4-405">Caching Schema Information</span></span>

<span data-ttu-id="e3df4-406">Os provedores devem, muitas vezes, armazenar acesso a informações de esquema.</span><span class="sxs-lookup"><span data-stu-id="e3df4-406">Providers must often cache access to schema information.</span></span> <span data-ttu-id="e3df4-407">Os dados armazenados em cache devem ser armazenados usando um nome de arquivo que é dado como parâmetro estático ou como dados do usuário.</span><span class="sxs-lookup"><span data-stu-id="e3df4-407">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="e3df4-408">Um exemplo de cache de `LocalSchemaFile` esquema é o parâmetro `FSharp.Data.TypeProviders` nos provedores do tipo na montagem.</span><span class="sxs-lookup"><span data-stu-id="e3df4-408">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="e3df4-409">Na implementação desses provedores, este parâmetro estático orienta o provedor de tipo a usar as informações do esquema no arquivo local especificado em vez de acessar a fonte de dados pela rede.</span><span class="sxs-lookup"><span data-stu-id="e3df4-409">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="e3df4-410">Para usar informações de esquema em cache, você `ForceUpdate` também `false`deve definir o parâmetro estático para .</span><span class="sxs-lookup"><span data-stu-id="e3df4-410">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="e3df4-411">Você pode usar uma técnica semelhante para permitir o acesso a dados on-line e off-line.</span><span class="sxs-lookup"><span data-stu-id="e3df4-411">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="e3df4-412">Montagem de apoio</span><span class="sxs-lookup"><span data-stu-id="e3df4-412">Backing Assembly</span></span>

<span data-ttu-id="e3df4-413">Quando você compila `.dll` `.exe` um ou arquivo, o arquivo de backup .dll para tipos gerados é estáticamente vinculado ao conjunto resultante.</span><span class="sxs-lookup"><span data-stu-id="e3df4-413">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="e3df4-414">Este link é criado copiando as definições do tipo Idioma Intermediário (IL) e quaisquer recursos gerenciados da montagem de apoio para a montagem final.</span><span class="sxs-lookup"><span data-stu-id="e3df4-414">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="e3df4-415">Quando você usa F# Interactive, o arquivo de backup .dll não é copiado e, em vez disso, é carregado diretamente no processo F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="e3df4-415">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="e3df4-416">Exceções e Diagnósticos de Provedores de Tipo</span><span class="sxs-lookup"><span data-stu-id="e3df4-416">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="e3df4-417">Todos os usos de todos os membros dos tipos fornecidos podem lançar exceções.</span><span class="sxs-lookup"><span data-stu-id="e3df4-417">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="e3df4-418">Em todos os casos, se um provedor de tipo lançar uma exceção, o compilador host atribui o erro a um provedor de tipo específico.</span><span class="sxs-lookup"><span data-stu-id="e3df4-418">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="e3df4-419">As exceções do provedor de tipos nunca devem resultar em erros internos do compilador.</span><span class="sxs-lookup"><span data-stu-id="e3df4-419">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="e3df4-420">Os provedores de tipos não podem relatar avisos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-420">Type providers can't report warnings.</span></span>

- <span data-ttu-id="e3df4-421">Quando um provedor de tipo está hospedado no compilador F#, em um ambiente de desenvolvimento F# ou no F# Interactive, todas as exceções desse provedor são capturadas.</span><span class="sxs-lookup"><span data-stu-id="e3df4-421">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="e3df4-422">A propriedade Mensagem é sempre o texto de erro, e nenhum rastreamento de pilha é exibido.</span><span class="sxs-lookup"><span data-stu-id="e3df4-422">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="e3df4-423">Se você vai abrir uma exceção, você pode `System.NotSupportedException`lançar `System.IO.IOException` `System.Exception`os seguintes exemplos: , , .</span><span class="sxs-lookup"><span data-stu-id="e3df4-423">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="e3df4-424">Fornecendo tipos gerados</span><span class="sxs-lookup"><span data-stu-id="e3df4-424">Providing Generated Types</span></span>

<span data-ttu-id="e3df4-425">Até agora, este documento explicou como fornecer tipos apagados.</span><span class="sxs-lookup"><span data-stu-id="e3df4-425">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="e3df4-426">Você também pode usar o mecanismo do provedor de tipo em F# para fornecer tipos gerados, que são adicionados como definições reais do tipo .NET no programa dos usuários.</span><span class="sxs-lookup"><span data-stu-id="e3df4-426">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="e3df4-427">Você deve consultar os tipos gerados fornecidos usando uma definição de tipo.</span><span class="sxs-lookup"><span data-stu-id="e3df4-427">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="e3df4-428">O código auxiliar ProvidedTypes-0.2 que faz parte da versão F# 3.0 tem apenas suporte limitado para fornecer tipos gerados.</span><span class="sxs-lookup"><span data-stu-id="e3df4-428">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="e3df4-429">As seguintes instruções devem ser verdadeiras para uma definição de tipo gerada:</span><span class="sxs-lookup"><span data-stu-id="e3df4-429">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="e3df4-430">`isErased` deve ser definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="e3df4-430">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="e3df4-431">O tipo gerado deve ser adicionado `ProvidedAssembly()`a um recém-construído, que representa um recipiente para fragmentos de código gerados.</span><span class="sxs-lookup"><span data-stu-id="e3df4-431">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="e3df4-432">O provedor deve ter um conjunto que tenha um arquivo .NET .dll de backup real com um arquivo .dll correspondente no disco.</span><span class="sxs-lookup"><span data-stu-id="e3df4-432">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>

## <a name="rules-and-limitations"></a><span data-ttu-id="e3df4-433">Regras e Limitações</span><span class="sxs-lookup"><span data-stu-id="e3df4-433">Rules and Limitations</span></span>

<span data-ttu-id="e3df4-434">Ao escrever provedores de tipo, tenha em mente as seguintes regras e limitações.</span><span class="sxs-lookup"><span data-stu-id="e3df4-434">When you write type providers, keep the following rules and limitations in mind.</span></span>

### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="e3df4-435">Os tipos fornecidos devem ser acessíveis</span><span class="sxs-lookup"><span data-stu-id="e3df4-435">Provided types must be reachable</span></span>

<span data-ttu-id="e3df4-436">Todos os tipos fornecidos devem ser acessíveis a partir dos tipos não aninhados.</span><span class="sxs-lookup"><span data-stu-id="e3df4-436">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="e3df4-437">Os tipos não aninhados são `TypeProviderForNamespaces` dados na chamada `AddNamespace`para o construtor ou uma chamada para .</span><span class="sxs-lookup"><span data-stu-id="e3df4-437">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="e3df4-438">Por exemplo, se o `StaticClass.P : T`provedor fornecer um tipo, você deve garantir que T seja um tipo não aninhado ou aninhado um.</span><span class="sxs-lookup"><span data-stu-id="e3df4-438">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="e3df4-439">Por exemplo, alguns provedores `DataTypes` têm uma `T1, T2, T3, ...` classe estática como a que contém esses tipos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-439">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="e3df4-440">Caso contrário, o erro diz que uma referência ao tipo T no conjunto A foi encontrada, mas o tipo não pôde ser encontrado naquele conjunto.</span><span class="sxs-lookup"><span data-stu-id="e3df4-440">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="e3df4-441">Se esse erro aparecer, verifique se todos os seus subtipos podem ser alcançados a partir dos tipos do provedor.</span><span class="sxs-lookup"><span data-stu-id="e3df4-441">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="e3df4-442">Nota: `T1, T2, T3...` Esses tipos são referidos como os tipos *on-the-fly.*</span><span class="sxs-lookup"><span data-stu-id="e3df4-442">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="e3df4-443">Lembre-se de colocá-los em um namespace acessível ou um tipo de pai.</span><span class="sxs-lookup"><span data-stu-id="e3df4-443">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="e3df4-444">Limitações do Mecanismo do Provedor de Tipo</span><span class="sxs-lookup"><span data-stu-id="e3df4-444">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="e3df4-445">O mecanismo do provedor de tipo em F# tem as seguintes limitações:</span><span class="sxs-lookup"><span data-stu-id="e3df4-445">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="e3df4-446">A infra-estrutura subjacente para provedores de tipo em F# não suporta tipos genéricos fornecidos ou métodos genéricos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-446">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="e3df4-447">O mecanismo não suporta tipos aninhados com parâmetros estáticos.</span><span class="sxs-lookup"><span data-stu-id="e3df4-447">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="e3df4-448">Dicas de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="e3df4-448">Development Tips</span></span>

<span data-ttu-id="e3df4-449">Você pode achar as seguintes dicas úteis durante o processo de desenvolvimento:</span><span class="sxs-lookup"><span data-stu-id="e3df4-449">You might find the following tips helpful during the development process:</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="e3df4-450">Execute duas instâncias do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e3df4-450">Run two instances of Visual Studio</span></span>

<span data-ttu-id="e3df4-451">Você pode desenvolver o provedor de tipo em uma instância e testar o provedor na outra, porque o IDE de teste fará um bloqueio no arquivo .dll que impede que o provedor do tipo seja reconstruído.</span><span class="sxs-lookup"><span data-stu-id="e3df4-451">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="e3df4-452">Assim, você deve fechar a segunda instância do Visual Studio enquanto o provedor é construído em primeira instância, e então você deve reabrir a segunda instância após a construção do provedor.</span><span class="sxs-lookup"><span data-stu-id="e3df4-452">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="e3df4-453">Provedores do tipo de depuração usando invocações de fsc.exe</span><span class="sxs-lookup"><span data-stu-id="e3df4-453">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="e3df4-454">Você pode invocar provedores de tipos usando as seguintes ferramentas:</span><span class="sxs-lookup"><span data-stu-id="e3df4-454">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="e3df4-455">fsc.exe (compilador de linha de comando F#)</span><span class="sxs-lookup"><span data-stu-id="e3df4-455">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="e3df4-456">fsi.exe (Compilador Interativo F#)</span><span class="sxs-lookup"><span data-stu-id="e3df4-456">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="e3df4-457">devenv.exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="e3df4-457">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="e3df4-458">Muitas vezes você pode depurar provedores de tipo mais facilmente usando fsc.exe em um arquivo de script de teste (por exemplo, script.fsx).</span><span class="sxs-lookup"><span data-stu-id="e3df4-458">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="e3df4-459">Você pode iniciar um depurador a partir de um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="e3df4-459">You can launch a debugger from a command prompt.</span></span>

```console
devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="e3df4-460">Você pode usar o registro impresso-to-stdout.</span><span class="sxs-lookup"><span data-stu-id="e3df4-460">You can use print-to-stdout logging.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3df4-461">Confira também</span><span class="sxs-lookup"><span data-stu-id="e3df4-461">See also</span></span>

- [<span data-ttu-id="e3df4-462">Provedores de Tipos</span><span class="sxs-lookup"><span data-stu-id="e3df4-462">Type Providers</span></span>](index.md)
- [<span data-ttu-id="e3df4-463">O provedor de tipo SDK</span><span class="sxs-lookup"><span data-stu-id="e3df4-463">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
