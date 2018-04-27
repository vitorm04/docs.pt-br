---
title: A expressão tem o tipo &#39; &lt;typename&gt; &#39; que é um tipo restrito e não pode ser usado para acessar membros herdados de &#39;objeto&#39; ou &#39;ValueType&#39;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ab4e48c93a6a3c645bf9b5cc6c536d418022ae86
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a>A expressão tem o tipo &#39; &lt;typename&gt; &#39; que é um tipo restrito e não pode ser usado para acessar membros herdados de &#39;objeto&#39; ou &#39;ValueType&#39;
Uma expressão é avaliada como um tipo que não pode ser convertido pelo common language runtime (CLR), mas acessa um membro que requer conversão.  
  
 *Conversão boxing* refere-se ao processamento necessário para converter um tipo para `Object` ou, ocasionalmente, <xref:System.ValueType>. O common language runtime não é possível caixa certos tipos de estrutura, por exemplo <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, e <xref:System.TypedReference>.  
  
 Essa expressão tenta usar o tipo restrito para chamar um método herdado de <xref:System.Object> ou <xref:System.ValueType>, como <xref:System.Object.GetHashCode%2A> ou <xref:System.Object.ToString%2A>. Para acessar esse método, o Visual Basic tentou uma conversão boxing implícita que causa esse erro.  
  
 **ID do erro:** BC31393  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Localize a expressão que é avaliada como o tipo citado.  
  
2.  Localize a parte da sua declaração que tenta chamar o método herdado de <xref:System.Object> ou <xref:System.ValueType>.  
  
3.  Reescreva a instrução para evitar a chamada do método.  
  
## <a name="see-also"></a>Consulte também  
 [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
