---
title: "Valor de soma de verifica&#231;&#227;o incorreto, d&#237;gitos n&#227;o hexadecimais ou n&#250;mero &#237;mpar de d&#237;gitos hexadecimais | Microsoft Docs"
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
  - "bc42033"
  - "vbc42033"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42033"
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Valor de soma de verifica&#231;&#227;o incorreto, d&#237;gitos n&#227;o hexadecimais ou n&#250;mero &#237;mpar de d&#237;gitos hexadecimais
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um valor de soma de verificação contém dígitos hexadecimais inválidos ou um número ímpar de dígitos.  
  
 Quando o ASP.NET gera um arquivo de origem do Visual Basic \(extensão .vb\), ele calcula uma soma de verificação e a coloca em um arquivo de origem oculto identificado por `#externalchecksum`.  Um usuário também pode gerar um arquivo .vb para isso, mas é melhor deixar esse processo para uso interno.  
  
 Por padrão, esta mensagem é um aviso.  Para informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **Identificação do erro:** BC42033  
  
### Para corrigir este erro  
  
1.  Se o ASP.NET estiver gerando o arquivo de origem do Visual Basic, reinicie a compilação do projeto.  
  
2.  Se esse aviso persistir após a reinicialização, reinstale o ASP.NET e tente compilar novamente.  
  
3.  Se o aviso ainda persistir, ou se você não estiver usando o ASP.NET, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.  
  
## Consulte também  
 [ASP.NET Overview](../Topic/ASP.NET%20Overview.md)   
 [Fale conosco](/visual-studio/ide/talk-to-us)