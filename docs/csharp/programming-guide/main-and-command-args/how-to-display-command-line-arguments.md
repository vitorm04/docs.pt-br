---
title: "Como exibir argumentos de linha de comando (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6ae495eef227c6e4d9fb9ca0d4d0c031163fd52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Como exibir argumentos de linha de comando (Guia de Programação em C#)
Os argumentos fornecidos a um executável na linha de comando são acessíveis por meio de um parâmetro opcional para `Main`. Os argumentos são fornecidos na forma de uma matriz de cadeias de caracteres. Cada elemento da matriz contém um argumento. O espaço em branco entre os argumentos é removido. Por exemplo, considere essas invocações de linha de comando de um executável fictício:  
  
|Entrada na linha de comando|Matriz de cadeias de caracteres passada a Main|  
|----------------------------|-------------------------------------|  
|**executável.exe a b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**executável.exe um dois**|"um"<br /><br /> "dois"|  
|**executável.exe "um dois" três**|“one two”<br /><br /> "three"|  
  
> [!NOTE]
>  Quando estiver executando um aplicativo no Visual Studio, você pode especificar argumentos de linha de comando na [Página de depuração, Designer de Projeto](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Exemplo  
 Este exemplo exibe os argumentos de linha de comando passados a um aplicativo de linha de comando. A saída mostrada é para a primeira entrada da tabela acima.  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Build pela linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [Main() e argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Como acessar argumentos de linha de comando usando foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [Valores de retorno de Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
