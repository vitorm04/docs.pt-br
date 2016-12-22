---
title: "Argumentos de linha de comando (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "argumentos de linha de comando [C#]"
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
caps.latest.revision: 27
caps.handback.revision: 27
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Argumentos de linha de comando (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

É possível enviar argumentos para o método `Main` definindo o método em uma das seguintes maneiras:  
  
 [!code-cs[csProgGuideMain#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_1.cs)]  
  
 [!code-cs[csProgGuideMain#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_2.cs)]  
  
> [!NOTE]
>  Para habilitar argumentos de linha de comando no método `Main` em um aplicativo Windows Forms, você deve modificar manualmente a assinatura de `Main`  em program.cs.  O código gerado pelo designer do Windows Forms cria `Main` sem um parâmetro de entrada.  Você também pode usar <xref:System.Environment.CommandLine%2A?displayProperty=fullName> ou <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=fullName> para acessar argumentos de linha de comando de um ponto qualquer em um console ou em um aplicativo do Windows.  
  
 O parâmetro do método `Main` é uma matriz <xref:System.String> que representa os argumentos de linha de comando.  Normalmente, você determina se os argumentos existem testando a propriedade de `Length`, por exemplo:  
  
 [!code-cs[csProgGuideMain#4](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_3.cs)]  
  
 Você também pode converter os argumentos de cadeia de caracteres para tipos numéricos usando a classe <xref:System.Convert> ou o método `Parse`.  Por exemplo, a seguinte declaração converte `string` em um número `long` usando o método <xref:System.Int64.Parse%2A>:  
  
```  
long num = Int64.Parse(args[0]);  
```  
  
 Também é possível usar o tipo C\# `long`, do qual os aliases `Int64`:  
  
```  
long num = long.Parse(args[0]);  
```  
  
 Você também pode usar o método `ToInt64` de classe `Convert` para fazer a mesma coisa:  
  
```  
long num = Convert.ToInt64(s);  
```  
  
 Para obter mais informações, consulte <xref:System.Int64.Parse%2A> e <xref:System.Convert>.  
  
## Exemplo  
 O exemplo a seguir mostra como usar argumentos de linha de comando em um aplicativo de console.  O aplicativo usa um argumento em tempo de execução, converte o argumento em um inteiro e calcula o fatorial do número.  Se nenhum argumento é fornecido, o aplicativo envia uma mensagem que explica o uso correto do programa.  
  
 Para compilar e executar o aplicativo de um prompt de comando, siga estas etapas:  
  
1.  Cole o código a seguir em qualquer editor de texto e salve o arquivo como um arquivo de texto com o nome `Factorial.cs`.  
  
     [!code-cs[csProgGuideMain#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_4.cs)]  
  
2.  Na tela **Iniciar** ou no menu **Iniciar**, abra uma janela **Prompt de Comando do Desenvolvedor** do Visual Studio e navegue até a pasta que contém o arquivo que você acabou de criar.  
  
3.  Insira o seguinte comando para compilar o aplicativo.  
  
     `csc Factorial.cs`  
  
     Se seu aplicativo não tem nenhum erro de compilação, um arquivo executável chamado `Factorial.exe` é criado.  
  
4.  Insira o seguinte comando para calcular o fatorial de 3:  
  
     `Factorial 3`  
  
5.  O comando gera esta saída: `The factorial of 3 is 6.`  
  
> [!NOTE]
>  Ao executar um aplicativo no Visual Studio, você pode especificar argumentos de linha de comando em [Página de Depuração, Designer de Projeto](/visual-studio/ide/reference/debug-page-project-designer).  
  
 Para obter mais exemplos sobre como usar argumentos de linha de comando, consulte [Como criar e usar assemblies usando a linha de comando](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Consulte também  
 <xref:System.Environment?displayProperty=fullName>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Main\(\) e argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md)   
 [Como exibir argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [Como acessar argumentos de linha de comando usando foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)   
 [Valores de retorno de Main\(\)](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)   
 [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)