---
title: Como testar a igualdade de referência (identidade) (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 4faa674f3f3d65b7c555d7feb9789637f39e9bd7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53125465"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a>Como testar a igualdade de referência (identidade) (Guia de Programação em C#)
Não é necessário implementar qualquer lógica personalizada para dar suporte a comparações de igualdade de referência em seus tipos. Essa funcionalidade é fornecida para todos os tipos pelo método estático <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>.  
  
 O exemplo a seguir mostra como determinar se duas variáveis têm *igualdade de referência*, que significa que elas se referem ao mesmo objeto na memória.  
  
 O exemplo também mostra por que <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> sempre retorna `false` para tipos de valor e por que você não deve usar <xref:System.Object.ReferenceEquals%2A> para determinar igualdade de cadeia de caracteres.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideObjects#90](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-test-for-reference-equality-identity_1.cs)]  
  
 A implementação de `Equals` na classe base universal <xref:System.Object?displayProperty=nameWithType> também realiza uma verificação de igualdade de referência, mas é melhor não usar isso, porque, se uma classe substituir o método, os resultados poderão não ser o que você espera. O mesmo é verdadeiro para os operadores `==` e `!=`. Quando eles estiverem operando em tipos de referência, o comportamento padrão de `==` e `!=` é realizar uma verificação de igualdade de referência. No entanto, as classes derivadas podem sobrecarregar o operador para executar uma verificação de igualdade de valor. Para minimizar o potencial de erro, será melhor usar sempre <xref:System.Object.ReferenceEquals%2A> quando for necessário determinar se os dois objetos têm igualdade de referência.  
  
 Cadeias de caracteres constantes dentro do mesmo assembly sempre são internalizadas pelo tempo de execução. Ou seja, apenas uma instância de cada cadeia de caracteres literal única é mantida. No entanto, o tempo de execução não garante que cadeias de caracteres criadas em tempo de execução sejam internalizadas nem garante que duas de cadeias de caracteres constantes iguais em diferentes assemblies sejam internalizadas.  
  
## <a name="see-also"></a>Consulte também

- [Comparações de igualdade](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)
