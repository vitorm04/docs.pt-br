---
title: Criar tipos mescla usando métodos de interface padrão
description: Usando membros de interface padrão, você pode estender interfaces com implementações padrão opcionais para implementadores.
ms.technology: csharp-advanced-concepts
ms.date: 10/04/2019
ms.openlocfilehash: 798413f0071159893de39f3e190a9b2693571bb7
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039272"
---
# <a name="tutorial-mix-in-functionality-when-creating-classes-using-interfaces-with-default-interface-methods"></a>Tutorial: misturar na funcionalidade ao criar classes usando interfaces com métodos de interface padrão

Desde o C# 8.0 no .NET Core 3.0, é possível definir uma implementação em que você declara um membro de uma interface. Esse recurso fornece novos recursos em que você pode definir implementações padrão para recursos declarados em interfaces. As classes podem escolher quando substituir a funcionalidade, quando usar a funcionalidade padrão e quando não declarar suporte para recursos discretos.

Neste tutorial, você aprenderá a:

> [!div class="checklist"]
>
> * Crie interfaces com implementações que descrevem recursos discretos.
> * Crie classes que usam as implementações padrão.
> * Crie classes que substituem algumas ou todas as implementações padrão.

## <a name="prerequisites"></a>Prerequisites

Você precisará configurar seu computador para executar o .NET Core, incluindo o C# compilador 8,0. O C# compilador 8,0 está disponível a partir do [Visual Studio 2019, 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)ou do [SDK do .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core) ou posterior.

## <a name="limitations-of-extension-methods"></a>Limitações dos métodos de extensão

Uma maneira de implementar o comportamento que aparece como parte de uma interface é definir [métodos de extensão](../programming-guide/classes-and-structs/extension-methods.md) que forneçam o comportamento padrão. As interfaces declaram um conjunto mínimo de membros, fornecendo uma área de superfície maior para qualquer classe que implemente essa interface. Por exemplo, os métodos de extensão no <xref:System.Linq.Enumerable> fornecem a implementação de qualquer sequência para ser a origem de uma consulta LINQ.

Os métodos de extensão são resolvidos no momento da compilação, usando o tipo declarado da variável. As classes que implementam a interface podem fornecer uma implementação melhor para qualquer método de extensão. Declarações de variáveis devem corresponder ao tipo de implementação para permitir que o compilador escolha essa implementação. Quando o tipo de tempo de compilação corresponde à interface, as chamadas de método são resolvidas para o método de extensão. Outra preocupação com métodos de extensão é que esses métodos sejam acessíveis sempre que a classe que contém os métodos de extensão estiver acessível. Classes não podem declarar se devem ou não devem fornecer recursos declarados em métodos de extensão.

A partir C# do 8,0, você pode declarar as implementações padrão como métodos de interface. Em seguida, cada classe usa automaticamente a implementação padrão. Qualquer classe que possa fornecer uma implementação melhor pode substituir a definição do método de interface por um algoritmo melhor. De certa forma, essa técnica parece semelhante a como você pode usar [métodos de extensão](../programming-guide/classes-and-structs/extension-methods.md).

Neste artigo, você aprenderá como as implementações de interface padrão habilitam novos cenários.

## <a name="design-the-application"></a>Criar o aplicativo

Considere um aplicativo de automação inicial. Você provavelmente tem muitos tipos diferentes de luzes e indicadores que poderiam ser usados em toda a casa. Cada luz deve dar suporte a APIs para ligá-las e reportar o estado atual. Algumas luzes e indicadores podem dar suporte a outros recursos, como:

- Ative a luz e desative-a após um temporizador.
- Pisque a luz por um período de tempo.

Alguns desses recursos estendidos podem ser emulados em dispositivos que dão suporte ao conjunto mínimo. Isso indica fornecer uma implementação padrão. Para os dispositivos que têm mais recursos internos, o software do dispositivo usaria os recursos nativos. Para outras luzes, eles poderiam optar por implementar a interface e usar a implementação padrão.

Membros de interface padrão é uma solução melhor para esse cenário do que métodos de extensão. Os autores de classe podem controlar quais interfaces eles optam por implementar. Essas interfaces que eles escolhem estão disponíveis como métodos. Além disso, como os métodos de interface padrão são virtuais por padrão, a expedição do método sempre escolhe a implementação na classe. 

Vamos criar o código para demonstrar essas diferenças.

## <a name="create-interfaces"></a>Criar interfaces

Comece criando a interface que define o comportamento para todas as luzes:

[!code-csharp[Declare base interface](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetILightInterfaceV1)]

Um acessório de luz de sobrecarga básica pode implementar essa interface, conforme mostrado no código a seguir:

[!code-csharp[First overhead light](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetOverheadLightV1)]

Neste tutorial, o código não impulsiona os dispositivos IoT, mas emula essas atividades gravando mensagens no console. Você pode explorar o código sem automatizar sua casa.

Em seguida, vamos definir a interface para uma luz que pode desligar automaticamente após um tempo limite:

[!code-csharp[pure Timer interface](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetPureTimerInterface)]

Você pode adicionar uma implementação básica à luz de sobrecarga, mas uma solução melhor é modificar essa definição de interface para fornecer uma implementação padrão `virtual`:

[!code-csharp[Timer interface](~/samples/csharp/tutorials/mixins-with-interfaces/ITimerLight.cs?name=SnippetTimerLightFinal)]

Ao adicionar essa alteração, a classe `OverheadLight` pode implementar a função de temporizador declarando suporte para a interface:

