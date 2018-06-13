---
title: Não é possível referenciar &#39; &lt;nome&gt; &#39; porque ele é um membro do campo de tipo de valor &#39; &lt;nome&gt; &#39; da classe &#39; &lt;classname&gt; &#39;que tem &#39;MarshalByRefObject&#39; como uma classe base
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: f44d33c9d51148e6bbcfbf5db4dbc115101df1f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586341"
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a>Não é possível referenciar &#39; &lt;nome&gt; &#39; porque ele é um membro do campo de tipo de valor &#39; &lt;nome&gt; &#39; da classe &#39; &lt;classname&gt; &#39;que tem &#39;MarshalByRefObject&#39; como uma classe base
O `System.MarshalByRefObject` classe permite que os aplicativos que oferecem suporte a acesso remoto a objetos nos limites do domínio de aplicativo. Tipos devem herdar do `MarshalByRejectObject` classe quando o tipo é usado além dos limites do domínio de aplicativo. O estado do objeto não deve ser copiado porque os membros do objeto não são utilizáveis fora do domínio de aplicativo no qual eles foram criados.  
  
 **ID do erro:** BC30310  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se a referência para certificar-se de que o membro que está sendo referenciado é válido.  
  
2.  Qualifique explicitamente o membro com o `Me` palavra-chave.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.MarshalByRefObject>  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
