---
title: "Main() e argumentos de linha de comando (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS5001"
  - "main_CSharpKeyword"
  - "Main"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "argumentos [C#], linha de comando"
  - "Linguagem C#, argumentos de linha de comando"
  - "linha de comando [C#], argumentos"
  - "argumentos de linha de comando [C#], método Main"
  - "Método Main [C#]"
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
caps.latest.revision: 30
caps.handback.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Main() e argumentos de linha de comando (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O método de`Main` é o ponto de entrada de um aplicativo de console C\# ou de um aplicativo do windows.  \(As bibliotecas e serviços não requerem um método de `Main` como um ponto de entrada.\).  Quando o aplicativo for iniciado, o método de `Main` é o primeiro método que é chamado.  
  
 Pode haver apenas um ponto de entrada em um programa C\#.  Se você tiver mais de uma classe que tem um método de `Main` , você deve compilar o programa com a opção de compilador **\/main** especificar qual método de `Main` para usar como ponto de entrada.  Para obter mais informações, consulte [\/main \(Specify Location of Main Method\)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).  
  
 [!code-cs[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]  
  
## Visão Geral  
  
-   O método de `Main` é o ponto de entrada de um programa .exe; é onde o é iniciado e termina de controle de programa.  
  
-   `Main` é declarado em uma classe ou estrutura.  `Main` deve ser [static](../../../csharp/language-reference/keywords/static.md) e não deve ser [público](../../../csharp/language-reference/keywords/public.md).  \(No exemplo anterior, recebe acesso padrão de [private](../../../csharp/language-reference/keywords/private.md).\) A classe ou estrutura o delimitador não precisam ser estático.  
  
-   `Main` enlata tem um tipo de retorno de `void` ou de `int` .  
  
-   O método de `Main` pode ser declarado com ou sem parâmetro de `string[]` que contém argumentos de linha de comando.  Ao usar [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] para criar aplicativos de formulários do Windows, você pode adicionar manualmente o parâmetro ou usar a classe de <xref:System.Environment> para obter os argumentos de linha de comando.  Os parâmetros são lidos como argumentos de linha de comando indexados zero. Diferentemente de C e C\+\+, o nome do programa não é tratado como o primeiro argumento de linha de comando.  
  
## Nesta seção  
  
-   [Argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
  
-   [Como exibir argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
  
-   [Como acessar argumentos de linha de comando usando foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
  
-   [Valores de retorno de Main\(\)](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Command\-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Métodos](../../../fsharp/language-reference/members/methods.md)   
 [Por dentro de um programa em C\#](../../../csharp/programming-guide/inside-a-program/index.md)   
 [Aplicativos C\# de exemplo](http://msdn.microsoft.com/pt-br/9a9d7aaa-51d3-4224-b564-95409b0f3e15)