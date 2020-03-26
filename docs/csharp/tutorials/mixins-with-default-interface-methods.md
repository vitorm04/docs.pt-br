---
title: Criar tipos de mixin usando métodos de interface padrão
description: Usando membros de interface padrão, você pode estender interfaces com implementações padrão opcionais para implementores.
ms.technology: csharp-advanced-concepts
ms.date: 10/04/2019
ms.openlocfilehash: ee0536ef51f9bea3e6851be23cc19fa28cc6916b
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134368"
---
# <a name="tutorial-mix-functionality-in-when-creating-classes-using-interfaces-with-default-interface-methods"></a>Tutorial: Misture a funcionalidade ao criar classes usando interfaces com métodos de interface padrão

Desde o C# 8.0 no .NET Core 3.0, é possível definir uma implementação em que você declara um membro de uma interface. Esse recurso fornece novos recursos onde você pode definir implementações padrão para recursos declarados em interfaces. As classes podem escolher quando substituir a funcionalidade, quando usar a funcionalidade padrão e quando não declarar suporte para recursos discretos.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
>
> * Crie interfaces com implementações que descrevam recursos discretos.
> * Crie classes que usam as implementações padrão.
> * Crie classes que sobrepõem algumas ou todas as implementações padrão.

## <a name="prerequisites"></a>Pré-requisitos

Você precisará configurar sua máquina para executar o .NET Core, incluindo o compilador C# 8.0. O compilador C# 8.0 está disponível a partir da [versão 16.3 do Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), ou do [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) ou posterior.

## <a name="limitations-of-extension-methods"></a>Limitações dos métodos de extensão

Uma maneira de implementar o comportamento que aparece como parte de uma interface é definir métodos de [extensão](../programming-guide/classes-and-structs/extension-methods.md) que fornecem o comportamento padrão. As interfaces declaram um conjunto mínimo de membros, ao mesmo tempo em que fornecem uma área de superfície maior para qualquer classe que implemente essa interface. Por exemplo, os métodos de extensão fornecem <xref:System.Linq.Enumerable> a implementação para que qualquer seqüência seja a fonte de uma consulta LINQ.

Os métodos de extensão são resolvidos no momento da compilação, utilizando o tipo declarado da variável. As classes que implementam a interface podem fornecer uma melhor implementação para qualquer método de extensão. As declarações variáveis devem corresponder ao tipo de implementação para permitir que o compilador escolha essa implementação. Quando o tipo de tempo de compilação corresponde à interface, as chamadas do método resolvem para o método de extensão. Outra preocupação com os métodos de extensão é que esses métodos são acessíveis onde a classe que contém os métodos de extensão é acessível. As classes não podem declarar se devem ou não fornecer recursos declarados em métodos de extensão.

Começando com C# 8.0, você pode declarar as implementações padrão como métodos de interface. Em seguida, cada classe usa automaticamente a implementação padrão. Qualquer classe que possa fornecer uma melhor implementação pode substituir a definição do método de interface com um algoritmo melhor. Em certo sentido, essa técnica soa semelhante à forma como você poderia usar [métodos de extensão](../programming-guide/classes-and-structs/extension-methods.md).

Neste artigo, você aprenderá como implementações de interface padrão permitem novos cenários.

## <a name="design-the-application"></a>Projete o aplicativo

Considere um aplicativo de automação residencial. Você provavelmente tem muitos tipos diferentes de luzes e indicadores que poderiam ser usados em toda a casa. Todas as luzes devem apoiar as APIs para atilá-las e reportá-las e informar o estado atual. Algumas luzes e indicadores podem suportar outras características, tais como:

- Acenda a luz e desligue-a depois de um temporizador.
- Pisque a luz por um período de tempo.

Alguns desses recursos estendidos podem ser emulados em dispositivos que suportam o conjunto mínimo. Isso indica fornecer uma implementação padrão. Para aqueles dispositivos que têm mais recursos incorporados, o software do dispositivo usaria os recursos nativos. Para outras luzes, eles poderiam optar por implementar a interface e usar a implementação padrão.

Membros de interface padrão são uma solução melhor para este cenário do que métodos de extensão. Os autores de classe podem controlar quais interfaces eles escolhem implementar. Essas interfaces que eles escolhem estão disponíveis como métodos. Além disso, como os métodos de interface padrão são virtuais por padrão, o despacho de métodosempre escolhe a implementação na classe.

Vamos criar o código para demonstrar essas diferenças.

## <a name="create-interfaces"></a>Criar interfaces

Comece criando a interface que define o comportamento de todas as luzes:

[!code-csharp[Declare base interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetILightInterfaceV1)]

Uma luminária de sobrecarga básica pode implementar esta interface como mostrado no código a seguir:

[!code-csharp[First overhead light](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetOverheadLightV1)]

Neste tutorial, o código não conduz dispositivos IoT, mas emula essas atividades escrevendo mensagens para o console. Você pode explorar o código sem automatizar sua casa.

Em seguida, vamos definir a interface para uma luz que pode desligar automaticamente após um intervalo de tempo:

[!code-csharp[pure Timer interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetPureTimerInterface)]

Você pode adicionar uma implementação básica à luz aérea, mas uma `virtual` solução melhor é modificar essa definição de interface para fornecer uma implementação padrão:

