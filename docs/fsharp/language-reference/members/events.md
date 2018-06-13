---
title: Eventos (F#)
description: 'Saiba como F # eventos permitem que você associe a ações do usuário, que são importantes na programação de GUI de chamadas de função.'
ms.date: 05/16/2016
ms.openlocfilehash: e90d3abc5b5222f60c4e08539ee40bf83ac70ec7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564738"
---
# <a name="events"></a>Eventos

> [!NOTE]
Os links de referência da API neste artigo levarão você até o MSDN.  A referência da API docs.microsoft.com não está completa.

Eventos permitem que você associe chamadas de função a ações de usuário e são importantes na programação da GUI. Os eventos também podem ser disparados por seus aplicativos ou pelo sistema operacional.

## <a name="handling-events"></a>Tratando eventos
Quando você usa uma biblioteca de GUI como o Windows Forms ou o Windows Presentation Foundation (WPF), grande parte do código em seu aplicativo é executado em resposta a eventos que são predefinidos pela biblioteca. Esses eventos predefinidos são membros de classes da GUI como formulários e controles. Você pode adicionar comportamento personalizado a um evento preexistente, como o clique de botão, ao fazer referência ao evento de interesse nomeado específico (por exemplo, o evento `Click` da classe `Form`) e invocar o método `Add` como mostrado no código a seguir. Se você executar isso do F# Interativo, omita a chamada a `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

O tipo do método `Add` é `('a -> unit) -> unit`. Portanto, o método do manipulador de eventos assume um parâmetro, normalmente os argumentos de evento, e retorna `unit`. O exemplo anterior mostra o manipulador de eventos como uma expressão lambda. O manipulador de eventos também pode ser um valor de função como no exemplo de código a seguir. O exemplo de código a seguir também mostra o uso de parâmetros do manipulador de eventos que fornecem informações específicas para o tipo de evento. Para um evento `MouseMove`, o sistema passa um objeto `System.Windows.Forms.MouseEventArgs` que contém a posição `X` e `Y` do ponteiro.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]
    
## <a name="creating-custom-events"></a>Criando eventos personalizados
F # eventos são representados por F # [evento](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) de classe que implementa o [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) interface. `IEvent` é uma interface que combina a funcionalidade de duas interfaces, `System.IObservable<'T>` e [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a). Portanto, `Event`s têm funcionalidade equivalente de delegados em outras linguagens, além da funcionalidade adicional de `IObservable` o que significa que os eventos de F# oferecem suporte à filtragem de eventos e ao uso de funções de primeira classe de F# e expressões lambda como manipuladores de eventos. Essa funcionalidade é fornecida no [módulo eventos](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).

Para criar um evento em uma classe que atue como qualquer outro evento do .NET Framework, adicione à classe uma associação `let` que defina um `Event` como um campo em uma classe. Você pode especificar o tipo de argumento de evento desejado como o argumento de tipo ou deixá-lo em branco e fazer com que o compilador deduza o tipo apropriado. Você também deve definir um membro de evento que exponha o evento como um evento de CLI. Esse membro deve ter o [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) atributo. Ela é declarada como uma propriedade e sua implementação é apenas uma chamada para o [publicar](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) propriedade do evento. Os usuários de sua classe podem usar o método `Add` do evento publicado para adicionar um manipulador. O argumento para o método `Add` pode ser uma expressão lambda. Você pode usar a propriedade `Trigger` do evento para gerar o evento, passando os argumentos à função do manipulador. O exemplo de código a seguir ilustra isso. Neste exemplo, o argumento do tipo inferido para o evento é uma tupla que representa os argumentos para a expressão lambda.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

A saída é a seguinte.

```
Event1 occurred! Object data: Hello World!
```

A funcionalidade adicional fornecida pelo módulo `Event` está ilustrada aqui. O exemplo de código a seguir ilustra o uso básico de `Event.create` para criar um evento e um método de gatilho, adicionar dois manipuladores de eventos na forma de expressões lambda e disparar o evento para executar ambas as expressões lambda.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

A saída do código anterior está a seguir.

```
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a>Processando fluxos de eventos
Em vez de apenas adicionar um manipulador de eventos para um evento usando o [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) função, você pode usar as funções no `Event` módulo para processo fluxos de eventos por meios altamente personalizados. Para fazer isso, use a barra vertical e o sinal maior que (`|>`) junto com o evento como o primeiro valor em uma série de chamadas de função e funções do módulo `Event` como chamadas de função subsequentes.

O exemplo de código a seguir mostra como configurar um evento em que o manipulador é chamado apenas em determinadas condições.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

O [módulo Observable](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) contém funções semelhantes que operam em objetos observáveis. Objetos observáveis são semelhantes a eventos, mas apenas assinam eventos ativamente se eles mesmos estiverem sendo assinados.


## <a name="implementing-an-interface-event"></a>Implementando um evento de interface
À medida em que desenvolve componentes de interface do usuário, você frequentemente começa ao criar um novo formulário ou um novo controle que herde de um formulário ou controle existente. Eventos são frequentemente definidos em uma interface e, nesse caso, você deve implementar a interface para implementar o evento. A interface `System.ComponentModel.INotifyPropertyChanged` define um único evento `System.ComponentModel.INotifyPropertyChanged.PropertyChanged`. O código a seguir ilustra como implementar o evento que essa interface herdada definiu:

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

type AppForm() as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs -> this.Property1 <- "text2"
        this.Property2 <- "text3")

    // This property does not have the property-changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property-changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    // Expose the PropertyChanged event as a first class .NET event.
    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish


    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = propertyChanged.Publish.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = propertyChanged.Publish.RemoveHandler(handler)

    // This is the event-handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
let inpc = appForm :> INotifyPropertyChanged
inpc.PropertyChanged.Add(appForm.OnPropertyChanged)
Application.Run(appForm)
```

Se você desejar conectar o evento no construtor, o código será um pouco mais complicado porque a conexão do evento deverá estar em um bloco `then` em um construtor adicional como no exemplo a seguir:

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

// Create a private constructor with a dummy argument so that the public
// constructor can have no arguments.
type AppForm private (dummy) as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs -> this.Property1 <- "text2"
        this.Property2 <- "text3")


    // This property does not have the property changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = this.PropertyChanged.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = this.PropertyChanged.RemoveHandler(handler)

    // This is the event handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

    new() as this =
        new AppForm(0)
        then
            let inpc = this :> INotifyPropertyChanged
            inpc.PropertyChanged.Add(this.OnPropertyChanged)


// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
Application.Run(appForm)
```

## <a name="see-also"></a>Consulte também
[Membros](index.md)

[Manipulando e acionando eventos](../../../../docs/standard/events/index.md)

[Expressões lambda: A `fun` palavra-chave](../functions/lambda-expressions-the-fun-keyword.md)

[Módulo Control. Event](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)

[Control. Event&#60;T'&#62; classe](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)

[Control. Event&#60;'Representante' Args&#62; classe](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)
