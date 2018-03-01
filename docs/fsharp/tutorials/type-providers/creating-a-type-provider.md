---
title: 'Tutorial: Criando um provedor de tipos (F#)'
description: "Saiba como criar seus próprios provedores de tipos F # em F # 3.0 examinando vários provedores de tipo simples para ilustrar os conceitos básicos."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 82bec076-19d4-470c-979f-6c3a14b7c70a
ms.openlocfilehash: c09f8abe4dd46453cb6cc5ed7dbb6f60dbf0ad98
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="tutorial-creating-a-type-provider"></a>Tutorial: Criando um provedor de tipos

> [!NOTE]
Este guia foi escrito para F # 3.0 e será atualizado.

O mecanismo de provedor do tipo F # 3.0 é uma parte significativa de seu suporte para programação avançada de informações. Este tutorial explica como criar seus próprios provedores de tipo, você acompanhará o desenvolvimento de vários provedores de tipo simples para ilustrar os conceitos básicos. Para obter mais informações sobre o mecanismo de provedor de tipo em F #, consulte [provedores de tipos](index.md).

F # 3.0 contém vários provedores de tipo interno para serviços de dados usados na Internet e enterprise. Esses provedores de tipo concedem acesso simple e regular para bancos de dados relacionais do SQL e serviços OData e WSDL baseados em rede. Esses provedores também suportam o uso de consultas LINQ F # em relação a essas fontes de dados.

Quando necessário, você pode criar provedores de tipo personalizado, ou você pode fazer referência a provedores de tipos que outros criaram. Por exemplo, sua organização pode ter um serviço de dados que fornece um número grande e crescente de conjuntos de dados nomeados, cada qual com seu próprio esquema de dados estáveis. Você pode criar um provedor de tipos que lê os esquemas e apresenta os conjuntos de dados atuais para o programador de maneira fortemente tipada.


## <a name="before-you-start"></a>Antes de começar
O mecanismo de provedor de tipo é projetado principalmente para injeção de dados estáveis e espaços de informações de serviço para o F # experiência em programação.

Esse mecanismo não foi projetado para injeção de espaços de informações cuja esquema é alterado durante a execução do programa de maneiras que são relevantes para a lógica do programa. Além disso, o mecanismo não foi projetado para intraidioma metaprogramação, mesmo que esse domínio contém alguns usos válidos. Você deve usar esse mecanismo somente quando necessário e onde o desenvolvimento de um provedor de tipo produz o valor muito alto.

Evite escrever um provedor de tipo em que um esquema não está disponível. Da mesma forma, evite escrever um provedor de tipo, onde um comum (ou até mesmo uma existente) biblioteca .NET seria suficiente.

Antes de começar, você pode responder às seguintes perguntas:


- Você tem um esquema para a fonte de informações? Nesse caso, o que é o mapeamento para o F # e sistema de tipo .NET?

- Você pode usar uma API (dinamicamente tipada) existente como ponto de partida para sua implementação?

- Você e sua organização terá suficiente usa do provedor de tipo para fazer a gravação vale a pena? Uma biblioteca .NET normal atendem às suas necessidades?

- Quanto alterará seu esquema?

- Ele será alterado durante a codificação?

- Ele será alterado entre as sessões de codificação?

- Ele será alterado durante a execução do programa?

Provedores de tipos são mais adequados para situações em que o esquema é estável no tempo de execução e durante o tempo de vida do código compilado.


