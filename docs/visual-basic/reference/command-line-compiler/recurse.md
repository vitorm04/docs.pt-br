---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd5dde46cdea67825b14a6f5fa96a82c8bab8d3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="-recurse"></a>-recurse
Compila arquivos de código-fonte em todos os diretórios filhos do diretório do projeto ou o diretório especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir`  
 Opcional. O diretório no qual você deseja que a pesquisa comece. Se não for especificado, a pesquisa começará no diretório do projeto.  
  
 `file`  
 Necessário. Os arquivos a serem pesquisados. São permitidos caracteres curinga.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar curingas no nome do arquivo para compilar todos os arquivos correspondentes no diretório do projeto sem usar `-recurse`. Se nenhum nome de arquivo de saída for especificado, o compilador baseia o nome do arquivo de saída no primeiro arquivo de saída processado. Isso geralmente é o primeiro arquivo na lista de arquivos compilados quando exibidos em ordem alfabética. Por esse motivo, é melhor especificar um arquivo de saída usando o `-out` opção.  
  
> [!NOTE]
>  O `-recurse` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.  
  
## <a name="example"></a>Exemplo  
 O comando a seguir compila todos os arquivos do Visual Basic no diretório atual.  
  
```console
vbc *.vb  
```  
  
 O comando a seguir compila todos os arquivos do Visual Basic no `Test\ABC` diretório e quaisquer diretórios abaixo dela e, em seguida, gera `Test.ABC.dll`.  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
