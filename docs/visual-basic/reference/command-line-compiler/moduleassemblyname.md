---
title: "/moduleassemblyname | Microsoft Docs"
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
  - "Opção de compilador /moduleassemblyname [Visual Basic]"
  - "Opção de compilador moduleassemblyname [Visual Basic]"
  - "Opção de compilador -moduleassemblyname [Visual Basic]"
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /moduleassemblyname
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica o nome do conjunto de módulos \(assembly\) de que este módulo será uma parte.  
  
## Sintaxe  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## Argumentos  
  
|||  
|-|-|  
|Termo|Definição|  
|`assembly_name`|O nome do conjunto de módulos \(assembly\) de que este módulo será uma parte.|  
  
## Comentários  
 O compilador processa a opção `/moduleassemblyname` somente se a opção `/target:module` tiver sido especificada.  Isso faz com que o compilador crie um módulo.  O módulo criado pelo compilador é válido somente para o conjunto especificado com a opção `/moduleassemblyname`.  Se você colocar o módulo em um conjunto diferente, ocorrerão erros em tempo de execução.  
  
 A opção `/moduleassemblyname` é necessária somente quando as seguintes condições forem verdadeiras:  
  
-   Um tipo de dados no módulo precisa acessar um tipo `Friend` em um conjunto referenciado.  
  
-   O conjunto referenciado concedeu acesso assembly autorizado ao conjunto de módulos \(assembly\) no qual o módulo será criado.  
  
 Para obter mais informações sobre como criar um módulo, consulte [\/target](../../../visual-basic/reference/command-line-compiler/target.md).  Para obter mais informações sobre conjuntos de módulos \(assemblies\) amigos, consulte [Assemblies amigáveis](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md).  
  
> [!NOTE]
>  A opção `/moduleassemblyname` não está disponível no ambiente de desenvolvimento Visual Studio; ela está disponível apenas quando você compila do prompt de comando.  
  
## Consulte também  
 [Como compilar um assembly de vários arquivos](../Topic/How%20to:%20Build%20a%20Multifile%20Assembly.md)   
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [\/main](../../../visual-basic/reference/command-line-compiler/main.md)   
 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)   
 [Assemblies e o cache de assemblies global](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Assemblies amigáveis](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)