---
title: "'<classname>' não é compatível com CLS porque a interface '<interfacename>' implementada não é compatível com CLS"
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: 24a0866544cc3cd058672d18c6a7670b0b1bb489
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584214"
---
# <a name="classname-is-not-cls-compliant-because-the-interface-interfacename-it-implements-is-not-cls-compliant"></a>'\<classname >' não é compatível com CLS porque a interface '\<interfacename >' ele implementa não é compatível com CLS
Uma classe ou interface é marcado como `<CLSCompliant(True)>` quando ela deriva de ou implementa um tipo que está marcado como `<CLSCompliant(False)>` ou não está marcado.  
  
 Para uma classe ou interface seja compatível com o [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), sua hierarquia de herança inteira deve estar em conformidade. Isso significa que todos os tipos da qual ela herda, direta ou indiretamente, devem estar em conformidade. Da mesma forma, se uma classe implementa uma ou mais interfaces, eles devem todos ser compatíveis em suas hierarquias de herança.  
  
 Quando você aplica a <xref:System.CLSCompliantAttribute> a um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar a compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40029  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Se você precisar de conformidade com CLS, defina este tipo em um esquema de implementação ou hierarquia de herança diferente.  
  
- Se você precisar que esse tipo permaneça em seu esquema atual de implementação ou hierarquia de herança, remova os <xref:System.CLSCompliantAttribute> de sua definição ou marque-a como `<CLSCompliant(False)>`.  
