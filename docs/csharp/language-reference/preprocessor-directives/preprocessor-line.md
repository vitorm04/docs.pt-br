---
title: '#line (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: f3ebecda7761e6249656e0b9f8543ae1252b844e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524532"
---
# <a name="line-c-reference"></a>#line (Referência de C#)
O `#line` permite modificar o número de linha do compilador e (opcionalmente) a saída do nome de arquivo para erros e avisos.

O exemplo a seguir mostra como relatar dois avisos associados aos números de linha. A diretiva `#line 200` força o próximo número de linha a ser 200 (embora o padrão seja #6) e, até a próxima diretiva #line, o nome de arquivo será relatado como "Especial". A diretiva padrão #line retorna a numeração de linhas à sua numeração padrão, que conta as linhas que foram renumeradas pela diretiva anterior.  
  
```csharp
class MainClass  
{  
    static void Main()  
    {  
#line 200 "Special"  
        int i;
        int j;
#line default  
        char c;
        float f;
#line hidden // numbering not affected  
        string s;   
        double d;
    }  
}  
```  
A compilação produz a saída a seguir:

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a>Comentários  
 A diretiva `#line` pode ser usada em uma etapa intermediária e automatizada no processo de build. Por exemplo, se linhas fossem removidas do arquivo de código-fonte original, mas você ainda deseja que o compilador gere a saída com base na numeração de linha original no arquivo, seria possível remover as linhas e, em seguida, simular a numeração de linha original com `#line`.  
  
 A diretiva `#line hidden` oculta as linhas sucessivas do depurador, de modo que, quando o desenvolvedor percorrer o código, quaisquer linhas entre um `#line hidden` e a próxima diretiva `#line` (supondo que não seja outra diretiva `#line hidden`) serão puladas. Essa opção também pode ser usada para permitir que o ASP.NET diferencie entre o código gerado pelo computador e definido pelo usuário. Embora o ASP.NET seja o principal consumidor desse recurso, é provável que mais geradores de origem façam uso dele.  
  
 A diretiva `#line hidden` não afeta os nomes de arquivo ou números de linha nos relatórios de erro. Ou seja, se um erro for encontrado em um bloco oculto, o compilador reportará o nome do arquivo atual e o número de linha do erro.  
  
 A diretiva `#line filename` especifica o nome de arquivo que você deseja que seja exibido na saída do compilador. Por padrão, é usado o nome real do arquivo de código-fonte. O nome de arquivo deve estar entre aspas duplas ("") e deve ser precedido por um número de linha.  
  
 Um arquivo de código-fonte pode ter qualquer número de diretivas `#line`.  
  
## <a name="example-1"></a>Exemplo 1  
 O exemplo a seguir mostra como o depurador ignora as linhas ocultas no código. Quando você executar o exemplo, ele exibirá três linhas de texto. No entanto, quando você definir um ponto de interrupção, conforme mostrado no exemplo e apertar F10 para percorrer o código, você observará que o depurador ignorará a linha oculta. Observe também que, mesmo que você defina um ponto de interrupção na linha oculta, o depurador ainda a ignorará.  
  
```csharp
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
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Diretivas do pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md)
