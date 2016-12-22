---
title: "O acessador &#39;Set&#39; da propriedade &#39;&lt;propertyname&gt;&#39; n&#227;o est&#225; acess&#237;vel | Microsoft Docs"
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
  - "vbc31102"
  - "bc31102"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31102"
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O acessador &#39;Set&#39; da propriedade &#39;&lt;propertyname&gt;&#39; n&#227;o est&#225; acess&#237;vel
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma declaração tenta recuperar o valor de uma propriedade quando ela não tem acesso ao procedimento `Set` da propriedade.  
  
 Se a [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md) está marcada com um nível de acesso mais restritivo que sua [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md),uma tentativa de ler o valor da propriedade pode falhar nos seguintes casos:  
  
-   A declaração `Set` está marcada [Particular](../../../visual-basic/language-reference/modifiers/private.md) e o código que a chama está fora da classe ou estrutura onde a propriedade foi definida.  
  
-   A declaração `Set` está marcada [Protegido](../../../visual-basic/language-reference/modifiers/protected.md) e o código que a chama está fora da classe ou estrutura onde a propriedade foi definida, nem numa classe derivada.  
  
-   A declaração `Set` está marcada [Friend](../../../visual-basic/language-reference/modifiers/friend.md) e o código que a chama não está no mesmo assembly no qual a propriedade é definida.  
  
 **Identificação do erro:**  BC31102  
  
### Para corrigir este erro  
  
-   Se você tem controle do código fonte definindo a propriedade, considere declarando o procedimento `Set` com o mesmo nível de acesso que a própria propriedade.  
  
-   Se você não tem controle do código fonte definindo a propriedade, você deve restringir o nível de acesso do procedimento `Set` mais que a própria propriedade, tente mover a declaração que lê o valor da propriedade para um região de código que tem um melhor acesso à propriedade.  
  
## Consulte também  
 [Procedimentos de propriedade](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Como declarar uma propriedade com níveis de acesso mistos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)