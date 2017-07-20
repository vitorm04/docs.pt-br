---
title: "Argumentos de linha de comando e Main() (Guia de programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
dev_langs:
- CSharp
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: eb1d380ee4dfd64081d8fe36880a06e3a450f639
ms.contentlocale: pt-br
ms.lasthandoff: 05/26/2017

---
<a id="main-and-command-line-arguments-c-programming-guide" class="xliff"></a>

# Main() e argumentos de linha de comando (Guia de Programação em C#)
O método `Main` é o ponto de entrada de um aplicativo de console C# ou aplicativo do Windows. (Bibliotecas e serviços não exigem um método `Main` como um ponto de entrada.) Quando o aplicativo é iniciado, o método `Main` é o primeiro método invocado.  
  
 Pode haver apenas um ponto de entrada em um programa C#. Se tiver mais de uma classe que tenha um `Main` método, você deverá compilar seu programa com a opção do compilador **/main** para especificar qual método `Main` será usado como ponto de entrada. Para obter mais informações, consulte [/main (opções do compilador C#)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).  
  
 [!code-cs[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]  
  
<a id="overview" class="xliff"></a>

## Visão geral  
  
-   O método `Main` é o ponto de entrada de um programa .exe; é onde o controle do programa começa e termina.  
  
-   `Main` é declarado dentro de uma classe ou struct. `Main` deve ser [estático](../../../csharp/language-reference/keywords/static.md) e não deve ser [público](../../../csharp/language-reference/keywords/public.md). (No exemplo anterior, ele recebe o acesso padrão de [particular](../../../csharp/language-reference/keywords/private.md).) A classe delimitadora ou struct não deve ser estático.  
  
-   `Main` pode ter um `void` ou o tipo de retorno `int`.  
  
-   O método `Main` pode ser declarado com ou sem um parâmetro `string[]` que contém os argumentos de linha de comando. Ao usar o [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] para criar aplicativos do Windows Forms, você pode adicionar o parâmetro manualmente ou usar a classe <xref:System.Environment> para obter os argumentos de linha de comando. Os parâmetros são lidos como argumentos de linha de comando indexados por zero. Ao contrário de C e C++, o nome do programa não é tratado como o primeiro argumento de linha de comando.  
  
<a id="in-this-section" class="xliff"></a>

## Nesta seção  
  
-   [Argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
  
-   [Como exibir argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
  
-   [Como acessar argumentos de linha de comando usando foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
  
-   [Valores de retorno de Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)  
  
<a id="c-language-specification" class="xliff"></a>

## Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
<a id="see-also" class="xliff"></a>

## Consulte também  
 [Compilação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [Guia de programação em C#](../../../csharp/programming-guide/index.md)   
 [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [Por dentro de um programa em C#](../../../csharp/programming-guide/inside-a-program/index.md)   
 [\<Aplicativos de exemplo do paveover>C#](http://msdn.microsoft.com/en-us/9a9d7aaa-51d3-4224-b564-95409b0f3e15)
