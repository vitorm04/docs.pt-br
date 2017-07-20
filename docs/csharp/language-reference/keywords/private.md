---
title: "private (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- private_CSharpKeyword
- private
dev_langs:
- CSharp
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6af1e4d3cc97b2a43a912c8e0b59ac9f9e192a62
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="private-c-reference"></a>private (Referência de C#)
A palavra-chave `private` é um modificador de acesso de membro. Acesso particular é o nível de acesso menos permissivo. Membros particulares são acessíveis somente dentro do corpo da classe ou do struct em que são declarados, como neste exemplo:  
  
```  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  
  
 Tipos aninhados no mesmo corpo também podem acessar os membros particulares.  
  
 É um erro em tempo de compilação fazer referência a um membro particular fora da classe ou do struct em que ele é declarado.  
  
 Para obter uma comparação de `private` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md) e [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, a classe `Employee` contém dois membros de dados particulares, `name` e `salary`. Como membros particulares, eles não podem ser acessados, exceto por métodos de membro. Métodos públicos chamados `GetName` e `Salary` foram adicionados para permitir acesso controlado aos membros particulares. O membro `name` é acessado por meio de um método público e o membro `salary` é acessado por meio de uma propriedade somente leitura pública. (Consulte [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md) para obter mais informações.)  
  
 [!code-cs[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Níveis de Acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)
