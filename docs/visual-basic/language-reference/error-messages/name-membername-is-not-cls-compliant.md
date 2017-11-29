---
title: "Nome &lt;membername&gt; não é compatível com CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords: BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7f574c2ebd71dbe06c4a687728e7812a18c8a949
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a>Nome &lt;membername&gt; não é compatível com CLS
Um assembly é marcado como `<CLSCompliant(True)>` , mas expõe um membro com um nome que começa com um sublinhado (`_`).  
  
 Um elemento de programação pode conter um ou mais sublinhados, mas to estar em conformidade com a [independência da linguagem e componentes independentes da linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), ele não deve começar com um sublinhado. Consulte [declarado nomes de elemento](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute> para um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40031  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se você tem controle sobre o código-fonte, altere o nome de membro para que ele não começa com um sublinhado.  
  
-   Se você precisar que o nome do membro permanecem inalteradas, remova o <xref:System.CLSCompliantAttribute> da sua definição ou marque-a como `<CLSCompliant(False)>`. Você ainda poderá marcar o assembly como `<CLSCompliant(True)>`.  
  
## <a name="see-also"></a>Consulte também  
 [Nomes de Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [\<PAVE sobre > escrevendo código compatível com CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
