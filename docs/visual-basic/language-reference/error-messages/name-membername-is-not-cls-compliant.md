---
title: Nome da &lt;membername&gt; não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: b950be530eb80fd1c65b48e1625eb344c642d260
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626362"
---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a>Nome da &lt;membername&gt; não é compatível com CLS
Um assembly é marcado como `<CLSCompliant(True)>` , mas expõe um membro com um nome que começa com um sublinhado (`_`).  
  
 Um elemento de programação pode conter um ou mais sublinhados, mas to estar em conformidade com o [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele não deve começar com um sublinhado. Ver [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Quando você aplica a <xref:System.CLSCompliantAttribute> a um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar a compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40031  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se você tem controle sobre o código-fonte, altere o nome do membro para que ele não começa com um sublinhado.  
  
-   Se você precisar que o nome do membro permanecem inalterados, remova os <xref:System.CLSCompliantAttribute> de sua definição ou marque-a como `<CLSCompliant(False)>`. Você ainda poderá marcar o assembly como `<CLSCompliant(True)>`.  
  
## <a name="see-also"></a>Consulte também
- [Nomes de Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)

