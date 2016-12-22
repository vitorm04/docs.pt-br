---
title: "Operador TryCast (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.trycast"
  - "trycast"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Palavra-chave TryCast"
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador TryCast (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Apresenta uma operação de conversão de tipo que não gera uma exceção.  
  
## Comentários  
 Se uma tentativa de conversão falhar, `CType` e `DirectCast` ambos lançam uma <xref:System.InvalidCastException> erro.  Isso pode afetar o desempenho do seu aplicativo.  `TryCast`Retorna [nada](../../../visual-basic/language-reference/nothing.md), de modo que, em vez de lidar com uma possível exceção, você só precisa testar o resultado retornado contra `Nothing`.  
  
 Você usa a palavra\-chave`TryCast`da mesma maneira que usa as palavras\-chave [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md) e a [Operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md).  Você fornecer uma expressão, como o primeiro argumento e um tipo para convertê\-lo para como o segundo argumento.  `TryCast`opera somente em tipos de referência, como, por exemplo, classes e interfaces.  Ele requer uma relação entre os dois tipos de herança ou implementação.  Isso significa que um tipo deve herdar de ou implementar o outro.  
  
## Erros e falhas  
 `TryCast` gera um erro do compilador se ele detectar que nenhuma relação de herança ou implementação existe.  Mas a falta de um erro do compilador não garante uma conversão bem\-sucedida.  Se a conversão desejada é de restrição, ele pode falhar em tempo de execução.  Se isso acontecer, `TryCast` retorna [nada](../../../visual-basic/language-reference/nothing.md).  
  
## Palavras\-chave conversão  
 Uma comparação entre as palavras\-chave conversão de tipos é a seguinte:  
  
|||||  
|-|-|-|-|  
|Keyword|Tipos de dados|Relacionamento de argumento|Falha em tempo de execução|  
|[Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)|Quaisquer tipos de dados|Expandir ou restringir a conversão deve ser definido entre os dois tipos de dados.|Gera <xref:System.InvalidCastException>|  
|[Operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md)|Quaisquer tipos de dados|Um tipo deve herdar de ou implementar o outro tipo|Gera <xref:System.InvalidCastException>|  
|`TryCast`|Somente tipos de referência|Um tipo deve herdar de ou implementar o outro tipo|Retorna [nada](../../../visual-basic/language-reference/nothing.md)|  
  
## Exemplo  
 O exemplo a seguir mostra como usar `TryCast`.  
  
 [!code-vb[VbVbalrKeywords#6](../../../visual-basic/language-reference/codesnippet/VisualBasic/trycast-operator_1.vb)]  
  
## Consulte também  
 [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Conversões implícitas e explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)