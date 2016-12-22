---
title: "-linkresource (Visual Basic) | Microsoft Docs"
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
  - "Opção de compilador /linkresource [Visual Basic]"
  - "Opção de compilador -linkresource [Visual Basic]"
  - "Opção de compilador linkresource [Visual Basic]"
  - "Opção de compilador /linkres [Visual Basic]"
  - "Opção de compilador linkres [Visual Basic]"
  - "Opção de compilador -linkres [Visual Basic]"
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /linkresource (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cria um link para um recurso gerenciado.  
  
## Sintaxe  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## Arguments  
 `filename`  
 Obrigatório. O arquivo de recurso para vincular ao assembly. Se o nome do arquivo contém um espaço, coloque o nome entre aspas \(""\).  
  
 `identifier`  
 Opcional. O nome lógico para o recurso. O nome que é usado para carregar o recurso. O padrão é o nome do arquivo. Opcionalmente, você pode especificar se o arquivo é pública ou privada no manifesto do assembly, por exemplo: `/linkres:filename.res,myname.res,public`. Por padrão, `filename` é público no assembly.  
  
## Comentários  
 O `/linkresource` opção não insere o arquivo de recurso no arquivo de saída; use o `/resource` como fazer isso.  
  
 O `/linkresource` opção requer um do `/target` diferente de opções `/target:module`.  
  
 Se `filename` é um [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] arquivo de recurso criado, por exemplo, pelo [Resgen.exe \(Gerador de Arquivo de Recurso\)](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) ou no ambiente de desenvolvimento, ele pode ser acessado com membros de <xref:System.Resources> namespace. \(Para obter mais informações, consulte <xref:System.Resources.ResourceManager>.\) Para acessar todos os outros recursos em tempo de execução, use os métodos que começam com `GetManifestResource` na <xref:System.Reflection.Assembly> classe.  
  
 O nome do arquivo pode ser qualquer formato de arquivo. Por exemplo, você talvez queira fazer uma parte DLL nativa do assembly, para que possa ser instalado no cache de assembly global e acessado a partir do código gerenciado no assembly.  
  
 A forma abreviada de `/linkresource` é `/linkres`.  
  
> [!NOTE]
>  O `/linkresource` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente quando você compilar na linha de comando.  
  
## Exemplo  
 O seguinte código compila `In.vb` e links para o arquivo de recurso `Rf.resource`.  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [\/resource](../../../visual-basic/reference/command-line-compiler/resource.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)