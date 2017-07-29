---
title: "Valores de retorno de Main() (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
caps.latest.revision: 20
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a24a0db126945d122db7a0c8d373d0c91e5da8a2
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="main-return-values-c-programming-guide"></a>Valores de retorno de Main() (Guia de Programação em C#)
O método `Main` pode retornar `void`:  
  
 [!code-cs[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_1.cs)]  
  
 Ele também pode retornar um `int`:  
  
 [!code-cs[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_2.cs)]  
  
 Se o valor retornado de `Main` não for usado, o retorno de `void` permite um código um pouco mais simples. No entanto, o retorno de um inteiro habilita o programa a comunicar informações de status para outros programas ou scripts, que invocam o arquivo executável. O exemplo a seguir mostra como o valor retornado de `Main` pode ser acessado.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, um arquivo em lotes é usado para executar um programa e testar o valor retornado da função `Main`. Quando um programa é executado no Windows, qualquer valor retornado da função `Main` é armazenado em uma variável de ambiente chamada `ERRORLEVEL`. Um arquivo em lotes pode determinar o resultado da execução, inspecionando a variável `ERRORLEVEL`. Tradicionalmente, um valor retornado de zero indica execução bem-sucedida. O exemplo a seguir é um programa simples que retorna zero da função `Main`. O zero indica que o programa foi executado com êxito. Salve o programa como MainReturnValTest.cs.  
  
 [!code-cs[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_3.cs)]  
  
## <a name="example"></a>Exemplo  
 Como este exemplo usa um arquivo em lotes, é melhor compilar o código em um prompt de comando. Siga as instruções em [Como configurar variáveis de ambiente para a linha de comando do Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) para habilitar builds de linha de comando ou use o prompt de comando do Visual Studio, disponível no menu **Iniciar** em **Ferramentas do Visual Studio**. No prompt de comando, navegue até a pasta na qual você salvou o programa. O comando a seguir compila o MainReturnValTest.cs e produz o arquivo executável MainReturnValTest.exe.  
  
 `csc MainReturnValTest.cs`  
  
 Em seguida, crie um arquivo em lotes para executar MainReturnValTest.exe e exibir o resultado. Cole o código a seguir em um arquivo de texto e salve-o como `test.bat` na pasta que contém o MainReturnValTest.cs e o MainReturnValTest.exe. Execute o arquivo em lotes digitando `test` no prompt de comando.  
  
 Como o código retorna zero, o arquivo em lotes relatará êxito. No entanto, se você alterar o MainReturnValTest.cs para retornar um valor diferente de zero e recompilar o programa, a execução subsequente do arquivo em lotes reportará falha.  
  
```  
rem test.bat  
@echo off  
MainReturnValTest  
@if "%ERRORLEVEL%" == "0" goto good  
  
:fail  
    echo Execution Failed  
    echo return value = %ERRORLEVEL%  
    goto end  
  
:good  
    echo Execution succeeded  
    echo Return value = %ERRORLEVEL%  
    goto end  
  
:end  
```  
  
## <a name="sample-output"></a>Saída de Exemplo  
 `Execution succeeded`  
  
 `Return value = 0`  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Main() e argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/index.md)   
 [Como exibir argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [Como acessar argumentos de linha de comando usando foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)

