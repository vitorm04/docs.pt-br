---
title: "/keyfile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "Opção de compilador /keyfile [Visual Basic]"
  - "Opção de compilador keyfile [Visual Basic]"
  - "Opção de compilador -keyfile [Visual Basic]"
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /keyfile
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica um arquivo que contém uma chave ou par de chaves para dar um nome forte de um assembly.  
  
## Sintaxe  
  
```  
/keyfile:file  
```  
  
## Argumentos  
 `file`  
 Obrigatório.  Arquivo que contém a chave.  Se o nome do arquivo contiver um espaço, envolva\-o com aspas  \(""\).  
  
## Comentários  
 O compilador insere a chave pública no manifesto do assembly e, em seguida, assina o conjunto final com a chave particular.  Para gerar um arquivo de chave, digite `sn -k file` na linha de comando.  Para obter mais informações, consulte [Sn.exe \(Ferramenta de Nome Forte\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md).  
  
 Se você compilar com `/target:module`, o nome da chave é mantida no módulo e incorporada no assembly, que é criado quando você compila um assembly com [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Você também pode passar suas informações de criptografia para o compilador com [\/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).  Use [\/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) se você quiser um assembly parcialmente assinado.  
  
 Você também pode especificar essa opção como um atributo personalizado \(<xref:System.Reflection.AssemblyKeyFileAttribute>\) no código fonte para qualquer módulo da Microsoft intermediate language.  
  
 Nesse caso ambos `/keyfile` e [\/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) são especificados \(por opção de linha de comando ou por atributo personalizado\) na mesma compilação, o compilador primeiro tenta o recipiente de chave.  Se for bem\-sucedida, que então conjunto é assinado com as informações no contêiner de chave.  Se o compilador não localizar o contêiner de chave, ele tenta o arquivo especificado com `/keyfile`.  Se isso tiver êxito, o assembly é assinado com as informações no arquivo de chave e as informações da chave estão instaladas no recipiente de chave \(semelhante a  `sn -i`\) para que na próxima compilação, o recipiente de chave será válido.  
  
 Observe que um arquivo de chave pode conter somente a chave pública.  
  
 Consulte [Criando e usando assemblies de nomes fortes](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md) para mais informações sobre como assinar um assembly.  
  
> [!NOTE]
>  A opção `/keyfile` não está disponível de dentro do ambiente de desenvolvimento [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]. Ela está disponível apenas quando se compila da linha de comando.  
  
## Exemplo  
 O código a seguir compila o arquivo de origem `Input.vb` e especifica um arquivo de chave.  
  
```  
vbc /keyfile:myfile.sn input.vb  
```  
  
## Consulte também  
 [Assemblies e o cache de assemblies global](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)