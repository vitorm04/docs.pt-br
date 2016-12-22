---
title: "Compara&#231;&#245;es de igualdade (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "igualdade de objetos [C#]"
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compara&#231;&#245;es de igualdade (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Às vezes é necessário comparar dois valores para igualdade.  Em alguns casos, você está testando para *igualdade de valor*, também conhecido como *equivalência*, o que significa que os valores contidos pelas duas variáveis são iguais.  Em outros casos, você precisa determinar se duas variáveis referem\-se ao mesmo objeto subjacente na memória.  Esse tipo de igualdade é chamado de *igualdade de referência* ou de *identidade*.  Este tópico descreve esses dois tipos de igualdade e oferece links para outros tópicos para obter mais informações.  
  
## Igualdade de referência  
 A igualdade de referência significa que duas referências a objetos referem\-se ao mesmo objeto subjacente.  Isso pode ocorrer por meio de uma atribuição simples, como mostrado no exemplo a seguir.  
  
 [!code-cs[csProgGuideStatements#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/equality-comparisons_1.cs)]  
  
 Nesse código, dois objetos são criados, mas após a instrução de atribuição, ambas as referências se referem ao mesmo objeto.  Portanto, eles têm igualdade de referência.  Use o método <xref:System.Object.ReferenceEquals%2A> para determinar se as duas referências referem\-se ao mesmo objeto.  
  
 O conceito de igualdade de referência se aplica somente a tipos de referência.  Os objetos do tipo de valor não podem ter a igualdade de referência, pois quando uma instância de um tipo de valor é atribuída a uma variável, uma cópia do valor é feita.  Dessa forma, você nunca terá duas estruturas desconvertidas que façam referência à mesma alocação na memória.  Além disso, se você usar <xref:System.Object.ReferenceEquals%2A> para comparar dois tipos de valor, o resultado será sempre `false`, mesmo se os valores contidos nos objetos forem todos idênticos.  Isso ocorre porque cada variável é convertida em uma instância separada do objeto.  Para obter mais informações, consulte [Como testar a igualdade de referência \(identidade\)](../Topic/How%20to:%20Test%20for%20Reference%20Equality%20\(Identity\)%20\(C%23%20Programming%20Guide\).md).  
  
## Igualdade de valor  
 A igualdade de valor significa que dois objetos contém o mesmo valor ou valores.  Para tipos de valores primitivos como [int](../../../csharp/language-reference/keywords/int.md) ou [bool](../../../csharp/language-reference/keywords/bool.md), os testes para igualdade de valores são simples.  É possível usar o operador [\=\=](../../../csharp/language-reference/operators/equality-comparison-operator.md), conforme mostrado no exemplo a seguir.  
  
```c#  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.   
if( b == a)   
{  
    // The two integers are equal.  
}  
```  
  
 Para a maioria dos outros tipos, testar a igualdade do valor é mais complexo porque requer que você entenda como o tipo o define.  Para as classes e estruturas que têm vários campos ou propriedades, a igualdade de valores é geralmente definida para indicar que todos os campos ou propriedades têm o mesmo valor.  Por exemplo, dois objetos `Point` podem ser definidos para ser equivalentes se pointA.X for igual a pointB.X e pointA.Y for igual a pointB.Y.  
  
 No entanto, não há requisitos para que a equivalência seja baseada em todos os campos de um tipo.  Pode ser baseada em um subconjunto.  Ao comparar os tipos que você não possui, é necessário certificar\-se de entender especificamente como a equivalência é definida para esse tipo.  Para obter mais informações sobre como definir a igualdade de valores em suas próprias classes e estruturas, consulte [Como definir a igualdade de valor para um tipo](../Topic/How%20to:%20Define%20Value%20Equality%20for%20a%20Type%20\(C%23%20Programming%20Guide\).md).  
  
### Igualdade de valor para valores de ponto flutuante  
 As comparações de igualdade de valores de ponto flutuante \([double](../../../csharp/language-reference/keywords/double.md) e [float](../../../csharp/language-reference/keywords/float.md)\) são problemáticas devido à imprecisão da aritmética de ponto flutuante em computadores binários.  Para obter mais informações, consulte os comentários no tópico <xref:System.Double?displayProperty=fullName>.  
  
## Tópicos relacionados  
  
|Nome|Descrição|  
|----------|---------------|  
|[Como testar a igualdade de referência \(identidade\)](../Topic/How%20to:%20Test%20for%20Reference%20Equality%20\(Identity\)%20\(C%23%20Programming%20Guide\).md)|Descreve como determinar se duas variáveis têm igualdade de referência.|  
|[Como definir a igualdade de valor para um tipo](../Topic/How%20to:%20Define%20Value%20Equality%20for%20a%20Type%20\(C%23%20Programming%20Guide\).md)|Descreve como fornecer uma definição personalizada de igualdade de valor para um tipo.|  
|[Guia de Programação em C\#](../../../csharp/programming-guide/index.md)|Fornece links para informações detalhadas sobre importantes recursos da linguagem C\# e recursos disponíveis para C\# por meio do .NET Framework.|  
|[Tipos](../../../visual-basic/reference/command-line-compiler/index.md)|Fornece informações sobre o sistema de tipos C\# e links para informações adicionais.|  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)