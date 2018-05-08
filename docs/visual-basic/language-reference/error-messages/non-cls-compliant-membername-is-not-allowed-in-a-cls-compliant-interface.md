---
title: Não compatível com CLS &lt;membername&gt; não é permitido em uma interface compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: ee533df5e06352034b24651b9173a88d090da0a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a>Não compatível com CLS &lt;membername&gt; não é permitido em uma interface compatível com CLS
Uma propriedade, procedimento ou evento em uma interface está marcado como `<CLSCompliant(True)>` quando a própria interface está marcada como `<CLSCompliant(False)>` ou não está marcado.  
  
 Para uma interface para ser compatível com o [independência da linguagem e componentes independentes da linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), todos os seus membros devem ser compatíveis.  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute> para um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40033  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se você precisar de compatibilidade com CLS e tem controle sobre o código de origem da interface, marque a interface como `<CLSCompliant(True)>` se todos os seus membros são compatíveis.  
  
-   Se você precisar de compatibilidade com CLS e não tem controle sobre o código de origem da interface, ou se ele não está qualificada para ser compatível, defina este membro dentro de uma interface diferente.  
  
-   Se você precisar que esse membro permaneça em sua interface atual, remova o <xref:System.CLSCompliantAttribute> da sua definição ou marque-a como `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
 
