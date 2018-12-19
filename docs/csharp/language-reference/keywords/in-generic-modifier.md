---
title: in (modificador genérico) – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: ea11fabd7974c67b1f1b3af017db1f34178bfae8
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238592"
---
# <a name="in-generic-modifier-c-reference"></a>in (modificador genérico) (Referência de C#)

Para parâmetros de tipo genérico, a palavra-chave `in` especifica que o parâmetro de tipo é contravariante. Você pode usar a palavra-chave `in` em delegados e interfaces genéricas.

A contravariância permite que você use um tipo menos derivado do que aquele especificado pelo parâmetro genérico. Isso permite a conversão implícita de classes que implementam interfaces variantes e a conversão implícita de tipos delegados. A covariância e a contravariância em parâmetros de tipo genérico têm suporte para tipos de referência, mas não para tipos de valor.

Um tipo pode ser declarado como contravariante em uma interface genérica ou como delegado somente se ele define o tipo de parâmetros de um método e não o tipo de retorno de um método. Os parâmetros `In`, `ref` e `out` precisam ser invariáveis, ou seja, nem covariantes nem contravariantes.

Uma interface que tem um parâmetro de tipo contravariante permite que os seus métodos aceitem argumentos de tipos menos derivados que aqueles especificados pelo parâmetro de tipo de interface. Por exemplo, na interface <xref:System.Collections.Generic.IComparer%601>, o tipo T é contravariante e você pode atribuir um objeto do tipo `IComparer<Person>` a um objeto do tipo `IComparer<Employee>`, sem usar nenhum método de conversão especial caso `Employee` herde `Person`.

Um delegado contravariante pode ser atribuído a outro delegado do mesmo tipo, mas com um parâmetro de tipo genérico menos derivado.

Para obter mais informações, consulte [Covariância e contravariância](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="contravariant-generic-interface"></a>Interface genérica contravariante

O exemplo a seguir mostra como declarar, estender e implementar uma interface genérica contravariante. Ele também mostra como você pode usar a conversão implícita para classes que implementam essa interface.

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a>Delegado genérico contravariante

O exemplo a seguir mostra como declarar, instanciar e invocar um delegado genérico contravariante. Ele também mostra como você pode converter implicitamente um tipo delegado.

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [out](out-generic-modifier.md)  
- [Covariância e Contravariância](../../programming-guide/concepts/covariance-contravariance/index.md)  
- [Modificadores](modifiers.md)  