---
title: "A propriedade padr&#227;o &#39;&lt;propertyname1&gt;&#39; est&#225; em conflito com a propriedade padr&#227;o &#39;&lt;propertyname2&gt;&#39; em &#39;&lt;classname&gt;&#39; e por isso deve ser declarada como &#39;Shadows&#39; | Microsoft Docs"
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
  - "vbc40007"
  - "bc40007"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40007"
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A propriedade padr&#227;o &#39;&lt;propertyname1&gt;&#39; est&#225; em conflito com a propriedade padr&#227;o &#39;&lt;propertyname2&gt;&#39; em &#39;&lt;classname&gt;&#39; e por isso deve ser declarada como &#39;Shadows&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma propriedade é declarada com o mesmo nome de uma propriedade definida na classe base.  Nesta situação, a propriedade nessa classe deve sombrear a propriedade na classe base.  
  
 Por padrão, esta é uma mensagem de aviso.  `Shadows`é assumido por padrão.  Para maiores informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **Identificação do erro:**  BC40007  
  
### Para corrigir este erro  
  
-   Adicionar a palavra\-chave`Shadows` à declaração, ou alterar o nome da propriedade que está sendo declarada.  
  
## Consulte também  
 [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)