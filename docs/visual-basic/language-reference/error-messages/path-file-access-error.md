---
title: "Erro de acesso ao caminho/arquivo | Microsoft Docs"
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
  - "vbrID75"
dev_langs: 
  - "VB"
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Erro de acesso ao caminho/arquivo
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Durante uma operação de acesso de arquivo ou disco, o sistema operacional não pôde estabelecer uma conexão entre o caminho e o nome de arquivo.  
  
### Para corrigir este erro  
  
1.  Certifique\-se de que a especificação de arquivo está corretamente formatada.  Um nome de arquivo pode conter um caminho totalmente qualificado \(absoluto\) ou um caminho relativo.  Um caminho totalmente qualificado inicia com o nome do drive \(se o caminho estiver em outro drive\) e lista o caminho específico da raiz do arquivo.  Qualquer caminho que não é totalmente qualificado é relativo com relação ao drive e diretório atuais.  
  
2.  Certifique\-se de que você não tentou salvar o arquivo que substituiria um arquivo somente\-leitura existente.  Se este é o caso, modifique o atributo somente\-leitura do arquivo de destino ou salve o arquivo com um nome de arquivo diferente.  
  
3.  Verifique se você não tentou abrir um arquivo somente leitura no seqüencial`Output`ou `Append` modo.  Se este é o caso, abra o arquivo no modo `Input` ou modifique o atributo somente\-leitura do arquivo.  
  
4.  Certifique\-se de que você não tentou modificar um projeto [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] dentro de uma base de dados ou documento.  
  
## Consulte também  
 [Tipos de erro](../../../visual-basic/programming-guide/language-features/error-types.md)