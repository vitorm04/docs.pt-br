---
title: "&#39;&lt;elementname&gt;&#39; est&#225; obsoleto (aviso do Visual Basic) | Microsoft Docs"
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
  - "vbc40008"
  - "bc40008"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40008"
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;elementname&gt;&#39; est&#225; obsoleto (aviso do Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma declaração tenta acessar um elemento de programação que foi marcado com o atributo <xref:System.ObsoleteAttribute> e a diretriz de tratá\-lo como um aviso.  
  
 Você pode marcar qualquer elemento de programação como sendo não mais em uso aplicando\-lhe <xref:System.ObsoleteAttribute>.  Se você fizer isso, você pode determinar a propriedade <xref:System.ObsoleteAttribute.IsError%2A> do atributo para ou `True` ou `False`.  Se você configurá\-lo para `True`, o compilador trata uma tentativa de usar o elemento como um erro.  Se você configurá\-lo para `False`, ou deixá\-lo por padrão em `False`, o compilador emite um aviso se houver uma tentativa de se usar o elemento.  
  
 Por padrão, essa mensagem é um aviso, porque a propriedade <xref:System.ObsoleteAttribute.IsError%2A> de <xref:System.ObsoleteAttribute> é `False`.  Para maiores informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **Identificação do erro:**  BC40008  
  
### Para corrigir este erro  
  
-   Assegure\-se de que a referência do código\-fonte está grafando o nome do elemento corretamente.  
  
## Consulte também  
 [Atributos](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)