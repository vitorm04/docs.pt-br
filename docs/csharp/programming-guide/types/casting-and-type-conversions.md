---
title: "Convers&#245;es cast e convers&#245;es de tipo (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "conversão [C#]"
  - "conversões [C#], tipo"
  - "convertendo tipos [C#]"
  - "conversão de tipo de dados [C#]"
  - "conversões numéricas [C#]"
  - "conversão de tipo [C#]"
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
caps.latest.revision: 52
caps.handback.revision: 52
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Convers&#245;es cast e convers&#245;es de tipo (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Como o C\# é estaticamente tipado no momento de compilar, após uma variável ser declarada, ela não pode ser declarada novamente ou usada para armazenar valores de outro tipo a menos que esse tipo seja conversível para o tipo da variável.  Por exemplo, não há nenhuma conversão de um número inteiro para qualquer seqüência de caracteres arbitrária.  Portanto, após declarar `i` como um inteiro, você não pode atribuir a seqüência de caracteres "Hello", conforme é mostrado no código a seguir.  
  
```c#  
int i;  
i = "Hello"; // Error: "Cannot implicitly convert type 'string' to 'int'"  
```  
  
 No entanto, às vezes, talvez seja necessário copiar um valor para um parâmetro de método ou variável de outro tipo.  Por exemplo, você pode ter uma variável integer que você precisa passar para um método cujo parâmetro é digitado como `double`.  Ou talvez você precise atribuir uma variável de classe a uma variável de um tipo de interface.  Esses tipos de operações são chamados de  *as conversões de tipo*.  Na C\#, você pode realizar os seguintes tipos de conversões:  
  
-   **Conversões implícitas**: nenhuma sintaxe especial é necessária porque a conversão é o tipo de seguro e nenhum dado será perdido.  Exemplos incluem conversões de tipos menores para maiores e conversões de classes derivadas para classes base.  
  
-   **Conversões explícitas \(projeções\)**: conversões explícitas exigem um operador cast.  A conversão é necessária quando as informações podem ser perdidas na conversão, ou quando a conversão talvez não seja bem\-sucedida por outros motivos.  Exemplos típicos incluem conversão numérica para um tipo que possui a menor precisão ou um intervalo menor e conversão de uma instância da classe base para uma classe derivada.  
  
-   **Conversões definidas pelo usuário**: conversões definidas pelo usuário são realizadas por métodos especiais que podem ser definidas para permitir conversões explícitas e implícitas entre tipos personalizados que não têm uma relação de classe base class–derived.  Para obter mais informações, consulte [Operadores de conversão](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).  
  
-   **Conversões com classes auxiliares**: para converter entre tipos de não\-compatíveis, como, por exemplo, inteiros e <xref:System.DateTime?displayProperty=fullName> objetos, ou seqüências de caracteres hexadecimais e matrizes de bytes, você pode usar o <xref:System.BitConverter?displayProperty=fullName> classe, o <xref:System.Convert?displayProperty=fullName> classe e o `Parse` tipos de métodos para o valor numérico que internos, como <xref:System.Int32.Parse%2A?displayProperty=fullName>.  Para obter mais informações, consulte [Como converter uma matriz de bytes em um int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md),  [Como converter uma cadeia de caracteres em um número](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md) e [Como converter entre cadeias de caracteres hexadecimais e tipos numéricos](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).  
  
## Conversões implícitas  
 Para tipos numéricos internos \(ou primitivos\), uma conversão implícita pode ser feita quando o valor a ser armazenado puder caber na varíavel, sem ser truncado ou arredondado.  Por exemplo, uma variável do tipo  [longo](../../../csharp/language-reference/keywords/long.md) \(inteiro de 8 bytes\) pode armazenar qualquer valor que uma  [int](../../../csharp/language-reference/keywords/int.md) \(4 bytes em um computador de 32 bits\) pode armazenar.  No exemplo a seguir, o compilador converte implicitamente o valor à direita para um tipo de `long` antes de atribuí\-lo para `bigNum`.  
  
 [!code-cs[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_1.cs)]  
  
 Para obter uma lista completa de todas as conversões implícitas de numéricas, consulte [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
 Tipos de referência, uma conversão implícita sempre existe de uma classe para qualquer uma das suas interfaces ou classes base diretas ou indiretas.  Nenhuma sintaxe especial é necessária porque uma classe derivada sempre contém todos os membros de uma classe base.  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## Conversões explícitas  
 No entanto, se uma conversão não pode ser feita sem um risco de perda de informações, o compilador requer que você executa uma conversão explícita, o que é chamada de um  *cast*.  A projeção é uma maneira de informar explicitamente o compilador que você pretende fazer a conversão e que você está ciente de que pode ocorrer perda de dados.  Para executar uma conversão, especifique o tipo que são a projeção para entre parênteses na frente do valor ou variável a ser convertido.  O seguinte programa projeções de um  [double](../../../csharp/language-reference/keywords/double.md) para um  [int](../../../csharp/language-reference/keywords/int.md).  O programa não será compilado sem a projeção.  
  
 [!code-cs[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_2.cs)]  
  
 Para obter uma lista as conversões explícitas numéricas permitidos, consulte [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
 Para tipos de referência, uma conversão explícita é necessária se você precisar converter de um tipo base para um tipo derivado:  
  
```c#  
// Create a new derived type.  
Giraffe g = new Giraffe();  
  
// Implicit conversion to base type is safe.  
Animal a = g;  
  
// Explicit conversion is required to cast back  
// to derived type. Note: This will compile but will  
// throw an exception at run time if the right-side  
// object is not in fact a Giraffe.  
Giraffe g2 = (Giraffe) a;  
```  
  
 Uma operação de conversão entre tipos de referência não altera o tipo de tempo de execução do objeto subjacente; ele apenas altera o tipo do valor que está sendo usado como uma referência a esse objeto.  Para obter mais informações, consulte [Polimorfismo](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## Exceções de conversão de tipo em tempo de execução  
 Em algumas conversões de tipo de referência, o compilador não pode determinar se um elenco será válido.  É possível que uma operação de conversão que compile corretamente a falhar em tempo de execução.  Conforme mostrado no exemplo a seguir, um tipo de projeção que falhar em tempo de execução fará com que uma <xref:System.InvalidCastException> seja lançada.  
  
 [!code-cs[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_3.cs)]  
  
 C\# fornece a  [é](../../../csharp/language-reference/keywords/is.md) e  [como](../../../csharp/language-reference/keywords/as.md) operadores para que você possa testar a compatibilidade antes de realmente executar uma conversão.  Para obter mais informações, consulte [Como executar conversão cast com segurança usando operadores as e is](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md).  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Capítulo do livro em destaque  
 [Mais informações sobre variáveis de](http://go.microsoft.com/fwlink/?LinkId=221230) na [início 2010 do Visual C\#](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Tipos](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Operador \(\)](../../../csharp/language-reference/operators/invocation-operator.md)   
 [explicit](../../../csharp/language-reference/keywords/explicit.md)   
 [implicit](../../../csharp/language-reference/keywords/implicit.md)   
 [Operadores de conversão](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)   
 [Generalized Type Conversion](../Topic/Generalized%20Type%20Conversion.md)   
 [Exported Type Conversion](http://msdn.microsoft.com/pt-br/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b)   
 [Como converter uma cadeia de caracteres em um número](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)