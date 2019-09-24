---
title: 'Tutorial: Criar um provedor de tipos'
description: Saiba como criar seus próprios F# provedores de tipo no F# 3,0 examinando vários provedores de tipo simples para ilustrar os conceitos básicos.
ms.date: 02/02/2019
ms.openlocfilehash: 8d1a1fedf03437ccbacd40616cc7dc3e1da435b2
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214277"
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="2f13e-103">Tutorial: Criar um provedor de tipos</span><span class="sxs-lookup"><span data-stu-id="2f13e-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="2f13e-104">O mecanismo do provedor de F# tipos no é uma parte significativa de seu suporte para a programação de informações ricas.</span><span class="sxs-lookup"><span data-stu-id="2f13e-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="2f13e-105">Este tutorial explica como criar seus próprios provedores de tipo orientando você pelo desenvolvimento de vários provedores de tipo simples para ilustrar os conceitos básicos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="2f13e-106">Para obter mais informações sobre o mecanismo do provedor F#de tipos no, consulte [provedores de tipos](index.md).</span><span class="sxs-lookup"><span data-stu-id="2f13e-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="2f13e-107">O F# ecossistema contém um intervalo de provedores de tipos para serviços de dados empresariais e da Internet comumente usados.</span><span class="sxs-lookup"><span data-stu-id="2f13e-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="2f13e-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2f13e-108">For example:</span></span>

