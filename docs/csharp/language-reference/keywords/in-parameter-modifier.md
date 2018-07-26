---
title: Modificador de parâmetro in (referência do C#)
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 58500cf2caa1446af6b663f1b765c0be92309f1d
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39198416"
---
# <a name="in-parameter-modifier-c-reference"></a>Modificador de parâmetro in (referência do C#)

A palavra-chave `in` faz com que os argumentos sejam passados por referência. É como as palavras-chave [ref](ref.md) ou [out](out-parameter-modifier.md), exceto que os argumentos `in` não podem ser modificados pelo método chamado. Enquanto os argumentos `ref` podem ser modificados, os argumentos `out` devem ser modificados pelo chamador, e será possível observar essas modificações no contexto da chamada.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

O exemplo anterior demonstra que o modificador `in` é geralmente desnecessário no site de chamada. Ele apenas é necessário na declaração do método.

> [!NOTE] 
> A palavra-chave `in` também pode ser usada com um parâmetro de tipo genérico para especificar que o parâmetro de tipo é contravariante, como parte de uma instrução `foreach` ou como parte de uma cláusula `join` em uma consulta LINQ. Para obter mais informações sobre o uso da palavra-chave `in` nesses contextos, confira [in](in.md) que fornece links para todos esses usos.
  
 As variáveis passadas como argumentos `in` precisam ser inicializadas antes de serem passadas em uma chamada de método. No entanto, o método chamado não pode atribuir um valor nem modificar o argumento.  
  
 Embora as palavras-chave `in`, `ref` e `out` causem um comportamento de tempo de execução diferente, elas não são consideradas parte da assinatura do método no tempo de compilação. Portanto, os métodos não poderão ser sobrecarregados se a única diferença for que um método usa um argumento `ref` ou `in` e o outro usa um argumento `out`. Por exemplo, o código a seguir, não será compilado:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
A sobrecarga com base na presença de `in` é permitida:  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a>Regras de resolução de sobrecarga

Você pode entender as regras de resolução de sobrecarga para métodos por valor versus argumentos `in`, compreendendo a motivação dos argumentos `in`. A definição de métodos usando parâmetros `in` é uma possível otimização de desempenho. Alguns argumentos de tipo `struct` podem ser grandes em tamanho e, quando os métodos são chamados em loops rígidos ou caminhos de código críticos, o custo da cópia dessas estruturas é crítico. Os métodos declaram parâmetros `in` para especificar que argumentos podem ser passados por referência com segurança porque o método chamado não modifica o estado desse argumento. A passagem desses argumentos por referência evita a cópia (possivelmente) dispendiosa. 

A especificação de `in` em argumentos no site de chamada é normalmente opcional. Não há diferença semântica entre passar argumentos por valor e transmiti-los por meio de referência usando o modificador `in`. O modificador `in` no site de chamada é opcional, pois não é necessário indicar que o valor do argumento pode ser alterado. Você adiciona explicitamente o modificador `in` no site de chamada para garantir que o argumento seja passado por referência, e não por valor. O uso explícito de `in` tem dois efeitos:

Primeiro: especificar `in` no site de chamada força o compilador a selecionar um método definido com um parâmetro `in` correspondente. Caso contrário, quando dois métodos diferem apenas na presença de `in`, a sobrecarga por valor é uma correspondência melhor.

Segundo: especificar `in` declara sua intenção de passar um argumento por referência. O argumento usado com `in` deve representar um local ao qual se possa fazer referência diretamente. As mesmas regras gerais para argumentos `out` e `ref` se aplicam: você não pode usar constantes, propriedades comuns ou outras expressões que produzem valores. Caso contrário, a omissão de `in` no site de chamada informa ao compilador que você permitirá a criação de uma variável temporária para passar por referência de somente leitura para o método. O compilador cria uma variável temporária para superar várias restrições com argumentos `in`:

- Uma variável temporária permite constantes de tempo de compilação como parâmetros `in`.
- Uma variável temporária permite propriedades ou outras expressões para parâmetros `in`.
- Uma variável temporária permite argumentos em que há uma conversão implícita do tipo de argumento para o tipo de parâmetro.

Em todas as instâncias anteriores, o compilador cria uma variável temporária que armazena o valor da constante, da propriedade ou de outra expressão.

O código a seguir ilustra essas regras:

```csharp
static void Method(in int argument)
{
    // implementation removed
}

Method(5); // OK, temporary variable created.
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // OK, temporary int created with the value 0
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // passed by readonly reference
Method(in i); // passed by readonly reference, explicitly using `in`
```

Agora, vamos supor que outro método usando argumentos por valor estivesse disponível. Os resultados são alterados conforme mostrado no código a seguir:

```csharp
static void Method(int argument)
{
    // implementation removed
}

static void Method(in int argument)
{
    // implementation removed
}

Method(5); // Calls overload passed by value
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // Calls overload passed by value.
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // Calls overload passed by value
Method(in i); // passed by readonly reference, explicitly using `in`
```

A única chamada de método em que o argumento é passado por referência é a chamada final.

> [!NOTE]
> O código anterior usa `int` como o tipo de argumento por questão de simplicidade. Como `int` não é maior que uma referência na maioria dos computadores modernos, não há nenhum benefício em passar um único `int` como uma referência readonly. 

## <a name="limitations-on-in-parameters"></a>Limitações em parâmetros `in`

Não é possível usar as palavras-chave `in`, `ref` e `out` para os seguintes tipos de métodos:  
  
- Métodos assíncronos, que você define usando o modificador [async](async.md).  
- Métodos de iterador, que incluem uma instrução [yield return](yield.md) ou `yield break`.  

## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../index.md)  
 [Guia de Programação em C#](../../programming-guide/index.md)  
 [Palavras-chave do C#](index.md)  
 [Parâmetros de método](method-parameters.md) [Semântica de referência com Tipos de valor](../../reference-semantics-with-value-types.md)
