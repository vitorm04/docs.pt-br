---
title: "/resource (Visual Basic) | Microsoft Docs"
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
  - "Opção de compilador /res [Visual Basic]"
  - "Opção de compilador /resource [Visual Basic]"
  - "Opção de compilador res [Visual Basic]"
  - "Opção de compilador -res [Visual Basic]"
  - "Opção de compilador resource [Visual Basic]"
  - "Opção de compilador -resource [Visual Basic]"
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /resource (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Incorpora um recurso gerenciado em um assembly.  
  
## Sintaxe  
  
```  
/resource:filename[,identifier[,public|private]]  
' -or-  
/res:filename[,identifier[,public|private]]  
```  
  
## Argumentos  
  
|||  
|-|-|  
|Termo|Definição|  
|`filename`|Necessário.  O nome do arquivo de recurso incorporado no arquivo de saída.  Por padrão, `filename` é público no assembly.  Envolva o nome de arquivo com aspas \(""\) se o nome contiver espaços.|  
|`identifier`|Opcional.  O nome lógico do recurso; o nome usado para carregá\-lo.  O padrão é o nome do arquivo.  Opcionalmente, você pode especificar se o recurso é público ou particular no manifesto do assembly, como com o seguinte: `/res:``filename.res`,`myname.res`,`public`|  
  
## Comentários  
 Use `/linkresource` para vincular um recurso a um assembly sem colocar o arquivo de recurso no arquivo de saída.  
  
 Se `filename` é um [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] arquivo de recurso criado, por exemplo, pela [Resgen.exe \(Gerador de Arquivo de Recurso\)](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) ou no ambiente de desenvolvimento, ele pode ser acessado com membros na <xref:System.Resources> namespace \(consulte <xref:System.Resources.ResourceManager> para obter mais informações\).  Para acessar todos os outros recursos em tempo de execução, use um dos seguintes métodos: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, ou <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.  
  
 A forma curta de `/resource`  é `/res`.  
  
 Para obter informações sobre como definir `/resource` no Visual Studio IDE, consulte [Gerenciando recursos de aplicativo \(.NET\)](/visual-studio/ide/managing-application-resources-dotnet).  
  
## Exemplo  
 O código a seguir compila `In.vb` e o arquivo de recurso anexa `Rf.resource`.  
  
```  
vbc /res:rf.resource in.vb  
```  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)   
 [\/linkresource \(Visual Basic\)](../../../visual-basic/reference/command-line-compiler/linkresource.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)