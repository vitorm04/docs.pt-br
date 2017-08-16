---
title: "A expressão tem o tipo &quot;&lt;typename&gt;&quot; que é um tipo restrito e não pode ser usado para acessar membros herdados de &quot;Object&quot; ou &quot;ValueType&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc31393
- vbc31393
dev_langs:
- VB
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
caps.latest.revision: 6
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
ms.openlocfilehash: aaedfd825889498159f92cbd1d615cc0064973d3
ms.lasthandoff: 03/13/2017

---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a>A expressão tem o tipo '&lt;typename&gt;' que é um tipo restrito e não pode ser usado para acessar membros herdados de 'Object' ou 'ValueType'
Uma expressão avaliada como um tipo que não pode ser convertido pelo common language runtime (CLR), mas acessa um membro que requer conversão.  
  
 *Conversão boxing* refere-se ao processamento necessário para converter um tipo para `Object` ou, ocasionalmente, para <xref:System.ValueType>.</xref:System.ValueType> O common language runtime não é possível caixa certos tipos de estrutura, por exemplo <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>e <xref:System.TypedReference>.</xref:System.TypedReference> </xref:System.RuntimeArgumentHandle> </xref:System.ArgIterator>  
  
 Essa expressão tenta usar o tipo restrito para chamar um método herdado de <xref:System.Object>ou <xref:System.ValueType>, como <xref:System.Object.GetHashCode%2A>ou <xref:System.Object.ToString%2A>.</xref:System.Object.ToString%2A> </xref:System.Object.GetHashCode%2A> </xref:System.ValueType> </xref:System.Object> Para acessar esse método, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tentou uma conversão boxing implícita que causa esse erro.  
  
 **ID do erro:** BC31393  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Localize a expressão que é avaliada como o tipo citado.  
  
2.  Localize a parte da sua declaração que tenta chamar o método herdado por <xref:System.Object>ou <xref:System.ValueType>.</xref:System.ValueType> </xref:System.Object>  
  
3.  Reescreva a instrução para evitar a chamada do método.  
  
## <a name="see-also"></a>Consulte também  
 [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
