---
title: "/win32icon | Microsoft Docs"
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
  - "Opção de compilador /win32icon [Visual Basic]"
  - "Opção de compilador win32icon [Visual Basic]"
  - "Opção de compilador -win32icon [Visual Basic]"
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /win32icon
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Insere um arquivo .ico no arquivo de saída.  Esse arquivo .ico representa o arquivo de saída em **Arquivo Explorer**.  
  
## Sintaxe  
  
```  
/win32icon:filename  
```  
  
## Argumentos  
  
|||  
|-|-|  
|Termo|Definição|  
|`filename`|O arquivo .ico adicionar ao seu arquivo de saída.  Envolva o nome de arquivo com aspas \(""\) se o nome contiver espaços.|  
  
## Comentários  
 Você pode criar um arquivo .ico com o compilador \(RC\) de recurso do Microsoft Windows.  O compilador de recurso é chamado quando você compila um programa em Visual C\+\+; um arquivo .ico é criado do arquivo de .rc.  As opções de `/win32icon` e de `/win32resource` são mutuamente exclusivos.  
  
 Consulte [\/linkresource \(Visual Basic\)](../../../visual-basic/reference/command-line-compiler/linkresource.md) para fazer referência a um arquivo de recurso de [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] , ou [\/resource](../../../visual-basic/reference/command-line-compiler/resource.md) para anexar um arquivo de recurso [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] .  Consulte [\/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) para importar um arquivo de .res.  
  
||  
|-|  
|Para definir \/win32icon no IDE do Visual Studio|  
|1.  Tenha um projeto selecionado no **Solution Explorer**.  No menu **Project**, clique em **Properties**..  Para mais informações, consulte [Introdução ao Project Designer](http://msdn.microsoft.com/pt-br/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Clique na guia **Application**.<br />3.  Modifique o valor na caixa de **Ícone** .|  
  
## Exemplo  
 O código a seguir compila `In.vb` e anexa um arquivo .ico, `Rf.ico`.  
  
```  
vbc /win32icon:rf.ico in.vb  
```  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)