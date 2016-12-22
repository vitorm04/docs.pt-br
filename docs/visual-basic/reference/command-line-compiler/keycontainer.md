---
title: "/keycontainer | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Opção de compilador /keycontainer [Visual Basic]"
  - "Opção de compilador keycontainer [Visual Basic]"
  - "Opção de compilador -keycontainer [Visual Basic]"
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /keycontainer
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica um nome de contêiner de chave para um par de chave para dar um nome forte a um assembly.  
  
## Sintaxe  
  
```  
/keycontainer:container  
```  
  
## Argumentos  
  
|||  
|-|-|  
|Termo|Definição|  
|`container`|Obrigatório.  Arquivo contêiner que contém a chave  Envolva o nome de arquivo em aspas \(""\) se o nome contém espaços.|  
  
## Comentários  
 O compilador cria o componente compartilhável inserindo uma chave pública no manifesto do assembly e assinando o assembly final com a chave privada.  Para gerar um arquivo de chave, digite `sn -k``file` na linha de comando.  A opção `-i`  instala o par de chaves no contêiner.  Para obter mais informações, consulte [Sn.exe \(Ferramenta de Nome Forte\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md).  
  
 Se você compilar com `/target:module`, o nome da chave é mantida no módulo e incorporada no assembly, que é criado quando você compila um assembly com [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Você também pode especificar esta opção como um atributo personalizado \(<xref:System.Reflection.AssemblyKeyNameAttribute>\) no código\-fonte para qualquer módulo de linguagem intermediária Microsoft \(MSIL\).  
  
 Você também pode passar suas informações de criptografia para o compilador com [\/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).  Use [\/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) se você quiser um assembly parcialmente assinado.  
  
 Consulte [Criando e usando assemblies de nomes fortes](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md) para mais informações sobre como assinar um assembly.  
  
> [!NOTE]
>  A opção `/keycontainer` não está disponível de dentro do ambiente de desenvolvimento Visual Studio. Ela está disponível apenas quando se compila da linha de comando.  
  
## Exemplo  
 O seguinte código compila o arquivo\-fonte `Input.vb` e especifica um contêiner de chave.  
  
```  
vbc /keycontainer:key1 input.vb  
```  
  
## Consulte também  
 [Assemblies e o cache de assemblies global](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)