---
title: enum (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 9714277f87095b709e37b582cd3435374d9a1555
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2018
---
# <a name="enum-c-reference"></a>enum (Referência de C#)
A palavra-chave `enum` é usada para declarar uma enumeração, um tipo distinto que consiste em um conjunto de constantes nomeadas denominado lista de enumeradores.  
  
 Normalmente, é melhor definir um enum diretamente dentro de um namespace para que todas as classes no namespace possam acessá-lo com a mesma conveniência. No entanto, um enum também pode ser aninhado dentro de uma classe ou struct.  
  
 Por padrão, o primeiro enumerador tem o valor 0 e o valor de cada enumerador seguinte é aumentado em 1. Por exemplo, na seguinte enumeração, `Sat` é `0`, `Sun` é `1`, `Mon` é `2` e assim por diante.  
  
```csharp  
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 Enumeradores podem usar inicializadores para substituir os valores padrão, conforme mostrado no exemplo a seguir.  
  
```csharp  
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 Nesta enumeração, a sequência de elementos é forçada a iniciar a partir de `1` em vez de `0`. No entanto, incluir uma constante que tenha o valor de 0 é recomendado. Para obter mais informações, consulte [Tipos de enumeração](../../../csharp/programming-guide/enumeration-types.md).  
  
 Cada tipo de enumeração tem um tipo subjacente, que pode ser qualquer tipo integral exceto por [char](../../../csharp/language-reference/keywords/char.md). O tipo subjacente padrão dos elementos de enumeração é [int](../../../csharp/language-reference/keywords/int.md). Para declarar um enum de outro tipo integral, como [bytes](../../../csharp/language-reference/keywords/byte.md), use uma vírgula após o identificador seguida pelo tipo, conforme mostrado no exemplo a seguir.  
  
```csharp  
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 Os tipos aprovados para um enum são [byte](../../../csharp/language-reference/keywords/byte.md), [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
 Qualquer valor no intervalo do tipo subjacente pode ser atribuído a uma variável do tipo `Day`; os valores não são limitados às constantes nomeadas.  
  
 O valor padrão de um `enum E` é o valor produzido pela expressão `(E)0`.  
  
> [!NOTE]
>  Um enumerador não pode conter espaços em branco em seu nome.  
  
 O tipo subjacente especifica quanto armazenamento é alocado para cada enumerador. No entanto, uma conversão explícita é necessária para converter de um tipo `enum` em um tipo integral. Por exemplo, a instrução a seguir atribui o enumerador `Sun` a uma variável do tipo [int](../../../csharp/language-reference/keywords/int.md) usando uma conversão para converter de `enum` em `int`.  
  
```csharp  
int x = (int)Day.Sun;  
```  
  
 Quando você aplica <xref:System.FlagsAttribute?displayProperty=nameWithType> a uma enumeração que contém elementos que podem ser combinados com uma operação `OR` bit a bit, o atributo afeta o comportamento do `enum` quando ele é usado com algumas ferramentas. Você pode observar essas alterações quando usa ferramentas como os métodos da classe <xref:System.Console> e o Avaliador de Expressão. (Consulte o terceiro exemplo.)  
  
## <a name="robust-programming"></a>Programação robusta  
 Assim como ocorre com qualquer constante, todas as referências aos valores individuais de um enum são convertidas em literais numéricos em tempo de compilação. Isso pode criar problemas de controle de versão, conforme descrito em [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md).  
  
 Atribuir valores adicionais a novas versões de enums ou alterar os valores dos membros de enum em uma nova versão pode causar problemas para códigos-fonte dependentes. Valores de enum frequentemente são usados em instruções [switch](../../../csharp/language-reference/keywords/switch.md). Se elementos adicionais tiverem sido adicionados ao tipo `enum`, a seção padrão da instrução switch pode ser selecionada inesperadamente.  
  
 Se outros desenvolvedores usarem seu código, você deverá fornecer diretrizes sobre como seu código deve reagir se novos elementos forem adicionados a qualquer tipo `enum`.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, uma enumeração, `Day`, é declarada. Dois enumeradores são convertidos explicitamente em inteiros e atribuídos a variáveis de inteiro.  
  
 [!code-csharp[csrefKeywordsTypes#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_1.cs)]  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, a opção de tipo base é usada para declarar uma `enum` cujos membros são do tipo `long`. Observe que, mesmo que o tipo subjacente da enumeração seja `long`, os membros da enumeração ainda devem ser convertidos explicitamente no tipo `long` usando uma conversão.  
  
 [!code-csharp[csrefKeywordsTypes#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_2.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir ilustra o uso e o efeito do atributo <xref:System.FlagsAttribute?displayProperty=nameWithType> em uma declaração `enum`.  
  
 [!code-csharp[csrefKeywordsTypes#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_3.cs)]  
  
## <a name="comments"></a>Comentários  
 Se você remover `Flags`, o exemplo exibirá os seguintes valores:  
  
 `5`  
  
 `5`  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Tipos de enumeração](../../../csharp/programming-guide/enumeration-types.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [Convenções de Nomenclatura do Enum](https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-classes-structs-and-interfaces#naming-enumerations)
