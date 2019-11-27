---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 380e71e462f736d4564a37b83567007fa9461b05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332963"
---
# <a name="-imports-visual-basic"></a>-importações (Visual Basic)
Importa namespaces de um assembly especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>Argumentos  
  
|Termo|Definição|  
|---|---|  
|`namespaceList`|Necessária. Lista delimitada por vírgulas de namespaces a serem importados.|  
  
## <a name="remarks"></a>Comentários  
 A opção `-imports` importa qualquer namespace definido dentro do conjunto atual de arquivos de origem ou de qualquer assembly referenciado.  
  
 Os membros em um namespace especificado com `-imports` estão disponíveis para todos os arquivos de código-fonte na compilação. Use a [instrução Imports (namespace e tipo do .net)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para usar um namespace em um único arquivo de código-fonte.  
  
|Para definir/Imports no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1. ter um projeto selecionado em **Gerenciador de soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2. Clique na guia **referências** .<br />3. Insira o nome do namespace na caixa ao lado do botão **Adicionar importação de usuário** .<br />4. Clique no botão **Adicionar importação de usuário** .|  
  
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
