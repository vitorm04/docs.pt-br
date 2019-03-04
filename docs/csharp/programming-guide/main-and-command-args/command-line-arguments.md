---
title: Argumentos de linha de comando – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
ms.openlocfilehash: 2c1416566ca59a44b36457c710955de863013417
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980705"
---
# <a name="command-line-arguments-c-programming-guide"></a>Argumentos de linha de comando (Guia de Programação em C#)
Você pode enviar argumentos para o método `Main` definindo o método de uma das seguintes maneiras:  
  
 [!code-csharp[csProgGuideMain#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#2)]  
  
 [!code-csharp[csProgGuideMain#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#3)]  
  
> [!NOTE]
>  Para habilitar os argumentos de linha de comando no método `Main` em um aplicativo do Windows Forms, você deve modificar manualmente a assinatura de `Main` em program.cs. O código gerado pelo Designer de Formulários do Windows cria um `Main` sem um parâmetro de entrada. Você também pode usar <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> ou <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType> para acessar os argumentos de linha de comando de qualquer ponto em um console ou um aplicativo do Windows.  
  
 O parâmetro do método `Main` é uma matriz <xref:System.String> que representa os argumentos de linha de comando. Geralmente você determina se os argumentos existem testando a propriedade `Length`, por exemplo:  
  
 [!code-csharp[csProgGuideMain#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#4)]  
  
 Você também pode converter os argumentos de cadeia de caracteres em tipos numéricos, usando a classe <xref:System.Convert> ou o método `Parse`. Por exemplo, a instrução a seguir converte o `string` em um número `long` usando o método <xref:System.Int64.Parse%2A>:  
  
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
  
     [!code-csharp[csProgGuideMain#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#16)]  
  
2.  Na tela **Inicial** ou no menu **Iniciar**, abra uma janela de **Prompt de Comando do Desenvolvedor** do Visual Studio e, em seguida, navegue até a pasta que contém o arquivo que você acabou de criar.  
  
3.  Digite o seguinte comando para compilar o aplicativo.  
  
     `csc Factorial.cs`  
  
     Se seu aplicativo não tiver erros de compilação, um arquivo executável chamado `Factorial.exe` será criado.  
  
4.  Digite o seguinte comando para calcular o fatorial de 3:  
  
     `Factorial 3`  
  
5.  O comando produz esta saída: `The factorial of 3 is 6.`  
  
> [!NOTE]
>  Ao executar um aplicativo no Visual Studio, você pode especificar argumentos de linha de comando na [Página de depuração, Designer de Projeto](/visualstudio/ide/reference/debug-page-project-designer).  
  
 Para obter mais exemplos sobre como usar argumentos de linha de comando, confira [Como criar e usar assemblies usando a linha de comando](../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Environment?displayProperty=nameWithType>
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Main() e argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/index.md)
- [Como: exibir argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [Como: acessar argumentos de linha de comando usando foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
- [Valores de retorno de Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
- [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)
