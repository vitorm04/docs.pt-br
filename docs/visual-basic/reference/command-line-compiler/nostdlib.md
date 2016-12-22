---
title: "/nostdlib (Visual Basic) | Microsoft Docs"
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
  - "Opção de compilador /nostdlib [Visual Basic]"
  - "Opção de compilador nostdlib [Visual Basic]"
  - "Opção de compilador -nostdlib [Visual Basic]"
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /nostdlib (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Faz com que o compilador não referencie automaticamente as bibliotecas padrão.  
  
## Sintaxe  
  
```  
/nostdlib  
```  
  
## Comentários  
 A opção `/nostdlib` remove a referência automática para o assembly System.dll e impede a leitura do arquivo Vbc.rsp pelo compilador.  O arquivo Vbc.rsp — que está localizado no mesmo diretório que o arquivo Vbc.exe — faz referência aos assemblies [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] comumente usados e importa os namespaces  `System` e `Microsoft.VisualBasic`.  
  
> [!NOTE]
>  Os assemblies mscorlib.dll e Microsoft.VisualBasic.dll são sempre referenciados.  
  
> [!NOTE]
>  A opção `/nostdlib` não está disponível de dentro do ambiente de desenvolvimento Visual Studio. Ela está disponível apenas quando se compila da linha de comando.  
  
## Exemplo  
 O código a seguir compila `T2.vb` sem fazer referência às bibliotecas padrão.  Você deve definir a constante `_MYTYPE` de compilação condicional para a sequência de caracteres "vazio" para remover o objeto `My`.  
  
```  
vbc /nostdlib /define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## Consulte também  
 [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Personalizando quais objetos estão disponíveis em My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)