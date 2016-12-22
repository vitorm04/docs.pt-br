---
title: "A primeira instru&#231;&#227;o deste &#39;Sub New&#39; deve ser uma chamada expl&#237;cita para MyBase.New&#39; ou &#39;MyClass.New&#39; porque &#39;&lt;constructorname&gt;&#39; na classe base &#39;&lt;baseclassname&gt;&#39; de &#39;&lt;derivedclassname&gt;&#39; est&#225; marcado como obsoleto: &#39;&lt;errormessage&gt;&#39; | Microsoft Docs"
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
  - "vbc30920"
  - "bc30920"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30920"
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A primeira instru&#231;&#227;o deste &#39;Sub New&#39; deve ser uma chamada expl&#237;cita para MyBase.New&#39; ou &#39;MyClass.New&#39; porque &#39;&lt;constructorname&gt;&#39; na classe base &#39;&lt;baseclassname&gt;&#39; de &#39;&lt;derivedclassname&gt;&#39; est&#225; marcado como obsoleto: &#39;&lt;errormessage&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um construtor de classes não chama um construtor de classe de base explicitamente, e o construtor da classe de base implícito está marcado com o atributo <xref:System.ObsoleteAttribute> e com a diretriz para tratá\-lo como um aviso.  
  
 Quando um construtor de classe derivada não chama um construtor de classe based, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tenta gerar uma chamda implícita para um construtor de classe de base livre de parâmetros.  Se não há construtor acessível na classe base que pode ser chamado sem argumentos, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não pode gerar uma chamada implícita.  Neste caso, o construtor exigido é marcado com o atributo <xref:System.ObsoleteAttribute>, então [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não pode chamá\-lo.  
  
 Você pode marcar qualquer elemento de programação como sendo não mais em uso aplicando\-lhe <xref:System.ObsoleteAttribute>.  Se você fizer isso, você pode determinar a propriedade <xref:System.ObsoleteAttribute.IsError%2A> do atributo para ou `True` ou `False`.  Se você configurá\-lo para `True`, o compilador trata uma tentativa de usar o elemento como um erro.  Se você configurá\-lo para `False`, ou deixá\-lo por padrão em `False`, o compilador emite um aviso se houver uma tentativa de se usar o elemento.  
  
 **Identificação do erro:**  BC30920  
  
### Para corrigir este erro  
  
1.  Examine a mensagem de erro citada e tome ações apropriadas.  
  
2.  Inclua uma chamada do `MyBase.New()` ou `MyClass.New()` como primeira declaração do `Sub New` na classe derivada.  
  
## Consulte também  
 [Atributos](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)