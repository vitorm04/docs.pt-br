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
# <a name="tutorial-create-a-type-provider"></a>Tutorial: Crie um provedor de tipos

O mecanismo do provedor de tipo em F# é uma parte significativa de seu suporte para programação rica em informações. Este tutorial explica como criar seus próprios provedores de tipo, guiando você através do desenvolvimento de vários provedores de tipo simples para ilustrar os conceitos básicos. Para obter mais informações sobre o mecanismo do provedor de tipo em F#, consulte [Provedores de tipo](index.md).

O ecossistema F# contém uma gama de provedores de tipo para serviços de dados corporativos e de Internet comumente usados. Por exemplo: 

- [O FSharp.Data](https://fsharp.github.io/FSharp.Data/) inclui provedores de tipo para formatos de documentos JSON, XML, CSV e HTML.

- [O SQLProvider](https://fsprojects.github.io/SQLProvider/) fornece acesso fortemente digitado a bancos de dados SQL por meio de um mapeamento de objetos e consultas F# LINQ contra essas fontes de dados.

- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) tem um conjunto de provedores de tipo para incorporação verificada por tempo de compilação do T-SQL em F#.

- [FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) é um conjunto mais antigo de provedores de tipo para uso apenas com programação .NET Framework para acessar serviços de dados SQL, Entity Framework, OData e WSDL.

Quando necessário, você pode criar provedores de tipo personalizados, ou pode referenciar provedores de tipo que outros criaram. Por exemplo, sua organização pode ter um serviço de dados que fornece um grande e crescente número de conjuntos de dados nomeados, cada um com seu próprio esquema de dados estáveis. Você pode criar um provedor de tipo que lê os esquemas e apresenta os conjuntos de dados atuais para o programador de forma fortemente digitada.

## <a name="before-you-start"></a>Antes de iniciar

O mecanismo do provedor de tipo foi projetado principalmente para injetar dados estáveis e espaços de informações de serviço na experiência de programação F#.

Este mecanismo não foi projetado para injetar espaços de informação cujo esquema muda durante a execução do programa de maneiras relevantes para a lógica do programa. Além disso, o mecanismo não foi projetado para meta-programação intra-linguagem, embora esse domínio contenha alguns usos válidos. Você deve usar este mecanismo apenas quando necessário e onde o desenvolvimento de um provedor de tipo produz um valor muito alto.

Você deve evitar escrever um provedor de tipo onde um esquema não está disponível. Da mesma forma, você deve evitar escrever um provedor de tipo onde uma biblioteca .NET ordinária (ou mesmo existente) seria suficiente.

Antes de começar, você pode fazer as seguintes perguntas:

- Você tem um esquema para sua fonte de informação? Se assim for, qual é o mapeamento no sistema do tipo F# e .NET?

- Você pode usar uma API (digitada dinamicamente) como ponto de partida para sua implementação?

- Você e sua organização terão usos suficientes do provedor do tipo para fazer com que a escrita valha a pena? Uma biblioteca normal .NET atenderia às suas necessidades?

- Quanto seu esquema mudará?

- Mudará durante a codificação?

- Mudará entre as sessões de codificação?

- Mudará durante a execução do programa?

Os provedores de tipos são mais adequados para situações em que o esquema é estável em tempo de execução e durante a vida útil do código compilado.

## <a name="a-simple-type-provider"></a>Um provedor de tipo simples

Esta amostra é Samples.HelloWorldTypeProvider, semelhante `examples` às amostras no diretório do Provedor de [Tipo F# SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/). O provedor disponibiliza um "espaço de tipo" que contém 100 tipos apagados, como mostra o código a `Type1`seguir usando a sintaxe de assinatura F# e omitindo os detalhes para todos, exceto . Para obter mais informações sobre tipos apagados, consulte [detalhes sobre tipos fornecidos apagados](#details-about-erased-provided-types) mais tarde neste tópico.

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

Observe que o conjunto de tipos e membros fornecidos é sabia estáticamente. Este exemplo não aproveita a capacidade dos provedores de fornecer tipos que dependem de um esquema. A implementação do provedor de tipo é descrita no código a seguir, e os detalhes são cobertos em seções posteriores deste tópico.

> [!WARNING]
> Pode haver diferenças entre este código e as amostras online.

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

Para usar este provedor, abra uma instância separada do Visual Studio, crie um script F# e adicione uma referência ao provedor do seu script usando #r como o seguinte código mostra:

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

Em seguida, procure `Samples.HelloWorldTypeProvider` os tipos o namespace que o provedor de tipo gerou.

Antes de recompilar o provedor, certifique-se de que você fechou todas as instâncias do Visual Studio e F# Interactive que estão usando o provedor DLL. Caso contrário, um erro de compilação ocorrerá porque a DLL de saída será bloqueada.

Para depurar este provedor usando instruções de impressão, faça um script que exponha um problema com o provedor e use o seguinte código:

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Para depurar este provedor usando o Visual Studio, abra o Prompt de comando do desenvolvedor para o Visual Studio com credenciais administrativas e execute o seguinte comando:

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Como alternativa, abra o Visual Studio, abra `Debug/Attach to process…`o menu `devenv` Debug, escolha e anexe a outro processo onde você está editando seu script. Usando este método, você pode direcionar mais facilmente a lógica específica no provedor de tipos digitando expressões interativamente na segunda instância (com intelliSense completo e outros recursos).

Você pode desativar a depuração do Just My Code para identificar melhor os erros no código gerado. Para obter informações sobre como ativar ou desativar esse recurso, consulte [Navegando através de Código com o Depurador](/visualstudio/debugger/navigating-through-code-with-the-debugger). Além disso, você também pode definir a `Debug` captura de `Exceptions` exceção de primeira chance abrindo o `Exceptions` menu e, em seguida, escolhendo ou escolhendo as teclas Ctrl+Alt+E para abrir a caixa de diálogo. Nessa caixa de `Common Language Runtime Exceptions`diálogo, `Thrown` em , selecione a caixa de seleção.

### <a name="implementation-of-the-type-provider"></a>Implementação do Provedor de Tipo

Esta seção orienta você através das principais seções da implementação do provedor de tipo. Primeiro, você define o tipo para o próprio provedor de tipo personalizado:

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

Esse tipo deve ser público, e você deve marcá-lo com o atributo [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) para que o compilador reconheça o provedor de tipos quando um projeto F# separado fizer referência ao conjunto que contém o tipo. O parâmetro *de configuração* é opcional e, se presente, contém informações de configuração contextuais para a instância do provedor de tipo que o compilador F# cria.

Em seguida, você implementa a interface [ITypeProvider.](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) Neste caso, você `TypeProviderForNamespaces` usa o `ProvidedTypes` tipo da API como um tipo de base. Este tipo de ajudante pode fornecer uma coleção finita de espaços de nome ansiosamente fornecidos, cada um dos quais contém diretamente um número finito de tipos fixos e ansiosamente fornecidos. Nesse contexto, o provedor gera *ansiosamente* tipos, mesmo que não sejam necessários ou usados.

```fsharp
inherit TypeProviderForNamespaces(config)
```

Em seguida, defina valores privados locais que especifiquem o namespace para os tipos fornecidos e encontre o próprio conjunto do provedor de tipos. Este conjunto é usado mais tarde como o tipo lógico dos tipos apagados que são fornecidos.

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

Em seguida, crie uma função para fornecer cada um dos tipos Tipo1... Tipo100. Esta função é explicada com mais detalhes mais tarde neste tópico.

```fsharp
let makeOneProvidedType (n:int) = …
```

Em seguida, gere os 100 tipos fornecidos:

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

Em seguida, adicione os tipos como um namespace fornecido:

```fsharp
do this.AddNamespace(namespaceName, types)
```

Finalmente, adicione um atributo de montagem que indique que você está criando um provedor de tipo DLL:

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a>fornecendo um tipo e seus membros

A `makeOneProvidedType` função faz o trabalho real de fornecer um dos tipos.

```fsharp
let makeOneProvidedType (n:int) =
…
```

Esta etapa explica a implementação dessa função. Primeiro, crie o tipo fornecido (por exemplo, Tipo1, quando n = 1, ou Type57, quando n = 57).

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

Você deve observar os seguintes pontos:

- Este tipo fornecido é apagado.  Como você indica que `obj`o tipo base é , as instâncias aparecerão como valores do tipo [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) em código compilado.

- Quando você especificar um tipo não aninhado, você deve especificar o conjunto e o namespace. Para tipos apagados, o conjunto deve ser o próprio conjunto do provedor do tipo.

Em seguida, adicione a documentação XML ao tipo. Esta documentação está atrasada, ou seja, calculada demanda se o compilador host precisar.

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

Em seguida, você adiciona uma propriedade estática fornecida ao tipo:

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

Conseguir essa propriedade sempre avaliará a string "Hello!". O `GetterCode` para a propriedade usa uma cotação F#, que representa o código que o compilador host gera para obter a propriedade. Para obter mais informações sobre cotações, consulte [Cotações de Código (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).

Adicione a documentação XML à propriedade.

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

Agora anexar a propriedade fornecida ao tipo fornecido. Você deve anexar um membro fornecido a um e apenas um tipo. Caso contrário, o membro nunca será acessível.

```fsharp
t.AddMember staticProp
```

Agora crie um construtor fornecido que não tome parâmetros.

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

O `InvokeCode` para o construtor retorna uma cotação F#, que representa o código que o compilador host gera quando o construtor é chamado. Por exemplo, você pode usar o seguinte construtor:

```fsharp
new Type10()
```

Uma instância do tipo fornecido será criada com dados subjacentes "Os dados do objeto". O código citado inclui uma conversão para [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) porque esse tipo é o apagamento deste tipo fornecido (como você especificou quando declarou o tipo fornecido).

Adicione a documentação XML ao construtor e adicione o construtor fornecido ao tipo fornecido:

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

Crie um segundo construtor fornecido que leve um parâmetro:

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

O `InvokeCode` para o construtor retorna novamente uma cotação F#, que representa o código que o compilador host gerou para uma chamada para o método. Por exemplo, você pode usar o seguinte construtor:

```fsharp
new Type10("ten")
```

Uma instância do tipo fornecido é criada com dados subjacentes "dez". Você já deve ter `InvokeCode` notado que a função retorna uma cotação. A entrada para esta função é uma lista de expressões, uma por parâmetro de construtor. Neste caso, uma expressão que representa o valor `args.[0]`único do parâmetro está disponível em . O código de uma chamada para o construtor coece o `obj`valor de retorno para o tipo apagado . Depois de adicionar o segundo construtor fornecido ao tipo, você cria uma propriedade de instância fornecida:

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

Obter esta propriedade retornará o comprimento da string, que é o objeto de representação. A `GetterCode` propriedade retorna uma cotação F# que especifica o código que o compilador host gera para obter a propriedade. Como, `InvokeCode` `GetterCode` a função retorna uma cotação. O compilador host chama essa função com uma lista de argumentos. Neste caso, os argumentos incluem apenas a expressão única que representa a instância sobre a `args.[0]`qual o getter está sendo chamado, que você pode acessar usando . A implementação de `GetterCode` então emenda na cotação de `obj`resultados no tipo apagado , e um molde é usado para satisfazer o mecanismo do compilador para verificar tipos de que o objeto é uma string. A próxima `makeOneProvidedType` parte fornece um método de ocorrência com um parâmetro.

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

Finalmente, crie um tipo aninhado que contenha 100 propriedades aninhadas. A criação desse tipo aninhado e suas propriedades está atrasada, ou seja, computada demanda.

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

### <a name="details-about-erased-provided-types"></a>Detalhes sobre tipos fornecidos apagados

O exemplo nesta seção fornece apenas *tipos apagados fornecidos,* que são particularmente úteis nas seguintes situações:

- Quando você está escrevendo um provedor para um espaço de informação que contém apenas dados e métodos.

- Quando você está escrevendo um provedor onde a semântica precisa do tipo runtime não é crítica para o uso prático do espaço de informação.

- Quando você está escrevendo um provedor para um espaço de informação tão grande e interconectado que não é tecnicamente viável gerar tipos .NET reais para o espaço de informação.

Neste exemplo, cada tipo fornecido é apagado `obj`para digitar , e todos `obj` os usos do tipo aparecerão como tipo em código compilado. Na verdade, os objetos subjacentes nesses exemplos são strings, mas o tipo aparecerá como `System.Object` em código compilado .NET. Como em todos os usos de apagamento de tipo, você pode usar boxe explícito, unboxing e elenco para subverter tipos apagados. Neste caso, uma exceção de elenco que não é válida pode resultar quando o objeto é usado. Um tempo de execução do provedor pode definir seu próprio tipo de representação privada para ajudar a proteger contra falsas representações. Você não pode definir tipos apagados em f# em si. Somente os tipos fornecidos podem ser apagados. Você deve entender as ramificações, tanto práticas quanto semânticas, de usar tipos apagados para o seu provedor de tipo ou um provedor que fornece tipos apagados. Um tipo apagado não tem nenhum tipo real .NET. Portanto, você não pode fazer uma reflexão precisa sobre o tipo, e você pode subverter tipos apagados se você usar moldes de tempo de execução e outras técnicas que dependem de semântica exata do tipo de tempo de execução. A subversão de tipos apagados frequentemente resulta em exceções de elenco de tipo em tempo de execução.

### <a name="choosing-representations-for-erased-provided-types"></a>Escolhendo representações para tipos fornecidos apagados

Para alguns usos de tipos apagados fornecidos, nenhuma representação é necessária. Por exemplo, o tipo apagado fornecido pode conter apenas propriedades estáticas e membros e sem construtores, e nenhum método ou propriedades retornaria uma instância do tipo. Se você pode alcançar instâncias de um tipo fornecido apagado, você deve considerar as seguintes perguntas:

**Qual é o apagamento de um tipo fornecido?**

- A eliminação de um tipo fornecido é como o tipo aparece no código .NET compilado.

- O apagamento de um tipo de classe apagado fornecido é sempre o primeiro tipo de base não apagado na cadeia de herança do tipo.

- O apagamento de um tipo de interface `System.Object`aserdestejada fornecido é sempre .

**Quais são as representações de um tipo fornecido?**

- O conjunto de possíveis objetos para um tipo apagado é chamado de suas representações. No exemplo deste documento, as representações de todos os `Type1..Type100` tipos apagados fornecidos são sempre objetos de cadeia.

Todas as representações de um tipo fornecido devem ser compatíveis com a eliminação do tipo fornecido. (Caso contrário, o compilador F# dará um erro para o uso do provedor de tipo ou o código .NET não verificável que não é válido será gerado. Um provedor de tipo não é válido se ele retornar código que dá uma representação que não é válida.)

Você pode escolher uma representação para objetos fornecidos usando qualquer uma das seguintes abordagens, ambas muito comuns:

- Se você está simplesmente fornecendo um invólucro fortemente digitado sobre um tipo .NET existente, muitas vezes faz sentido para o seu tipo apagar para esse tipo, usar instâncias desse tipo como representações, ou ambos. Esta abordagem é apropriada quando a maioria dos métodos existentes nesse tipo ainda fazem sentido ao usar a versão fortemente digitada.

- Se você quiser criar uma API que difere significativamente de qualquer API .NET existente, faz sentido criar tipos de tempo de execução que serão o apagamento do tipo e representações para os tipos fornecidos.

O exemplo neste documento usa strings como representações de objetos fornecidos. Frequentemente, pode ser apropriado usar outros objetos para representações. Por exemplo, você pode usar um dicionário como saco de propriedades:

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

Como alternativa, você pode definir um tipo no provedor de tipo que será usado em tempo de execução para formar a representação, juntamente com uma ou mais operações em tempo de execução:

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

Desde que os membros possam construir instâncias desse tipo de objeto:

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

Neste caso, você pode (opcionalmente) usar esse tipo como apagamento `baseType` de tipo `ProvidedTypeDefinition`especificando este tipo como o ao construir o :

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a>Lições-chave

A seção anterior explicou como criar um provedor de tipo de apagamento simples que fornece uma variedade de tipos, propriedades e métodos. Esta seção também explicou o conceito de eliminação de tipos, incluindo algumas das vantagens e desvantagens de fornecer tipos apagados de um provedor de tipo, e discutiu representações de tipos apagados.

## <a name="a-type-provider-that-uses-static-parameters"></a>Um provedor de tipo que usa parâmetros estáticos

A capacidade de parametrizar provedores de tipos por dados estáticos permite muitos cenários interessantes, mesmo nos casos em que o provedor não precisa acessar nenhum dado local ou remoto. Nesta seção, você aprenderá algumas técnicas básicas para montar tal provedor.

### <a name="type-checked-regex-provider"></a>Provedor Regex verificado de tipo

Imagine que você deseja implementar um provedor de tipo para <xref:System.Text.RegularExpressions.Regex> expressões regulares que envolva as bibliotecas .NET em uma interface que fornece as seguintes garantias de tempo de compilação:

- Verificando se uma expressão regular é válida.

- Fornecendo propriedades nomeadas em correspondências baseadas em nomes de grupo na expressão regular.

Esta seção mostra como usar provedores de tipo para criar um `RegexTyped` tipo que o padrão de expressão regular parametriza para fornecer esses benefícios. O compilador relatará um erro se o padrão fornecido não for válido, e o provedor de tipo pode extrair os grupos do padrão para que você possa acessá-los usando propriedades nomeadas em correspondências. Quando você projeta um provedor de tipo, você deve considerar como sua API exposta deve parecer para usuários finais e como esse design se traduzirá em código .NET. O exemplo a seguir mostra como usar tal API para obter os componentes do código de área:

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

O exemplo a seguir mostra como o provedor de tipos traduz essas chamadas:

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

Observe os seguintes pontos:

- O tipo Regex padrão representa `RegexTyped` o tipo parametrizado.

- O `RegexTyped` construtor resulta em uma chamada para o construtor Regex, passando no argumento do tipo estático para o padrão.

- Os resultados `Match` do método são <xref:System.Text.RegularExpressions.Match> representados pelo tipo padrão.

- Cada grupo nomeado resulta em uma propriedade fornecida, e acessar a propriedade resulta `Groups` no uso de um indexador na coleção de uma partida.

O código a seguir é o núcleo da lógica para implementar tal provedor, e este exemplo omite a adição de todos os membros ao tipo fornecido. Para obter informações sobre cada membro adicionado, consulte a seção apropriada mais tarde neste tópico. Para obter o código completo, baixe a amostra do [F# 3.0 Sample Pack](https://archive.codeplex.com/?p=fsharp3sample) no site do CodePlex.

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

Observe os seguintes pontos:

- O provedor de tipos tem `pattern`dois parâmetros estáticos: o , que é obrigatório, e o `options`, que são opcionais (porque um valor padrão é fornecido).

- Depois que os argumentos estáticos são fornecidos, você cria uma instância da expressão regular. Esta instância abrirá uma exceção se o Regex estiver mal formado e esse erro será relatado aos usuários.

- Dentro `DefineStaticParameters` do retorno de chamada, você define o tipo que será devolvido após o fornecimento dos argumentos.

- Este código `HideObjectMethods` define-se como verdadeiro para que a experiência do IntelliSense permaneça simplificada. Esse atributo `Equals` `GetHashCode`faz `Finalize`com `GetType` que os membros sejam suprimidos das listas do IntelliSense para um objeto fornecido.

- Você `obj` usa como o tipo base do método, `Regex` mas você usará um objeto como a representação em tempo de execução deste tipo, como mostra o próximo exemplo.

- A chamada `Regex` para o <xref:System.ArgumentException> construtor joga um quando uma expressão regular não é válida. O compilador captura essa exceção e relata uma mensagem de erro para o usuário na hora da compilação ou no editor do Visual Studio. Essa exceção permite que expressões regulares sejam validadas sem executar um aplicativo.

O tipo definido acima ainda não é útil porque não contém nenhum método ou propriedades significativas. Primeiro, adicione `IsMatch` um método estático:

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

O código anterior define `IsMatch`um método , que toma `bool`uma seqüência como entrada e retorna a . A única parte complicada é `args` o uso `InvokeCode` do argumento dentro da definição. Neste exemplo, `args` há uma lista de citações que representa os argumentos para este método. Se o método é um método de `this` instância, o primeiro argumento representa o argumento. No entanto, para um método estático, os argumentos são todos apenas os argumentos explícitos para o método. Observe que o tipo do valor citado deve corresponder ao tipo `bool`de retorno especificado (neste caso, ). Observe também que este `AddXmlDoc` código usa o método para garantir que o método fornecido também tenha documentação útil, que você pode fornecer através do IntelliSense.

Em seguida, adicione um método de correspondência de ocorrência. No entanto, este método deve `Match` retornar um valor de um tipo fornecido para que os grupos possam ser acessados de forma fortemente digitada. Assim, primeiro você `Match` declara o tipo. Como esse tipo depende do padrão fornecido como argumento estático, esse tipo deve ser aninhado dentro da definição de tipo parametrizado:

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

Em seguida, adicione uma propriedade ao tipo Match para cada grupo. Em tempo de execução, <xref:System.Text.RegularExpressions.Match> uma partida é representada como um valor, <xref:System.Text.RegularExpressions.Match.Groups> de modo que a cotação que define a propriedade deve usar a propriedade indexada para obter o grupo relevante.

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

Novamente, observe que você está adicionando a documentação XML à propriedade fornecida. Observe também que uma propriedade `GetterCode` pode ser lida se uma função for `SetterCode` fornecida, e a propriedade pode ser escrita se uma função for fornecida, de modo que a propriedade resultante seja apenas lida.

Agora você pode criar um método de `Match` instância que retorna um valor desse tipo:

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

Porque você está criando `args.[0]` um método `RegexTyped` de instância, representa a `args.[1]` instância na qual o método está sendo chamado, e é o argumento de entrada.

Finalmente, forneça um construtor para que instâncias do tipo fornecido possam ser criadas.

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

O construtor simplesmente apaga para a criação de uma instância padrão .NET Regex, que é novamente encaixotada em um objeto porque `obj` é o apagamento do tipo fornecido. Com essa mudança, o uso da API amostra que especificava anteriormente no tópico funciona conforme esperado. O seguinte código é completo e final:

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

### <a name="key-lessons"></a>Lições-chave

Esta seção explicou como criar um provedor de tipo que opera em seus parâmetros estáticos. O provedor verifica o parâmetro estático e fornece operações com base em seu valor.

## <a name="a-type-provider-that-is-backed-by-local-data"></a>Um provedor de tipo que é apoiado por dados locais

Frequentemente, você pode querer que os provedores de tipos apresentem APIs com base não apenas em parâmetros estáticos, mas também em informações de sistemas locais ou remotos. Esta seção discute provedores de tipo que são baseados em dados locais, como arquivos de dados locais.

### <a name="simple-csv-file-provider"></a>Provedor de arquivos CSV simples

Como exemplo simples, considere um provedor de tipo para acessar dados científicos no formato CSV (Comma Separated Value). Esta seção assume que os arquivos CSV contêm uma linha de cabeçalho seguida de dados de ponto flutuante, como ilustra a tabela a seguir:

|Distância (medidor)|Tempo (segundo)|
|----------------|-------------|
|50.0|3.7|
|100.0|5.2|
|150.0|6.4|

Esta seção mostra como fornecer um tipo que você `Distance` pode `float<meter>` usar `Time` para obter `float<second>`linhas com uma propriedade de tipo e uma propriedade do tipo . Para simplificar, são feitas as seguintes suposições:

- Os nomes de cabeçalho são sem unidade ou têm o formulário "Nome (unidade)" e não contêm commas.

- As unidades são todas unidades do System International (SI) como define o módulo [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#).](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b)

- As unidades são todas simples (por exemplo, medidor) em vez de compostas (por exemplo, medidor/segundo).

- Todas as colunas contêm dados de pontos flutuantes.

Um provedor mais completo afrouxaria essas restrições.

Novamente, o primeiro passo é considerar como a API deve ficar. Dado `info.csv` um arquivo com o conteúdo da tabela anterior (em formato separado por comma), os usuários do provedor devem ser capazes de escrever código que se assemelha ao seguinte exemplo:

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

Neste caso, o compilador deve converter essas chamadas em algo como o seguinte exemplo:

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

A tradução ideal exigirá que o `CsvFile` provedor de tipos defina um tipo real na montagem do provedor do tipo. Os provedores de tipos geralmente dependem de alguns tipos e métodos auxiliares para envolver uma lógica importante. Como as medidas são apagadas em tempo `float[]` de execução, você pode usar um tipo agravado para uma linha. O compilador tratará diferentes colunas como tendo diferentes tipos de medidas. Por exemplo, a primeira coluna `float<meter>`em nosso exemplo `float<second>`tem tipo , e a segunda tem . No entanto, a representação apagada pode permanecer bastante simples.

O código a seguir mostra o núcleo da implementação.

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

Observe os seguintes pontos sobre a implementação:

- Os construtores sobrecarregados permitem que o arquivo original ou um que tenha um esquema idêntico seja lido. Esse padrão é comum quando você escreve um provedor de tipo para fontes de dados locais ou remotas, e esse padrão permite que um arquivo local seja usado como modelo para dados remotos.

- Você pode usar o valor [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) que é passado para o construtor do provedor de tipos para resolver nomes de arquivos relativos.

- Você pode `AddDefinitionLocation` usar o método para definir a localização das propriedades fornecidas. Portanto, se você `Go To Definition` usar em uma propriedade fornecida, o arquivo CSV será aberto no Visual Studio.

- Você pode `ProvidedMeasureBuilder` usar o tipo para procurar as unidades `float<_>` SI e gerar os tipos relevantes.

### <a name="key-lessons"></a>Lições-chave

Esta seção explicou como criar um provedor de tipo para uma fonte de dados local com um esquema simples que está contido na própria fonte de dados.

## <a name="going-further"></a>Aprofundamento

As seções a seguir incluem sugestões para um estudo mais aprofundado.

### <a name="a-look-at-the-compiled-code-for-erased-types"></a>Uma olhada no código compilado para tipos apagados

Para dar uma ideia de como o uso do provedor de tipo corresponde ao código emitido, `HelloWorldTypeProvider` consulte a seguinte função usando o que é usado anteriormente neste tópico.

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

Aqui está uma imagem do código resultante descompilado usando ildasm.exe:

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

Como o exemplo mostra, todas `Type1` as `InstanceProperty` menções do tipo e da propriedade foram apagadas, deixando apenas operações nos tipos de tempo de execução envolvidos.

### <a name="design-and-naming-conventions-for-type-providers"></a>Convenções de Design e Nomeação para Provedores de Tipos

Observe as seguintes convenções ao criar provedores de tipos.

**Provedores de Protocolos de Conectividade** Em geral, os nomes da maioria dos DLLs do provedor para protocolos de conectividade de `TypeProvider` `TypeProviders`dados e serviços, como conexões OData ou SQL, devem terminar em ou . Por exemplo, use um nome DLL que se assemelhe à seguinte seqüência de string:

`Fabrikam.Management.BasicTypeProviders.dll`

Certifique-se de que seus tipos fornecidos são membros do namespace correspondente e indique o protocolo de conectividade que você implementou:

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

**Provedores de utilidades para codificação geral**.  Para um provedor de tipo de utilidade como o de expressões regulares, o provedor de tipo pode fazer parte de uma biblioteca base, como mostra o exemplo a seguir:

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

Neste caso, o tipo fornecido apareceria em um ponto apropriado de acordo com as convenções normais de design .NET:

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

**Fontes de dados de Singleton**. Alguns provedores de tipo se conectam a uma única fonte de dados dedicada e fornecem apenas dados. Neste caso, você deve `TypeProvider` soltar o sufixo e usar convenções normais para nomear .NET:

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

Para obter mais `GetConnection` informações, consulte a convenção de design descrita mais tarde neste tópico.

### <a name="design-patterns-for-type-providers"></a>Padrões de design para provedores de tipos

As seções a seguir descrevem padrões de design que você pode usar ao criar provedores de tipos.

#### <a name="the-getconnection-design-pattern"></a>O padrão de design getconnection

A maioria dos provedores `GetConnection` de tipos deve ser escrita para usar o padrão usado pelos provedores de tipo em FSharp.Data.TypeProviders.dll, como mostra o exemplo a seguir:

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>Provedores de tipo apoiados por dados e serviços remotos

Antes de criar um provedor de tipo que seja apoiado por dados e serviços remotos, você deve considerar uma série de problemas que são inerentes à programação conectada. Essas questões incluem as seguintes considerações:

- mapeamento esquema

- vida e invalidação na presença de mudança de esquema

- cache esquema

- implementações assíncronas de operações de acesso a dados

- suporte a consultas, incluindo consultas LINQ

- credenciais e autenticação

Este tópico não explora mais essas questões.

### <a name="additional-authoring-techniques"></a>Técnicas adicionais de autoria

Quando você escreve seus próprios provedores de tipo, você pode querer usar as seguintes técnicas adicionais.

### <a name="creating-types-and-members-on-demand"></a>Criando tipos e membros demanda

A API ProvidedType tem versões atrasadas do AddMember.

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

Essas versões são usadas para criar espaços demanda de tipos.

### <a name="providing-array-types-and-generic-type-instantiations"></a>Fornecendo tipos de array e instanciações genéricas do tipo

Você faz membros fornecidos (cujas assinaturas incluem tipos de matriz, tipos de byref `MakePointerType`e `MakeGenericType` instanciações de tipos genéricos) usando o normal <xref:System.Type> `MakeArrayType`, e em qualquer instância de , incluindo `ProvidedTypeDefinitions`.

> [!NOTE]
> Em alguns casos, você pode `ProvidedTypeBuilder.MakeGenericType`ter que usar o ajudante em .  Consulte a [documentação do Provedor de Tipo SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) para obter mais detalhes.

### <a name="providing-unit-of-measure-annotations"></a>Fornecendo Anotações de Unidade de Medida

A API ProvidedTypes fornece ajuda para fornecer anotações de medida. Por exemplo, para `float<kg>`fornecer o tipo, use o seguinte código:

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  Para fornecer `Nullable<decimal<kg/m^2>>`o tipo, use o seguinte código:

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a>Acessando recursos locais de projeto ou script

Cada instância de um provedor `TypeProviderConfig` de tipo pode receber um valor durante a construção. Este valor contém a "pasta de resolução" para o provedor (ou seja, a pasta do projeto para a compilação ou o diretório que contém um script), a lista de conjuntos referenciados e outras informações.

### <a name="invalidation"></a>Invalidação

Os provedores podem levantar sinais de invalidação para notificar o serviço de idioma F# de que as suposições do esquema podem ter mudado. Quando ocorre a invalidação, uma verificação de tipo é refeita se o provedor estiver hospedado no Visual Studio. Esse sinal será ignorado quando o provedor estiver hospedado no F# Interactive ou no F# Compiler (fsc.exe).

### <a name="caching-schema-information"></a>Informações sobre esquemas de cache

Os provedores devem, muitas vezes, armazenar acesso a informações de esquema. Os dados armazenados em cache devem ser armazenados usando um nome de arquivo que é dado como parâmetro estático ou como dados do usuário. Um exemplo de cache de `LocalSchemaFile` esquema é o parâmetro `FSharp.Data.TypeProviders` nos provedores do tipo na montagem. Na implementação desses provedores, este parâmetro estático orienta o provedor de tipo a usar as informações do esquema no arquivo local especificado em vez de acessar a fonte de dados pela rede. Para usar informações de esquema em cache, você `ForceUpdate` também `false`deve definir o parâmetro estático para . Você pode usar uma técnica semelhante para permitir o acesso a dados on-line e off-line.

### <a name="backing-assembly"></a>Montagem de apoio

Quando você compila `.dll` `.exe` um ou arquivo, o arquivo de backup .dll para tipos gerados é estáticamente vinculado ao conjunto resultante. Este link é criado copiando as definições do tipo Idioma Intermediário (IL) e quaisquer recursos gerenciados da montagem de apoio para a montagem final. Quando você usa F# Interactive, o arquivo de backup .dll não é copiado e, em vez disso, é carregado diretamente no processo F# Interactive.

### <a name="exceptions-and-diagnostics-from-type-providers"></a>Exceções e Diagnósticos de Provedores de Tipo

Todos os usos de todos os membros dos tipos fornecidos podem lançar exceções. Em todos os casos, se um provedor de tipo lançar uma exceção, o compilador host atribui o erro a um provedor de tipo específico.

- As exceções do provedor de tipos nunca devem resultar em erros internos do compilador.

- Os provedores de tipos não podem relatar avisos.

- Quando um provedor de tipo está hospedado no compilador F#, em um ambiente de desenvolvimento F# ou no F# Interactive, todas as exceções desse provedor são capturadas. A propriedade Mensagem é sempre o texto de erro, e nenhum rastreamento de pilha é exibido. Se você vai abrir uma exceção, você pode `System.NotSupportedException`lançar `System.IO.IOException` `System.Exception`os seguintes exemplos: , , .

#### <a name="providing-generated-types"></a>Fornecendo tipos gerados

Até agora, este documento explicou como fornecer tipos apagados. Você também pode usar o mecanismo do provedor de tipo em F# para fornecer tipos gerados, que são adicionados como definições reais do tipo .NET no programa dos usuários. Você deve consultar os tipos gerados fornecidos usando uma definição de tipo.

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

O código auxiliar ProvidedTypes-0.2 que faz parte da versão F# 3.0 tem apenas suporte limitado para fornecer tipos gerados. As seguintes instruções devem ser verdadeiras para uma definição de tipo gerada:

- `isErased` deve ser definido como `false`.

- O tipo gerado deve ser adicionado `ProvidedAssembly()`a um recém-construído, que representa um recipiente para fragmentos de código gerados.

- O provedor deve ter um conjunto que tenha um arquivo .NET .dll de backup real com um arquivo .dll correspondente no disco.

## <a name="rules-and-limitations"></a>Regras e Limitações

Ao escrever provedores de tipo, tenha em mente as seguintes regras e limitações.

### <a name="provided-types-must-be-reachable"></a>Os tipos fornecidos devem ser acessíveis

Todos os tipos fornecidos devem ser acessíveis a partir dos tipos não aninhados. Os tipos não aninhados são `TypeProviderForNamespaces` dados na chamada `AddNamespace`para o construtor ou uma chamada para . Por exemplo, se o `StaticClass.P : T`provedor fornecer um tipo, você deve garantir que T seja um tipo não aninhado ou aninhado um.

Por exemplo, alguns provedores `DataTypes` têm uma `T1, T2, T3, ...` classe estática como a que contém esses tipos. Caso contrário, o erro diz que uma referência ao tipo T no conjunto A foi encontrada, mas o tipo não pôde ser encontrado naquele conjunto. Se esse erro aparecer, verifique se todos os seus subtipos podem ser alcançados a partir dos tipos do provedor. Nota: `T1, T2, T3...` Esses tipos são referidos como os tipos *on-the-fly.* Lembre-se de colocá-los em um namespace acessível ou um tipo de pai.

### <a name="limitations-of-the-type-provider-mechanism"></a>Limitações do Mecanismo do Provedor de Tipo

O mecanismo do provedor de tipo em F# tem as seguintes limitações:

- A infra-estrutura subjacente para provedores de tipo em F# não suporta tipos genéricos fornecidos ou métodos genéricos fornecidos.

- O mecanismo não suporta tipos aninhados com parâmetros estáticos.

## <a name="development-tips"></a>Dicas de desenvolvimento

Você pode achar as seguintes dicas úteis durante o processo de desenvolvimento:

### <a name="run-two-instances-of-visual-studio"></a>Execute duas instâncias do Visual Studio

Você pode desenvolver o provedor de tipo em uma instância e testar o provedor na outra, porque o IDE de teste fará um bloqueio no arquivo .dll que impede que o provedor do tipo seja reconstruído. Assim, você deve fechar a segunda instância do Visual Studio enquanto o provedor é construído em primeira instância, e então você deve reabrir a segunda instância após a construção do provedor.

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a>Provedores do tipo de depuração usando invocações de fsc.exe

Você pode invocar provedores de tipos usando as seguintes ferramentas:

- fsc.exe (compilador de linha de comando F#)

- fsi.exe (Compilador Interativo F#)

- devenv.exe (Visual Studio)

Muitas vezes você pode depurar provedores de tipo mais facilmente usando fsc.exe em um arquivo de script de teste (por exemplo, script.fsx). Você pode iniciar um depurador a partir de um prompt de comando.

```console
devenv /debugexe fsc.exe script.fsx
```

  Você pode usar o registro impresso-to-stdout.

## <a name="see-also"></a>Confira também

- [Provedores de Tipos](index.md)
- [O provedor de tipo SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
