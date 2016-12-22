---
title: "Nome ou n&#250;mero de arquivo inv&#225;lido | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrID52"
dev_langs: 
  - "VB"
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nome ou n&#250;mero de arquivo inv&#225;lido
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Ocorreu um erro ao tentar acessar o arquivo especificado.  Entre as causas possíveis para esse erro estão:  
  
-   Uma declaração se refere a um arquivo com um nome de arquivo ou o número que não foi especificado no `FileOpen` instrução ou que foi especificado em um `FileOpen` instrução, mas foi subseqüentemente fechado.  
  
-   Uma declaração se refere a um arquivo com um número que está fora do intervalo de números de arquivo.  
  
-   Uma declaração se refere a um nome de arquivo ou número que não é válido.  
  
### Para corrigir este erro  
  
1.  Verifique se o nome do arquivo é especificado em um `FileOpen` instrução.  Observe que, se você chamou o `FileClose` instrução sem argumentos, você pode inadvertidamente fechou todos os arquivos abertos.  
  
2.  Se seu código está gerando era números de arquivo, verifique se que os números são válidos.  
  
3.  Verifique os nomes de arquivo para certificar\-se de que estejam em conformidade com as convenções do sistema operacional.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>   
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)