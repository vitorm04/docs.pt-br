---
title: Não pode se referir a &#39; &lt;nome&gt; &#39; porque ele é um membro do campo tipo de valor de &#39; &lt;nome&gt; &#39; da classe &#39; &lt;classname&gt; &#39;que tem &#39;System. MarshalByRefObject&#39; como uma classe base
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: a6298c3e0f5102397d5cc3f237a186598c6b5ecc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739291"
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a>Não pode se referir a &#39; &lt;nome&gt; &#39; porque ele é um membro do campo tipo de valor de &#39; &lt;nome&gt; &#39; da classe &#39; &lt;classname&gt; &#39;que tem &#39;System. MarshalByRefObject&#39; como uma classe base
O `System.MarshalByRefObject` classe permite que os aplicativos que dão suporte ao acesso remoto a objetos entre limites de domínio de aplicativo. Tipos devem herdar a `MarshalByRejectObject` classe quando o tipo é usado entre os limites de domínio de aplicativo. O estado do objeto não deve ser copiado porque os membros do objeto não são utilizáveis fora do domínio de aplicativo no qual eles foram criados.  
  
 **ID do erro:** BC30310  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se a referência para garantir que o membro que está sendo referenciado é válido.  
  
2.  Qualifique explicitamente o membro com o `Me` palavra-chave.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.MarshalByRefObject>
- [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
