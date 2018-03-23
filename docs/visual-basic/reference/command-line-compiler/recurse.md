---
title: -recurse
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb1cc114c2882aa82787f94a271dd7684c716b01
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
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
 O comando a seguir compila todos os [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] arquivos no diretório atual.  
  
```console
vbc *.vb  
```  
  
 O comando a seguir compila todos os [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] arquivos de `Test\ABC` diretório e quaisquer diretórios abaixo dela e, em seguida, gera `Test.ABC.dll`.  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
