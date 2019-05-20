---
title: 'Como: exibir argumentos de linha de comando – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: c88219d03d40c814338a1b09ccd37cfc03c2d577
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881022"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Como: exibir argumentos de linha de comando (Guia de Programação em C#)
Os argumentos fornecidos a um executável na linha de comando são acessíveis por meio de um parâmetro opcional para `Main`. Os argumentos são fornecidos na forma de uma matriz de cadeias de caracteres. Cada elemento da matriz contém um argumento. O espaço em branco entre os argumentos é removido. Por exemplo, considere essas invocações de linha de comando de um executável fictício:  
  
|Entrada na linha de comando|Matriz de cadeias de caracteres passada a Main|  
|----------------------------|-------------------------------------|  
|**executável.exe a b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**executável.exe um dois**|"um"<br /><br /> "dois"|  
|**executável.exe "um dois" três**|"one two"<br /><br /> "three"|  
  
> [!NOTE]
>  Quando estiver executando um aplicativo no Visual Studio, você pode especificar argumentos de linha de comando na [Página de depuração, Designer de Projeto](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Exemplo  
 Este exemplo exibe os argumentos de linha de comando passados a um aplicativo de linha de comando. A saída mostrada é para a primeira entrada da tabela acima.  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Build pela linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Main() e argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/index.md)
- [Valores de retorno de Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
