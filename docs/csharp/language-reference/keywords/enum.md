---
title: "enum (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "enum"
  - "enum_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave enum [C#]"
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
caps.latest.revision: 36
caps.handback.revision: 36
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# enum (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `enum` palavra\-chave é usada para declarar uma enumeração, um tipo distinto que consiste em um conjunto de constantes nomeadas denominada lista de enumerador.  
  
 Geralmente é melhor definir um enum dentro de um namespace para que todas as classes no namespace possam acessá\-lo com a conveniência de igual.  No entanto, um enum também pode ser aninhado em class ou struct.  
  
 Por padrão, o primeiro enumerador tem o valor 0 e o valor de cada enumerador sucessiva aumenta em 1.  Por exemplo, na enumeração seguinte, `Sat` é `0`, `Sun` é `1`, `Mon` é `2`, e assim por diante.  
  
```  
  
enum Days {Sat, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 Enumeradores podem usar os inicializadores para substituir os valores padrão, conforme mostrado no exemplo a seguir.  
  
```  
  
enum Days {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 Desta enumeração, a seqüência dos elementos é forçada para iniciar a partir de `1` em vez de `0`.  No entanto, incluindo uma constante que tem o valor 0 é recomendado.  Para obter mais informações, consulte [Tipos de enumeração](../../../csharp/programming-guide/enumeration-types.md).  
  
 Cada tipo de enumeração tem um tipo subjacente, o que pode ser qualquer tipo integral, exceto  [char](../../../csharp/language-reference/keywords/char.md).  O tipo subjacente de elementos de enumeração de padrão é  [int](../../../csharp/language-reference/keywords/int.md).  Para declarar um enum de outro tipo integral, tais como  [bytes](../../../csharp/language-reference/keywords/byte.md), use uma vírgula após o identificador seguido do tipo, conforme mostrado no exemplo a seguir.  
  
```  
  
enum Days : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 The approved types for an enum are `byte`, [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
 Uma variável do tipo `Days` pode ser atribuído qualquer valor no intervalo do tipo subjacente; os valores não são limitados às constantes nomeadas.  
  
 O valor padrão de um `enum E` é o valor produzido pela expressão `(E)0`.  
  
> [!NOTE]
>  Um enumerador não pode conter espaços em branco em seu nome.  
  
 O tipo subjacente Especifica a quantidade de armazenamento é alocado para cada enumerador.  No entanto, uma conversão explícita é necessário converter de `enum` tipo de tipo integral.  Por exemplo, a instrução a seguir atribui o enumerador `Sun` a uma variável do tipo  [int](../../../csharp/language-reference/keywords/int.md) , usando uma conversão para converter de `enum` para `int`.  
  
```  
  
int x = (int)Days.Sun;  
```  
  
 Quando você aplica <xref:System.FlagsAttribute?displayProperty=fullName> em uma enumeração que contém elementos que podem ser combinados com um bit a bit `OR` operação, o atributo afeta o comportamento da `enum` quando ele é usado com algumas ferramentas.  Você pode observar essas alterações quando você usa ferramentas como o <xref:System.Console> o avaliador da expressão e métodos de classe.  \(Consulte o terceiro exemplo\).  
  
## Programação robusta  
 Assim como acontece com qualquer constante, todas as referências para os valores individuais de um enum são convertidas em literais numéricos em tempo de compilação.  Isso pode criar possíveis problemas de versionamento, conforme descrito em [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md).  
  
 Atribuindo valores adicionais para novas versões de enums ou alterando os valores dos membros enum em uma nova versão, pode causar problemas para o código\-fonte dependentes.  Valores de enumeração são freqüentemente usados em  [Alternar](../../../csharp/language-reference/keywords/switch.md) instruções.  Se os elementos adicionais foram adicionados para o `enum` pode ser selecionado o tipo, a seção padrão da instrução switch inesperadamente.  
  
 Se outros desenvolvedores usam seu código, você deve fornecer diretrizes sobre como o seu código deve reagir se novos elementos são adicionados a qualquer `enum` tipos.  
  
## Exemplo  
 No exemplo a seguir, uma enumeração, `Days`, é declarada.  Dois enumeradores explicitamente são convertidas em inteiro e atribuídos a variáveis de inteiro.  
  
 [!CODE [csrefKeywordsTypes#10](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#10)]  
  
## Exemplo  
 No exemplo a seguir, a opção tipo de base é usada para declarar um `enum` cujos membros são do tipo `long`.  Observe que, mesmo que o tipo subjacente da enumeração `long`, os membros de enumeração ainda devem ser explicitamente convertidos no tipo `long` usando a projeção.  
  
 [!CODE [csrefKeywordsTypes#11](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#11)]  
  
## Exemplo  
 O exemplo de código a seguir ilustra o uso e o efeito do <xref:System.FlagsAttribute?displayProperty=fullName> de atributo em um `enum` declaração.  
  
 [!CODE [csrefKeywordsTypes#12](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#12)]  
  
## Comentários  
 Se você remover `Flags`, o exemplo exibe os seguintes valores:  
  
 `5`  
  
 `5`  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Tipos de enumeração](../../../csharp/programming-guide/enumeration-types.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)