---
title: '@ (especificar arquivo de resposta) (Visual Basic)'
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af66000208dee0896792892a52dc6acdf5cb1e37
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-specify-response-file-visual-basic"></a>@ (especificar arquivo de resposta) (Visual Basic)
Especifica um arquivo que contém opções do compilador e arquivos de código-fonte para compilar.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Arguments  
 `response_file`  
 Necessário. Um arquivo que lista as opções do compilador ou arquivos de código-fonte para compilar. Coloque o nome do arquivo entre aspas ("") se ele contiver um espaço.  
  
## <a name="remarks"></a>Comentários  
 O compilador processa as opções do compilador e arquivos de código-fonte especificados em um arquivo de resposta como se eles tivessem sido especificados na linha de comando.  
  
 Para especificar mais de um arquivo de resposta em uma compilação, especifique várias opções de arquivo de resposta, como a seguir.  
  
```  
@file1.rsp @file2.rsp  
```  
  
 Arquivo, várias opções do compilador e arquivos de código-fonte podem aparecer em uma linha em uma resposta. Uma especificação de opção de compilador único deve aparecer em uma linha (não pode abranger várias linhas). Arquivos de resposta podem ter os comentários que começam com o `#` símbolo.  
  
 Você pode combinar as opções especificadas na linha de comando com as opções especificadas em um ou mais arquivos de resposta. O compilador processa as opções de comando como encontrá-las. Portanto, argumentos de linha de comando podem substituir as opções listadas anteriormente em arquivos de resposta. Por outro lado, opções em um arquivo de resposta substituem as opções listadas anteriormente na linha de comando ou em outros arquivos de resposta.  
  
 Visual Basic fornece o arquivo Vbc.rsp, que está localizado no mesmo diretório que o arquivo Vbc.exe. O arquivo Vbc.rsp está incluído por padrão, a menos que o `-noconfig` opção é usada. Para obter mais informações, consulte [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).  
  
> [!NOTE]
>  O `@` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.  
  
## <a name="example"></a>Exemplo  
 As linhas a seguir são de um arquivo de resposta de exemplo.  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como usar o `@` opção com o arquivo de resposta chamado `File1.rsp`.  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
