---
title: "'<elementname>' está obsoleto (aviso do Visual Basic)"
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: c6d927ef6681838d8a77a0c6018eb6bbe30913e8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255855"
---
# <a name="elementname-is-obsolete-visual-basic-warning"></a>'\<elementname >' é obsoleto (aviso do Visual Basic)
Uma instrução tenta acessar um elemento de programação que foi marcado com o <xref:System.ObsoleteAttribute> atributo e a diretiva para tratá-lo como um aviso.  
  
 Você pode marcar qualquer elemento de programação como sendo não mais em uso por meio da aplicação <xref:System.ObsoleteAttribute> a ele. Se você fizer isso, você pode definir o atributo <xref:System.ObsoleteAttribute.IsError%2A> propriedade para um `True` ou `False`. Se você defini-lo como `True`, o compilador trata uma tentativa de usar o elemento como um erro. Se você defini-lo `False`, ou deixá-lo como padrão `False`, o compilador emitirá um aviso se não houver uma tentativa de usar o elemento.  
  
 Por padrão, essa mensagem é um aviso, porque o <xref:System.ObsoleteAttribute.IsError%2A> propriedade de <xref:System.ObsoleteAttribute> é `False`. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40008  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Certifique-se de que a referência do código-fonte é o nome do elemento digitado corretamente.  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)
