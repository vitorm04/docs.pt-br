---
title: "@ (Opções do compilador de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d4dc8c81a9afd60add4c2a62be6804a0f6446124
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="-c-compiler-options"></a>@ (Opções do compilador de C#)
A opção @ possibilita especificar um arquivo que contém opções do compilador e arquivos de código-fonte a serem compilados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Arguments  
 `response_file`  
 Um arquivo que lista as opções do compilador ou os arquivos de código-fonte a serem compilados.  
  
## <a name="remarks"></a>Comentários  
 As opções do compilador e os arquivos de código-fonte serão processados pelo compilador apenas se eles tiverem sido especificados na linha de comando.  
  
 Para especificar mais de um arquivo de resposta em uma compilação, especifique várias opções de arquivo de resposta. Por exemplo:  
  
```  
@file1.rsp @file2.rsp  
```  
  
 Em um arquivo de resposta, várias opções de compilador e de arquivos de código-fonte podem ser exibidas em uma linha. Uma única especificação de opção do compilador deve ser exibida em uma linha (não é possível abranger várias linhas). Os arquivos de resposta podem ter comentários que começam com o símbolo #.  
  
 Especificar opções do compilador de dentro de um arquivo de resposta é como emitir esses comandos na linha de comando. Consulte [Compilando da linha de comando](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) para obter mais informações.  
  
 O compilador processa as opções de comando como elas são encontradas. Portanto, os argumentos da linha de comando podem substituir opções listadas anteriormente em arquivos de resposta. Por outro lado, opções em um arquivo de resposta substituirão as opções listadas anteriormente na linha de comando ou em outros arquivos de resposta.  
  
 O C# fornece o arquivo csc.rsp, localizado no mesmo diretório que o arquivo csc.exe. Consulte [/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) para obter informações sobre csc.rsp.  
  
 Essa opção do compilador não pode ser definida no ambiente de desenvolvimento do Visual Studio nem pode ser alterada por meio de programação.  
  
## <a name="example"></a>Exemplo  
 A seguir, há algumas linhas de um exemplo de arquivo de resposta:  
  
```console  
# build the first output file  
/target:exe /out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)
