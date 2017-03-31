---
title: "Argumentos de linha de comando (Guia de programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
caps.latest.revision: 27
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4034f1575321c94f003a12a83df617d4a0d50702
ms.lasthandoff: 03/13/2017

---
# <a name="command-line-arguments-c-programming-guide"></a>Argumentos de linha de comando (Guia de Programação em C#)
Você pode enviar argumentos para o método `Main` definindo o método de uma das seguintes maneiras:  
  
 [!code-cs[csProgGuideMain#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_1.cs)]  
  
 [!code-cs[csProgGuideMain#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_2.cs)]  
  
> [!NOTE]
>  Para habilitar os argumentos de linha de comando no método `Main` em um aplicativo do Windows Forms, você deve modificar manualmente a assinatura de `Main` em program.cs. O código gerado pelo Designer de Formulários do Windows cria um `Main` sem um parâmetro de entrada. Você também pode usar <xref:System.Environment.CommandLine%2A?displayProperty=fullName> ou <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=fullName> para acessar os argumentos de linha de comando de qualquer ponto em um console ou nos aplicativos do Windows.  
  
 O parâmetro do método `Main` é uma matriz <xref:System.String> que representa os argumentos de linha de comando. Geralmente você determina se os argumentos existem testando a propriedade `Length`, por exemplo:  
  
 [!code-cs[csProgGuideMain#4](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_3.cs)]  
  
 Você também pode converter os argumentos de cadeia de caracteres em tipos numéricos, usando a classe <xref:System.Convert> ou o método `Parse`. Por exemplo, a instrução a seguir converte a `string` para um número `long` usando o método <xref:System.Int64.Parse%2A>:  
  
```  
long num = Int64.Parse(args[0]);  
```  
  
 Também é possível usar o tipo `long` de C#, que funciona como alias de `Int64`:  
  
```  
long num = long.Parse(args[0]);  
```  
  
 Você também pode usar o método da classe `Convert`, o `ToInt64`, para fazer a mesma coisa:  
  
```  
long num = Convert.ToInt64(s);  
```  
  
 Para obter mais informações, consulte <xref:System.Int64.Parse%2A> e <xref:System.Convert>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar argumentos de linha de comando em um aplicativo de console. O aplicativo recebe um argumento em tempo de execução, converte o argumento em um número inteiro e calcula o fatorial do número. Se nenhum argumento for fornecido, o aplicativo emitirá uma mensagem que explica o uso correto do programa.  
  
 Para compilar e executar o aplicativo em um prompt de comando, siga estas etapas:  
  
1.  Cole o código a seguir em qualquer editor de texto e, em seguida, salve o arquivo como um arquivo de texto com o nome `Factorial.cs`.  
  
     [!code-cs[csProgGuideMain#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_4.cs)]  
  
2.  Na tela **Inicial** ou no menu **Iniciar**, abra uma janela de **Prompt de Comando do Desenvolvedor** do Visual Studio e, em seguida, navegue até a pasta que contém o arquivo que você acabou de criar.  
  
3.  Digite o seguinte comando para compilar o aplicativo.  
  
     `csc Factorial.cs`  
  
     Se seu aplicativo não tiver erros de compilação, um arquivo executável chamado `Factorial.exe` será criado.  
  
4.  Digite o seguinte comando para calcular o fatorial de 3:  
  
     `Factorial 3`  
  
5.  O comando produz esta saída: `The factorial of 3 is 6.`  
  
> [!NOTE]
>  Ao executar um aplicativo no Visual Studio, você pode especificar argumentos de linha de comando na [Página de depuração, Designer de Projeto](https://docs.microsoft.com/visualstudio/ide/reference/debug-page-project-designer).  
  
 Para obter mais exemplos de como usar argumentos de linha de comando, consulte [Como criar e usar assemblies usando a linha de comando](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Environment?displayProperty=fullName>   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Main() e argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/index.md)   
 [Como exibir argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [Como acessar argumentos de linha de comando usando foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)   
 [Valores retornados de Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)   
 [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)
