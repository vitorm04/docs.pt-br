---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 71613af0f1c319801296180d49dbacfedf0ceca4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005253"
---
# <a name="-recurse"></a>-recurse
Compila os arquivos de código-fonte em todos os diretórios filho do diretório especificado ou do diretório do projeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Argumentos  
 `dir`  
 Opcional. O diretório no qual você deseja que a pesquisa comece. Se não for especificado, a pesquisa começará no diretório do projeto.  
  
 `file`  
 Necessário. Os arquivos a serem pesquisados. São permitidos caracteres curinga.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar caracteres curinga em um nome de arquivo para compilar todos os arquivos correspondentes no diretório do projeto sem usar `-recurse`. Se nenhum nome de arquivo de saída for especificado, o compilador baseará o nome do arquivo de saída no primeiro arquivo de entrada processado. Esse é geralmente o primeiro arquivo na lista de arquivos compilados quando exibidos em ordem alfabética. Por esse motivo, é melhor especificar um arquivo de saída usando a opção `-out`.  
  
> [!NOTE]
> A opção `-recurse` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.  
  
## <a name="example"></a>Exemplo  
 O comando a seguir compila todos os arquivos de Visual Basic no diretório atual.  
  
```console
vbc *.vb  
```  
  
 O comando a seguir compila todos os Visual Basic arquivos no diretório `Test\ABC` e em todos os diretórios abaixo dele e, em seguida, gera `Test.ABC.dll`.  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
