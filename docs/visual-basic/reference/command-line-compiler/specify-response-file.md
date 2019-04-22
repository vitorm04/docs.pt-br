---
title: '@ (especificar arquivo de resposta) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: 6b993a6399eec4e203821109db153aadf246cbac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838112"
---
# <a name="-specify-response-file-visual-basic"></a>@ (especificar arquivo de resposta) (Visual Basic)
Especifica um arquivo que contém as opções do compilador e arquivos de código-fonte para compilar.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Arguments  
 `response_file`  
 Necessário. Um arquivo que lista Opções do compilador ou arquivos de código-fonte para compilar. Coloque o nome do arquivo entre aspas ("") se ele contiver um espaço.  
  
## <a name="remarks"></a>Comentários  
 O compilador processa as opções do compilador e arquivos de código-fonte especificados em um arquivo de resposta, como se eles tivessem sido especificados na linha de comando.  
  
 Para especificar mais de um arquivo de resposta em uma compilação, especifique várias opções de arquivo de resposta, como a seguir.  
  
```  
@file1.rsp @file2.rsp  
```  
  
 Em uma resposta de arquivo, várias opções do compilador e arquivos de código-fonte podem aparecer em uma única linha. Uma especificação de opção de compilador único deve aparecer em uma linha (não pode abranger várias linhas). Arquivos de resposta podem ter comentários que começam com o `#` símbolo.  
  
 Você pode combinar as opções especificadas na linha de comando com as opções especificadas em um ou mais arquivos de resposta. O compilador processa as opções de comando ao encontrá-los. Portanto, os argumentos de linha de comando podem substituir opções listadas anteriormente em arquivos de resposta. Por outro lado, as opções em um arquivo de resposta substituem as opções listadas anteriormente na linha de comando ou em outros arquivos de resposta.  
  
 Visual Basic fornece o arquivo Vbc. rsp, localizado no mesmo diretório que o arquivo Vbc.exe. O arquivo Vbc. exe é incluído por padrão, a menos que o `-noconfig` opção é usada. Para obter mais informações, consulte [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).  
  
> [!NOTE]
>  O `@` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.  
  
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

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
