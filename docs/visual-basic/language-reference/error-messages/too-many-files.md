---
title: "Muitos arquivos | Microsoft Docs"
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
  - "vbrID67"
dev_langs: 
  - "VB"
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Muitos arquivos
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O mais arquivos foram criados no diretório raiz que o sistema operacional permite, ou mais arquivos foram abertos que o número especificado no **arquivos \=** definição no arquivo CONFIG. Arquivo SYS.  
  
### Para corrigir este erro  
  
1.  Se o seu programa é abrir, fechar ou salvar arquivos no diretório raiz, altere seu programa para que ele use um subdiretório.  
  
2.  Aumentar o número de arquivos especificados no seu **arquivos \=** definição no arquivo CONFIG. SYS e reinicie o computador.  
  
## Consulte também  
 [Tipos de erro](../../../visual-basic/programming-guide/language-features/error-types.md)