```csharp
public class OverheadLight : ITimerLight { }
```

Um tipo de luz diferente pode dar suporte a um protocolo mais sofisticado. Ele pode fornecer sua própria implementação para `TurnOnFor`, conforme mostrado no código a seguir:

[!code-csharp[Override the timer function](~/samples/csharp/tutorials/mixins-with-interfaces/HalogenLight.cs?name=SnippetHalogenLight)]

Ao contrário da substituição de métodos de classe virtual, a declaração de `TurnOnFor` na classe `HalogenLight` não usa a palavra-chave `override`. 

## <a name="mix-and-match-capabilities"></a>Recursos de combinação e correspondência

As vantagens dos métodos de interface padrão se tornam mais claras à medida que você introduz recursos mais avançados. O uso de interfaces permite misturar e combinar recursos. Ele também permite que cada autor de classe escolha entre a implementação padrão e uma implementação personalizada. Vamos adicionar uma interface com uma implementação padrão para uma luz intermitente:

[!code-csharp[Define the blinking light interface](~/samples/csharp/tutorials/mixins-with-interfaces/IBlinkingLight.cs?name=SnippetBlinkingLight)]

A implementação padrão permite que qualquer luz pisque. A luz de sobrecarga pode adicionar recursos de temporizador e de intermitência usando a implementação padrão:

[!code-csharp[Use the default blink function](~/samples/csharp/tutorials/mixins-with-interfaces/OverheadLight.cs?name=SnippetOverheadLight)]

Um novo tipo de luz, o `LEDLight` dá suporte à função de temporizador e à função de intermitência diretamente. Esse estilo leve implementa as interfaces `ITimerLight` e `IBlinkingLight` e substitui o método `Blink`:

[!code-csharp[Override the blink function](~/samples/csharp/tutorials/mixins-with-interfaces/LEDLight.cs?name=SnippetLEDLight)]

Um `ExtraFancyLight` pode dar suporte a ambas as funções de intermitência e de temporizador diretamente:

[!code-csharp[Override the blink and timer function](~/samples/csharp/tutorials/mixins-with-interfaces/ExtraFancyLight.cs?name=SnippetExtraFancyLight)]

O `HalogenLight` criado anteriormente não dá suporte a intermitência. Portanto, não adicione o `IBlinkingLight` à lista de suas interfaces com suporte.

## <a name="detect-the-light-types-using-pattern-matching"></a>Detectar os tipos de luz usando correspondência de padrões

Em seguida, vamos escrever um código de teste. Você pode fazer uso do C#recurso de [correspondência de padrões](../pattern-matching.md) para determinar os recursos de uma luz examinando quais interfaces ele suporta.  O método a seguir exercita os recursos com suporte de cada luz:

[!code-csharp[Test a light's capabilities](~/samples/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetTestLightFunctions)]

O código a seguir no método `Main` cria cada tipo de luz em sequência e testa essa luz:

[!code-csharp[Test a light's capabilities](~/samples/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetMainMethod)]

## <a name="how-the-compiler-determines-best-implementation"></a>Como o compilador determina a melhor implementação

Esse cenário mostra uma interface base sem nenhuma implementação. A adição de um método à interface `ILight` apresenta novas complexidades. As regras de linguagem que regem os métodos de interface padrão minimizam o efeito nas classes concretas que implementam várias interfaces derivadas. Vamos aprimorar a interface original com um novo método para mostrar como isso altera seu uso. Cada luz do indicador pode relatar seu status de energia como um valor enumerado:

[!code-csharp[Enumeration for power status](~/samples/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetPowerStatus)]

A implementação padrão pressupõe energia CA:

[!code-csharp[Report a default power status](~/samples/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetILightInterface)]

Essas alterações são compiladas corretamente, mesmo que o `ExtraFancyLight` declare o suporte para a interface `ILight` e ambas as interfaces derivadas, `ITimerLight` e `IBlinkingLight`. Há apenas uma implementação "mais próxima" declarada na interface `ILight`. Qualquer classe que declarou uma substituição se tornaria a única implementação "mais próxima". Você viu exemplos nas classes anteriores que substituiu os membros de outras interfaces derivadas.

Evite substituir o mesmo método em várias interfaces derivadas. Isso cria uma chamada de método ambígua sempre que uma classe implementa ambas as interfaces derivadas. O compilador não pode escolher um único método melhor para que ele emita um erro. Por exemplo, se o `IBlinkingLight` e o `ITimerLight` implementaram uma substituição de `PowerStatus`, o `OverheadLight` precisaria fornecer uma substituição mais específica. Caso contrário, o compilador não pode escolher entre as implementações nas duas interfaces derivadas. Normalmente, você pode evitar essa situação mantendo as definições de interface pequenas e concentradas em um recurso. Nesse cenário, cada recurso de uma luz é sua própria interface; várias interfaces são herdadas apenas por classes.

Este exemplo mostra um cenário em que você pode definir recursos discretos que podem ser misturados em classes. Você declara qualquer conjunto de funcionalidades com suporte declarando a quais interfaces uma classe dá suporte. O uso de métodos de interface padrão virtuais permite que as classes usem ou definam uma implementação diferente para qualquer ou todos os métodos de interface. Esse recurso de linguagem fornece novas maneiras de modelar os sistemas do mundo real que você está criando. Os métodos de interface padrão fornecem uma maneira mais clara de expressar classes relacionadas que podem misturar e corresponder recursos diferentes usando implementações virtuais desses recursos.