## <a name="a-simple-type-provider"></a>Um provedor de tipo simples
Este exemplo é Samples.HelloWorldTypeProvider no `SampleProviders\Providers` diretório do [pacote de exemplo do F # 3.0](https://fsharp3sample.codeplex.com) no site da Codeplex. O provedor torna disponível um "espaço de tipo" que contém 100 tipos apagados, como mostra o seguinte código usando a sintaxe de assinatura do F # e omitir os detalhes para todos, exceto `Type1`. Para obter mais informações sobre tipos apagados, consulte [detalhes sobre apagados fornecido tipos](#details-about-erased-provided-types) mais adiante neste tópico.

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

    /// This is an instance property.
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

Observe que o conjunto de tipos e membros fornecidos estaticamente é conhecido. Este exemplo não aproveitar a capacidade de provedores para fornecer tipos que dependem de um esquema. A implementação do provedor de tipo é descrita no código a seguir, e os detalhes são abordados nas seções posteriores deste tópico.


>[!WARNING] 
Pode haver algumas pequenas diferenças de nomenclatura entre esse código e as amostras online.

```fsharp
namespace Samples.FSharp.HelloWorldTypeProvider

open System
open System.Reflection
open Samples.FSharp.ProvidedTypes
open Microsoft.FSharp.Core.CompilerServices
open Microsoft.FSharp.Quotations

// This type defines the type provider. When compiled to a DLL, it can be added
// as a reference to an F# command-line compilation, script, or project.
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this = 

  // Inheriting from this type provides implementations of ITypeProvider 
  // in terms of the provided types below.
  inherit TypeProviderForNamespaces()

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

Para usar esse provedor, abra uma instância separada do Visual Studio 2012, criar um script de F # e, em seguida, adicione uma referência para o provedor do seu script usando #r como o código a seguir mostra:

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

Procure os tipos sob o `Samples.HelloWorldTypeProvider` namespace que o provedor de tipos gerado.

Antes de você recompile o provedor, certifique-se de que você fechou todas as instâncias do Visual Studio e F # interativo que estiver usando a DLL do provedor. Caso contrário, ocorrerá um erro de compilação porque a DLL de saída será bloqueada.

Para depurar este provedor usando as instruções print, faça um script que expõe um problema com o provedor e, em seguida, use o seguinte código:

```fsharp
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Para depurar este provedor usando o Visual Studio, abra um prompt de comando do Visual Studio com credenciais administrativas e execute o seguinte comando:

```fsharp
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Como alternativa, abra o Visual Studio, abra o menu Depurar, escolha `Debug/Attach to process…`e anexar para outro `devenv` processo em que você está editando seu script. Usando esse método, você pode direcionar mais facilmente a lógica específica no provedor de tipo digitando interativamente expressões na segunda instância (com e outros recursos do IntelliSense completo).

Você pode desabilitar apenas meu código depuração para identificar melhor erros no código gerado. Para obter informações sobre como habilitar ou desabilitar esse recurso, consulte [navegar pelo código com o depurador](/visualstudio/debugger/navigating-through-code-with-the-debugger). Além disso, você também pode definir exceções de primeira chance capturando abrindo o `Debug` menu e, em seguida, escolhendo `Exceptions` ou escolhendo as teclas Ctrl + Alt + E para abrir o `Exceptions` caixa de diálogo. Na caixa de diálogo, em `Common Language Runtime Exceptions`, selecione o `Thrown` caixa de seleção.


### <a name="implementation-of-the-type-provider"></a>Implementação do provedor de tipo
Esta seção orienta você pelas seções principais da implementação do provedor de tipo. Primeiro, você define o tipo para o provedor de tipo personalizado próprio:

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

Esse tipo deve ser público e você deve marcar com o [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) para que o compilador reconhecerá o provedor de tipo quando um projeto separado de F # referencia o assembly que contém o tipo de atributo. O *config* parâmetro é opcional e, se presente, contém informações de configuração contextual para a instância do provedor de tipo que cria o compilador F #.

Em seguida, você implementa o [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface. Nesse caso, você usa o `TypeProviderForNamespaces` tipo o `ProvidedTypes` API como um tipo base. Esse tipo de auxiliar pode fornecer um conjunto finito de ansiosamente fornecida namespaces, diretamente, cada uma delas contém um número finito de fixo, ansiosamente tipos. Nesse contexto, o provedor *ansiosamente* gera tipos, mesmo se eles não são necessários ou usados.

```fsharp
inherit TypeProviderForNamespaces()
```

Em seguida, definir valores particulares locais que especifique o namespace para os tipos fornecidos e localizar o assembly do provedor de tipo em si. Este assembly é usado posteriormente como o tipo de pai lógico dos tipos apagados que são fornecidos.

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

Em seguida, crie uma função para fornecer a cada um dos tipos Type1... Type100. Essa função é explicada em mais detalhes posteriormente neste tópico.

```fsharp
let makeOneProvidedType (n:int) = …
```

Em seguida, gere os 100 tipos fornecidos:

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

Em seguida, adicione os tipos de um namespace fornecido:

```fsharp
do this.AddNamespace(namespaceName, types)
```

Finalmente, adicione um atributo de assembly que indica que você está criando uma DLL de provedor do tipo:

```fsharp
[<assembly:TypeProviderAssembly>] 
do()
```

### <a name="providing-one-type-and-its-members"></a>Fornecendo um tipo e seus membros
O `makeOneProvidedType` função faz o trabalho real do fornecimento de um dos tipos.

```fsharp
let makeOneProvidedType (n:int) = 
…
```

Esta etapa explica a implementação dessa função. Primeiro, crie o tipo fornecido (por exemplo, Type1, quando n = 1 ou Type57, quando n = 57).

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code, 
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly,namespaceName,
"Type" + string n,
baseType = Some typeof<obj>)
```

Você deve observar os seguintes pontos:


- Isso fornecido o tipo é apagado.  Porque você indicar que o tipo base é `obj`, instâncias serão exibidos como valores do tipo [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) no código compilado.
<br />

- Quando você especifica um tipo aninhado não, você deve especificar o assembly e o namespace. Para tipos apagados, o assembly deve ser o assembly do provedor de tipo em si.
<br />

Em seguida, adicione a documentação XML para o tipo. Esta documentação está atrasada, ou seja, computados sob demanda, se o compilador host necessitar.

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

Em seguida, você adiciona uma propriedade de estática fornecida para o tipo:

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty", 
propertyType = typeof<string>, 
IsStatic=true,
GetterCode= (fun args -> <@@ "Hello!" @@>))
```

Obter esta propriedade será sempre avaliada como a cadeia de caracteres "Olá!". O `GetterCode` para a propriedade usa uma cotação F #, que representa o código que gera o compilador de host para a obtenção da propriedade. Para obter mais informações sobre cotações, consulte [citações de código (F #)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).

Adicione documentação XML para a propriedade.

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

Agora, anexe a propriedade fornecida para o tipo fornecido. Você deve anexar um membro fornecido para apenas um tipo. Caso contrário, o membro nunca poderá ser acessado.

```fsharp
t.AddMember staticProp
```

Agora, crie um construtor fornecido sem parâmetros.

```fsharp
let ctor = ProvidedConstructor(parameters = [ ], 
InvokeCode= (fun args -> <@@ "The object data" :> obj @@>))
```

O `InvokeCode` para o construtor retorna uma cotação F #, que representa o código que o compilador host gera quando o construtor é chamado. Por exemplo, você pode usar o seguinte construtor:

```fsharp
new Type10()
```

Uma instância do tipo fornecido será criada com os dados subjacentes "Os dados do objeto". O código entre aspas inclui uma conversão [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) porque esse tipo é a eliminação de tipo isso fornecido (conforme especificado quando você declarou o tipo fornecido).

Adicionar a documentação XML para o construtor e, em seguida, adicione o construtor fornecido para o tipo fornecido:

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

Crie um segundo construtor fornecido que recebe um parâmetro:

```fsharp
let ctor2 = 
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ], 
InvokeCode= (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

O `InvokeCode` para o construtor novamente retorna uma cotação F #, que representa o código que o compilador host gerado para uma chamada ao método. Por exemplo, você pode usar o seguinte construtor:

```fsharp
new Type10("ten")
```

Uma instância do tipo fornecido é criada com os dados subjacentes "10". Você já deve ter notado que o `InvokeCode` função retorna uma citação. A entrada para esta função é uma lista de expressões, um por um parâmetro de construtor. Nesse caso, uma expressão que representa o valor do parâmetro único está disponível em `args.[0]`. O código para chamar o construtor converte o valor de retorno para o tipo apagado `obj`. Depois de adicionar o segundo construtor fornecido para o tipo, você pode criar uma propriedade de instância fornecida:

```fsharp
let instanceProp = 
ProvidedProperty(propertyName = "InstanceProperty", 
propertyType = typeof<int>, 
GetterCode= (fun args -> 
<@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

Obter esta propriedade retornará o comprimento da cadeia de caracteres, que é o objeto de representação. O `GetterCode` propriedade retorna uma cotação de F # que especifica o código que gera o compilador de host para obter a propriedade. Como `InvokeCode`, o `GetterCode` função retorna uma citação. O compilador de host chama essa função com uma lista de argumentos. Nesse caso, os argumentos incluem a expressão único que representa a instância na qual está sendo chamado getter, que pode ser acessado usando `args.[0]`. A implementação de `GetterCode` une em aspas o resultado no tipo apagado `obj`, e uma conversão é usada para satisfazer o mecanismo do compilador para verificar os tipos de objeto é uma cadeia de caracteres. A próxima parte do `makeOneProvidedType` fornece um método de instância com um parâmetro.

```fsharp
let instanceMeth = 
ProvidedMethod(methodName = "InstanceMethod", 
parameters = [ProvidedParameter("x",typeof<int>)], 
returnType = typeof<char>, 
InvokeCode = (fun args -> 
<@@ ((%%(args.[0]) : obj) :?> string).Chars(%%(args.[1]) : int) @@>))

instanceMeth.AddXmlDocDelayed(fun () -> "This is an instance method")
// Add the instance method to the type.
t.AddMember instanceMeth
```

Finalmente, crie um tipo aninhado que contém as propriedades aninhadas 100. A criação deste aninhados tipo e suas propriedades estiver atrasada, ou seja, computados sob demanda.

```fsharp
t.AddMembersDelayed(fun () -> 
let nestedType = ProvidedTypeDefinition("NestedType",
Some typeof<obj>

)

nestedType.AddMembersDelayed (fun () -> 
let staticPropsInNestedType = 
[ for i in 1 .. 100 do
let valueOfTheProperty = "I am string "  + string i

let p = ProvidedProperty(propertyName = "StaticProperty" + string i, 
propertyType = typeof<string>, 
IsStatic=true,
GetterCode= (fun args -> <@@ valueOfTheProperty @@>))

p.AddXmlDocDelayed(fun () -> 
sprintf "This is StaticProperty%d on NestedType" i)

yield p ]
staticPropsInNestedType)

[nestedType])

// The result of makeOneProvidedType is the type.
t
```

### <a name="details-about-erased-provided-types"></a>Detalhes sobre tipos fornecidos apagados
O exemplo nesta seção fornece apenas *apagados tipos fornecidos*, que são particularmente úteis nas seguintes situações:


- Quando você estiver escrevendo um provedor para um espaço de informações que contém somente os dados e métodos.
<br />

- Quando você estiver escrevendo um provedor onde semântica precisa de tipo de tempo de execução não é essencial para o uso prático do espaço de informações.
<br />

- Quando você estiver escrevendo um provedor para um espaço de informações é tão grande e interconectadas que não seja tecnicamente possível gerar tipos .NET reais para o espaço de informações.
<br />

Neste exemplo, cada fornecida tipo será apagado para o tipo `obj`, e todos os usos do tipo aparecerão como tipo `obj` no código compilado. Na verdade, os objetos subjacentes nesses exemplos são cadeias de caracteres, mas o tipo será exibido como `System.Object` no .NET código compilado. Como com todos os usos de eliminação de tipo, você pode usar a conversão explícita, unboxing e conversão de subverter apagados tipos. Nesse caso, uma exceção de conversão não é válida pode resultar quando o objeto é usado. Um provedor de tempo de execução pode definir seu próprio tipo de representação privada para ajudar a proteger contra representações falsas. Você não pode definir tipos apagados em F # em si. Apenas tipos fornecidos poderão ser apagados. Você deve entender as implicações, ambas as práticas e apagados apagados tipos para o provedor de tipo ou um provedor que fornece semântica, usando um tipos. Um tipo apagado não tem nenhum tipo real do .NET. Portanto, não é possível fazer o reflexo preciso sobre o tipo e você pode subverter tipos apagados se você usar outras técnicas que dependem de semântica do tipo de tempo de execução exata e conversões de tempo de execução. Subversão dos tipos apagados frequentemente resulta em exceções de conversão de tipo em tempo de execução.


### <a name="choosing-representations-for-erased-provided-types"></a>Escolher representações para apagados fornecido tipos
Para alguns usos de tipos fornecidos apagados, nenhuma representação é necessária. Por exemplo, o apagados fornecido tipo pode conter apenas as propriedades estáticas e membros e nenhum construtor e sem propriedades ou métodos retorna uma instância do tipo. Se você pode acessar instâncias de um apagados tipo fornecido, você deve considerar as seguintes perguntas:


- O que é a eliminação de um tipo fornecido?
<br />
  - A eliminação de um tipo fornecido é como o tipo é exibido no código compilado do .NET.
<br />

  - A eliminação de um tipo de classe apagados fornecido é sempre o primeiro não apagados tipo base na cadeia de herança do tipo.
<br />

  - A eliminação de um tipo de interface apagados fornecida é sempre `System.Object`.
<br />

- Quais são as representações de um tipo fornecido?
<br />
  - O conjunto de objetos possíveis para um tipo fornecido apagados são chamados de suas representações. O exemplo neste documento, as representações de todos os fornecidos o apagados tipos `Type1..Type100` sempre são objetos de cadeia de caracteres.
<br />

Todas as representações de um tipo fornecido devem ser compatíveis com a eliminação do tipo fornecido. (Caso contrário, o compilador F # fornecerão um erro para uso do provedor de tipo, ou será gerado o código .NET não verificado que não é válido. Um provedor de tipo não é válido se ele retorna o código que fornece uma representação que não é válida.)

Você pode escolher uma representação para objetos fornecidos usando qualquer um dos procedimentos a seguir, que são muito comuns:


- Se você simplesmente fornece um wrapper com rigidez de tipos em um tipo .NET existente, geralmente faz sentido para o seu tipo apagar a esse tipo, use instâncias desse tipo como representações, ou ambos. Essa abordagem é apropriada quando a maioria dos métodos existentes no tipo ainda faz sentido ao usar a versão fortemente tipada.
<br />

- Se você quiser criar uma API que difere significativamente da API .NET existentes, faz sentido criar tipos de tempo de execução serão a eliminação de tipo e representações para os tipos fornecidos.
<br />

O exemplo neste documento usa cadeias de caracteres como representações de objetos fornecidos. Com frequência, é apropriado usar outros objetos para representações. Por exemplo, você pode usar um dicionário como um recipiente de propriedades:

```fsharp
ProvidedConstructor(parameters = [], 
InvokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

Como alternativa, você pode definir um tipo no seu provedor de tipo que será usado em tempo de execução para formar a representação, juntamente com uma ou mais operações de tempo de execução:

```fsharp
type DataObject() =
let data = Dictionary<string,obj>()
member x.RuntimeOperation() = data.Count
```

Membros fornecidos, em seguida, podem construir instâncias deste tipo de objeto:

```fsharp
ProvidedConstructor(parameters = [], 
InvokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

(Nesse caso, você pode opcionalmente) use esse tipo como a eliminação de tipo ao especificar esse tipo como o `baseType` ao construir o `ProvidedTypeDefinition`:

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

`Key Lessons`

A seção anterior explicou como criar um provedor de tipo apagar simples que fornece uma variedade de tipos, propriedades e métodos. Esta seção também explicado o conceito de eliminação de tipo, incluindo algumas das vantagens e desvantagens de fornecer tipos apagados de um provedor de tipo e discutido representações de tipos apagados.


## <a name="a-type-provider-that-uses-static-parameters"></a>Um provedor de tipo que usa parâmetros estáticos
A capacidade de parametrizar os provedores de tipos por dados estáticos permite muitos cenários interessantes, mesmo em casos em que o provedor não precisa acessar os dados locais ou remotos. Nesta seção, você aprenderá algumas técnicas básicas de reunir esse provedor.


### <a name="type-checked-regex-provider"></a>Tipo verificado provedor Regex
Imagine que você deseja implementar um provedor de tipos de expressões regulares que encapsula o .NET `System.Text.RegularExpressions.Regex` bibliotecas em uma interface que fornece as seguintes garantias do tempo de compilação:


- Verificando se uma expressão regular é válida.
<br />

- Fornecendo propriedades nomeadas em correspondências com base em quaisquer nomes de grupo na expressão regular.
<br />

Esta seção mostra como usar provedores de tipos para criar um `RegExProviderType` tipo que o padrão de expressão regular parametriza para fornecer esses benefícios. O compilador relatará um erro se o padrão fornecido não é válido, e o provedor de tipo pode extrair os grupos do padrão para que você pode acessá-los usando propriedades de correspondências nomeados. Quando você cria um provedor de tipos, você deve considerar deve ser a aparência de sua API exposto aos usuários finais e como esse design se traduzirá em código .NET. O exemplo a seguir mostra como usar esse uma API para obter os componentes do código de área:

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

O exemplo a seguir mostra como o provedor de tipos converte essas chamadas:

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

Observe os seguintes pontos:


- O tipo padrão de Regex representa o parametrizadas `RegexTyped` tipo.
<br />

- O `RegexTyped` construtor resulta em uma chamada para o construtor de Regex, passando o argumento de tipo estático para o padrão.
<br />

- Os resultados de `Match` método são representados pelo padrão `System.Text.RegularExpressions.Match` tipo.
<br />

- Cada grupo denominado resulta em uma propriedade fornecida e acessar a propriedade resulta em um uso de um indexador em uma correspondência `Groups` coleção.
<br />

O código a seguir é o núcleo da lógica de implementar esse provedor, e este exemplo omite a adição de todos os membros para o tipo fornecido. Para obter informações sobre cada membro adicionado, consulte a seção apropriada mais adiante neste tópico. Para o código completo, baixe o exemplo da [pacote de exemplo do F # 3.0](https://fsharp3sample.codeplex.com) no site da Codeplex.

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
let ty = ProvidedTypeDefinition(
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


- O provedor de tipo utiliza dois parâmetros estáticos: o `pattern`, que é obrigatório e o `options`, que são opcional (como um valor padrão é fornecido).
<br />

- Depois que os argumentos estáticos são fornecidos, você cria uma instância da expressão regular. Esta instância lançará uma exceção se a Regex está mal formado, e esse erro será relatado para os usuários.
<br />

- Dentro de `DefineStaticParameters` retorno de chamada, você define o tipo que será retornado após os argumentos fornecidos.
<br />

- Esse código define `HideObjectMethods` como verdadeiro para que a experiência IntelliSense permanecerá simplificada. Esse atributo faz com que o `Equals`, `GetHashCode`, `Finalize`, e `GetType` membros a serem suprimidos de listas do IntelliSense para um objeto fornecido.
<br />

- Você usa `obj` como o tipo base do método, mas você usará uma `Regex` objeto como a representação de tempo de execução desse tipo, como mostra o exemplo seguinte.
<br />

- A chamada para o `Regex` construtor lança um `System.ArgumentException` quando uma expressão regular não é válida. O compilador captura essa exceção e reportará uma mensagem de erro para o usuário em tempo de compilação ou no editor do Visual Studio. Essa exceção permite que as expressões regulares a ser validado sem executar um aplicativo.
<br />

O tipo definido acima ainda não está útil porque ele não contém quaisquer propriedades ou métodos significativos. Primeiro, adicione um estático `IsMatch` método:

```fsharp
let isMatch = ProvidedMethod(
methodName = "IsMatch", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = typeof<bool>, 
IsStaticMethod = true,
InvokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>) 

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string." 
ty.AddMember isMatch
```

O código anterior define um método `IsMatch`, que usa uma cadeia de caracteres como entrada e retorna um `bool`. A única parte complicada é o uso do `args` argumento dentro de `InvokeCode` definição. Neste exemplo, `args` é uma lista de aspas que representa os argumentos para esse método. Se o método é um método de instância, o primeiro argumento representa o `this` argumento. No entanto, para um método estático, os argumentos são todos apenas os argumentos explícitos para o método. Observe que o tipo do valor entre aspas deve corresponder ao tipo de retorno especificado (nesse caso, `bool`). Observe também que esse código usa o `AddXmlDoc` método para certificar-se de que o método fornecido também possui documentação útil que você pode fornecer por meio do IntelliSense.

Em seguida, adicione uma instância de método de correspondência. No entanto, esse método deve retornar um valor de um fornecido `Match` tipo de forma que os grupos podem ser acessados de forma fortemente tipada. Assim, você primeiro declarar a `Match` tipo. Como esse tipo depende do padrão que foi fornecido como argumento estático, esse tipo deve estar aninhado dentro da definição de tipo com parâmetros:

```fsharp
let matchTy = ProvidedTypeDefinition(
"MatchType", 
baseType = Some baseTy, 
HideObjectMethods = true)

ty.AddMember matchTy
```

Você, em seguida, adicionar uma propriedade para o tipo de correspondência para cada grupo. Em tempo de execução, uma correspondência é representada como um `System.Text.RegularExpressions.Match` valor, portanto, as aspas que define a propriedade devem usar o `System.Text.RegularExpressions.Match.Groups` propriedade para o grupo relevantes indexada.

```fsharp
for group in r.GetGroupNames() do
// Ignore the group named 0, which represents all input.
if group <> "0" then
let prop = ProvidedProperty(
propertyName = group, 
propertyType = typeof<Group>, 
GetterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
matchTy.AddMember prop
```

Novamente, observe que você está adicionando documentação XML para a propriedade fornecida. Observe também que uma propriedade pode ser lidos se um `GetterCode` função é fornecida, e a propriedade pode ser gravada se um `SetterCode` função é fornecida para a propriedade resultante é somente leitura.

Agora você pode criar um método de instância que retorna um valor `Match` tipo:

```fsharp
let matchMethod = 
ProvidedMethod(
methodName = "Match", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = matchTy, 
InvokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
matchMeth.AddXmlDoc "Searches the specified input string for the first ocurrence of this regular expression" 

ty.AddMember matchMeth
```

Porque você está criando um método de instância, `args.[0]` representa o `RegexTyped` instância na qual o método está sendo chamado, e `args.[1]` é o argumento de entrada.

Por fim, forneça um construtor para que a instância do tipo fornecido pode ser criada.

```fsharp
let ctor = ProvidedConstructor(
parameters = [], 
InvokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)
ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

Simplesmente apaga o construtor para a criação de uma instância de Regex .NET padrão, que é convertida novamente para um objeto porque `obj` é a eliminação do tipo fornecido. Com essa alteração, o exemplo de uso de API especificado anteriormente no tópico funciona conforme o esperado. O código a seguir é concluída e final:

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



let ty = ProvidedTypeDefinition(
thisAssembly, 
rootNamespace, 
typeName, 
baseType = Some baseTy)

ty.AddXmlDoc "A strongly typed interface to the regular expression '%s'"

// Provide strongly typed version of Regex.IsMatch static method.
let isMatch = ProvidedMethod(
methodName = "IsMatch", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = typeof<bool>, 
IsStaticMethod = true,
InvokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>) 

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string"

ty.AddMember isMatch

// Provided type for matches
// Again, erase to obj even though the representation will always be a Match
let matchTy = ProvidedTypeDefinition(
"MatchType", 
baseType = Some baseTy, 
HideObjectMethods = true)

// Nest the match type within parameterized Regex type.
ty.AddMember matchTy

// Add group properties to match type
for group in r.GetGroupNames() do
// Ignore the group named 0, which represents all input.
if group <> "0" then
let prop = ProvidedProperty(
propertyName = group, 
propertyType = typeof<Group>, 
GetterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
matchTy.AddMember(prop)

// Provide strongly typed version of Regex.Match instance method.
let matchMeth = ProvidedMethod(
methodName = "Match", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = matchTy, 
InvokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
matchMeth.AddXmlDoc "Searches the specified input string for the first occurence of this regular expression"

ty.AddMember matchMeth

// Declare a constructor.
let ctor = ProvidedConstructor(
parameters = [], 
InvokeCode = fun args -> <@@ Regex(pattern) :> obj @@>)

// Add documentation to the constructor.
ctor.AddXmlDoc "Initializes a regular expression instance"

ty.AddMember ctor

ty
| _ -> failwith "unexpected parameter values")) 

do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

`Key Lessons`

Esta seção explica como criar um provedor de tipos que opera em seus parâmetros estáticos. O provedor verifica se o parâmetro static e fornece operações com base em seu valor.


## <a name="a-type-provider-that-is-backed-by-local-data"></a>Um provedor de tipo que é apoiado por dados locais
Com frequência, convém provedores de tipo para apresentar as APIs com base em não apenas parâmetros estáticos, mas também informações de sistemas locais ou remotos. Esta seção discute os provedores de tipos que se baseiam em dados locais, como arquivos de dados locais.


### <a name="simple-csv-file-provider"></a>Provedor de arquivo CSV simples
Como um exemplo simples, considere um provedor de tipo para acessar dados científicos no formato de valor separado por vírgula (CSV). Esta seção pressupõe que os arquivos CSV contém uma linha de cabeçalho seguida pelos dados de ponto flutuante, como mostra a tabela a seguir:



|Distância (medidor)|Hora (segundos)|
|----------------|-------------|
|50.0|3.7|
|100.0|5.2|
|150.0|6.4|
Esta seção mostra como fornecer um tipo que você pode usar para obter as linhas com um `Distance` propriedade do tipo `float<meter>` e um `Time` propriedade do tipo `float<second>`. Para simplificar, as seguintes suposições são feitas:


- Nomes de cabeçalho são sem unidade ou ter o formato "Nome (unidade)" e não conter vírgulas.
<br />

- As unidades são todas as unidades de Systeme internacional (SI) como o [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames módulo (F #)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) módulo define.
<br />

- As unidades são todos simples (por exemplo, monitorar) em vez de composta (por exemplo, o medidor/segundo).
<br />

- Todas as colunas contêm dados de ponto flutuante.
<br />

Um provedor mais completo seria solte essas restrições.

Novamente, a primeira etapa é considerar a aparência de API. Dado um `info.csv` arquivo com o conteúdo da tabela anterior (no formato delimitado por vírgula), os usuários do provedor devem ser capazes de gravar o código semelhante ao exemplo a seguir:

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

Nesse caso, o compilador deve converter essas chamadas em algo parecido com o exemplo a seguir:

```fsharp
let info = new MiniCsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

A conversão ideal exigirá o provedor de tipo para definir um real `CsvFile` tipo no assembly do provedor de tipo. Provedores de tipos geralmente dependem de alguns tipos de auxiliar e métodos para encapsular a lógica de importante. Como as medidas são apagadas em tempo de execução, você pode usar um `float[]` como o tipo apagado para uma linha. O compilador tratará colunas diferentes têm tipos de medida diferente. Por exemplo, a primeira coluna em nosso exemplo tem tipo `float<meter>`, e o segundo tem `float<second>`. No entanto, a representação apagada pode permanecer muito simple.

O código a seguir mostra os principais da implementação.

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
inherit TypeProviderForNamespaces()

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

let prop = ProvidedProperty(fieldName, fieldTy, 
GetterCode = fun [row] -> <@@ (%%row:float[]).[i] @@>)

// Add metadata that defines the property's location in the referenced file.
prop.AddDefinitionLocation(1, headers.[i].Index + 1, filename)
rowTy.AddMember(prop) 

// Define the provided type, erasing to CsvFile.
let ty = ProvidedTypeDefinition(asm, ns, tyName, Some(typeof<CsvFile>))

// Add a parameterless constructor that loads the file that was used to define the schema.
let ctor0 = ProvidedConstructor([], 
InvokeCode = fun [] -> <@@ CsvFile(resolvedFilename) @@>)
ty.AddMember ctor0

// Add a constructor that takes the file name to load.
let ctor1 = ProvidedConstructor([ProvidedParameter("filename", typeof<string>)], 
InvokeCode = fun [filename] -> <@@ CsvFile(%%filename) @@>)
ty.AddMember ctor1

// Add a more strongly typed Data property, which uses the existing property at runtime.
let prop = ProvidedProperty("Data", typedefof<seq<_>>.MakeGenericType(rowTy), 
GetterCode = fun [csvFile] -> <@@ (%%csvFile:CsvFile).Data @@>)
ty.AddMember prop

// Add the row type as a nested type.
ty.AddMember rowTy
ty)

// Add the type to the namespace.
do this.AddNamespace(ns, [csvTy])
```

Observe os seguintes pontos sobre a implementação:


- Construtores sobrecarregados permitem que o arquivo original ou um que tenha um esquema idêntico a ser lido. Esse padrão é comum quando você escrever um provedor de tipos de fontes de dados local ou remoto e esse padrão permite que um arquivo local a ser usado como o modelo de dados remotos.
<br />  Você pode usar o [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) valor que é passado para o construtor do provedor de tipo para resolver nomes de arquivo relativo.
<br />

- Você pode usar o `AddDefinitionLocation` método para definir o local das propriedades fornecidos. Portanto, se você usar `Go To Definition` em uma propriedade fornecida, o arquivo CSV será aberto no Visual Studio.
<br />

- Você pode usar o `ProvidedMeasureBuilder` tipo para pesquisar as unidades de SI e gerar relevante `float<_>` tipos.
<br />

`Key Lessons`

Esta seção explica como criar um provedor de tipo para uma fonte de dados local com um esquema simple que está contido na fonte de dados em si.


## <a name="going-further"></a>Continuar
As seções a seguir incluem sugestões para estudar em mais detalhes.


### <a name="a-look-at-the-compiled-code-for-erased-types"></a>Examinar o código compilado para tipos apagados
Para dar uma ideia de como o uso do provedor de tipo corresponde ao código que é emitido, examine a seguinte função usando o `HelloWorldTypeProvider` que é usada neste tópico.

```fsharp
let function1 () = 
let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
obj1.InstanceProperty
```

Aqui está uma imagem do código resultante descompilado usando ildasm.exe:

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

Como mostra o exemplo, todos os menções do tipo `Type1` e `InstanceProperty` propriedade foi apagado, deixando apenas operações nos tipos de tempo de execução envolvidos.


### <a name="design-and-naming-conventions-for-type-providers"></a>Design e convenções de nomenclatura para provedores de tipos
Observe as convenções a seguir ao criar provedores de tipos.


- `Providers for Connectivity Protocols`
<br />  Em geral, os nomes de provedor a maioria das DLLs para protocolos de conectividade de dados e serviços, como conexões do OData ou SQL, devem terminar em `TypeProvider` ou `TypeProviders`. Por exemplo, use um nome DLL que é semelhante a cadeia de caracteres a seguir:
<br />

```
  Fabrikam.Management.BasicTypeProviders.dll
```

  Certifique-se de que seus tipos fornecidos são membros do namespace correspondente e indicam o protocolo de conectividade implementadas:
<br />

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

- `Utility Providers for General Coding`
<br />  Para um provedor de tipos de utilitário como expressões regulares, o provedor de tipo pode ser parte de uma biblioteca de base, como mostra o exemplo a seguir:
<br />

```fsharp
  #r "Fabrikam.Core.Text.Utilities.dll"
```

  Nesse caso, o tipo fornecido apareceria em um ponto apropriado de acordo com as convenções de design normais .NET:
<br />

```fsharp
  open Fabrikam.Core.Text.RegexTyped
  
  let regex = new RegexTyped<"a+b+a+b+">()
```

- `Singleton Data Sources`
<br />  Alguns provedores de tipo se conectar a uma fonte de dados dedicado e fornecem apenas os dados. Nesse caso, você deve descartar o `TypeProvider` sufixo e use normais convenções de nomenclatura do .NET:
<br />

```fsharp
  #r "Fabrikam.Data.Freebase.dll"
  
  let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

  Para obter mais informações, consulte o `GetConnection` design convenção é descrita posteriormente neste tópico.
<br />


### <a name="design-patterns-for-type-providers"></a>Padrões de design para provedores de tipos
As seções a seguir descrevem os padrões de design, que você pode usar ao criar provedores de tipos.


#### <a name="the-getconnection-design-pattern"></a>O padrão de Design de GetConnection
A maioria dos provedores de tipo deve ser gravado para usar o `GetConnection` padrão que é usado pelos provedores de tipo em FSharp.Data.TypeProviders.dll, como mostra o exemplo a seguir:

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>Provedores de tipos com o apoio de serviços e dados remotos
Antes de criar um provedor de tipo que é apoiado por serviços e dados remotos, você deve considerar uma variedade de problemas inerentes a programação conectada. Esses problemas incluem as seguintes considerações:


- Mapeamento de esquema
<br />

- alocação e invalidação na presença de alteração de esquema
<br />

- cache de esquemas
<br />

- implementações assíncronas de operações de acesso de dados
<br />

- suporte a consultas, inclusive consultas LINQ
<br />

- autenticação e credenciais
<br />

Este tópico não explorar ainda mais esses problemas.


### <a name="additional-authoring-techniques"></a>Técnicas de criação adicionais
Quando você escrever seus próprios provedores de tipo, você talvez queira usar as seguintes técnicas adicionais.


- `Creating Types and Members On-Demand`
<br />  A API ProvidedType adiou a versões do AddMember.
<br />

```fsharp
  type ProvidedType =
  member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
  member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

  Essas versões são usadas para criar espaços de sob demanda de tipos.
<br />

- `Providing Array, ByRef, and Pointer types`
<br />  Tornar membros fornecidos (cujas assinaturas incluem tipos de matriz byref tipos e instâncias de tipos genéricos) usando o normal `MakeArrayType`, `MakePointerType`, e `MakeGenericType` em qualquer instância de System. Type, incluindo `ProvidedTypeDefinitions`.
<br />

- `Providing Unit of Measure Annotations`
<br />  A API ProvidedTypes fornece auxiliares para criar anotações de medida. Por exemplo, para fornecer o tipo `float<kg>`, use o seguinte código:
<br />

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  Para fornecer o tipo `Nullable<decimal<kg/m^2>>`, use o seguinte código:
<br />

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

- `Accessing Project-Local or Script-Local Resources`
<br />  Cada instância de um provedor de tipo pode ser fornecida um `TypeProviderConfig` valor durante a construção. Esse valor contém a pasta"Resolução" para o provedor (ou seja, a pasta de projeto para a compilação ou o diretório que contém um script), a lista de assemblies referenciados e outras informações.
<br />

- `Invalidation`
<br />  Provedores podem gerar sinais de invalidação para notificar o serviço de linguagem F # que as suposições de esquema podem ter sido alterado. Quando ocorre a invalidação, um typecheck é refeito se o provedor está sendo hospedado no Visual Studio. Este sinal será ignorado quando o provedor é hospedado em F # interativo ou pelo compilador F # (fsc.exe).
<br />

- `Caching Schema Information`
<br />  Provedores geralmente devem armazenar em cache acesso às informações de esquema. Os dados armazenados em cache devem ser armazenados usando um nome de arquivo que é fornecido como um parâmetro estático ou como dados de usuário. Um exemplo de cache de esquema é o `LocalSchemaFile` os provedores de tipo no parâmetro de `FSharp.Data.TypeProviders` assembly. A implementação desses provedores, esse parâmetro estático instrui o provedor de tipo para usar as informações de esquema no arquivo local especificado em vez de acessar a fonte de dados pela rede. Para usar as informações de esquema em cache, você também deve definir o parâmetro static `ForceUpdate` para `false`. Você pode usar uma técnica semelhante para habilitar o acesso de dados online e offline.
<br />

- `Backing Assembly`
<br />  Quando você compila um arquivo. dll ou .exe, o arquivo. dll de apoio para tipos gerados está estaticamente vinculado o assembly resultante. Esse link é criado, copiando as definições de tipo de linguagem intermediária (IL) e todos os recursos gerenciados do conjunto de backup no assembly final. Quando você usar o F # interativo, o arquivo. dll de backup não é copiado e em vez disso, é carregado diretamente no processo de F # interativo.
<br />

- `Exceptions and Diagnostics from Type Providers`
<br />  Todos os usos de todos os membros de tipos fornecidos podem ocasionar exceções. Em todos os casos, se um provedor de tipo lança uma exceção, o compilador host atributos o erro para um provedor de tipo específico.
<br />
  - Exceções de provedor de tipo nunca devem resultar em erros do compilador interno.
<br />

  - Provedores de tipos não podem relatar avisos.
<br />

  - Quando um provedor de tipo é hospedado no compilador F #, um ambiente de desenvolvimento do F # ou F # interativo, todas as exceções do provedor são capturadas. A propriedade de mensagem sempre é o texto de erro e nenhum rastreamento de pilha é exibida. Se você vai lançar uma exceção, você pode lançar os exemplos a seguir:
<br />
    - `System.NotSupportedException`
<br />

    - `System.IO.IOException`
<br />

    - `System.Exception`
<br />


#### <a name="providing-generated-types"></a>Fornece tipos gerados
Até agora, este documento explicou como fornecer tipos apagados. Você também pode usar o mecanismo de provedor de tipo em F # para fornecer tipos gerados, que são adicionados como definições de tipo .NET reais no programa dos usuários. Você deve se referir a gerado fornecida tipos usando uma definição de tipo.

```fsharp
open Microsoft.FSharp.TypeProviders 

type Service = ODataService<" https://services.odata.org/Northwind/Northwind.svc/">
```

O código auxiliar 0,2 ProvidedTypes que faz parte da versão do F # 3.0 tem somente suporte limitado para fornecer tipos gerados. As instruções a seguir devem ser verdadeiras para uma definição de tipo gerado:


- IsErased deve ser definido como `false`.
<br />

- O provedor deve ter um assembly que tem um arquivo do backup real .NET. dll com um arquivo. dll correspondente no disco.
<br />

Você também deve chamar `ConvertToGenerated` em um tipo de raiz fornecido cujos tipos aninhados formam um conjunto fechado de tipos gerados. Essa chamada emite a definição de determinado tipo fornecido e suas definições de tipo aninhado em um assembly e ajusta a `Assembly` propriedade de todas as definições de tipo fornecido para retornar a esse assembly. O assembly é emitido somente quando a propriedade do Assembly no tipo de raiz é acessada pela primeira vez. O compilador F # host acessar essa propriedade quando ele processa uma declaração de tipo produtivas para o tipo.


## <a name="rules-and-limitations"></a>Regras e limitações
Quando você escreve provedores de tipos, tenha as seguintes regras e limitações em mente.


- `Provided types must be reachable.`
<br />  Todos os fornecidos tipos devem ser os tipos aninhados não pode ser acessados. Os tipos aninhados não são fornecidos na chamada para o `TypeProviderForNamespaces` construtor ou uma chamada para `AddNamespace`. Por exemplo, se o provedor fornece um tipo `StaticClass.P : T`, certifique-se de que T é um tipo aninhado não ou aninhados em um.
<br />  Por exemplo, alguns provedores têm uma classe estática, como `DataTypes` que contêm esses `T1, T2, T3, ...` tipos. Caso contrário, o erro afirma que uma referência ao tipo T no assembly A foi encontrada, mas não foi possível encontrar o tipo nesse assembly. Se esse erro aparecer, verifique se todos os seus subtipos podem ser alcançados dos tipos de provedor. Observação: Essas `T1, T2, T3...` tipos são denominados de *durante a execução* tipos. Lembre-se de colocá-los em um namespace acessível ou um tipo de pai.
<br />

- `Limitations of the Type Provider Mechanism`
<br />  O mecanismo de provedor de tipo em F # tem as seguintes limitações:
<br />
  - A infraestrutura subjacente para provedores de tipos em F # não dá suporte a fornecida genérico tipos ou métodos genéricos de fornecido.
<br />

  - O mecanismo não dá suporte a tipos aninhados com parâmetros estáticos.
<br />

- `Limitations of the ProvidedTypes Support Code`
<br />  O `ProvidedTypes` código de suporte tem as seguintes regras e limitações:
<br />
  1. As propriedades fornecidas com indexada getters e setters não são implementadas.
<br />

  2. Os eventos fornecidos não são implementados.
<br />

  3. Os objetos de informações e tipos fornecidos deve ser usada somente para o mecanismo de provedor de tipo em F #. Eles não são mais amplamente utilizáveis como objetos System. Type.
<br />

  4. As construções que você pode usar aspas que definem as implementações de método têm várias limitações. Você pode consultar o código-fonte para ProvidedTypes -*versão* para ver quais construções são suportadas com aspas.
<br />

- `Type providers must generate output assemblies that are .dll files, not .exe files.`
<br />


## <a name="development-tips"></a>Dicas de desenvolvimento
Você pode encontrar as seguintes dicas úteis durante o processo de desenvolvimento.


- `Run Two Instances of Visual Studio.` Você pode desenvolver o provedor de tipo em uma instância e o provedor de teste nos outros porque o IDE de teste tem um bloqueio no arquivo. dll que impede que o provedor de tipo que está sendo recriado. Portanto, você deve fechar a segunda instância do Visual Studio enquanto o provedor é criado na primeira ocorrência e, em seguida, você deverá reabri-la a segunda instância depois que o provedor for criado.
<br />

- `Debug type providers by using invocations of fsc.exe.` Você pode chamar os provedores de tipos, usando as seguintes ferramentas:
<br />
  - FSC.exe (compilador de linha de comando do F #)
<br />

  - FSI.exe (compilador o F # interativo)
<br />

  - devenv.exe (Visual Studio)
<br />

  Geralmente você pode depurar provedores de tipos mais facilmente usando fsc.exe em um arquivo de script de teste (por exemplo, script.fsx). Você pode iniciar um depurador em um prompt de comando.
<br />

```
  devenv /debugexe fsc.exe script.fsx
```

  Você pode usar o log de impressão para stdout.
<br />


## <a name="see-also"></a>Consulte também
[Provedores de Tipos](index.md)
