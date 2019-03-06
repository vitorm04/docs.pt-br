---
title: 'Tutorial: Criar um provedor de tipo'
description: Saiba como criar seu próprio F# digite provedores no F# 3.0, examinando a vários provedores de tipo simples para ilustrar os conceitos básicos.
ms.date: 02/02/2019
ms.openlocfilehash: ec26f25ad39ca432d6ef11238268e1704bd9638b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371549"
---
# <a name="tutorial-create-a-type-provider"></a>Tutorial: Criar um provedor de tipo

O mecanismo de provedor de tipo no F# é uma parte significativa do seu suporte para programação rica de informações. Este tutorial explica como criar seus próprios provedores de tipos ao guiá-lo através do desenvolvimento de vários provedores de tipo simples para ilustrar os conceitos básicos. Para obter mais informações sobre o mecanismo de provedor de tipo em F#, consulte [provedores de tipos](index.md).

O F# ecossistema contém uma variedade de provedores de tipos para serviços de dados corporativos e da Internet comumente usados. Por exemplo:

- [FSharp](https://fsharp.github.io/FSharp.Data/) inclui provedores de tipos de formatos de documentos JSON, XML, CSV e HTML.

- [SQLProvider](https://fsprojects.github.io/SQLProvider/) fornece acesso fortemente tipado para bancos de dados SQL por meio de um mapeamento de objeto e F# consultas LINQ em relação a essas fontes de dados.

- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) tem um conjunto de provedores de tipo para o tempo de compilação verificada incorporação do T-SQL no F#.

- [Typeproviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) é um conjunto mais antigo de provedores de tipos para uso apenas com a programação do .NET Framework para acessar os serviços de dados SQL, Entity Framework, OData e WSDL.

Onde for necessário, você pode criar provedores de tipos personalizados, ou você pode fazer referência a provedores de tipos criados por outros usuários. Por exemplo, sua organização pode ter um serviço de dados que fornece um grande e crescente número de conjuntos de dados nomeados, cada um com seu próprio esquema de dados estáveis. Você pode criar um provedor de tipo que lê os esquemas e apresenta os conjuntos de dados atuais para o programador de uma forma fortemente tipada.

## <a name="before-you-start"></a>Antes de começar

O mecanismo de provedor de tipo é projetado principalmente para injetar dados estáveis e espaços de informações do serviço para o F# experiência de programação.

Esse mecanismo não foi projetado para injetar espaços informações cujo esquema é alterado durante a execução do programa de maneiras que sejam relevantes para a lógica do programa. Além disso, o mecanismo não foi projetado para intraidioma metaprogramação, mesmo que esse domínio contém alguns usos válidos. Você deve usar esse mecanismo somente quando necessário e, em que o desenvolvimento de um provedor de tipo produz o valor muito alto.

Você deve evitar escrever um provedor de tipo no qual um esquema não está disponível. Da mesma forma, você deve evitar escrever um provedor de tipo, onde um comum (ou até mesmo um existente) biblioteca .NET seria suficiente.

Antes de começar, você pode fazer as perguntas a seguir:

- Você tem um esquema para sua fonte de informações? Se assim, o que é o mapeamento para o F# e o sistema de tipos do .NET?

- Você pode usar uma API (dinamicamente tipada) existente como ponto de partida para sua implementação?

- Você e sua organização terá suficiente usos do provedor do tipo para tornar a escrevê-lo que vale a pena? Uma biblioteca .NET normal atendem suas necessidades?

- Quanto seu esquema será alterado?

- Ele será alterado durante a codificação?

- Ele será alterado entre as sessões de codificação?

- Ele será alterado durante a execução do programa?

Provedores de tipos são mais adequados para situações em que o esquema é estável no tempo de execução e durante o tempo de vida do código compilado.

## <a name="a-simple-type-provider"></a>Um provedor de tipo simples

Esta amostra é Samples.HelloWorldTypeProvider, semelhante aos exemplos na `examples` diretório da [ F# tipo de provedor de SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/). O provedor torna disponível um "espaço de tipo" que contém 100 tipos apagados, como mostra o código usando F# sintaxe de assinatura e omitindo os detalhes para todos, exceto `Type1`. Para obter mais informações sobre os tipos de apagados, consulte [detalhes sobre apagados fornecidos tipos](#details-about-erased-provided-types) mais adiante neste tópico.

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

Observe que o conjunto de tipos e membros fornecidos é conhecido estaticamente. Este exemplo não aproveita a capacidade de provedores fornecem tipos que dependem de um esquema. A implementação do provedor de tipo é descrita no código a seguir, e os detalhes são abordados nas seções posteriores deste tópico.

> [!WARNING]
> Pode haver diferenças entre esse código e os exemplos on-line.

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

Para usar esse provedor, abra uma instância separada do Visual Studio, crie um F# script e, em seguida, adicione uma referência para o provedor do seu script usando #r, como mostra o código a seguir:

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

Em seguida, procure os tipos no `Samples.HelloWorldTypeProvider` namespace que o provedor de tipos gerado.

Antes de recompilar o provedor, certifique-se de que você fechar todas as instâncias do Visual Studio e F# interativo que estiver usando a DLL do provedor. Caso contrário, ocorrerá um erro de compilação porque a DLL de saída será bloqueada.

Para depurar este provedor usando as instruções print, fazer com que um script que expõe um problema com o provedor e, em seguida, use o seguinte código:

```
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Para depurar este provedor usando o Visual Studio, abra o Prompt de comando do desenvolvedor para Visual Studio com credenciais administrativas e execute o seguinte comando:

```
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Como alternativa, abra o Visual Studio, abra o menu de depuração, escolha `Debug/Attach to process…`e anexar para outro `devenv` processo no qual você está editando o script. Usando esse método, você pode direcionar mais facilmente a lógica específica no provedor de tipos digitando interativamente expressões na segunda instância (com suporte total ao IntelliSense e outros recursos).

Você pode desabilitar apenas meu código de depuração para identificar melhor os erros no código gerado. Para obter informações sobre como habilitar ou desabilitar esse recurso, consulte [navegar pelo código com o depurador](/visualstudio/debugger/navigating-through-code-with-the-debugger). Além disso, você também pode definir exceções de primeira chance capturando abrindo o `Debug` menu e, em seguida, escolhendo `Exceptions` ou escolhendo as teclas Ctrl + Alt + E para abrir o `Exceptions` caixa de diálogo. Na caixa de diálogo, sob `Common Language Runtime Exceptions`, selecione o `Thrown` caixa de seleção.

### <a name="implementation-of-the-type-provider"></a>Implementação do provedor de tipo

Esta seção explica as seções principais da implementação do provedor de tipo. Primeiro, defina o tipo para o próprio provedor de tipo personalizado:

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

Esse tipo deve ser público e você deve marcá-la com o [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) para que o compilador reconheça o provedor de tipo quando um separado do atributo F# projeto faz referência ao assembly que contém o tipo. O *config* parâmetro é opcional e, se estiver presente, contém informações de configuração contextual para o provedor de tipo de instância que o F# compilador cria.

Em seguida, você implementa o [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface. Nesse caso, você usa o `TypeProviderForNamespaces` tipo do `ProvidedTypes` API como um tipo base. Esse tipo de auxiliar pode fornecer uma coleção finita de avidamente fornecida namespaces, diretamente, cada um deles contém um número finito de fixo, avidamente tipos. Nesse contexto, o provedor *avidamente* gera tipos, mesmo se eles não são necessários ou usados.

```fsharp
inherit TypeProviderForNamespaces(config)
```

Em seguida, definir valores particulares locais que especificam o namespace para os tipos fornecidos e localizar o assembly do provedor de tipo em si. Esse assembly é usado posteriormente como o tipo de pai lógico dos tipos de apagados que são fornecidos.

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

Em seguida, crie uma função para fornecer cada um dos tipos Type1... Type100. Essa função é explicada em mais detalhes mais adiante neste tópico.

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

Finalmente, adicione um atributo de assembly que indica que você está criando uma DLL do provedor de tipo:

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a>Fornecendo um tipo e seus membros

O `makeOneProvidedType` função faz o trabalho real de fornecer um dos tipos.

```fsharp
let makeOneProvidedType (n:int) =
…
```

Esta etapa explica a implementação dessa função. Primeiro, crie o tipo fornecido (por exemplo, Type1, quando n = 1 ou Type57, quando n = 57).

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

Você deve observar os seguintes pontos:

- Isso proporcionou tipo é apagado.  Porque você indica que o tipo base é `obj`, instâncias serão exibidos como valores do tipo [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) no código compilado.

- Quando você especifica um tipo não aninhado, você deve especificar o assembly e namespace. Para tipos apagados, o assembly deve ser o assembly do provedor de tipo em si.

Em seguida, adicione a documentação XML para o tipo. Esta documentação está atrasada, ou seja, computados sob demanda se o compilador de host precisa dela.

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

Em seguida, você adicione uma propriedade estática fornecida para o tipo:

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

Obter esta propriedade será sempre avaliada como a cadeia de caracteres "Olá!". O `GetterCode` para a propriedade usa um F# aspas simples, que representa o código que o compilador de host gera para a obtenção da propriedade. Para obter mais informações sobre cotações, consulte [citações de código (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).

Adicione a documentação XML para a propriedade.

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

Agora, anexe a propriedade fornecida para o tipo fornecido. Você deve anexar o membro fornecido para apenas um tipo. Caso contrário, o membro nunca poderão ser acessado.

```fsharp
t.AddMember staticProp
```

Agora, crie um construtor fornecido que não usa nenhum parâmetro.

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

O `InvokeCode` para o construtor retorna um F# aspas simples, que representa o código que o compilador de host gera quando o construtor é chamado. Por exemplo, você pode usar o seguinte construtor:

```fsharp
new Type10()
```

Uma instância do tipo fornecido será criada com dados subjacentes "Os dados do objeto". O código entre aspas inclui uma conversão [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) porque esse tipo é a eliminação de Isso proporcionou tipo (conforme especificado quando você declarou que o tipo fornecido).

Adicionar a documentação XML para o construtor e adicione o construtor fornecido para o tipo fornecido:

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

Crie um segundo construtor fornecido que aceite um parâmetro:

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

O `InvokeCode` para o construtor novamente retorna um F# aspas simples, que representa o código que o compilador de host gerado para uma chamada ao método. Por exemplo, você pode usar o seguinte construtor:

```fsharp
new Type10("ten")
```

Uma instância do tipo fornecido é criada com os dados subjacentes "dez". Você talvez já notou que o `InvokeCode` função retorna uma cotação. A entrada para essa função é uma lista de expressões, um por um parâmetro de construtor. Nesse caso, uma expressão que representa o valor do parâmetro único está disponível em `args.[0]`. O código para chamar o construtor força o valor de retorno para o tipo apagado `obj`. Depois de adicionar o segundo construtor fornecido para o tipo, você pode criar uma propriedade de instância fornecida:

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

Obter esta propriedade retornará o comprimento da cadeia de caracteres, que é o objeto de representação. O `GetterCode` propriedade retorna um F# que especifica o código que o compilador de host gera para obter a propriedade de cotação. Como o `InvokeCode`, o `GetterCode` função retorna uma cotação. O compilador de host chama essa função com uma lista de argumentos. Nesse caso, os argumentos incluem apenas a única expressão que representa a instância na qual o getter está sendo chamado, que pode ser acessada usando `args.[0]`. A implementação de `GetterCode` une na cotação de resultado no tipo apagado `obj`, e uma conversão é usada para satisfazer o mecanismo do compilador para verificar os tipos que o objeto é uma cadeia de caracteres. A próxima parte do `makeOneProvidedType` fornece um método de instância com um parâmetro.

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

Por fim, crie um tipo aninhado que contém 100 propriedades aninhadas. A criação deste aninhadas de tipo e suas propriedades estiver atrasada, ou seja, computados sob demanda.

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

### <a name="details-about-erased-provided-types"></a>Detalhes sobre os tipos fornecidos apagados

O exemplo nesta seção só fornece *apagados tipos fornecidos*, que são particularmente úteis nas seguintes situações:

- Quando você estiver escrevendo um provedor para um espaço de informações que contém somente dados e métodos.

- Quando você estiver escrevendo um provedor de onde a semântica de tipo de tempo de execução precisa não é essencial para o uso prático do espaço de informações.

- Quando você estiver escrevendo um provedor para um espaço de informações é tão grande e interconectados que não é tecnicamente possível gerar tipos reais do .NET para o espaço de informações.

Neste exemplo, cada um fornecido tipo for apagado para digitar `obj`, e todos os usos do tipo serão exibido como tipo `obj` no código compilado. Na verdade, os objetos subjacentes nesses exemplos são cadeias de caracteres, mas o tipo será exibido como `System.Object` no .NET de código compilado. Como com todos os usos de eliminação de tipo, você pode usar a conversão boxing explícita, conversão unboxing e de conversão subverter apagados tipos. Nesse caso, uma exceção de conversão não é válida pode resultar quando o objeto é usado. Um provedor de tempo de execução pode definir seu próprio tipo de representação privada para se proteger contra representações falsos. Você não pode definir tipos apagados no F# em si. Somente os tipos fornecidos podem ser apagados. Você deve compreender as ramificações, ambos os práticos e apagado tipos apagados para seu provedor de tipo ou um provedor que fornece semântica, usando um tipos. Um tipo apagado não tem nenhum tipo .NET real. Portanto, não é possível fazer o reflexo preciso sobre o tipo e você pode subverter tipos apagados se você usar conversões de tempo de execução e outras técnicas que dependem de semântica de tipo de tempo de execução exato. O Subversion dos tipos apagados frequentemente resulta em exceções de conversão de tipo em tempo de execução.

### <a name="choosing-representations-for-erased-provided-types"></a>Escolher representações para apagados tipos fornecidos

Para alguns usos de tipos fornecidos apagados, nenhuma representação é necessária. Por exemplo, o apagados fornecido tipo pode conter somente propriedades estáticas e membros e nenhum construtor, e não há métodos ou propriedades retornaria uma instância do tipo. Se você pode acessar instâncias de um apagados fornecido do tipo, você deve considerar as seguintes perguntas:

**O que é a eliminação de um tipo fornecido?**

- A eliminação de um tipo fornecido é como o tipo é exibido no código compilado do .NET.

- A remoção de um tipo de classe apagados fornecida é sempre o primeiro não apagados tipo base da cadeia de herança do tipo.

- A remoção de um tipo de interface apagados fornecida é sempre `System.Object`.

**Quais são as representações de um tipo fornecido?**

- O conjunto de objetos possíveis para um apagados fornecido do tipo são chamados de suas representações. O exemplo neste documento, as representações de todos os fornecidos a apagados tipos `Type1..Type100` sempre são objetos de cadeia de caracteres.

Todas as representações de um tipo fornecido devem ser compatíveis com a eliminação de tipo fornecido. (Caso contrário, ambos o F# compilador fornecerão um erro para uso do provedor de tipos, ou será gerado um código .NET não verificável que não é válido. Um provedor de tipo não é válido se ele retorna o código que fornece uma representação que não é válida.)

Você pode escolher uma representação para objetos fornecidos usando qualquer uma das abordagens a seguir, que são muito comuns:

- Se você simplesmente fornece um wrapper fortemente tipado sobre um tipo .NET existente, geralmente faz sentido para seu tipo apagar a esse tipo, use instâncias desse tipo como representações, ou ambos. Essa abordagem é apropriada quando a maioria dos métodos existentes nesse tipo ainda faz sentido ao usar a versão fortemente tipada.

- Se você quiser criar uma API que difere significativamente, de qualquer API existente do .NET, faz sentido criar tipos de tempo de execução que serão a eliminação de tipo e representações para os tipos fornecidos.

O exemplo neste documento usa cadeias de caracteres como representações dos objetos fornecidos. Com frequência, pode ser apropriado para usar outros objetos para representações. Por exemplo, você pode usar um dicionário como um recipiente de propriedades:

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

Como alternativa, você pode definir um tipo em seu provedor de tipo que será usado em tempo de execução para formar a representação, juntamente com uma ou mais operações de tempo de execução:

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

Membros fornecidos, em seguida, podem construir instâncias desse tipo de objeto:

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

Nesse caso, você pode (opcionalmente) usar esse tipo como a eliminação de tipo ao especificar esse tipo como o `baseType` ao construir o `ProvidedTypeDefinition`:

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a>Principais lições

A seção anterior explicou como criar um provedor de tipo de apagamento simples que fornece uma variedade de tipos, propriedades e métodos. Esta seção também explicou o conceito de eliminação de tipo, incluindo algumas das vantagens e desvantagens do fornecimento de tipos apagados de um provedor de tipo e discutido representações de tipos apagados.

## <a name="a-type-provider-that-uses-static-parameters"></a>Um provedor de tipo que usa parâmetros estáticos

A capacidade de parametrizar os provedores de tipos por dados estáticos permite muitos cenários interessantes, até mesmo em casos em que o provedor não precisa acessar os dados locais ou remotos. Nesta seção, você aprenderá algumas técnicas básicas para reunir-se de que esse provedor.

### <a name="type-checked-regex-provider"></a>Tipo verificado provedor Regex

Imagine que você deseja implementar um provedor de tipo para expressões regulares que encapsula o .NET <xref:System.Text.RegularExpressions.Regex> bibliotecas em uma interface que fornece as seguintes garantias de tempo de compilação:

- Verificando se uma expressão regular é válida.

- Fornecendo propriedades nomeadas em correspondências com base em quaisquer nomes de grupo na expressão regular.

Esta seção mostra como usar provedores de tipos para criar um `RegexTyped` de tipo que o padrão de expressão regular parametriza para fornecer esses benefícios. O compilador relatará um erro se o padrão fornecido não é válido e o provedor de tipos pode extrair os grupos do padrão para que você pode acessá-los por meio de propriedades em correspondências nomeadas. Quando você cria um provedor de tipos, você deve considerar deve ser a aparência de sua API exposta aos usuários finais e como esse design se traduzirá em código .NET. O exemplo a seguir mostra como usar uma API desse tipo para obter os componentes do código de área:

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

O exemplo a seguir mostra como o provedor de tipo traduz essas chamadas:

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

Observe os seguintes pontos:

- O tipo padrão de Regex representa com parâmetros `RegexTyped` tipo.

- O `RegexTyped` construtor resulta em uma chamada para o construtor de Regex, passando o argumento de tipo estático para o padrão.

- Os resultados do `Match` método são representados pelo padrão <xref:System.Text.RegularExpressions.Match> tipo.

- Cada grupo nomeado resulta em uma propriedade fornecida e acessar a propriedade resulta em um uso de um indexador em uma correspondência `Groups` coleção.

O código a seguir é o núcleo da lógica para implementar esse provedor, e este exemplo omite a adição de todos os membros para o tipo fornecido. Para obter informações sobre cada membro adicionado, consulte a seção apropriada mais adiante neste tópico. Para o código completo, baixe o exemplo do [ F# pacote de exemplo 3.0](https://fsharp3sample.codeplex.com) no site da Codeplex.

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

- O provedor de tipo leva dois parâmetros estáticos: o `pattern`, que é obrigatório e o `options`, quais são opcionais (porque um valor padrão é fornecido).

- Depois que os argumentos estáticos são fornecidos, você cria uma instância da expressão regular. Esta instância lançará uma exceção se a expressão regular está malformada e esse erro será relatado para os usuários.

- Dentro de `DefineStaticParameters` retorno de chamada, você define o tipo que será retornado depois que os argumentos são fornecidos.

- Esse código define `HideObjectMethods` como true para que a experiência de IntelliSense permanecerá simplificada. Esse atributo faz com que o `Equals`, `GetHashCode`, `Finalize`, e `GetType` membros a serem suprimidos nas listas de IntelliSense para um objeto fornecido.

- Você usa `obj` como o tipo base do método, mas você usará um `Regex` objeto como a representação de tempo de execução desse tipo, como a exemplo a seguir mostra.

- A chamada para o `Regex` construtor lança um <xref:System.ArgumentException> quando uma expressão regular não é válida. O compilador captura essa exceção e relata uma mensagem de erro para o usuário em tempo de compilação ou no editor do Visual Studio. Essa exceção permite que as expressões regulares a ser validado sem executar um aplicativo.

O tipo definido acima ainda não está útil porque ele não contém todos os métodos significativos ou propriedades. Primeiro, adicione um estático `IsMatch` método:

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

O código anterior define um método `IsMatch`, que usa uma cadeia de caracteres como entrada e retorna um `bool`. A única parte difícil é o uso do `args` argumento dentro de `InvokeCode` definição. Neste exemplo, `args` é uma lista de cotações que representa os argumentos para esse método. Se o método é um método de instância, o primeiro argumento representa o `this` argumento. No entanto, para um método estático, os argumentos são apenas os argumentos explícitos ao método. Observe que o tipo do valor entre aspas deve corresponder ao tipo de retorno especificado (nesse caso, `bool`). Observe também que esse código usa o `AddXmlDoc` método para certificar-se de que o método fornecido também possui documentação útil que você pode fornecer por meio do IntelliSense.

Em seguida, adicione um método de correspondência de instância. No entanto, esse método deve retornar um valor de fornecido `Match` tipo de forma que os grupos podem ser acessados de uma maneira fortemente tipada. Portanto, você deve primeiramente declarar o `Match` tipo. Porque esse tipo depende do padrão que foi fornecido como um argumento estático, esse tipo deve ser aninhado dentro da definição de tipo parametrizado:

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

Você, em seguida, adicione uma propriedade para o tipo de correspondência para cada grupo. Em tempo de execução, uma correspondência é representada como uma <xref:System.Text.RegularExpressions.Match> de valor, portanto, as aspas que define a propriedade devem usar o <xref:System.Text.RegularExpressions.Match.Groups> indexado de propriedade para obter o grupo relevante.

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

Novamente, observe que você está adicionando documentação XML a propriedade fornecida. Observe também que uma propriedade pode ser lidos se um `GetterCode` função é fornecida, e a propriedade pode ser escrita se um `SetterCode` função for fornecida, portanto, a propriedade resultante é somente leitura.

Agora você pode criar um método de instância que retorna um valor deste `Match` tipo:

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

Porque você está criando um método de instância `args.[0]` representa o `RegexTyped` instância na qual o método está sendo chamado, e `args.[1]` é o argumento de entrada.

Por fim, fornece um construtor para que a instância do tipo fornecido pode ser criada.

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

O construtor simplesmente apaga à criação de uma instância de Regex do .NET standard, que é convertida novamente para um objeto porque `obj` é a eliminação de tipo fornecido. Com essa alteração, o exemplo de uso de API que especificou anteriormente no tópico funciona conforme o esperado. O código a seguir é concluída e final:

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

### <a name="key-lessons"></a>Principais lições

Esta seção explicou como criar um provedor de tipos que opera em seus parâmetros estáticos. O provedor verifica o parâmetro static e fornece operações com base em seu valor.

## <a name="a-type-provider-that-is-backed-by-local-data"></a>Um provedor de tipo que é apoiado por dados locais

Com frequência, convém provedores de tipos para apresentar as APIs com base em não apenas parâmetros estáticos, mas também informações de sistemas locais ou remotos. Esta seção discute os provedores de tipos se baseiam em dados locais, como arquivos de dados local.

### <a name="simple-csv-file-provider"></a>Provedor de arquivo CSV simples

Como um exemplo simples, considere um provedor de tipos para acessar dados científicos; dados no formato de valor separados por vírgulas (CSV). Esta seção pressupõe que os arquivos CSV contêm uma linha de cabeçalho seguida pelos dados de ponto flutuante, como mostra a tabela a seguir:

|Distância (medidor)|Tempo (segundos)|
|----------------|-------------|
|50.0|3.7|
|100.0|5.2|
|150.0|6.4|

Esta seção mostra como fornecer um tipo que você pode usar para obter linhas com um `Distance` propriedade do tipo `float<meter>` e uma `Time` propriedade do tipo `float<second>`. Para simplificar, as seguintes suposições são feitas:

- Nomes de cabeçalho são menos de unidade ou têm o formato "Nome (unidade)" e não contêm vírgulas.

- As unidades são todas as unidades de sistema internacional (SI) como o [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames módulo (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) módulo define.

- As unidades são tudo simples (por exemplo, medidor) em vez de compostos (por exemplo, medidor/segundo).

- Todas as colunas contêm dados de ponto flutuante.

Um provedor mais completo seria solte essas restrições.

Novamente, a primeira etapa é considerar como a API deve ser. Dado um `info.csv` arquivo com o conteúdo da tabela anterior (em formato separado por vírgula), os usuários do provedor devem ser capazes de gravar o código semelhante ao exemplo a seguir:

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

Nesse caso, o compilador deve converter essas chamadas em algo semelhante ao seguinte exemplo:

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

A tradução ideal exigirá o provedor de tipo para definir um real `CsvFile` tipo no assembly do provedor de tipo. Provedores de tipos geralmente dependem de alguns tipos auxiliares e métodos para encapsular a lógica importante. Como as medidas são apagadas em tempo de execução, você pode usar um `float[]` como o tipo apagado para uma linha. O compilador tratará colunas diferentes têm tipos diferentes de medida. Por exemplo, a primeira coluna em nosso exemplo tem o tipo `float<meter>`, e o segundo tem `float<second>`. No entanto, a representação apagada pode permanecer bastante simple.

O código a seguir mostra o núcleo da implementação.

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

Observe os seguintes pontos sobre a implementação:

- Construtores sobrecarregados permitem que o arquivo original ou um que tenha um esquema idêntico a serem lidos. Esse padrão é comum quando você escrever um provedor de tipo para fontes de dados local ou remoto e esse padrão permite que um arquivo local a ser usado como modelo para dados remotos.

- Você pode usar o [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) valor que é passado para o construtor de tipo de provedor para resolver nomes de arquivo relativos.

- Você pode usar o `AddDefinitionLocation` método para definir o local das propriedades fornecidas. Portanto, se você usar `Go To Definition` em uma propriedade fornecida, o arquivo CSV será aberto no Visual Studio.

- Você pode usar o `ProvidedMeasureBuilder` digite para pesquisar as unidades de SI e para gerar o relevantes `float<_>` tipos.

### <a name="key-lessons"></a>Principais lições

Esta seção explicou como criar um provedor de tipo para uma fonte de dados local com um esquema simples que está contido na fonte de dados em si.

## <a name="going-further"></a>Indo mais além

As seções a seguir incluem sugestões para estudar em mais detalhes.

### <a name="a-look-at-the-compiled-code-for-erased-types"></a>Examinar o código compilado para tipos apagados

Para dar uma ideia de como o uso do provedor de tipo corresponde ao código que é emitido, examine a seguinte função usando o `HelloWorldTypeProvider` que é usado no início deste tópico.

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

Aqui está uma imagem do código descompilado usando ildasm.exe resultante:

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

Como mostra o exemplo, todos os menções do tipo `Type1` e o `InstanceProperty` propriedade foram apagados, deixando apenas as operações nos tipos de tempo de execução envolvidos.

### <a name="design-and-naming-conventions-for-type-providers"></a>Design e convenções de nomenclatura para provedores de tipos

Observe as convenções a seguir ao criar provedores de tipos.

**Provedores para protocolos de conectividade** em geral, nomes de provedor a maioria das DLLs para protocolos de conectividade de dados e o serviço, como conexões do OData ou SQL, devem terminar com `TypeProvider` ou `TypeProviders`. Por exemplo, use um nome DLL que se parece com a cadeia de caracteres a seguir:

```
  Fabrikam.Management.BasicTypeProviders.dll
```

Certifique-se de que seus tipos fornecidos são membros do namespace correspondente e indicam o protocolo de conectividade que você tiver implementado:

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

**Provedores de utilitário para codificação geral**.  Para um provedor de tipo de utilitário, como para expressões regulares, o provedor de tipo pode ser parte de uma biblioteca de base, como mostra o exemplo a seguir:

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

Nesse caso, o tipo fornecido apareceria em um ponto apropriado de acordo com as convenções normais de design do .NET:

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

**Fontes de dados singleton**. Alguns provedores de tipos se conectar a uma fonte de dados dedicado e fornecem apenas os dados. Nesse caso, você deve descartar o `TypeProvider` sufixo e use normais convenções de nomenclatura do .NET:

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

Para obter mais informações, consulte o `GetConnection` projetar convenção que é descrita posteriormente neste tópico.

### <a name="design-patterns-for-type-providers"></a>Padrões de design para provedores de tipos

As seções a seguir descrevem padrões de design, que você pode usar ao criar provedores de tipos.

#### <a name="the-getconnection-design-pattern"></a>O padrão de Design GetConnection

A maioria dos provedores de tipo deve ser escrito para usar o `GetConnection` padrão que é usado pelos provedores de tipo em FSharp.Data.TypeProviders.dll, como mostra o exemplo a seguir:

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>Provedores de tipos com suporte pelos serviços e dados remotos

Antes de criar um provedor de tipo que é apoiado por serviços e dados remotos, você deve considerar uma variedade de problemas inerentes à programação conectada. Esses problemas incluem as seguintes considerações:

- mapeamento de esquema

- alocação e a invalidação na presença de alteração de esquema

- cache de esquemas

- implementações assíncronas de operações de acesso de dados

- suporte a consultas, incluindo consultas LINQ

- autenticação e credenciais

Este tópico não explorar ainda mais esses problemas.

### <a name="additional-authoring-techniques"></a>Técnicas de criação adicionais

Quando você escrever seus próprios provedores de tipos, você talvez queira usar as seguintes técnicas adicionais.

### <a name="creating-types-and-members-on-demand"></a>Criação de tipos e membros sob demanda

A API ProvidedType adiou a versões do AddMember.

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

Essas versões são usadas para criar espaços de demanda de tipos.

### <a name="providing-array-types-and-generic-type-instantiations"></a>Fornecendo instanciações de tipo genérico e tipos de matriz

Tornar membros fornecidos (cujas assinaturas incluem tipos de matriz e tipos byref instanciações de tipos genéricos) usando o vetor perpendicular `MakeArrayType`, `MakePointerType`, e `MakeGenericType` em qualquer instância do <xref:System.Type>, incluindo `ProvidedTypeDefinitions`.

> [!NOTE]
> Em alguns casos você talvez precise usar o auxiliar em `ProvidedTypeBuilder.MakeGenericType`.  Consulte a [documentação do SDK do provedor de tipo](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) para obter mais detalhes.

### <a name="providing-unit-of-measure-annotations"></a>Fornecendo a unidade de medida anotações

A API ProvidedTypes fornece auxiliares para fornecer anotações de medida. Por exemplo, para fornecer o tipo `float<kg>`, use o seguinte código:

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  Para fornecer o tipo `Nullable<decimal<kg/m^2>>`, use o seguinte código:

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a>Acessando recursos do projeto Local ou Local de Script

Cada instância de um provedor de tipo pode ser fornecida um `TypeProviderConfig` valor durante a construção. Esse valor contém a pasta"Resolução" para o provedor (ou seja, a pasta de projeto para a compilação ou o diretório que contém um script), a lista de assemblies referenciados e outras informações.

### <a name="invalidation"></a>Invalidação

Provedores podem gerar sinais de invalidação para notificar o F# serviço de linguagem que as suposições de esquema podem ter sido alterado. Quando ocorre a invalidação, um typecheck é refeito se o provedor está sendo hospedado no Visual Studio. Esse sinal será ignorado quando o provedor estiver hospedado em F# interativo ou o F# (fsc.exe) do compilador.

### <a name="caching-schema-information"></a>Armazenar em cache informações de esquema

Provedores devem armazenar em cache geralmente acesso às informações de esquema. Os dados armazenados em cache devem ser armazenados usando um nome de arquivo que é fornecido como um parâmetro estático ou como dados de usuário. Um exemplo de cache de esquema é o `LocalSchemaFile` os provedores de tipo no parâmetro o `FSharp.Data.TypeProviders` assembly. Na implementação desses provedores, esse parâmetro estático instrui o provedor de tipo para usar as informações de esquema no arquivo local especificado em vez de acessar a fonte de dados pela rede. Para usar as informações de esquema em cache, você também deve definir o parâmetro static `ForceUpdate` para `false`. Você pode usar uma técnica semelhante para habilitar o acesso de dados online e offline.

### <a name="backing-assembly"></a>Assembly de suporte

Quando você compila um `.dll` ou `.exe` arquivo, o arquivo. dll de suporte para tipos gerados está vinculada estaticamente o assembly resultante. Esse link é criado, copiando as definições de tipo de linguagem intermediária (IL) e todos os recursos gerenciados do conjunto de backup no assembly final. Quando você usa F# interativo, o arquivo. dll de backup não sejam copiado e em vez disso, é carregado diretamente no F# processo interativo.

### <a name="exceptions-and-diagnostics-from-type-providers"></a>Exceções e diagnóstico de provedores de tipos

Todos os usos de todos os membros de tipos fornecidos podem lançar exceções. Em todos os casos, se um provedor de tipos gera uma exceção, o compilador de host atributos o erro para um provedor de tipo específico.

- Tipo de provedor exceções nunca deve resultar em erros internos do compilador.

- Provedores de tipos não podem relatar avisos.

- Quando um provedor de tipo é hospedado no F# compilador, um F# ambiente de desenvolvimento, ou F# interativo, todas as exceções do provedor são capturadas. A propriedade de mensagem sempre é o texto de erro e nenhum rastreamento de pilha é exibida. Se você pretende lançar uma exceção, você pode lançar os exemplos a seguir: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.

#### <a name="providing-generated-types"></a>Fornecimento de tipos gerados

Até agora, este documento explicou como fornecer tipos apagados. Você também pode usar o mecanismo de provedor de tipo no F# para fornecer tipos gerados, que são adicionados como reais definições de tipo de .NET no programa dos usuários. Você deve se referir a gerado tipos fornecidos por meio de uma definição de tipo.

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

O código do auxiliar de 0,2 ProvidedTypes que faz parte do F# versão 3.0 tem somente suporte limitado para fornecer tipos gerados. As instruções a seguir devem ser verdadeiras para uma definição de tipo gerado:

- `isErased` deve ser definido como `false`.

- O tipo gerado deve ser adicionado a um recentemente construído `ProvidedAssembly()`, que representa um contêiner para fragmentos de código gerado.

- O provedor deve ter um assembly que tem um arquivo. dll do .NET de backup real com um arquivo. dll correspondente no disco.

## <a name="rules-and-limitations"></a>Regras e limitações

Quando você escrever provedores de tipos, tenha as seguintes regras e limitações em mente.

### <a name="provided-types-must-be-reachable"></a>Tipos fornecidos devem ser acessíveis

Todos fornecidos tipos devem ser acessíveis a partir de tipos não aninhadas. Os tipos aninhados não são fornecidos na chamada para o `TypeProviderForNamespaces` construtor ou uma chamada para `AddNamespace`. Por exemplo, se o provedor fornece um tipo `StaticClass.P : T`, você deve garantir que T é um tipo não aninhado ou aninhados em um.

Por exemplo, alguns provedores têm uma classe estática, como `DataTypes` que contêm esses `T1, T2, T3, ...` tipos. Caso contrário, o erro afirma que uma referência ao tipo T em um assembly foi encontrada, mas não foi possível encontrar o tipo nesse assembly. Se esse erro aparecer, verifique se todos os seus subtipos podem ser acessados entre os tipos de provedor. Observação: Eles `T1, T2, T3...` tipos são chamados da *em interrupções* tipos. Lembre-se de colocá-los em um namespace acessível ou um tipo de pai.

### <a name="limitations-of-the-type-provider-mechanism"></a>Limitações do mecanismo de provedor de tipo

O mecanismo de provedor de tipo no F# tem as seguintes limitações:

- A infraestrutura subjacente para provedores de tipos em F# não dá suporte a fornecido genérico tipos ou fornecidos métodos genéricos.

- O mecanismo não dá suporte a tipos aninhados com parâmetros estáticos.

## <a name="development-tips"></a>Dicas de desenvolvimento

Você pode encontrar as seguintes dicas úteis durante o processo de desenvolvimento:

### <a name="run-two-instances-of-visual-studio"></a>Executar duas instâncias do Visual Studio

Você pode desenvolver o provedor de tipo em uma instância e testar o provedor nos outros porque o IDE de teste tem um bloqueio no arquivo. dll que impede que o provedor de tipo que está sendo recriado. Portanto, você deve fechar a segunda instância do Visual Studio enquanto o provedor é criado na primeira instância e, em seguida, você deverá reabri-la a segunda instância depois que o provedor é compilado.

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a>Provedores de tipos de depuração por meio de invocações de fsc.exe

Você pode invocar provedores de tipos, usando as seguintes ferramentas:

- FSC.exe (o F# compilador de linha de comando)

- FSI.exe (o F# compilador interativa)

- devenv.exe (Visual Studio)

Muitas vezes você pode depurar provedores de tipos com mais facilidade usando fsc.exe em um arquivo de script de teste (por exemplo, script.fsx). Você pode iniciar um depurador em um prompt de comando.

```
  devenv /debugexe fsc.exe script.fsx
```

  Você pode usar o log de impressão para stdout.

## <a name="see-also"></a>Consulte também

- [Provedores de Tipos](index.md)
- [O SDK do provedor de tipo](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
