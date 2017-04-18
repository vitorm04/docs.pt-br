---
title: "Não é possível referenciar &quot;&lt;nome&gt;&quot;porque ele é membro do campo de tipo de valor&quot;&lt;nome&gt;&quot;da classe&quot;&lt;classname&gt;&quot; que tem &quot;System. MarshalByRefObject&quot; como uma classe base | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30310
- bc30310
dev_langs:
- VB
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 790078438c0ba608bcb3fe80a409094b99cf5653
ms.lasthandoff: 03/13/2017

---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a>Não é possível referenciar '&lt;nome&gt;'porque ele é membro do campo de tipo de valor'&lt;nome&gt;'da classe'&lt;classname&gt;' que tem 'System. MarshalByRefObject' como uma classe base
O `System.MarshalByRefObject` classe permite que os aplicativos que oferecem suporte a acesso remoto a objetos nos limites do domínio de aplicativo. Tipos devem herdar do `MarshalByRejectObject` classe quando o tipo é usado nos limites do domínio de aplicativo. O estado do objeto não deve ser copiado porque os membros do objeto não são utilizáveis fora do domínio de aplicativo no qual eles foram criados.  
  
 **ID do erro:** BC30310  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique a referência para certificar-se de que o membro sendo referenciado é válido.  
  
2.  Qualifique explicitamente o membro com o `Me` palavra-chave.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.MarshalByRefObject></xref:System.MarshalByRefObject>   
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
