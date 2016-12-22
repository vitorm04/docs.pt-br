---
title: "Acessando dados do usu&#225;rio (Visual Basic) | Microsoft Docs"
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
  - "dados [Visual Basic], acessando dados do usuário"
  - "nomes de domínios, recuperando"
  - "exemplos [Visual Basic], acessando dados do usuário"
  - "nomes de login"
  - "Objeto My.User, tarefas"
  - "dados do usuário, acessando"
  - "dados do usuário, domínio"
  - "nomes de usuário, recuperando"
ms.assetid: 32492a15-ee59-4a63-a1f1-9b24cc13140a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Acessando dados do usu&#225;rio (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Esta seção contém tópicos tratando do objeto `My.User` e das tarefas que você pode realizar com ele.  
  
 O objeto `My.User` fornece acesso a informações sobre o usuário conectado, retornando um objeto que implementa a interface <xref:System.Security.Principal.IPrincipal>.  
  
## Tarefas  
  
|Para|Consulte|  
|----------|--------------|  
|Obter nome de login do usuário|<xref:Microsoft.VisualBasic.ApplicationServices.User.Name%2A>|  
|Obter nome de domínio do usuário, se o aplicativo usa autenticação do Windows|<xref:Microsoft.VisualBasic.ApplicationServices.User.CurrentPrincipal>|  
|Determinar a função do usuário|<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>|  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>