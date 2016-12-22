---
title: "Valor do tipo &#39;type1&#39; n&#227;o pode ser convertido em &#39;type2&#39; | Microsoft Docs"
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
  - "vbc31194"
  - "bc31194"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31194"
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Valor do tipo &#39;type1&#39; n&#227;o pode ser convertido em &#39;type2&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Valor do tipo 'Type 1' não pode ser convertido em 'Tipo2'.Você pode usar a propriedade 'Value' para obter o valor do primeiro elemento da sequência de caracteres de '\< ElementoPai \>'.  
  
 Foi feita uma tentativa para converter implicitamente um literal XML para um tipo específico.  O literal XML não pode ser convertido implicitamente para o tipo especificado.  
  
 **Identificação do erro:**  BC31194  
  
### Para corrigir este erro  
  
-   Use a propriedade `Value` do literal XML para referenciar seu valor como uma `String`.  Use a função `CType`, outra função de conversão de tipos ou a classe <xref:System.Convert> para converter o valor para o tipo especificado.  
  
## Consulte também  
 <xref:System.Convert>   
 [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)