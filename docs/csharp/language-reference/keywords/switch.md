---
title: "Palavra-chave switch (Referência de C#)"
ms.date: 03/07/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
caps.latest.revision: "47"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 66528c9804b74b0bba088627b3116be804c65eb0
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2017
---
# <a name="switch-c-reference"></a>switch (Referência de C#)
`switch` é uma instrução de seleção que escolhe uma única *seção switch* para ser executada de uma lista de candidatas com base em uma correspondência de padrão com a *expressão de correspondência*. 
  
 [!code-cs[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]  

A instrução `switch` geralmente é usada como uma alternativa para um constructo [if-else](if-else.md) se uma única expressão é testada com três ou mais condições. Por exemplo, a instrução `switch` a seguir determina se uma variável do tipo `Color` tem um dos três valores: 

[!code-cs[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)] 

Ele é equivalente ao exemplo a seguir que usa um constructo `if`-`else`. 

[!code-cs[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)] 

## <a name="the-match-expression"></a>A expressão de correspondência

A expressão de correspondência fornece o valor para corresponder aos padrões nos rótulos `case`. A sintaxe é:

```csharp
   switch (expr)
```

No C# 6, a expressão de correspondência deve ser uma expressão que retorna um valor dos seguintes tipos:

- um [char](char.md).
- um [string](string.md).
- um [bool](bool.md). 
- um valor de inteiro, como um [int](int.md) ou um [long](long.md).
- um valor [enum](enum.md).

Começando com o C# 7, a expressão de correspondência pode ser qualquer expressão não nula.
 
## <a name="the-switch-section"></a>A seção switch
 
 Uma instrução `switch` inclui uma ou mais seções do comutador. Cada seção switch contém um ou mais *rótulos case* seguidos por uma ou mais instruções. O exemplo a seguir mostra uma instrução `switch` simples que tem três seções switch. Cada seção switch tem um rótulo case, como `case 1:` e duas instruções.
 
  Uma instrução `switch` pode incluir qualquer número de seções switch e cada seção pode ter um ou mais rótulos case, conforme mostrado no exemplo a seguir. No entanto, dois rótulos case não podem conter a mesma expressão.  

 [!code-cs[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]  

 Apenas uma seção switch em uma instrução switch é executada. O C# não permite que a execução continue de uma seção switch para a próxima. Por isso, o código a seguir gera um erro do compilador, CS0163: "O controle não pode passar de um rótulo case (<case label>) para outro".   

```csharp  
switch (caseSwitch)  
{  
    // The following switch section causes an error.  
    case 1:  
        Console.WriteLine("Case 1...");  
        // Add a break or other jump statement here.  
    case 2:  
        Console.WriteLine("... and/or Case 2");  
        break;  
}  
```  
Esse requisito é atendido normalmente saindo explicitamente da seção switch usando uma instrução [break](break.md), [goto](goto.md) ou [return](return.md). No entanto, o código a seguir também é válido, pois garante que o controle do programa não pode passar para a seção switch `default`.
  
 [!code-cs[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]    
  
 A execução da lista de instruções na seção switch com um rótulo case que corresponde à expressão de correspondência começa com a primeira instrução e continua pela lista de instruções, normalmente até uma instrução de salto como `break`, `goto case`, `goto label`, `return` ou `throw` ser atingida. Nesse ponto, o controle é transferido para fora da instrução `switch` ou para outro rótulo case. Se uma instrução `goto` for usada, ela deverá transferir controle para um rótulo de constante. Essa restrição é necessária, já que tentar transferir o controle para um rótulo não constante pode ter efeitos colaterais indesejáveis, tais como transferência do controle para um local não intencional no código ou criação de um loop infinito.

## <a name="case-labels"></a>Rótulos case

 Cada rótulo case especifica um padrão a ser comparado com a expressão de correspondência (a variável `caseSwitch` nos exemplos anteriores). Se eles corresponderem, o controle será transferido para a seção switch que contém o **primeiro** rótulo case correspondente. Se nenhum padrão de rótulo de caso corresponder à expressão de correspondência, o controle será transferido para a seção com o rótulo de caso `default`, se existir algum. Se não houver nenhum case `default`, nenhuma declaração em qualquer seção switch será executada e o controle será transferido para fora da instrução `switch`.

 Para obter informações sobre a instrução `switch` e a correspondência de padrões, consulte a seção [Correspondência de padrões com a instrução `switch`](#pattern).

 Como o C# 6 dá suporte apenas ao padrão de constante e não permite a repetição de valores de constantes, os rótulos case definem valores mutuamente exclusivos e apenas um padrão pode corresponder à expressão de correspondência. Como resultado, a ordem na qual as instruções `case` aparecem não é importante.

 No C# 7, no entanto, como outros padrões têm suporte, os rótulos case não precisam definir valores mutuamente exclusivos e vários padrões podem corresponder à expressão de correspondência. Como apenas as instruções na seção switch que contém o primeiro padrão de correspondência são executadas, a ordem na qual as instruções `case` aparecem agora é importante. Se o C# detecta uma seção switch cujas instruções case são equivalentes ou são subconjuntos de instruções anteriores, ele gera um erro do compilador, CS8120, “O switch case já foi tratado por um case anterior”. 

 O exemplo a seguir ilustra uma instrução `switch` que usa uma variedade de padrões não mutuamente exclusivos. Se você mover a seção switch `case 0:` para que ela não seja mais a primeira seção na instrução `switch`, o C# gera um erro do compilador porque um inteiro cujo valor é zero é um subconjunto de todos os inteiros, que é o padrão definido pela instrução `case int val`.

 [!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]    

Você pode corrigir esse problema e eliminar o aviso do compilador em uma das duas maneiras:

- Alterando a ordem das seções switch. 
 
- Usando uma </a name="when">cláusula when</a> no rótulo `case`.
 
## <a name="the-default-case"></a>O case `default`

O case `default` especifica a seção switch a ser executada se a expressão de correspondência não corresponder a nenhum outro rótulo `case`. Se um case `default` não estiver presente e a expressão de correspondência não corresponder a nenhum outro rótulo `case`, o fluxo do programa passará pela instrução `switch`.

O case `default` pode aparecer em qualquer ordem na instrução `switch`. Independentemente de sua ordem no código-fonte, ele é sempre avaliado por último, afinal os rótulos `case` foram avaliados.

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><a name="pattern" /> Correspondência de padrões com a instrução `switch`
  
Cada instrução `case` define um padrão que, se corresponde à expressão de correspondência, faz com que sua seção switch recipiente seja executada. Todas as versões do C# dão suporte ao padrão de constante. Os padrões restantes têm suporte a partir do C# 7. 
  
### <a name="constant-pattern"></a>Padrão de constante 

O padrão de constante testa se a expressão de correspondência é igual a uma constante especificada. A sintaxe é:

```csharp
   case constant:
```

em que *constant* é o valor para testar. *constant* pode ser qualquer uma das expressões de constante a seguir: 

- Um literal [bool](bool.md), `true` ou `false`.
- Qualquer constante integral, como um [int](int.md), um [long](long.md) ou um [byte](byte.md). 
- O nome de uma variável `const` declarada.
- Uma constante de enumeração.
- Um literal [char](char.md).
- Um literal [string](string.md).

A expressão de constante é avaliada da seguinte forma:

- Se *expr* e *constant* forem tipos integrais, o operador de igualdade de C# determinará se a expressão retorna `true` (ou seja, se `expr == constant`).

- Caso contrário, o valor da expressão será determinado por uma chamada ao método estático [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)).  

O exemplo a seguir usa o padrão de constante para determinar se uma data específica é um final de semana, o primeiro dia, o último dia ou o meio da semana de trabalho. Ele avalia a propriedade <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> do dia atual em relação aos membros da enumeração <xref:System.DayOfWeek>. 

[!code-cs[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

O exemplo a seguir usa o padrão de constante para manipular a entrada do usuário em um aplicativo de console que simula uma máquina de café automática.
  
 [!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]  

### <a name="type-pattern"></a>Padrão de tipo

O padrão de tipo permite a conversão e a avaliação do tipo concisa. Quando usado com a instrução `switch` para realizar a correspondência de padrões, testa se uma expressão pode ser convertida para um tipo especificado e, se puder, o converte em uma variável desse tipo. A sintaxe é:

```csharp
   case type varname 
```
em que *type* é o nome do tipo no qual o resultado de *expr* deverá ser convertido e *varname* é o objeto para o qual o resultado de *expr* é convertido se a correspondência é bem-sucedida. 

A expressão `case` será `true` se qualquer uma das condições seguintes for verdadeira:

- *expr* for uma instância do mesmo tipo que *type*.

- *expr* for uma instância de um tipo derivado de *type*. Em outras palavras, o resultado de *expr* pode sofrer upcast para uma instância de *type*.

- *expr* tem um tipo de tempo de compilação que é uma classe base de *type* e *expr* tem um tipo de tempo de execução que é *type* ou é derivado de *type*. O *tipo do tempo de compilação* de uma variável é o tipo da variável conforme definido em sua declaração de tipo. O *tipo de tempo de execução* de uma variável é o tipo da instância atribuída a essa variável.

- *expr* é uma instância de um tipo que implementa a interface de *type*.

Se a expressão case for true, *varname* será definitivamente atribuído e terá o escopo local dentro da seção switch apenas.

Observe que `null` não corresponde a um tipo. Para corresponder um `null`, use o seguinte rótulo `case`:

```csharp
case null:
```
 
O exemplo a seguir usa o padrão de tipo para fornecer informações sobre vários tipos de coleção.

[!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

Sem a correspondência de padrões, esse código pode ser escrito da seguinte maneira. O uso da correspondência de padrões de tipo produz um código mais compacto e legível eliminando a necessidade de testar se o resultado de uma conversão é um `null` ou executar conversões repetidas.  

[!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a>A instrução `case` e a cláusula `when`

A partir do C# 7, como as instruções case não precisam ser mutuamente exclusivas, você pode usar a adição de uma cláusula `when` para especificar uma condição adicional que deve ser atendida para a instrução case ser avaliada como true. A cláusula `when` pode ser qualquer expressão que retorna um valor booliano. Um dos usos mais comuns para a cláusula `when` é para impedir que uma seção switch seja executada quando o valor de uma expressão de correspondência é `null`. 

 O exemplo a seguir define uma classe `Shape` base, uma classe `Rectangle` que deriva de `Shape` e uma classe `Square` que deriva de `Rectangle`. Ele usa a cláusula `when` para garantir que o trata `ShowShapeInfo` um objeto `Rectangle` que recebeu comprimentos e larguras como um `Square` mesmo se ele não tiver sido instanciado como um objeto `Square`. O método não tenta exibir informações a sobre um objeto que é `null` ou uma forma cuja área é zero. 

[!code-cs[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]
  
Observe que a cláusula `when` no exemplo que tenta testar se um objeto `Shape` é `null` não é executada. O padrão de tipo correto para testar um `null` é `case null:`.

## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](../../../../includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  

 [Referência de C#](../index.md)   
 [Guia de Programação em C#](../../programming-guide/index.md)   
 [Palavras-chave de C#](index.md)   
 [if-else](if-else.md)   
 [Correspondência Padrão](../../pattern-matching.md)   
 

 
