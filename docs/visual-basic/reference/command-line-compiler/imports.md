---
title: -importações (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 929e24a1ffd02d4e21ab1b925ddd59050b5d3cc4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005569"
---
# <a name="-imports-visual-basic"></a>-importações (Visual Basic)
Importa namespaces de um assembly especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`namespaceList`|Necessário. Lista delimitada por vírgulas de namespaces a serem importados.|  
  
## <a name="remarks"></a>Comentários  
 A opção `-imports` importa qualquer namespace definido dentro do conjunto atual de arquivos de origem ou de qualquer assembly referenciado.  
  
 Os membros em um namespace especificado com `-imports` estão disponíveis para todos os arquivos de código-fonte na compilação. Use a [instrução Imports (namespace e tipo do .net)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para usar um namespace em um único arquivo de código-fonte.  
  
|Para definir/Imports no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Referências**.<br />3.  Digite o nome do namespace na caixa ao lado do botão **Adicionar importação de usuário** .<br />4.  Clique no botão **Adicionar importação de usuário** .|  
  
## <a name="example"></a>Exemplo  
 O código a seguir é compilado quando `/imports:system.globalization` é especificado. Sem ele, a compilação bem-sucedida requer que uma instrução `Imports System.Globalization` seja incluída no início do arquivo de código-fonte ou que a propriedade seja totalmente qualificada como `System.Globalization.CultureInfo.CurrentCulture.Name`.

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Referências e a Instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
