---
title: /recurse | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fbf7d67c7f70345e62ddbb03c8626b688b5c593b
ms.lasthandoff: 03/13/2017

---
# <a name="recurse"></a>/recurse
Compila arquivos de código-fonte no todos os diretórios filhos do diretório especificado ou o diretório do projeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir`  
 Opcional. O diretório no qual você deseja começar a pesquisa. Se não for especificado, a pesquisa começará no diretório do projeto.  
  
 `file`  
 Necessário. Os arquivos para pesquisar. Caracteres curinga são permitidos.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar caracteres curinga em um nome de arquivo para compilar todos os arquivos correspondentes no diretório do projeto sem usar `/recurse`. Se nenhum nome de arquivo de saída for especificado, o compilador baseia o nome do arquivo de saída no primeiro arquivo de saída processado. Isso geralmente é o primeiro arquivo na lista de arquivos compilados quando exibidos em ordem alfabética. Por esse motivo, é melhor especificar um arquivo de saída usando o `/out` opção.  
  
> [!NOTE]
>  O `/recurse` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila todos os [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] arquivos no diretório atual.  
  
```  
vbc *.vb  
```  
  
 O código a seguir compila todos os [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] arquivos de `Test\ABC` directory e quaisquer diretórios abaixo dela e, em seguida, gera `Test.ABC.dll`.  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [entrada/saída (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)   
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