- <span data-ttu-id="2f13e-109">O [FSharp. Data](https://fsharp.github.io/FSharp.Data/) inclui provedores de tipos para formatos de documento JSON, XML, CSV e HTML.</span><span class="sxs-lookup"><span data-stu-id="2f13e-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="2f13e-110">O [Sqlfornecetor](https://fsprojects.github.io/SQLProvider/) fornece acesso fortemente tipado a bancos de dados SQL por meio de um F# mapeamento de objeto e consultas LINQ em relação a essas fontes.</span><span class="sxs-lookup"><span data-stu-id="2f13e-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="2f13e-111">O [FSharp. Data. SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) tem um conjunto de provedores de tipos para a inserção verificada em tempo de compilação do F#T-SQL no.</span><span class="sxs-lookup"><span data-stu-id="2f13e-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="2f13e-112">[FSharp. Data. TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) é um conjunto mais antigo de provedores de tipo para uso somente com .NET Framework programação para acessar serviços de dados SQL, Entity Framework, ODATA e WSDL.</span><span class="sxs-lookup"><span data-stu-id="2f13e-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="2f13e-113">Quando necessário, você pode criar provedores de tipo personalizados ou pode referenciar provedores de tipos que outras pessoas criaram.</span><span class="sxs-lookup"><span data-stu-id="2f13e-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="2f13e-114">Por exemplo, sua organização pode ter um serviço de dados que fornece um número grande e crescente de conjuntos de dados nomeados, cada um com seu próprio esquema de dados estável.</span><span class="sxs-lookup"><span data-stu-id="2f13e-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="2f13e-115">Você pode criar um provedor de tipos que lê os esquemas e apresenta os conjuntos de dados atuais para o programador de uma maneira fortemente tipada.</span><span class="sxs-lookup"><span data-stu-id="2f13e-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="2f13e-116">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="2f13e-116">Before You Start</span></span>

<span data-ttu-id="2f13e-117">O mecanismo do provedor de tipos é projetado principalmente para injetar dados estáveis e espaços de informações F# de serviço na experiência de programação.</span><span class="sxs-lookup"><span data-stu-id="2f13e-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="2f13e-118">Esse mecanismo não é projetado para injetar espaços de informações cujo esquema muda durante a execução do programa de maneiras relevantes para a lógica do programa.</span><span class="sxs-lookup"><span data-stu-id="2f13e-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="2f13e-119">Além disso, o mecanismo não é projetado para a metaprogramação entre idiomas, mesmo que esse domínio contenha alguns usos válidos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="2f13e-120">Você deve usar esse mecanismo somente quando necessário e onde o desenvolvimento de um provedor de tipo produz um valor muito alto.</span><span class="sxs-lookup"><span data-stu-id="2f13e-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="2f13e-121">Você deve evitar escrever um provedor de tipos em que um esquema não esteja disponível.</span><span class="sxs-lookup"><span data-stu-id="2f13e-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="2f13e-122">Da mesma forma, você deve evitar escrever um provedor de tipos em que uma biblioteca .NET comum (ou até mesmo uma existente) seria suficiente.</span><span class="sxs-lookup"><span data-stu-id="2f13e-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="2f13e-123">Antes de começar, você pode fazer as seguintes perguntas:</span><span class="sxs-lookup"><span data-stu-id="2f13e-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="2f13e-124">Você tem um esquema para sua fonte de informações?</span><span class="sxs-lookup"><span data-stu-id="2f13e-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="2f13e-125">Nesse caso, qual é o mapeamento para o F# sistema de tipos do e .net?</span><span class="sxs-lookup"><span data-stu-id="2f13e-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="2f13e-126">Você pode usar uma API existente (digitada dinamicamente) como um ponto de partida para sua implementação?</span><span class="sxs-lookup"><span data-stu-id="2f13e-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="2f13e-127">Você e sua organização têm usos suficientes do provedor de tipos para tornar a sua leitura vale a pena?</span><span class="sxs-lookup"><span data-stu-id="2f13e-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="2f13e-128">Uma biblioteca .NET normal atende às suas necessidades?</span><span class="sxs-lookup"><span data-stu-id="2f13e-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="2f13e-129">Quanto seu esquema vai mudar?</span><span class="sxs-lookup"><span data-stu-id="2f13e-129">How much will your schema change?</span></span>

- <span data-ttu-id="2f13e-130">Ele será alterado durante a codificação?</span><span class="sxs-lookup"><span data-stu-id="2f13e-130">Will it change during coding?</span></span>

- <span data-ttu-id="2f13e-131">Ele será alterado entre as sessões de codificação?</span><span class="sxs-lookup"><span data-stu-id="2f13e-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="2f13e-132">Ele será alterado durante a execução do programa?</span><span class="sxs-lookup"><span data-stu-id="2f13e-132">Will it change during program execution?</span></span>

<span data-ttu-id="2f13e-133">Os provedores de tipos são mais adequados para situações em que o esquema é estável em tempo de execução e durante a vida útil do código compilado.</span><span class="sxs-lookup"><span data-stu-id="2f13e-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>

## <a name="a-simple-type-provider"></a><span data-ttu-id="2f13e-134">Um provedor de tipo simples</span><span class="sxs-lookup"><span data-stu-id="2f13e-134">A Simple Type Provider</span></span>

<span data-ttu-id="2f13e-135">Este exemplo é Samples. HelloWorldTypeProvider, semelhante aos exemplos no `examples` diretório do SDK do [ F# provedor de tipos](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span><span class="sxs-lookup"><span data-stu-id="2f13e-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="2f13e-136">O provedor disponibiliza um "espaço de tipo" que contém os tipos apagados 100, como mostra o código a seguir F# , usando a sintaxe de assinatura e omitindo os `Type1`detalhes para todos, exceto.</span><span class="sxs-lookup"><span data-stu-id="2f13e-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="2f13e-137">Para obter mais informações sobre tipos apagados, consulte [detalhes sobre os tipos fornecidos e apagados](#details-about-erased-provided-types) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="2f13e-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

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

<span data-ttu-id="2f13e-138">Observe que o conjunto de tipos e membros fornecidos é estaticamente conhecido.</span><span class="sxs-lookup"><span data-stu-id="2f13e-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="2f13e-139">Este exemplo não aproveita a capacidade dos provedores de fornecer tipos que dependem de um esquema.</span><span class="sxs-lookup"><span data-stu-id="2f13e-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="2f13e-140">A implementação do provedor de tipos é descrita no código a seguir, e os detalhes são abordados nas seções posteriores deste tópico.</span><span class="sxs-lookup"><span data-stu-id="2f13e-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>

> [!WARNING]
> <span data-ttu-id="2f13e-141">Pode haver diferenças entre esse código e os exemplos online.</span><span class="sxs-lookup"><span data-stu-id="2f13e-141">There may be differences between this code and the online samples.</span></span>

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

<span data-ttu-id="2f13e-142">Para usar esse provedor, abra uma instância separada do Visual Studio, crie um F# script e, em seguida, adicione uma referência ao provedor do seu script usando #r como mostra o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="2f13e-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

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

<span data-ttu-id="2f13e-143">Em seguida, procure os tipos no `Samples.HelloWorldTypeProvider` namespace que o provedor de tipos gerou.</span><span class="sxs-lookup"><span data-stu-id="2f13e-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="2f13e-144">Antes de recompilar o provedor, verifique se você fechou todas as instâncias do Visual Studio e F# interativas que estão usando a DLL do provedor.</span><span class="sxs-lookup"><span data-stu-id="2f13e-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="2f13e-145">Caso contrário, ocorrerá um erro de compilação porque a DLL de saída será bloqueada.</span><span class="sxs-lookup"><span data-stu-id="2f13e-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="2f13e-146">Para depurar esse provedor usando instruções PRINT, crie um script que expõe um problema com o provedor e, em seguida, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="2f13e-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="2f13e-147">Para depurar esse provedor usando o Visual Studio, abra o Prompt de Comando do Desenvolvedor para Visual Studio com credenciais administrativas e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="2f13e-147">To debug this provider by using Visual Studio, open the Developer Command Prompt for Visual Studio with administrative credentials, and run the following command:</span></span>

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="2f13e-148">Como alternativa, abra o Visual Studio, abra o menu Depurar, escolha `Debug/Attach to process…`e anexe a outro `devenv` processo em que você está editando o script.</span><span class="sxs-lookup"><span data-stu-id="2f13e-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="2f13e-149">Usando esse método, você pode direcionar com mais facilidade uma lógica específica no provedor de tipos, digitando expressões interativamente na segunda instância (com IntelliSense completo e outros recursos).</span><span class="sxs-lookup"><span data-stu-id="2f13e-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="2f13e-150">Você pode desabilitar a depuração de Apenas Meu Código para identificar melhor os erros no código gerado.</span><span class="sxs-lookup"><span data-stu-id="2f13e-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="2f13e-151">Para obter informações sobre como habilitar ou desabilitar esse recurso, consulte [navegando pelo código com o depurador](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span><span class="sxs-lookup"><span data-stu-id="2f13e-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="2f13e-152">Além disso, você também pode definir a captura de exceção de primeira chance `Debug` abrindo o menu e `Exceptions` escolhendo ou escolhendo as teclas CTRL + ALT + E para abrir a `Exceptions` caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="2f13e-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="2f13e-153">Nessa caixa de diálogo, em `Common Language Runtime Exceptions`, marque a `Thrown` caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="2f13e-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>

### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="2f13e-154">Implementação do provedor de tipos</span><span class="sxs-lookup"><span data-stu-id="2f13e-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="2f13e-155">Esta seção orienta você pelas seções principais da implementação do provedor de tipos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="2f13e-156">Primeiro, você define o tipo para o próprio provedor de tipo personalizado:</span><span class="sxs-lookup"><span data-stu-id="2f13e-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="2f13e-157">Esse tipo deve ser público e você deve marcá-lo com o atributo [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) para que o compilador reconheça o provedor de tipos quando um F# projeto separado referencia o assembly que contém o tipo.</span><span class="sxs-lookup"><span data-stu-id="2f13e-157">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="2f13e-158">O parâmetro *config* é opcional e, se presente, contém informações de configuração contextuais para a instância do provedor de F# tipos que o compilador cria.</span><span class="sxs-lookup"><span data-stu-id="2f13e-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="2f13e-159">Em seguida, implemente a interface [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) .</span><span class="sxs-lookup"><span data-stu-id="2f13e-159">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="2f13e-160">Nesse caso, você usa o `TypeProviderForNamespaces` tipo `ProvidedTypes` da API como um tipo base.</span><span class="sxs-lookup"><span data-stu-id="2f13e-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="2f13e-161">Esse tipo de auxiliar pode fornecer uma coleção finita de namespaces fornecidos com mais adiantamento, cada um dos quais contém diretamente um número finito de tipos fixos e fornecidos com mais adiantamento.</span><span class="sxs-lookup"><span data-stu-id="2f13e-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="2f13e-162">Nesse contexto, *o provedor gera* com mais regularidade tipos, mesmo que eles não sejam necessários ou usados.</span><span class="sxs-lookup"><span data-stu-id="2f13e-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="2f13e-163">Em seguida, defina valores privados locais que especificam o namespace para os tipos fornecidos e localize o próprio assembly do provedor de tipos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="2f13e-164">Esse assembly é usado posteriormente como o tipo de pai lógico dos tipos apagados que são fornecidos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="2f13e-165">Em seguida, crie uma função para fornecer cada um dos tipos type1... Type100.</span><span class="sxs-lookup"><span data-stu-id="2f13e-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="2f13e-166">Essa função é explicada em mais detalhes posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="2f13e-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="2f13e-167">Em seguida, gere os tipos fornecidos 100:</span><span class="sxs-lookup"><span data-stu-id="2f13e-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="2f13e-168">Em seguida, adicione os tipos como um namespace fornecido:</span><span class="sxs-lookup"><span data-stu-id="2f13e-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="2f13e-169">Por fim, adicione um atributo de assembly que indica que você está criando uma DLL de provedor de tipos:</span><span class="sxs-lookup"><span data-stu-id="2f13e-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="2f13e-170">Fornecendo um tipo e seus membros</span><span class="sxs-lookup"><span data-stu-id="2f13e-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="2f13e-171">A `makeOneProvidedType` função faz o trabalho real de fornecer um dos tipos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) =
…
```

<span data-ttu-id="2f13e-172">Esta etapa explica a implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="2f13e-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="2f13e-173">Primeiro, crie o tipo fornecido (por exemplo, type1, quando n = 1 ou Type57, quando n = 57).</span><span class="sxs-lookup"><span data-stu-id="2f13e-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="2f13e-174">Você deve observar os seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="2f13e-174">You should note the following points:</span></span>

- <span data-ttu-id="2f13e-175">Esse tipo fornecido é apagado.</span><span class="sxs-lookup"><span data-stu-id="2f13e-175">This provided type is erased.</span></span>  <span data-ttu-id="2f13e-176">Como você indica que o tipo base é `obj`, as instâncias serão exibidas como valores do tipo [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) no código compilado.</span><span class="sxs-lookup"><span data-stu-id="2f13e-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="2f13e-177">Ao especificar um tipo não aninhado, você deve especificar o assembly e o namespace.</span><span class="sxs-lookup"><span data-stu-id="2f13e-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="2f13e-178">Para tipos apagados, o assembly deve ser o próprio assembly do provedor de tipos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="2f13e-179">Em seguida, adicione a documentação XML ao tipo.</span><span class="sxs-lookup"><span data-stu-id="2f13e-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="2f13e-180">Esta documentação está atrasada, ou seja, calculada sob demanda se o compilador do host precisar dela.</span><span class="sxs-lookup"><span data-stu-id="2f13e-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="2f13e-181">Em seguida, você adiciona uma propriedade estática fornecida ao tipo:</span><span class="sxs-lookup"><span data-stu-id="2f13e-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="2f13e-182">Obter essa propriedade sempre será avaliada como a cadeia de caracteres "Olá!".</span><span class="sxs-lookup"><span data-stu-id="2f13e-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="2f13e-183">O `GetterCode` para a propriedade usa uma F# cotação, que representa o código que o compilador host gera para obter a propriedade.</span><span class="sxs-lookup"><span data-stu-id="2f13e-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="2f13e-184">Para obter mais informações sobre cotações, consulte [Code RequotasF#()](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span><span class="sxs-lookup"><span data-stu-id="2f13e-184">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="2f13e-185">Adicione a documentação XML à propriedade.</span><span class="sxs-lookup"><span data-stu-id="2f13e-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="2f13e-186">Agora, anexe a propriedade fornecida ao tipo fornecido.</span><span class="sxs-lookup"><span data-stu-id="2f13e-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="2f13e-187">Você deve anexar um membro fornecido a um e apenas um tipo.</span><span class="sxs-lookup"><span data-stu-id="2f13e-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="2f13e-188">Caso contrário, o membro nunca estará acessível.</span><span class="sxs-lookup"><span data-stu-id="2f13e-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="2f13e-189">Agora, crie um construtor fornecido que não usa parâmetros.</span><span class="sxs-lookup"><span data-stu-id="2f13e-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="2f13e-190">O `InvokeCode` para o construtor retorna uma F# cotação, que representa o código que o compilador host gera quando o construtor é chamado.</span><span class="sxs-lookup"><span data-stu-id="2f13e-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="2f13e-191">Por exemplo, você pode usar o seguinte construtor:</span><span class="sxs-lookup"><span data-stu-id="2f13e-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="2f13e-192">Uma instância do tipo fornecido será criada com os dados subjacentes "os dados do objeto".</span><span class="sxs-lookup"><span data-stu-id="2f13e-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="2f13e-193">O código entre aspas inclui uma conversão para [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) porque esse tipo é a eliminação desse tipo fornecido (como especificado quando você declarou o tipo fornecido).</span><span class="sxs-lookup"><span data-stu-id="2f13e-193">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="2f13e-194">Adicione a documentação XML ao construtor e adicione o construtor fornecido ao tipo fornecido:</span><span class="sxs-lookup"><span data-stu-id="2f13e-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="2f13e-195">Crie um segundo construtor fornecido que aceite um parâmetro:</span><span class="sxs-lookup"><span data-stu-id="2f13e-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="2f13e-196">O `InvokeCode` para o construtor retorna novamente uma F# cotação, que representa o código gerado pelo compilador de host para uma chamada para o método.</span><span class="sxs-lookup"><span data-stu-id="2f13e-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="2f13e-197">Por exemplo, você pode usar o seguinte construtor:</span><span class="sxs-lookup"><span data-stu-id="2f13e-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="2f13e-198">Uma instância do tipo fornecido é criada com os dados subjacentes "dez".</span><span class="sxs-lookup"><span data-stu-id="2f13e-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="2f13e-199">Talvez você já tenha notado que a `InvokeCode` função retorna uma cotação.</span><span class="sxs-lookup"><span data-stu-id="2f13e-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="2f13e-200">A entrada para essa função é uma lista de expressões, uma por parâmetro de construtor.</span><span class="sxs-lookup"><span data-stu-id="2f13e-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="2f13e-201">Nesse caso, uma expressão que representa o valor de parâmetro único está disponível em `args.[0]`.</span><span class="sxs-lookup"><span data-stu-id="2f13e-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="2f13e-202">O código para uma chamada para o Construtor impõe o valor de retorno para o tipo `obj`apagado.</span><span class="sxs-lookup"><span data-stu-id="2f13e-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="2f13e-203">Depois de adicionar o segundo construtor fornecido ao tipo, você cria uma propriedade de instância fornecida:</span><span class="sxs-lookup"><span data-stu-id="2f13e-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="2f13e-204">Obter essa propriedade retornará o comprimento da cadeia de caracteres, que é o objeto de representação.</span><span class="sxs-lookup"><span data-stu-id="2f13e-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="2f13e-205">A `GetterCode` propriedade retorna uma F# cotação que especifica o código que o compilador host gera para obter a propriedade.</span><span class="sxs-lookup"><span data-stu-id="2f13e-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="2f13e-206">Como `InvokeCode`, a `GetterCode` função retorna uma cotação.</span><span class="sxs-lookup"><span data-stu-id="2f13e-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="2f13e-207">O compilador do host chama essa função com uma lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="2f13e-208">Nesse caso, os argumentos incluem apenas a única expressão que representa a instância sobre a qual o getter está sendo chamado, que você pode acessar usando `args.[0]`.</span><span class="sxs-lookup"><span data-stu-id="2f13e-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.</span></span> <span data-ttu-id="2f13e-209">A implementação de `GetterCode` , em seguida, se unirá à cotação resultante no tipo `obj`apagado, e uma conversão é usada para satisfazer o mecanismo do compilador para verificar os tipos que o objeto é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2f13e-209">The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="2f13e-210">A próxima parte de `makeOneProvidedType` fornece um método de instância com um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2f13e-210">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

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

<span data-ttu-id="2f13e-211">Por fim, crie um tipo aninhado que contenha 100 propriedades aninhadas.</span><span class="sxs-lookup"><span data-stu-id="2f13e-211">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="2f13e-212">A criação desse tipo aninhado e suas propriedades são atrasadas, ou seja, calculadas sob demanda.</span><span class="sxs-lookup"><span data-stu-id="2f13e-212">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

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

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="2f13e-213">Detalhes sobre os tipos fornecidos e apagados</span><span class="sxs-lookup"><span data-stu-id="2f13e-213">Details about Erased Provided Types</span></span>

<span data-ttu-id="2f13e-214">O exemplo nesta seção fornece apenas os *tipos fornecidos e apagados*, que são particularmente úteis nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="2f13e-214">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="2f13e-215">Quando você está escrevendo um provedor para um espaço de informações que contém apenas dados e métodos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-215">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="2f13e-216">Quando você está escrevendo um provedor onde a semântica de tipo de tempo de execução precisa não é essencial para o uso prático do espaço de informações.</span><span class="sxs-lookup"><span data-stu-id="2f13e-216">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="2f13e-217">Quando você está escrevendo um provedor para um espaço de informações tão grande e interconectado, não é tecnicamente viável gerar tipos .NET reais para o espaço de informações.</span><span class="sxs-lookup"><span data-stu-id="2f13e-217">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="2f13e-218">Neste exemplo, cada tipo fornecido é apagado para o tipo `obj`, e todos os usos do tipo aparecerão como tipo `obj` no código compilado.</span><span class="sxs-lookup"><span data-stu-id="2f13e-218">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="2f13e-219">Na verdade, os objetos subjacentes nesses exemplos são cadeias de caracteres, mas o tipo `System.Object` será exibido como no código compilado do .net.</span><span class="sxs-lookup"><span data-stu-id="2f13e-219">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="2f13e-220">Assim como acontece com todos os usos do tipo erasureing, você pode usar boxing, unboxing e Cast explícitos para os tipos de subtextos apagados.</span><span class="sxs-lookup"><span data-stu-id="2f13e-220">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="2f13e-221">Nesse caso, uma exceção de conversão que não é válida pode resultar quando o objeto é usado.</span><span class="sxs-lookup"><span data-stu-id="2f13e-221">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="2f13e-222">Um tempo de execução do provedor pode definir seu próprio tipo de representação particular para ajudar a proteger contra representações falsas.</span><span class="sxs-lookup"><span data-stu-id="2f13e-222">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="2f13e-223">Você não pode definir os tipos apagados em F# si.</span><span class="sxs-lookup"><span data-stu-id="2f13e-223">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="2f13e-224">Somente tipos fornecidos podem ser apagados.</span><span class="sxs-lookup"><span data-stu-id="2f13e-224">Only provided types may be erased.</span></span> <span data-ttu-id="2f13e-225">Você deve entender as ramificações, práticas e semânticas, do uso de tipos apagados para seu provedor de tipos ou um provedor que fornece tipos apagados.</span><span class="sxs-lookup"><span data-stu-id="2f13e-225">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="2f13e-226">Um tipo apagado não tem nenhum tipo .NET real.</span><span class="sxs-lookup"><span data-stu-id="2f13e-226">An erased type has no real .NET type.</span></span> <span data-ttu-id="2f13e-227">Portanto, você não pode fazer uma reflexão precisa sobre o tipo, e você pode subverter tipos apagados se usar conversões de tempo de execução e outras técnicas que dependem da semântica de tipo de tempo de execução exato.</span><span class="sxs-lookup"><span data-stu-id="2f13e-227">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="2f13e-228">A subversão de tipos apagados frequentemente resulta em exceções de conversão de tipo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2f13e-228">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>

### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="2f13e-229">Escolhendo representações para tipos fornecidos e apagados</span><span class="sxs-lookup"><span data-stu-id="2f13e-229">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="2f13e-230">Para alguns usos de tipos fornecidos e apagados, nenhuma representação é necessária.</span><span class="sxs-lookup"><span data-stu-id="2f13e-230">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="2f13e-231">Por exemplo, o tipo fornecido apagado pode conter apenas propriedades e membros estáticos e nenhum construtor, e nenhum método ou propriedade retornaria uma instância do tipo.</span><span class="sxs-lookup"><span data-stu-id="2f13e-231">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="2f13e-232">Se você puder acessar instâncias de um tipo fornecido, você deve considerar as seguintes perguntas:</span><span class="sxs-lookup"><span data-stu-id="2f13e-232">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="2f13e-233">**Qual é a eliminação de um tipo fornecido?**</span><span class="sxs-lookup"><span data-stu-id="2f13e-233">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="2f13e-234">A eliminação de um tipo fornecido é como o tipo aparece no código .NET compilado.</span><span class="sxs-lookup"><span data-stu-id="2f13e-234">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="2f13e-235">A eliminação de um tipo de classe apagado fornecido é sempre o primeiro tipo base não apagado na cadeia de herança do tipo.</span><span class="sxs-lookup"><span data-stu-id="2f13e-235">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="2f13e-236">A eliminação de um tipo de interface apagado fornecido é `System.Object`sempre.</span><span class="sxs-lookup"><span data-stu-id="2f13e-236">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="2f13e-237">**Quais são as representações de um tipo fornecido?**</span><span class="sxs-lookup"><span data-stu-id="2f13e-237">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="2f13e-238">O conjunto de objetos possíveis para um tipo fornecido apagado é chamado de suas representações.</span><span class="sxs-lookup"><span data-stu-id="2f13e-238">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="2f13e-239">No exemplo deste documento, as representações de todos os tipos `Type1..Type100` fornecidos apagados são sempre objetos de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2f13e-239">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="2f13e-240">Todas as representações de um tipo fornecido devem ser compatíveis com a eliminação do tipo fornecido.</span><span class="sxs-lookup"><span data-stu-id="2f13e-240">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="2f13e-241">(Caso contrário, o F# compilador apresentará um erro para um uso do provedor de tipos, ou o código .net não verificável que não for válido será gerado.</span><span class="sxs-lookup"><span data-stu-id="2f13e-241">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="2f13e-242">Um provedor de tipos não será válido se retornar um código que forneça uma representação que não seja válida.)</span><span class="sxs-lookup"><span data-stu-id="2f13e-242">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="2f13e-243">Você pode escolher uma representação para os objetos fornecidos usando uma das abordagens a seguir, os quais são muito comuns:</span><span class="sxs-lookup"><span data-stu-id="2f13e-243">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="2f13e-244">Se você estiver simplesmente fornecendo um wrapper fortemente tipado em um tipo .NET existente, geralmente faz sentido para que o tipo seja apagado para esse tipo, use instâncias desse tipo como representações, ou ambas.</span><span class="sxs-lookup"><span data-stu-id="2f13e-244">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="2f13e-245">Essa abordagem é apropriada quando a maioria dos métodos existentes nesse tipo ainda faz sentido ao usar a versão com rigidez de tipos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-245">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="2f13e-246">Se você quiser criar uma API que difere significativamente de qualquer API .NET existente, faz sentido criar tipos de tempo de execução que serão a eliminação de tipos e representações para os tipos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-246">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="2f13e-247">O exemplo neste documento usa cadeias de caracteres como representações de objetos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-247">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="2f13e-248">Frequentemente, pode ser apropriado usar outros objetos para representações.</span><span class="sxs-lookup"><span data-stu-id="2f13e-248">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="2f13e-249">Por exemplo, você pode usar um dicionário como um recipiente de propriedades:</span><span class="sxs-lookup"><span data-stu-id="2f13e-249">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="2f13e-250">Como alternativa, você pode definir um tipo em seu provedor de tipos que será usado em tempo de execução para formar a representação, juntamente com uma ou mais operações de tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="2f13e-250">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="2f13e-251">Os membros fornecidos podem então construir instâncias desse tipo de objeto:</span><span class="sxs-lookup"><span data-stu-id="2f13e-251">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="2f13e-252">Nesse caso, você pode (opcionalmente) usar esse tipo como a eliminação de tipo, especificando esse tipo como o `baseType` ao construir o: `ProvidedTypeDefinition`</span><span class="sxs-lookup"><span data-stu-id="2f13e-252">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="2f13e-253">Principais lições</span><span class="sxs-lookup"><span data-stu-id="2f13e-253">Key Lessons</span></span>

<span data-ttu-id="2f13e-254">A seção anterior explicou como criar um provedor de tipo de apagamento simples que fornece uma variedade de tipos, propriedades e métodos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-254">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="2f13e-255">Esta seção também explicou o conceito de eliminação de tipo, incluindo algumas das vantagens e desvantagens de fornecer tipos apagados de um provedor de tipos e discutiu representações de tipos apagados.</span><span class="sxs-lookup"><span data-stu-id="2f13e-255">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>

## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="2f13e-256">Um provedor de tipos que usa parâmetros estáticos</span><span class="sxs-lookup"><span data-stu-id="2f13e-256">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="2f13e-257">A capacidade de parametrizar provedores de tipo por dados estáticos permite muitos cenários interessantes, mesmo em casos em que o provedor não precisa acessar dados locais ou remotos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-257">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="2f13e-258">Nesta seção, você aprenderá algumas técnicas básicas para reunir esse provedor.</span><span class="sxs-lookup"><span data-stu-id="2f13e-258">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>

### <a name="type-checked-regex-provider"></a><span data-ttu-id="2f13e-259">Provedor de Regex de tipo verificado</span><span class="sxs-lookup"><span data-stu-id="2f13e-259">Type Checked Regex Provider</span></span>

<span data-ttu-id="2f13e-260">Imagine que você queira implementar um provedor de tipos para expressões regulares que encapsula as bibliotecas .NET <xref:System.Text.RegularExpressions.Regex> em uma interface que fornece as seguintes garantias de tempo de compilação:</span><span class="sxs-lookup"><span data-stu-id="2f13e-260">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="2f13e-261">Verificando se uma expressão regular é válida.</span><span class="sxs-lookup"><span data-stu-id="2f13e-261">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="2f13e-262">Fornecer propriedades nomeadas em correspondências que se baseiam em qualquer nome de grupo na expressão regular.</span><span class="sxs-lookup"><span data-stu-id="2f13e-262">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="2f13e-263">Esta seção mostra como usar provedores de tipos para criar um `RegexTyped` tipo que o padrão de expressão regular parametriza para fornecer esses benefícios.</span><span class="sxs-lookup"><span data-stu-id="2f13e-263">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="2f13e-264">O compilador relatará um erro se o padrão fornecido não for válido e o provedor de tipos puder extrair os grupos do padrão para que você possa acessá-los usando propriedades nomeadas em correspondências.</span><span class="sxs-lookup"><span data-stu-id="2f13e-264">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="2f13e-265">Quando você cria um provedor de tipos, deve considerar como sua API exposta deve procurar os usuários finais e como esse design será traduzido para o código .NET.</span><span class="sxs-lookup"><span data-stu-id="2f13e-265">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="2f13e-266">O exemplo a seguir mostra como usar essa API para obter os componentes do código de área:</span><span class="sxs-lookup"><span data-stu-id="2f13e-266">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="2f13e-267">O exemplo a seguir mostra como o provedor de tipos traduz essas chamadas:</span><span class="sxs-lookup"><span data-stu-id="2f13e-267">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="2f13e-268">Observe os seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="2f13e-268">Note the following points:</span></span>

- <span data-ttu-id="2f13e-269">O tipo Regex padrão representa o `RegexTyped` tipo parametrizado.</span><span class="sxs-lookup"><span data-stu-id="2f13e-269">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="2f13e-270">O `RegexTyped` Construtor resulta em uma chamada para o construtor Regex, passando o argumento de tipo estático para o padrão.</span><span class="sxs-lookup"><span data-stu-id="2f13e-270">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="2f13e-271">Os resultados do `Match` método são representados pelo tipo padrão <xref:System.Text.RegularExpressions.Match> .</span><span class="sxs-lookup"><span data-stu-id="2f13e-271">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="2f13e-272">Cada grupo nomeado resulta em uma propriedade fornecida e o acesso à propriedade resulta em um uso de um indexador na `Groups` coleção de uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="2f13e-272">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="2f13e-273">O código a seguir é o núcleo da lógica para implementar tal provedor, e este exemplo omite a adição de todos os membros ao tipo fornecido.</span><span class="sxs-lookup"><span data-stu-id="2f13e-273">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="2f13e-274">Para obter informações sobre cada membro adicionado, consulte a seção apropriada mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="2f13e-274">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="2f13e-275">Para o código completo, baixe o exemplo do [ F# pacote de exemplo 3,0](https://archive.codeplex.com/?p=fsharp3sample) no site do CodePlex.</span><span class="sxs-lookup"><span data-stu-id="2f13e-275">For the full code, download the sample from the [F# 3.0 Sample Pack](https://archive.codeplex.com/?p=fsharp3sample) on the CodePlex website.</span></span>

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

<span data-ttu-id="2f13e-276">Observe os seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="2f13e-276">Note the following points:</span></span>

- <span data-ttu-id="2f13e-277">O provedor de tipos usa dois parâmetros estáticos `pattern`: o, que é obrigatório e `options`o, que são opcionais (porque um valor padrão é fornecido).</span><span class="sxs-lookup"><span data-stu-id="2f13e-277">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="2f13e-278">Depois que os argumentos estáticos são fornecidos, você cria uma instância da expressão regular.</span><span class="sxs-lookup"><span data-stu-id="2f13e-278">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="2f13e-279">Essa instância gerará uma exceção se o Regex estiver malformado e esse erro será relatado aos usuários.</span><span class="sxs-lookup"><span data-stu-id="2f13e-279">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="2f13e-280">`DefineStaticParameters` No retorno de chamada, você define o tipo que será retornado depois que os argumentos forem fornecidos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-280">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="2f13e-281">Esse código define `HideObjectMethods` como true para que a experiência do IntelliSense permaneça simplificada.</span><span class="sxs-lookup"><span data-stu-id="2f13e-281">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="2f13e-282">Esse atributo faz com `Equals`que `GetHashCode`os `Finalize`Membros, `GetType` , e sejam suprimidos das listas do IntelliSense para um objeto fornecido.</span><span class="sxs-lookup"><span data-stu-id="2f13e-282">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="2f13e-283">Você usa `obj` como o tipo base do método, mas usará um `Regex` objeto como a representação de tempo de execução desse tipo, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2f13e-283">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="2f13e-284">A chamada para o `Regex` Construtor gera um <xref:System.ArgumentException> quando uma expressão regular não é válida.</span><span class="sxs-lookup"><span data-stu-id="2f13e-284">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="2f13e-285">O compilador captura essa exceção e relata uma mensagem de erro para o usuário no momento da compilação ou no editor do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f13e-285">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="2f13e-286">Essa exceção permite que expressões regulares sejam validadas sem executar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2f13e-286">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="2f13e-287">O tipo definido acima não é útil ainda porque ele não contém nenhum método ou Propriedade significativo.</span><span class="sxs-lookup"><span data-stu-id="2f13e-287">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="2f13e-288">Primeiro, adicione um método `IsMatch` estático:</span><span class="sxs-lookup"><span data-stu-id="2f13e-288">First, add a static `IsMatch` method:</span></span>

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

<span data-ttu-id="2f13e-289">O código anterior define um método `IsMatch`, que usa uma cadeia de caracteres como entrada e `bool`retorna um.</span><span class="sxs-lookup"><span data-stu-id="2f13e-289">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="2f13e-290">A única parte complicada é o uso do `args` argumento dentro da `InvokeCode` definição.</span><span class="sxs-lookup"><span data-stu-id="2f13e-290">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="2f13e-291">Neste exemplo, `args` é uma lista de Cotações que representa os argumentos para esse método.</span><span class="sxs-lookup"><span data-stu-id="2f13e-291">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="2f13e-292">Se o método for um método de instância, o primeiro argumento representará o `this` argumento.</span><span class="sxs-lookup"><span data-stu-id="2f13e-292">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="2f13e-293">No entanto, para um método estático, os argumentos são apenas os argumentos explícitos para o método.</span><span class="sxs-lookup"><span data-stu-id="2f13e-293">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="2f13e-294">Observe que o tipo de valor entre aspas deve corresponder ao tipo de retorno especificado (nesse caso, `bool`).</span><span class="sxs-lookup"><span data-stu-id="2f13e-294">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="2f13e-295">Observe também que esse código usa o `AddXmlDoc` método para garantir que o método fornecido também tenha documentação útil, que você pode fornecer por meio do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="2f13e-295">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="2f13e-296">Em seguida, adicione um método de correspondência de instância.</span><span class="sxs-lookup"><span data-stu-id="2f13e-296">Next, add an instance Match method.</span></span> <span data-ttu-id="2f13e-297">No entanto, esse método deve retornar um valor de `Match` um tipo fornecido para que os grupos possam ser acessados de maneira fortemente tipada.</span><span class="sxs-lookup"><span data-stu-id="2f13e-297">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="2f13e-298">Portanto, primeiro você declara o `Match` tipo.</span><span class="sxs-lookup"><span data-stu-id="2f13e-298">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="2f13e-299">Como esse tipo depende do padrão que foi fornecido como um argumento estático, esse tipo deve ser aninhado dentro da definição de tipo com parâmetros:</span><span class="sxs-lookup"><span data-stu-id="2f13e-299">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="2f13e-300">Em seguida, você adiciona uma propriedade ao tipo de correspondência para cada grupo.</span><span class="sxs-lookup"><span data-stu-id="2f13e-300">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="2f13e-301">Em tempo de execução, uma correspondência é representada <xref:System.Text.RegularExpressions.Match> como um valor, portanto, a cotação que define a <xref:System.Text.RegularExpressions.Match.Groups> propriedade deve usar a propriedade indexada para obter o grupo relevante.</span><span class="sxs-lookup"><span data-stu-id="2f13e-301">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

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

<span data-ttu-id="2f13e-302">Novamente, observe que você está adicionando a documentação XML à propriedade fornecida.</span><span class="sxs-lookup"><span data-stu-id="2f13e-302">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="2f13e-303">Observe também que uma propriedade pode ser lida se uma `GetterCode` função for fornecida e a propriedade puder ser gravada se uma `SetterCode` função for fornecida, portanto, a propriedade resultante será somente leitura.</span><span class="sxs-lookup"><span data-stu-id="2f13e-303">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="2f13e-304">Agora você pode criar um método de instância que retorna um valor desse `Match` tipo:</span><span class="sxs-lookup"><span data-stu-id="2f13e-304">Now you can create an instance method that returns a value of this `Match` type:</span></span>

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

<span data-ttu-id="2f13e-305">Como você está criando um método de instância `args.[0]` , representa `RegexTyped` a instância na qual o método está sendo chamado e `args.[1]` é o argumento de entrada.</span><span class="sxs-lookup"><span data-stu-id="2f13e-305">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="2f13e-306">Por fim, forneça um construtor para que as instâncias do tipo fornecido possam ser criadas.</span><span class="sxs-lookup"><span data-stu-id="2f13e-306">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="2f13e-307">O Construtor simplesmente apaga a criação de uma instância Regex .NET padrão, que é novamente emoldurada em um objeto porque `obj` é a eliminação do tipo fornecido.</span><span class="sxs-lookup"><span data-stu-id="2f13e-307">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="2f13e-308">Com essa alteração, o uso da API de exemplo especificado anteriormente no tópico funciona conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="2f13e-308">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="2f13e-309">O código a seguir está completo e final:</span><span class="sxs-lookup"><span data-stu-id="2f13e-309">The following code is complete and final:</span></span>

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

### <a name="key-lessons"></a><span data-ttu-id="2f13e-310">Principais lições</span><span class="sxs-lookup"><span data-stu-id="2f13e-310">Key Lessons</span></span>

<span data-ttu-id="2f13e-311">Esta seção explicou como criar um provedor de tipos que opera em seus parâmetros estáticos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-311">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="2f13e-312">O provedor verifica o parâmetro estático e fornece operações com base em seu valor.</span><span class="sxs-lookup"><span data-stu-id="2f13e-312">The provider checks the static parameter and provides operations based on its value.</span></span>

## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="2f13e-313">Um provedor de tipos que é apoiado por dados locais</span><span class="sxs-lookup"><span data-stu-id="2f13e-313">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="2f13e-314">Frequentemente, você pode querer que os provedores de tipos apresentem APIs com base em parâmetros estáticos e também informações de sistemas locais ou remotos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-314">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="2f13e-315">Esta seção discute os provedores de tipos baseados em dados locais, como arquivos de dados locais.</span><span class="sxs-lookup"><span data-stu-id="2f13e-315">This section discusses type providers that are based on local data, such as local data files.</span></span>

### <a name="simple-csv-file-provider"></a><span data-ttu-id="2f13e-316">Provedor de arquivo CSV simples</span><span class="sxs-lookup"><span data-stu-id="2f13e-316">Simple CSV File Provider</span></span>

<span data-ttu-id="2f13e-317">Como um exemplo simples, considere um provedor de tipos para acessar dados científicos em formato CSV (valores separados por vírgula).</span><span class="sxs-lookup"><span data-stu-id="2f13e-317">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="2f13e-318">Esta seção pressupõe que os arquivos CSV contêm uma linha de cabeçalho seguida por dados de ponto flutuante, como mostra a tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="2f13e-318">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>

|<span data-ttu-id="2f13e-319">Distância (medidor)</span><span class="sxs-lookup"><span data-stu-id="2f13e-319">Distance (meter)</span></span>|<span data-ttu-id="2f13e-320">Tempo (segundo)</span><span class="sxs-lookup"><span data-stu-id="2f13e-320">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="2f13e-321">50.0</span><span class="sxs-lookup"><span data-stu-id="2f13e-321">50.0</span></span>|<span data-ttu-id="2f13e-322">3.7</span><span class="sxs-lookup"><span data-stu-id="2f13e-322">3.7</span></span>|
|<span data-ttu-id="2f13e-323">100.0</span><span class="sxs-lookup"><span data-stu-id="2f13e-323">100.0</span></span>|<span data-ttu-id="2f13e-324">5.2</span><span class="sxs-lookup"><span data-stu-id="2f13e-324">5.2</span></span>|
|<span data-ttu-id="2f13e-325">150.0</span><span class="sxs-lookup"><span data-stu-id="2f13e-325">150.0</span></span>|<span data-ttu-id="2f13e-326">6.4</span><span class="sxs-lookup"><span data-stu-id="2f13e-326">6.4</span></span>|

<span data-ttu-id="2f13e-327">Esta seção mostra como fornecer um tipo que você pode usar para `Distance` obter linhas com uma propriedade do tipo `float<meter>` e uma `Time` Propriedade do tipo `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="2f13e-327">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="2f13e-328">Para simplificar, são feitas as seguintes suposições:</span><span class="sxs-lookup"><span data-stu-id="2f13e-328">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="2f13e-329">Os nomes de cabeçalho são menos unitários ou têm a forma "nome (unidade)" e não contêm vírgulas.</span><span class="sxs-lookup"><span data-stu-id="2f13e-329">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="2f13e-330">Unidades são todas as unidades internacionais (si) do sistema, como o módulo [Microsoft. FSharp. Data. UnitSystems. si.F#unitnames ()](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) define.</span><span class="sxs-lookup"><span data-stu-id="2f13e-330">Units are all System International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="2f13e-331">As unidades são todas simples (por exemplo, medidor) em vez de compostas (por exemplo, medidor/segundo).</span><span class="sxs-lookup"><span data-stu-id="2f13e-331">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="2f13e-332">Todas as colunas contêm dados de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="2f13e-332">All columns contain floating point data.</span></span>

<span data-ttu-id="2f13e-333">Um provedor mais completo desafrouxaria essas restrições.</span><span class="sxs-lookup"><span data-stu-id="2f13e-333">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="2f13e-334">Novamente, a primeira etapa é considerar a aparência da API.</span><span class="sxs-lookup"><span data-stu-id="2f13e-334">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="2f13e-335">Dado um `info.csv` arquivo com o conteúdo da tabela anterior (em formato separado por vírgula), os usuários do provedor devem ser capazes de escrever um código semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2f13e-335">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="2f13e-336">Nesse caso, o compilador deve converter essas chamadas em algo semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2f13e-336">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="2f13e-337">A tradução ideal exigirá que o provedor de tipos defina um `CsvFile` tipo real no assembly do provedor de tipos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-337">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="2f13e-338">Provedores de tipo geralmente dependem de alguns tipos auxiliares e métodos para encapsular lógica importante.</span><span class="sxs-lookup"><span data-stu-id="2f13e-338">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="2f13e-339">Como as medidas são apagadas no tempo de execução, você `float[]` pode usar um como o tipo apagado para uma linha.</span><span class="sxs-lookup"><span data-stu-id="2f13e-339">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="2f13e-340">O compilador tratará colunas diferentes como tendo tipos de medidas diferentes.</span><span class="sxs-lookup"><span data-stu-id="2f13e-340">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="2f13e-341">Por exemplo, a primeira coluna em nosso exemplo tem tipo `float<meter>`e a segunda tem. `float<second>`</span><span class="sxs-lookup"><span data-stu-id="2f13e-341">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="2f13e-342">No entanto, a representação apagada pode permanecer bem simples.</span><span class="sxs-lookup"><span data-stu-id="2f13e-342">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="2f13e-343">O código a seguir mostra o núcleo da implementação.</span><span class="sxs-lookup"><span data-stu-id="2f13e-343">The following code shows the core of the implementation.</span></span>

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

<span data-ttu-id="2f13e-344">Observe os seguintes pontos sobre a implementação:</span><span class="sxs-lookup"><span data-stu-id="2f13e-344">Note the following points about the implementation:</span></span>

- <span data-ttu-id="2f13e-345">Construtores sobrecarregados permitem que o arquivo original ou um que tenha um esquema idêntico seja lido.</span><span class="sxs-lookup"><span data-stu-id="2f13e-345">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="2f13e-346">Esse padrão é comum quando você escreve um provedor de tipos para fontes de dados locais ou remotas, e esse padrão permite que um arquivo local seja usado como modelo para dados remotos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-346">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="2f13e-347">Você pode usar o valor [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) que é passado para o construtor do provedor de tipos para resolver nomes de arquivo relativos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-347">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="2f13e-348">Você pode usar o `AddDefinitionLocation` método para definir o local das propriedades fornecidas.</span><span class="sxs-lookup"><span data-stu-id="2f13e-348">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="2f13e-349">Portanto, se você usar `Go To Definition` o em uma propriedade fornecida, o arquivo CSV será aberto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f13e-349">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="2f13e-350">Você pode usar o `ProvidedMeasureBuilder` tipo para pesquisar as unidades de si e gerar os tipos relevantes `float<_>` .</span><span class="sxs-lookup"><span data-stu-id="2f13e-350">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="2f13e-351">Principais lições</span><span class="sxs-lookup"><span data-stu-id="2f13e-351">Key Lessons</span></span>

<span data-ttu-id="2f13e-352">Esta seção explicou como criar um provedor de tipos para uma fonte de dados local com um esquema simples contido na própria fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="2f13e-352">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>

## <a name="going-further"></a><span data-ttu-id="2f13e-353">Indo mais</span><span class="sxs-lookup"><span data-stu-id="2f13e-353">Going Further</span></span>

<span data-ttu-id="2f13e-354">As seções a seguir incluem sugestões para um estudo adicional.</span><span class="sxs-lookup"><span data-stu-id="2f13e-354">The following sections include suggestions for further study.</span></span>

### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="2f13e-355">Uma olhada no código compilado para tipos apagados</span><span class="sxs-lookup"><span data-stu-id="2f13e-355">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="2f13e-356">Para lhe dar uma ideia de como o uso do provedor de tipos corresponde ao código emitido, examine a seguinte função usando o `HelloWorldTypeProvider` que é usado anteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="2f13e-356">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="2f13e-357">Aqui está uma imagem do código resultante descompilado usando ildasm. exe:</span><span class="sxs-lookup"><span data-stu-id="2f13e-357">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

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

<span data-ttu-id="2f13e-358">Como mostra o exemplo, todas as menção do tipo `Type1` e da `InstanceProperty` Propriedade foram apagadas, deixando apenas as operações nos tipos de tempo de execução envolvidos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-358">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>

### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="2f13e-359">Design e convenções de nomenclatura para provedores de tipo</span><span class="sxs-lookup"><span data-stu-id="2f13e-359">Design and Naming Conventions for Type Providers</span></span>

<span data-ttu-id="2f13e-360">Observe as seguintes convenções ao criar provedores de tipos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-360">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="2f13e-361">**Provedores para protocolos de conectividade** Em geral, os nomes da maioria das DLLs de provedor para dados e protocolos de conectividade de serviço, como conexões OData ou SQL `TypeProvider` , `TypeProviders`devem terminar no ou no.</span><span class="sxs-lookup"><span data-stu-id="2f13e-361">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="2f13e-362">Por exemplo, use um nome de DLL que se assemelha à seguinte cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="2f13e-362">For example, use a DLL name that resembles the following string:</span></span>

`Fabrikam.Management.BasicTypeProviders.dll`

<span data-ttu-id="2f13e-363">Verifique se os tipos fornecidos são membros do namespace correspondente e indique o protocolo de conectividade que você implementou:</span><span class="sxs-lookup"><span data-stu-id="2f13e-363">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="2f13e-364">**Provedores de utilitários para codificação geral**.</span><span class="sxs-lookup"><span data-stu-id="2f13e-364">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="2f13e-365">Para um provedor de tipos de utilitário como, para expressões regulares, o provedor de tipos pode fazer parte de uma biblioteca base, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2f13e-365">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="2f13e-366">Nesse caso, o tipo fornecido apareceria em um ponto apropriado de acordo com as convenções normais de design do .NET:</span><span class="sxs-lookup"><span data-stu-id="2f13e-366">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="2f13e-367">**Fontes de dados singleton**.</span><span class="sxs-lookup"><span data-stu-id="2f13e-367">**Singleton Data Sources**.</span></span> <span data-ttu-id="2f13e-368">Alguns provedores de tipos se conectam a uma única fonte de dados dedicada e fornecem apenas dados.</span><span class="sxs-lookup"><span data-stu-id="2f13e-368">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="2f13e-369">Nesse caso, você deve remover o `TypeProvider` sufixo e usar convenções normais de nomenclatura do .net:</span><span class="sxs-lookup"><span data-stu-id="2f13e-369">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="2f13e-370">Para obter mais informações, consulte `GetConnection` a Convenção de design descrita mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="2f13e-370">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>

### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="2f13e-371">Padrões de design para provedores de tipo</span><span class="sxs-lookup"><span data-stu-id="2f13e-371">Design Patterns for Type Providers</span></span>

<span data-ttu-id="2f13e-372">As seções a seguir descrevem os padrões de design que você pode usar ao criar provedores de tipo.</span><span class="sxs-lookup"><span data-stu-id="2f13e-372">The following sections describe design patterns you can use when authoring type providers.</span></span>

#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="2f13e-373">O padrão de design getConnection</span><span class="sxs-lookup"><span data-stu-id="2f13e-373">The GetConnection Design Pattern</span></span>

<span data-ttu-id="2f13e-374">A maioria dos provedores de tipo deve ser escrita `GetConnection` para usar o padrão usado pelos provedores de tipo em FSharp. Data. TypeProviders. dll, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2f13e-374">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="2f13e-375">Provedores de tipos apoiados por dados e serviços remotos</span><span class="sxs-lookup"><span data-stu-id="2f13e-375">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="2f13e-376">Antes de criar um provedor de tipos que é apoiado por dados e serviços remotos, você deve considerar uma variedade de problemas inerentes à programação conectada.</span><span class="sxs-lookup"><span data-stu-id="2f13e-376">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="2f13e-377">Esses problemas incluem as seguintes considerações:</span><span class="sxs-lookup"><span data-stu-id="2f13e-377">These issues include the following considerations:</span></span>

- <span data-ttu-id="2f13e-378">mapeamento de esquema</span><span class="sxs-lookup"><span data-stu-id="2f13e-378">schema mapping</span></span>

- <span data-ttu-id="2f13e-379">vida e invalidação na presença de alteração de esquema</span><span class="sxs-lookup"><span data-stu-id="2f13e-379">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="2f13e-380">cache de esquema</span><span class="sxs-lookup"><span data-stu-id="2f13e-380">schema caching</span></span>

- <span data-ttu-id="2f13e-381">implementações assíncronas de operações de acesso a dados</span><span class="sxs-lookup"><span data-stu-id="2f13e-381">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="2f13e-382">suporte a consultas, incluindo consultas LINQ</span><span class="sxs-lookup"><span data-stu-id="2f13e-382">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="2f13e-383">credenciais e autenticação</span><span class="sxs-lookup"><span data-stu-id="2f13e-383">credentials and authentication</span></span>

<span data-ttu-id="2f13e-384">Este tópico não explora mais esses problemas.</span><span class="sxs-lookup"><span data-stu-id="2f13e-384">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="2f13e-385">Técnicas de criação adicionais</span><span class="sxs-lookup"><span data-stu-id="2f13e-385">Additional Authoring Techniques</span></span>

<span data-ttu-id="2f13e-386">Ao escrever seus próprios provedores de tipo, talvez você queira usar as técnicas adicionais a seguir.</span><span class="sxs-lookup"><span data-stu-id="2f13e-386">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="2f13e-387">Criando tipos e membros sob demanda</span><span class="sxs-lookup"><span data-stu-id="2f13e-387">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="2f13e-388">A API fornecida tem versões atrasadas de AddMember.</span><span class="sxs-lookup"><span data-stu-id="2f13e-388">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="2f13e-389">Essas versões são usadas para criar espaços de tipos sob demanda.</span><span class="sxs-lookup"><span data-stu-id="2f13e-389">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="2f13e-390">Fornecendo tipos de matriz e instanciações de tipo genérico</span><span class="sxs-lookup"><span data-stu-id="2f13e-390">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="2f13e-391">Você faz com que os membros fornecidos (cujas assinaturas incluem tipos de matriz, tipos ByRef e instanciações de tipos genéricos) usando `MakeArrayType`o `MakePointerType`normal, `MakeGenericType` e em qualquer instância <xref:System.Type>do, `ProvidedTypeDefinitions`incluindo.</span><span class="sxs-lookup"><span data-stu-id="2f13e-391">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="2f13e-392">Em alguns casos, talvez seja necessário usar o auxiliar no `ProvidedTypeBuilder.MakeGenericType`.</span><span class="sxs-lookup"><span data-stu-id="2f13e-392">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="2f13e-393">Consulte a [documentação do SDK do provedor de tipos](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="2f13e-393">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="2f13e-394">Fornecendo anotações de unidade de medida</span><span class="sxs-lookup"><span data-stu-id="2f13e-394">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="2f13e-395">A API ProvidedTypes fornece auxiliares para fornecer anotações de medida.</span><span class="sxs-lookup"><span data-stu-id="2f13e-395">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="2f13e-396">Por exemplo, para fornecer o tipo `float<kg>`, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="2f13e-396">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="2f13e-397">Para fornecer o tipo `Nullable<decimal<kg/m^2>>`, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="2f13e-397">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="2f13e-398">Acessando projetos-recursos locais ou de script local</span><span class="sxs-lookup"><span data-stu-id="2f13e-398">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="2f13e-399">Cada instância de um provedor de tipos pode receber um `TypeProviderConfig` valor durante a construção.</span><span class="sxs-lookup"><span data-stu-id="2f13e-399">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="2f13e-400">Esse valor contém a "pasta de resolução" para o provedor (ou seja, a pasta do projeto para a compilação ou o diretório que contém um script), a lista de assemblies referenciados e outras informações.</span><span class="sxs-lookup"><span data-stu-id="2f13e-400">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="2f13e-401">Invalidação</span><span class="sxs-lookup"><span data-stu-id="2f13e-401">Invalidation</span></span>

<span data-ttu-id="2f13e-402">Os provedores podem gerar sinais de invalidação para notificar o F# serviço de linguagem que as suposições de esquema podem ter alterado.</span><span class="sxs-lookup"><span data-stu-id="2f13e-402">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="2f13e-403">Quando ocorrer invalidação, um typecheck será refeito se o provedor estiver sendo hospedado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f13e-403">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="2f13e-404">Esse sinal será ignorado quando o provedor for hospedado em F# interativo ou pelo F# compilador (FSC. exe).</span><span class="sxs-lookup"><span data-stu-id="2f13e-404">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="2f13e-405">Armazenando em cache informações de esquema</span><span class="sxs-lookup"><span data-stu-id="2f13e-405">Caching Schema Information</span></span>

<span data-ttu-id="2f13e-406">Os provedores geralmente devem armazenar em cache o acesso a informações de esquema.</span><span class="sxs-lookup"><span data-stu-id="2f13e-406">Providers must often cache access to schema information.</span></span> <span data-ttu-id="2f13e-407">Os dados armazenados em cache devem ser armazenados usando um nome de arquivo que é fornecido como um parâmetro estático ou como dados do usuário.</span><span class="sxs-lookup"><span data-stu-id="2f13e-407">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="2f13e-408">Um exemplo de cache de esquema é `LocalSchemaFile` o parâmetro nos provedores de tipos `FSharp.Data.TypeProviders` no assembly.</span><span class="sxs-lookup"><span data-stu-id="2f13e-408">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="2f13e-409">Na implementação desses provedores, esse parâmetro estático direciona o provedor de tipos para usar as informações de esquema no arquivo local especificado em vez de acessar a fonte de dados pela rede.</span><span class="sxs-lookup"><span data-stu-id="2f13e-409">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="2f13e-410">Para usar as informações de esquema em cache, você também deve definir o `ForceUpdate` parâmetro `false`estático como.</span><span class="sxs-lookup"><span data-stu-id="2f13e-410">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="2f13e-411">Você pode usar uma técnica semelhante para habilitar o acesso a dados online e offline.</span><span class="sxs-lookup"><span data-stu-id="2f13e-411">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="2f13e-412">Assembly de backup</span><span class="sxs-lookup"><span data-stu-id="2f13e-412">Backing Assembly</span></span>

<span data-ttu-id="2f13e-413">Quando você compila um `.dll` arquivo `.exe` ou, o arquivo. dll de backup para tipos gerados é vinculado estaticamente ao assembly resultante.</span><span class="sxs-lookup"><span data-stu-id="2f13e-413">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="2f13e-414">Esse link é criado copiando as definições de tipo IL (linguagem intermediária) e todos os recursos gerenciados do assembly de backup para o assembly final.</span><span class="sxs-lookup"><span data-stu-id="2f13e-414">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="2f13e-415">Quando você usa F# interativo, o arquivo. dll de backup não é copiado e, em vez disso F# , é carregado diretamente no processo interativo.</span><span class="sxs-lookup"><span data-stu-id="2f13e-415">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="2f13e-416">Exceções e diagnósticos de provedores de tipos</span><span class="sxs-lookup"><span data-stu-id="2f13e-416">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="2f13e-417">Todos os usos de todos os membros de tipos fornecidos podem gerar exceções.</span><span class="sxs-lookup"><span data-stu-id="2f13e-417">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="2f13e-418">Em todos os casos, se um provedor de tipos lançar uma exceção, o compilador do host irá reattributeá-lo para um provedor de tipos específico.</span><span class="sxs-lookup"><span data-stu-id="2f13e-418">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="2f13e-419">Exceções de provedor de tipo nunca devem resultar em erros de compilador interno.</span><span class="sxs-lookup"><span data-stu-id="2f13e-419">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="2f13e-420">Os provedores de tipos não podem relatar avisos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-420">Type providers can't report warnings.</span></span>

- <span data-ttu-id="2f13e-421">Quando um provedor de tipos é hospedado no F# compilador, em F# um ambiente de desenvolvimento F# ou interativo, todas as exceções desse provedor são detectadas.</span><span class="sxs-lookup"><span data-stu-id="2f13e-421">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="2f13e-422">A propriedade Message sempre é o texto de erro e nenhum rastreamento de pilha é exibido.</span><span class="sxs-lookup"><span data-stu-id="2f13e-422">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="2f13e-423">Se você for lançar uma exceção, poderá lançar os seguintes exemplos: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="2f13e-423">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="2f13e-424">Fornecendo tipos gerados</span><span class="sxs-lookup"><span data-stu-id="2f13e-424">Providing Generated Types</span></span>

<span data-ttu-id="2f13e-425">Até agora, este documento explicou como fornecer tipos apagados.</span><span class="sxs-lookup"><span data-stu-id="2f13e-425">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="2f13e-426">Você também pode usar o mecanismo do provedor de F# tipos no para fornecer tipos gerados, que são adicionados como definições de tipo .net reais no programa dos usuários.</span><span class="sxs-lookup"><span data-stu-id="2f13e-426">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="2f13e-427">Você deve referir-se aos tipos fornecidos gerados usando uma definição de tipo.</span><span class="sxs-lookup"><span data-stu-id="2f13e-427">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="2f13e-428">O código auxiliar ProvidedTypes-0,2 que faz parte da versão F# 3,0 tem apenas suporte limitado para fornecer tipos gerados.</span><span class="sxs-lookup"><span data-stu-id="2f13e-428">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="2f13e-429">As instruções a seguir devem ser verdadeiras para uma definição de tipo gerada:</span><span class="sxs-lookup"><span data-stu-id="2f13e-429">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="2f13e-430">`isErased`deve ser definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="2f13e-430">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="2f13e-431">O tipo gerado deve ser adicionado a um recém-criado `ProvidedAssembly()`, que representa um contêiner para fragmentos de código gerados.</span><span class="sxs-lookup"><span data-stu-id="2f13e-431">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="2f13e-432">O provedor deve ter um assembly que tenha um arquivo .NET. dll de backup real com um arquivo. dll correspondente no disco.</span><span class="sxs-lookup"><span data-stu-id="2f13e-432">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>

## <a name="rules-and-limitations"></a><span data-ttu-id="2f13e-433">Regras e limitações</span><span class="sxs-lookup"><span data-stu-id="2f13e-433">Rules and Limitations</span></span>

<span data-ttu-id="2f13e-434">Ao escrever provedores de tipo, mantenha as seguintes regras e limitações em mente.</span><span class="sxs-lookup"><span data-stu-id="2f13e-434">When you write type providers, keep the following rules and limitations in mind.</span></span>

### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="2f13e-435">Os tipos fornecidos devem estar acessíveis</span><span class="sxs-lookup"><span data-stu-id="2f13e-435">Provided types must be reachable</span></span>

<span data-ttu-id="2f13e-436">Todos os tipos fornecidos devem ser acessíveis a partir de tipos não aninhados.</span><span class="sxs-lookup"><span data-stu-id="2f13e-436">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="2f13e-437">Os tipos não aninhados são fornecidos na chamada ao `TypeProviderForNamespaces` Construtor ou a uma chamada para. `AddNamespace`</span><span class="sxs-lookup"><span data-stu-id="2f13e-437">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="2f13e-438">Por exemplo, se o provedor fornecer um tipo `StaticClass.P : T`, você deve garantir que T seja um tipo não aninhado ou aninhado em um.</span><span class="sxs-lookup"><span data-stu-id="2f13e-438">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="2f13e-439">Por exemplo, alguns provedores têm uma classe estática, `DataTypes` como a que contém esses `T1, T2, T3, ...` tipos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-439">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="2f13e-440">Caso contrário, o erro indica que uma referência ao tipo T no assembly A foi encontrada, mas o tipo não pôde ser encontrado nesse assembly.</span><span class="sxs-lookup"><span data-stu-id="2f13e-440">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="2f13e-441">Se esse erro for exibido, verifique se todos os seus subtipos podem ser acessados dos tipos de provedor.</span><span class="sxs-lookup"><span data-stu-id="2f13e-441">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="2f13e-442">Observação: Esses `T1, T2, T3...` tipos são chamados de tipos *em tempo real* .</span><span class="sxs-lookup"><span data-stu-id="2f13e-442">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="2f13e-443">Lembre-se de colocá-los em um namespace acessível ou em um tipo pai.</span><span class="sxs-lookup"><span data-stu-id="2f13e-443">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="2f13e-444">Limitações do mecanismo do provedor de tipos</span><span class="sxs-lookup"><span data-stu-id="2f13e-444">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="2f13e-445">O mecanismo do provedor de F# tipos no tem as seguintes limitações:</span><span class="sxs-lookup"><span data-stu-id="2f13e-445">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="2f13e-446">A infraestrutura subjacente para provedores de tipos F# no não dá suporte a tipos genéricos fornecidos ou métodos genéricos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-446">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="2f13e-447">O mecanismo não dá suporte a tipos aninhados com parâmetros estáticos.</span><span class="sxs-lookup"><span data-stu-id="2f13e-447">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="2f13e-448">Dicas de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="2f13e-448">Development Tips</span></span>

<span data-ttu-id="2f13e-449">Você pode encontrar as seguintes dicas úteis durante o processo de desenvolvimento:</span><span class="sxs-lookup"><span data-stu-id="2f13e-449">You might find the following tips helpful during the development process:</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="2f13e-450">Executar duas instâncias do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2f13e-450">Run two instances of Visual Studio</span></span>

<span data-ttu-id="2f13e-451">Você pode desenvolver o provedor de tipos em uma instância e testar o provedor no outro porque o IDE de teste usará um bloqueio no arquivo. dll que impede que o provedor de tipos seja recriado.</span><span class="sxs-lookup"><span data-stu-id="2f13e-451">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="2f13e-452">Portanto, você deve fechar a segunda instância do Visual Studio enquanto o provedor é criado na primeira instância e, em seguida, deve reabrir a segunda instância depois que o provedor é compilado.</span><span class="sxs-lookup"><span data-stu-id="2f13e-452">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="2f13e-453">Depurar provedores de tipo usando invocações de FSC. exe</span><span class="sxs-lookup"><span data-stu-id="2f13e-453">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="2f13e-454">Você pode invocar provedores de tipo usando as seguintes ferramentas:</span><span class="sxs-lookup"><span data-stu-id="2f13e-454">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="2f13e-455">FSC. exe (o F# compilador de linha de comando)</span><span class="sxs-lookup"><span data-stu-id="2f13e-455">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="2f13e-456">FSI. exe (o F# compilador interativo)</span><span class="sxs-lookup"><span data-stu-id="2f13e-456">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="2f13e-457">devenv. exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="2f13e-457">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="2f13e-458">Geralmente, é possível depurar provedores de tipos com mais facilidade usando o FSC. exe em um arquivo de script de teste (por exemplo, script. fsx).</span><span class="sxs-lookup"><span data-stu-id="2f13e-458">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="2f13e-459">Você pode iniciar um depurador a partir de um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="2f13e-459">You can launch a debugger from a command prompt.</span></span>

```console
devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="2f13e-460">Você pode usar o log de impressão para stdout.</span><span class="sxs-lookup"><span data-stu-id="2f13e-460">You can use print-to-stdout logging.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f13e-461">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f13e-461">See also</span></span>

- [<span data-ttu-id="2f13e-462">Provedores de Tipos</span><span class="sxs-lookup"><span data-stu-id="2f13e-462">Type Providers</span></span>](index.md)
- [<span data-ttu-id="2f13e-463">O SDK do provedor de tipos</span><span class="sxs-lookup"><span data-stu-id="2f13e-463">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
