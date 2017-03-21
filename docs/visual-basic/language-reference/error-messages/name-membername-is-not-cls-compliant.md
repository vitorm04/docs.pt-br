---
title: "Nome &lt;membername&gt; não é compatível com CLS | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40031
- vbc40031
dev_langs:
- VB
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
caps.latest.revision: 9
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
ms.openlocfilehash: 6a678c66580a7917a3869aac81418152130debff
ms.lasthandoff: 03/13/2017

---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a>Nome &lt;membername&gt; não é compatível com CLS
Um assembly é marcado como `<CLSCompliant(True)>` , mas expõe um membro com um nome que começa com um sublinhado (`_`).  
  
 Um elemento de programação pode conter um ou mais sublinhados, mas to ser compatível com o [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), ele não deve começar com um sublinhado. Consulte [nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute>para um elemento de programação, você definir o atributo `isCompliant` parâmetro como `True` ou `False` para indicar compatibilidade ou incompatibilidade.</xref:System.CLSCompliantAttribute> Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar o <xref:System.CLSCompliantAttribute>a um elemento, ele é considerado incompatível.</xref:System.CLSCompliantAttribute>  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40031  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se você tem controle sobre o código-fonte, altere o nome do membro para que ele não começa com um sublinhado.  
  
-   Se você precisar que o nome do membro permaneça inalterado, remova o <xref:System.CLSCompliantAttribute>da sua definição ou marque-a como `<CLSCompliant(False)>`.</xref:System.CLSCompliantAttribute> Você ainda poderá marcar o assembly como `<CLSCompliant(True)>`.  
  
## <a name="see-also"></a>Consulte também  
 [Nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [\<PAVE em > escrevendo código compatível com CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