[!code-csharp[Timer interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ITimerLight.cs?name=SnippetTimerLightFinal)]

Adicionando essa alteração, a `OverheadLight` classe pode implementar a função temporizador declarando suporte para a interface:

```csharp
public class OverheadLight : ITimerLight { }
```

Um tipo de luz diferente pode suportar um protocolo mais sofisticado. Ele pode fornecer sua `TurnOnFor`própria implementação para, como mostrado no seguinte código:

[!code-csharp[Override the timer function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/HalogenLight.cs?name=SnippetHalogenLight)]

Ao contrário de dominar métodos `TurnOnFor` de `HalogenLight` classe virtual, `override` a declaração da classe não usa a palavra-chave.

## <a name="mix-and-match-capabilities"></a>Misturar e combinar capacidades

As vantagens dos métodos de interface padrão tornam-se mais claras à medida que você introduz recursos mais avançados. O uso de interfaces permite misturar e combinar recursos. Ele também permite que cada autor de classe escolha entre a implementação padrão e uma implementação personalizada. Vamos adicionar uma interface com uma implementação padrão para uma luz piscando:

[!code-csharp[Define the blinking light interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/IBlinkingLight.cs?name=SnippetBlinkingLight)]

A implementação padrão permite que qualquer luz pisce. A luz de sobrecarga pode adicionar recursos de temporizador e piscar usando a implementação padrão:

[!code-csharp[Use the default blink function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/OverheadLight.cs?name=SnippetOverheadLight)]

Um novo tipo `LEDLight` de luz, suporta tanto a função do temporizador quanto a função blink diretamente. Este estilo de luz `ITimerLight` `IBlinkingLight` implementa as interfaces `Blink` e substitui o método:

[!code-csharp[Override the blink function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/LEDLight.cs?name=SnippetLEDLight)]

Um `ExtraFancyLight` pode suportar funções de piscar e temporizador diretamente:

[!code-csharp[Override the blink and timer function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ExtraFancyLight.cs?name=SnippetExtraFancyLight)]

O `HalogenLight` que você criou anteriormente não suporta piscar. Então, não adicione a `IBlinkingLight` lista de suas interfaces suportadas.

## <a name="detect-the-light-types-using-pattern-matching"></a>Detecte os tipos de luz usando correspondência de padrão

Em seguida, vamos escrever algum código de teste. Você pode fazer uso do recurso de correspondência de [padrões](../pattern-matching.md) de C#para determinar as capacidades de uma luz examinando quais interfaces ela suporta.  O método a seguir exerce as capacidades suportadas de cada luz:

[!code-csharp[Test a light's capabilities](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetTestLightFunctions)]

O código a `Main` seguir no seu método cria cada tipo de luz em seqüência e testa essa luz:

[!code-csharp[Test a light's capabilities](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetMainMethod)]

## <a name="how-the-compiler-determines-best-implementation"></a>Como o compilador determina a melhor implementação

Este cenário mostra uma interface base sem implementações. Adicionar um método `ILight` à interface introduz novas complexidades. As regras de idioma que regem os métodos de interface padrão minimizam o efeito nas classes concretas que implementam múltiplas interfaces derivadas. Vamos melhorar a interface original com um novo método para mostrar como isso muda seu uso. Cada luz indicadora pode relatar seu status de potência como um valor enumerado:

[!code-csharp[Enumeration for power status](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetPowerStatus)]

A implementação padrão não pressupõe energia:

[!code-csharp[Report a default power status](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetILightInterface)]

Essas alterações compilam de `ExtraFancyLight` forma limpa, `ILight` embora o suporte declarado `ITimerLight` para `IBlinkingLight`a interface e ambas as interfaces derivadas, e . Há apenas uma implementação "mais próxima" `ILight` declarada na interface. Qualquer classe que declarasse uma substituição se tornaria a implementação "mais próxima". Você viu exemplos nas classes anteriores que sobreporam os membros de outras interfaces derivadas.

Evite sobrepor o mesmo método em várias interfaces derivadas. Isso cria uma chamada de método ambígua sempre que uma classe implementa ambas as interfaces derivadas. O compilador não pode escolher um único método melhor, então ele emite um erro. Por exemplo, se `IBlinkingLight` `ITimerLight` o e implementado `PowerStatus`um `OverheadLight` sobreposição de , a necessidade de fornecer uma substituição mais específica. Caso contrário, o compilador não pode escolher entre as implementações nas duas interfaces derivadas. Você geralmente pode evitar essa situação mantendo as definições de interface pequenas e focadas em um recurso. Nesse cenário, cada capacidade de uma luz é sua própria interface; interfaces múltiplas são herdadas apenas por classes.

Esta amostra mostra um cenário onde você pode definir características discretas que podem ser misturadas em classes. Você declara qualquer conjunto de funcionalidades suportadas declarando quais interfaces uma classe suporta. O uso de métodos de interface padrão virtuais permite que as classes usem ou definam uma implementação diferente para qualquer ou todos os métodos de interface. Este recurso de linguagem fornece novas maneiras de modelar os sistemas do mundo real que você está construindo. Os métodos de interface padrão fornecem uma maneira mais clara de expressar classes relacionadas que podem misturar e combinar diferentes recursos usando implementações virtuais desses recursos.
