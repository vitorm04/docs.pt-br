---
title: "Como testar a igualdade de referência (identidade) (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
caps.latest.revision: 13
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b8b0d2d646357e7d49e0d1203b08af2af3698d8c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a>Como testar a igualdade de referência (identidade) (Guia de Programação em C#)
Não é necessário implementar qualquer lógica personalizada para dar suporte a comparações de igualdade de referência em seus tipos. Essa funcionalidade é fornecida para todos os tipos pelo método <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> estático.  
  
 O exemplo a seguir mostra como determinar se duas variáveis têm *igualdade de referência*, que significa que elas se referem ao mesmo objeto na memória.  
  
 O exemplo também mostra por que <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> sempre retorna `false` para tipos de valor e por que você não deve usar <xref:System.Object.ReferenceEquals%2A> para determinar a igualdade da cadeia de caracteres.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csProgGuideObjects#90](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-test-for-reference-equality-identity_1.cs)]  
  
 A implementação de `Equals` na classe base universal <xref:System.Object?displayProperty=fullName> também realiza uma verificação de igualdade de referência, mas é melhor não usar isso, porque, se uma classe acabar substituindo o método, os resultados podem não ser o que você espera. O mesmo é verdadeiro para os operadores `==` e `!=`. Quando estiverem operando em tipos de referência, o comportamento padrão de == e `!=` deve realizar uma verificação de igualdade de referência. No entanto, as classes derivadas podem sobrecarregar o operador para executar uma verificação de igualdade de valor. Para minimizar o potencial de erro, será melhor usar sempre <xref:System.Object.ReferenceEquals%2A> quando for necessário determinar se os dois objetos têm igualdade de referência.  
  
 Cadeias de caracteres constantes dentro do mesmo assembly sempre são internalizadas pelo tempo de execução. Ou seja, apenas uma instância de cada cadeia de caracteres literal única é mantida. No entanto, o tempo de execução não garante que cadeias de caracteres criadas em tempo de execução sejam internalizadas nem garante que duas de cadeias de caracteres constantes iguais em diferentes assemblies sejam internalizadas.  
  
## <a name="see-also"></a>Consulte também  
 [Comparações de igualdade](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)
