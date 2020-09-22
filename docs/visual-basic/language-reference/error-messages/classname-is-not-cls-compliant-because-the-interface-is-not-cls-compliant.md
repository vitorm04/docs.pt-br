---
title: "'<classname>' não é compatível com CLS porque a interface '<interfacename>' implementada não é compatível com CLS"
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: a482d14094a3fa86b56ca84af46c45e6093416c5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874622"
---
# <a name="classname-is-not-cls-compliant-because-the-interface-interfacename-it-implements-is-not-cls-compliant"></a>'\<classname>' não é compatível com CLS porque a interface '\<interfacename>' implementada não é compatível com CLS

Uma classe ou interface é marcada como `<CLSCompliant(True)>` quando deriva de ou implementa um tipo que está marcado como `<CLSCompliant(False)>` ou não está marcado.  
  
 Para que uma classe ou interface seja compatível com a [independência de linguagem e com os componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), sua hierarquia de herança inteira deve ser compatível. Isso significa que todos os tipos dos quais ele herda, direta ou indiretamente, devem ser compatíveis. Da mesma forma, se uma classe implementa uma ou mais interfaces, todas elas devem estar em conformidade em suas hierarquias de herança.  
  
 Quando você aplica o a <xref:System.CLSCompliantAttribute> um elemento de programação, você define o parâmetro do atributo `isCompliant` como `True` ou `False` para indicar conformidade ou não conformidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, será considerado como não compatível.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40029  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Se você precisar de conformidade com CLS, defina esse tipo em uma hierarquia de herança ou esquema de implementação diferente.  
  
- Se você precisar que esse tipo permaneça em sua hierarquia de herança ou esquema de implementação atual, remova o <xref:System.CLSCompliantAttribute> de sua definição ou marque-o como `<CLSCompliant(False)>` .  
