---
title: "private (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "private_CSharpKeyword"
  - "private"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave private [C#]"
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# private (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `private` palavra\-chave é um modificador de acesso de membro.  Acesso privado é o nível de acesso menos permissivo.  Membros particulares são acessíveis somente dentro do corpo da classe ou estrutura em que são declaradas, como no exemplo:  
  
```  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  
  
 Tipos aninhados no mesmo corpo também podem acessar esses membros particulares.  
  
 Ele é um erro de tempo de compilação para fazer referência a um membro privado, fora da classe ou estrutura na qual é declarada.  
  
 Para obter uma comparação de `private` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md) e [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
## Exemplo  
 Neste exemplo, o `Employee` classe contém dois membros de dados privados, `name` e `salary`.  Como membros privados, eles não podem ser acessados, exceto pelos métodos de membro.  Métodos públicos chamados `GetName` e `Salary` são adicionados para permitir o acesso controlado para os membros privados.  O `name` membro é acessado por meio de um método público e o `salary` membro é acessado por meio de uma propriedade pública de somente leitura.  \(Consulte [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md) para obter mais informações.\)  
  
 [!code-cs[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)