---
title: "#line (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "#line"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Diretiva #line [C#]"
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #line (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`#line`permite modificar o número da linha do compilador e \(opcionalmente\) a saída de nome de arquivo para erros e avisos.  Este exemplo mostra como denunciar dois avisos associados com números de linha.  O `#line 200` diretiva força o número de linha a ser 200 \(embora o padrão é \# 7\) e até a próxima diretiva \# line, o nome do arquivo será relatada como "Especial".  A diretiva padrão \# line retorna a sua numeração padrão, a numeração de linha que conta as linhas que foram renumeradas pela diretiva anterior.  
  
```  
class MainClass  
{  
    static void Main()  
    {  
#line 200 "Special"  
        int i;    // CS0168 on line 200  
        int j;    // CS0168 on line 201  
#line default  
        char c;   // CS0168 on line 9  
        float f;  // CS0168 on line 10  
#line hidden // numbering not affected  
        string s;   
        double d; // CS0168 on line 13  
    }  
}  
```  
  
## Comentários  
 O `#line` diretiva pode ser usada em uma etapa automatizada e intermediária no processo de compilação.  Por exemplo, se linhas foram removidas do arquivo de código fonte original, mas ainda quiser o compilador gere com base na linha original de numeração no arquivo de saída, você pode remover linhas e simular a numeração de linha original com `#line`.  
  
 O `#line hidden` diretiva oculta as linhas sucessivas do depurador, de modo que quando o desenvolvedor percorre o código, qualquer linhas entre um `#line hidden` e o próximo `#line` diretiva \(supondo que não é outro `#line hidden` diretiva\) ele irá ser apresentado pela.  Esta opção também pode ser usada para permitir ao ASP.NET para diferenciar entre o código gerado pelo computador e definidos pelo usuário.  Embora o ASP.NET é o consumidor primário desse recurso, é provável que fará com que geradores de origem mais usá\-lo.  
  
 A `#line hidden` diretiva não afeta os nomes de arquivo nem números no relatório de erros de linha.  Ou seja, se um erro é encontrado em um bloco oculto, o compilador reportará o número de arquivo atual nome e a linha do erro.  
  
 O `#line filename` diretiva especifica o nome do arquivo que você deseja que apareça na saída do compilador.  Por padrão, o nome real do arquivo de código fonte é usado.  O nome do arquivo deve estar entre aspas duplas \(""\) e deve ser precedido por um número de linha.  
  
 Um arquivo de código\-fonte pode ter qualquer número de `#line` diretivas.  
  
## Exemplo 1  
 O exemplo a seguir mostra como o depurador ignora as linhas ocultas no código.  Quando você executar o exemplo, ele exibirá três linhas de texto.  No entanto, quando você definir um ponto de interrupção, como mostrado no exemplo e aperte F10 para depurar o código, você irá notar que o depurador ignora a linha oculta.  Observe também que, mesmo se você definir um ponto de interrupção na linha de oculta, o depurador irá ainda ignorá\-la.  
  
```  
// preprocessor_linehidden.cs  
using System;  
class MainClass   
{  
    static void Main()   
    {  
        Console.WriteLine("Normal line #1."); // Set break point here.  
#line hidden  
        Console.WriteLine("Hidden line.");  
#line default  
        Console.WriteLine("Normal line #2.");  
    }  
}  
```  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Diretivas de pré\-processador em C\#](../../../visual-basic/reference/command-line-compiler/index.md)