---
title: A expressão tem o tipo '<typename>', que é um tipo restrito e não pode ser usado para acessar membros herdados de 'Object' ou 'ValueType'
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 017a2458562068727674bd3fd9cda8c33d989e8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803162"
---
# <a name="expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a>Expressão tem o tipo '\<typename >' que é um tipo restrito e não pode ser usado para acessar membros herdados de 'Object' ou 'ValueType'
Uma expressão é avaliada como um tipo que não pode ser convertido pelo common language runtime (CLR), mas acessa um membro que requer conversão boxing.  
  
 *Conversão boxing* refere-se ao processamento necessário para converter um tipo para `Object` ou, às vezes, para <xref:System.ValueType>. O common language runtime não pode encaixotar certos tipos de estrutura, por exemplo <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, e <xref:System.TypedReference>.  
  
 Essa expressão tenta usar o tipo restrito para chamar um método herdado de <xref:System.Object> ou <xref:System.ValueType>, como <xref:System.Object.GetHashCode%2A> ou <xref:System.Object.ToString%2A>. Para acessar esse método, Visual Basic foi tentada uma conversão boxing implícita que causa esse erro.  
  
 **ID do erro:** BC31393  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Localize a expressão que é avaliada como o tipo citado.  
  
2. Localize a parte da sua declaração que tenta chamar o método herdado de <xref:System.Object> ou <xref:System.ValueType>.  
  
3. Reescreva a instrução para evitar a chamada de método.  
  
## <a name="see-also"></a>Consulte também

- [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
