---
title: "Modo de arquivo inv&#225;lido | Microsoft Docs"
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
  - "vbrID54"
dev_langs: 
  - "VB"
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Modo de arquivo inv&#225;lido
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Declarações usadas em conteúdo de manipulação de arquivo devem ser apropriadas ao modo no qual o arquivo foi aberto.  Possíveis causas incluem:  
  
-   Um declaração `FilePutObject` ou `FileGetObject` especifica um arquivo sequencial.  
  
-   Um declaração `Print` especifica um arquivo aberto para um modo de acesso diferente de `Output` ou `Append`.  
  
-   Uma declaração `Input` especifica um arquivo aberto para um modo de acesso diferente de `Input`.  
  
-   Uma tentativa de se escrever num arquivo somente\-leitura.  
  
### Para corrigir este erro  
  
-   Certifique\-se de que `FilePutObject` e `FileGetObject` estão se referindo apenas a arquivos abertos para acesso `Random` ou `Binary`.  
  
-   Certifique\-se de que `Print` especifique um arquivo aberto para ou o modo de acesso `Output` ou o `Append`.  Se não, use uma declaração diferente para colocar dados no arquivo, ou reabra o arquivo no modo apropriado.  
  
-   Certifique\-se de que `Input` especifique um arquivo aberto para `Input`.  Se não, use uma declaração diferente para colocar dados no arquivo ou reabra o arquivo num modo apropriado.  
  
-   Se você está escrevendo num arquivo somente\-leitura, altere o estado ler\/escrever do arquivo e não tente escrever nele.  
  
-   Use a funcionalidade disponível no objeto `My.Computer.FileSystem`.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileSystem>   
 [Solucionando problemas: lendo e gravando em arquivos de texto](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)