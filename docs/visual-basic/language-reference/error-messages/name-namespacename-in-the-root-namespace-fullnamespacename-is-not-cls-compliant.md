---
title: "O nome &lt;namespacename&gt; no namespace raiz &lt;fullnamespacename&gt; n&#227;o &#233; compat&#237;vel com CLS | Microsoft Docs"
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
  - "vbc40039"
  - "bc40039"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40039"
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O nome &lt;namespacename&gt; no namespace raiz &lt;fullnamespacename&gt; n&#227;o &#233; compat&#237;vel com CLS
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um assembly está marcado como `<CLSCompliant(True)>`, mas um elemento do nome do namespace raiz começa com um sublinhado \(`_`\).  
  
 Um elemento de programação pode conter um ou mais sublinhados, mas para ser compatível com o [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), ele não deve começar com um sublinhado.  Veja [Nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute> a um elemento de programação, você define o parâmetro `isCompliant` do atributo para `True` ou `False` para indicar compatibilidade ou incompatibilidade.  Não há padrão para este parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, ele vai ser considerado incompatível.  
  
 Por padrão, este mensagem é um aviso.  Para informações sobre esconder avisos ou tratar avisos como erros, veja [Configurando avisos no Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **Identificação do erro:** BC40039  
  
### Para corrigir este erro  
  
-   Se você precisar de compatibilidade com CLS, altere o nome do namespace raiz para que nenhum dos seus elementos começa com um sublinhado.  
  
-   Se você solicitar o nome do namespace permanecem inalteradas, remover o <xref:System.CLSCompliantAttribute> do assembly ou marcá\-lo como `<CLSCompliant(False)>`.  
  
## Consulte também  
 [Instrução Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [\/rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)   
 [Página de Aplicativo, Designer de Projeto \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)   
 [Nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3)