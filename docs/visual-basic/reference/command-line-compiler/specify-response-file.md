---
title: "@ (especificar arquivo de resposta) (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Opção de compilador @ (Especificar Arquivo de Resposta) [Visual Basic]"
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# @ (especificar arquivo de resposta) (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica um arquivo que contém opções do compilador e arquivos de código fonte para compilar.  
  
## Sintaxe  
  
```  
@response_file  
```  
  
## Argumentos  
 `response_file`  
 Obrigatório.  Um arquivo que lista opções do compilador ou arquivos de código fonte para compilar.  Envolva o nome de arquivo com aspas \(""\) se o nome contiver espaços.  
  
## Comentários  
 O compilador processa as opções do compilador e arquivos de código\-fonte especificados em um arquivo de resposta como se eles tivessem sido especificados em linha de comando.  
  
 Para especificar mais de um arquivo de resposta em uma compilação, especifique várias opções de arquivo de resposta, como a seguir.  
  
```  
@file1.rsp @file2.rsp  
```  
  
 Em um arquivo de resposta, várias opções do compilador e arquivos de código\-fonte podem aparecer em uma linha.  Uma especificação de opção de compilador único deve aparecer em uma linha \(não pode abranger várias linhas\).  Arquivos de resposta podem ter os comentários que começam com o símbolo `#`.  
  
 Você pode combinar as opções especificadas na linha de comando com as opções especificadas em um ou mais arquivos de resposta.  O compilador processa as opções de linha de comando ao encontrá\-las.  Portanto, argumentos de linha de comando podem substituir as opções listadas anteriormente em arquivos de resposta.  Por outro lado, as opções em um arquivo de resposta substituem as opções listadas anteriormente na linha de comando ou outros arquivos de resposta.  
  
 Visual Basic fornece o arquivo Vbc.rsp  localizado no mesmo diretório que o arquivo Vbc.exe.  O arquivo Vbc.rsp é incluído por padrão, a menos que a opção `/noconfig` seja usada.  Para obter mais informações, consulte [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).  
  
> [!NOTE]
>  A opção `@` não está disponível de dentro do ambiente de desenvolvimento Visual Studio. Ela está disponível apenas quando se compila da linha de comando.  
  
## Exemplo  
 As seguintes linhas são de um arquivo de resposta de exemplo.  
  
```  
# build the first output file  
/target:exe   
/out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## Exemplo  
 O exemplo a seguir demonstra como usar a opção `@` com o arquivo de resposta chamado `File1.rsp`.  
  
```  
vbc @file1.rsp  
```  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)