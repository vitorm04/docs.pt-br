---
title: Nome &lt;membername&gt; não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 26ff13de461d5a96724868b7928129a326cdf1d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a>Nome &lt;membername&gt; não é compatível com CLS
Um assembly é marcado como `<CLSCompliant(True)>` , mas expõe um membro com um nome que começa com um sublinhado (`_`).  
  
 Um elemento de programação pode conter um ou mais sublinhados, mas to estar em conformidade com a [independência da linguagem e componentes independentes da linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele não deve começar com um sublinhado. Consulte [declarado nomes de elemento](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
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

