---
title: Não é possível fazer referência a '<name>' porque ele é um membro do campo de tipo de valor '<name>' da classe '<classname>' que tem 'System.MarshalByRefObject' como uma classe base
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: c29d3def2299dc1d7e3b084b3408b3f919addc63
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279573"
---
# <a name="cannot-refer-to-name-because-it-is-a-member-of-the-value-typed-field-name-of-class-classname-which-has-systemmarshalbyrefobject-as-a-base-class"></a>Não é possível referenciar '\<nome >' porque ele é um membro do campo de tipo de valor '\<nome >' da classe\<classname >' que tem 'System. MarshalByRefObject' como uma classe base
O `System.MarshalByRefObject` classe permite que os aplicativos que dão suporte ao acesso remoto a objetos entre limites de domínio de aplicativo. Tipos devem herdar a `MarshalByRejectObject` classe quando o tipo é usado entre os limites de domínio de aplicativo. O estado do objeto não deve ser copiado porque os membros do objeto não são utilizáveis fora do domínio de aplicativo no qual eles foram criados.  
  
 **ID do erro:** BC30310  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se a referência para garantir que o membro que está sendo referenciado é válido.  
  
2.  Qualifique explicitamente o membro com o `Me` palavra-chave.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.MarshalByRefObject>
- [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
