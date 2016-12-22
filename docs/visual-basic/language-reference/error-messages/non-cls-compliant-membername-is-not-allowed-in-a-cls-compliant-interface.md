---
title: "&lt;membername&gt; n&#227;o compat&#237;vel com CLS n&#227;o &#233; permitido em uma interface compat&#237;vel com CLS | Microsoft Docs"
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
  - "bc40033"
  - "vbc40033"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40033"
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;membername&gt; n&#227;o compat&#237;vel com CLS n&#227;o &#233; permitido em uma interface compat&#237;vel com CLS
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma propriedade, procedimento ou evento em uma interface está marcado como `<CLSCompliant(True)>` quando a própria interface está marcada como `<CLSCompliant(False)>` ou não está marcada.  
  
 Para uma interface ser compatível com o [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), todos os seus membros devem ser compatíveis.  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute> a um elemento de programação, você define o parâmetro `isCompliant` do atributo para `True` ou `False` para indicar compatibilidade ou incompatibilidade.  Não há padrão para este parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, ele vai ser considerado incompatível.  
  
 Por padrão, essa é uma mensagem de aviso.  Para informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **Identificação do erro:**  BC40033  
  
### Para corrigir este erro  
  
-   Se você necessita de compatibilidade CLS e tem controle sobre o código\-fonte da interface, marque a interface como `<CLSCompliant(True)>` se todos os seus membros forem compatíveis.  
  
-   Se você necessita de compatibilidade com CLS e não tem controle sobre o código\-fonte da interface, ou se ela não for compatível, defina este membro numa classe diferente.  
  
-   Se você precisa que esse membro permaneça em sua interface atual, remova sua definição de <xref:System.CLSCompliantAttribute> ou marque\-a como `<CLSCompliant(False)>`.  
  
## Consulte também  
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3)