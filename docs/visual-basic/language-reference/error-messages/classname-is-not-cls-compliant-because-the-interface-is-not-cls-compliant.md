---
title: "'<classname>' não é compatível com CLS porque a interface '<interfacename>' implementada não é compatível com CLS"
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: 063c42249abbfb506fd15311659599b4777d397f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975540"
---
# <a name="classname-is-not-cls-compliant-because-the-interface-interfacename-it-implements-is-not-cls-compliant"></a>'\<classname >' não é compatível com CLS porque a interface '\<interfacename >' ele implementa não é compatível com CLS
Uma classe ou interface é marcado como `<CLSCompliant(True)>` quando ela deriva de ou implementa um tipo que está marcado como `<CLSCompliant(False)>` ou não está marcado.  
  
 Para uma classe ou interface seja compatível com o [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), sua hierarquia de herança inteira deve estar em conformidade. Isso significa que todos os tipos da qual ela herda, direta ou indiretamente, devem estar em conformidade. Da mesma forma, se uma classe implementa uma ou mais interfaces, eles devem todos ser compatíveis em suas hierarquias de herança.  
  
 Quando você aplica a <xref:System.CLSCompliantAttribute> a um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar a compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40029  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se você precisar de conformidade com CLS, defina este tipo em um esquema de implementação ou hierarquia de herança diferente.  
  
-   Se você precisar que esse tipo permaneça em seu esquema atual de implementação ou hierarquia de herança, remova os <xref:System.CLSCompliantAttribute> de sua definição ou marque-a como `<CLSCompliant(False)>`.  
