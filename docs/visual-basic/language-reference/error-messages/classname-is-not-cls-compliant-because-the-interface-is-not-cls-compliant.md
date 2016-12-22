---
title: "&#39;&lt;classname&gt;&#39; n&#227;o &#233; compat&#237;vel com CLS porque a interface &#39;&lt;interfacename&gt;&#39; implementada n&#227;o &#233; compat&#237;vel com CLS | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40029"
  - "vbc40029"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40029"
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;classname&gt;&#39; n&#227;o &#233; compat&#237;vel com CLS porque a interface &#39;&lt;interfacename&gt;&#39; implementada n&#227;o &#233; compat&#237;vel com CLS
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma classe ou interface está marcada como `<CLSCompliant(True)>` quando ela deriva de ou implementa um tipo que está marcado como `<CLSCompliant(False)>` ou não está marcado.  
  
 Para que uma classe ou interface seja compatível com o [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), sua hierarquia de herança inteira deve ser compatível.  Isso significa que todos os tipos dos quais ela herda, direta ou indiretamente, devem ser compatíveis.  Da mesma forma, se uma classe implementa uma ou mais interfaces, todas elas devem ser compatíveis em suas hierarquias de herança.  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute> a um elemento de programação, você define o parâmetro `isCompliant` do atributo para `True` ou `False` para indicar compatibilidade ou incompatibilidade.  Não há padrão para este parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, ele vai ser considerado incompatível.  
  
 Por padrão, essa é uma mensagem de aviso.  Para informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **Identificação do erro:**  BC40029  
  
### Para corrigir este erro  
  
-   Se você precisar de conformidade CLS, defina este tipo em uma hierarquia de herança ou implementação de esquema diferente.  
  
-   Se você precisar que esse tipo permaneça em sua hierarquia de herança ou esquema de implementação atual, remova o <xref:System.CLSCompliantAttribute> de sua definição ou marque\-o como `<CLSCompliant(False)>`.  
  
## Consulte também  
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3)