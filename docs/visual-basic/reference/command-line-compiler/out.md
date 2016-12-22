---
title: "/out (Visual Basic) | Microsoft Docs"
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
  - "Opção de compilador /out [Visual Basic]"
  - "Opção de compilador out [Visual Basic]"
  - "Opção de compilador -out [Visual Basic]"
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /out (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica o nome do arquivo de saída.  
  
## Sintaxe  
  
```  
/out:filename  
```  
  
## Argumentos  
  
|||  
|-|-|  
|Termo|Definição|  
|`filename`|Obrigatório.  O nome do arquivo de saída que o compilador cria.  Se o nome do arquivo contiver um espaço, envolva\-o com aspas  \(""\).|  
  
## Comentários  
 Especifique a extensão e o nome completo do arquivo a ser criado.  Se isso não for feito, o arquivo .exe leva seu nome a partir do arquivo código\-fonte que contém o procedimento `Sub Main`,e o arquivo .dll leva seu nome do primeiro  arquivo código\-fonte.  
  
 Se você especificar um nome de arquivo sem extensão. exe ou. dll, o compilador adiciona automaticamente a extensão para você, dependendo do valor especificado para o `/target` opção de compilador.  
  
||  
|-|  
|Configurar \/out no ambiente de desenvolvimento integrado Visual Studio|  
|1.  Tenha um projeto selecionado no **Solution Explorer**.  No menu **Project**, clique em **Properties**..  Para obter mais informações, consulte [Introdução ao Project Designer](http://msdn.microsoft.com/pt-br/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Clique na guia **Application**.<br />3.  Modifique o valor na caixa  **Nome do conjunto**  Caixa.|  
  
## Exemplo  
 O código a seguir compila `T2.vb` e cria o arquivo de saída  `T2.exe`.  
  
```  
vbc t2.vb /out:t3.exe  
```  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)