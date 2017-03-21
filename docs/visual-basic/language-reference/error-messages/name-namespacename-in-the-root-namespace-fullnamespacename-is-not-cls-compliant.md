---
title: "Nome &lt;nomenamespace&gt; no namespace raiz &lt;fullnamespacename&gt; não é compatível com CLS | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40039
- bc40039
dev_langs:
- VB
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 344a0ca098160a8d9f5bc8281a941311f82000c4
ms.lasthandoff: 03/13/2017

---
# <a name="name-ltnamespacenamegt-in-the-root-namespace-ltfullnamespacenamegt-is-not-cls-compliant"></a>Nome &lt;nomenamespace&gt; no namespace raiz &lt;fullnamespacename&gt; não é compatível com CLS
Um assembly é marcado como `<CLSCompliant(True)>`, mas um elemento do nome do namespace raiz começa com um sublinhado (`_`).  
  
 Um elemento de programação pode conter um ou mais sublinhados, mas to ser compatível com o [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), ele não deve começar com um sublinhado. Consulte [nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute>para um elemento de programação, você definir o atributo `isCompliant` parâmetro como `True` ou `False` para indicar compatibilidade ou incompatibilidade.</xref:System.CLSCompliantAttribute> Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar o <xref:System.CLSCompliantAttribute>a um elemento, ele é considerado incompatível.</xref:System.CLSCompliantAttribute>  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40039  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se você precisar de compatibilidade com CLS, altere o nome do namespace raiz para que nenhum de seus elementos começa com um sublinhado.  
  
-   Se você precisar que o nome do namespace permanecem inalterados, em seguida, remova o <xref:System.CLSCompliantAttribute>do assembly ou marcá-lo como `<CLSCompliant(False)>`.</xref:System.CLSCompliantAttribute>  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [/RootNamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)   
 [Página de Aplicativo, Designer de Projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)   
 [Nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [\<PAVE em > escrevendo código compatível com CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
