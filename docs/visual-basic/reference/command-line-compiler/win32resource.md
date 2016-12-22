---
title: "/win32resource | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/win32resource"
  - "win32resource"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Opção de compilador /win32resource [Visual Basic]"
  - "Opção de compilador win32resource [Visual Basic]"
  - "Opção de compilador -win32resource [Visual Basic]"
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /win32resource
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Insere um arquivo de recurso Win32 no arquivo de saída.  
  
## Sintaxe  
  
```  
/win32resource:filename  
```  
  
## Argumentos  
 `filename`  
 O nome do arquivo de recurso para adicionar ao seu arquivo de saída.  Envolva o nome de arquivo com aspas \(""\) se o nome contiver espaços.  
  
## Comentários  
 Você pode criar um arquivo de recurso Win32 com o compilador \(RC\) de recurso do Microsoft Windows.  
  
 Um recurso Win32 pode conter informações de versão ou bitmap \(ícone\) que ajudam a identificar seu aplicativo em **Arquivo Explorer**.  Se você não especificar `/win32resource`, o compilador gera informações de versão baseada na versão do assembly.  As opções de `/win32resource` e de `/win32icon` são mutuamente exclusivos.  
  
 Consulte [\/linkresource \(Visual Basic\)](../../../visual-basic/reference/command-line-compiler/linkresource.md) para fazer referência a um arquivo de recurso de [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] , ou [\/resource](../../../visual-basic/reference/command-line-compiler/resource.md) para anexar um arquivo de recurso [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] .  
  
> [!NOTE]
>  A opção `/win32resource` não está disponível dentro do ambiente de desenvolvimento Visual Studio. Ela está disponível apenas quando se compila da linha de comando.  
  
## Exemplo  
 O código a seguir compila `In.vb` e anexa um arquivo de recurso Win32, `Rf.res`:  
  
```  
vbc /win32resource:rf.res in.vb  
```  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)