---
title: "O nome &lt;membername&gt; n&#227;o &#233; compat&#237;vel com CLS | Microsoft Docs"
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
  - "bc40031"
  - "vbc40031"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40031"
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O nome &lt;membername&gt; n&#227;o &#233; compat&#237;vel com CLS
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um assembly está marcado como `<CLSCompliant(True)>` , mas expõe um membro com um nome que começa com um sublinhado \(`_`\).  
  
 Um elemento de programação pode conter um ou mais caracteres de sublinhado, mas para ser compatível com o [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), ele não deve começar com um sublinhado.  Consulte [Nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute> a um elemento de programação, você define o parâmetro `isCompliant` do atributo para `True` ou `False` para indicar compatibilidade ou incompatibilidade.  Não há padrão para este parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, ele vai ser considerado incompatível.  
  
 Por padrão, essa é uma mensagem de aviso.  Para informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **Identificação do erro:**  BC40031  
  
### Para corrigir este erro  
  
-   Se você tem controle sobre o código\-fonte, altere o nome do membro, de modo que ele não começa com um sublinhado.  
  
-   Se você precisar que o nome do membro permanecem inalteradas, remover o <xref:System.CLSCompliantAttribute> de sua definição ou marcá\-lo como `<CLSCompliant(False)>`.  Você ainda poderá marcar o assembly como `<CLSCompliant(True)>`.  
  
## Consulte também  
 [Nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3)