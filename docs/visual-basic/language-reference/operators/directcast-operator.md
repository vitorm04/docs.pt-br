---
title: "Operador DirectCast (Visual Basic) | Microsoft Docs"
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
  - "vb.directCast"
  - "directCast"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Palavra-chave DirectCast"
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador DirectCast (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Introduz uma operação de conversão de tipos baseadas em herança ou implementação.  
  
## Comentários  
 `DirectCast` não usa as rotinas auxiliares de tempo de execução do Visual Basic para conversão, portanto, ele poderá fornecer um desempenho melhor do que `CType` durante a conversão tendo como origem ou destino `Object`.  
  
 Você pode usar o `DirectCast` a palavra\-chave semelhante à maneira como você pode usar o [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md) e o [Operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md) palavra\-chave.  Você fornecer uma expressão, como o primeiro argumento e um tipo para convertê\-lo para como o segundo argumento.  `DirectCast`requer uma relação de herança ou implementação entre os tipos de dados dos dois argumentos.  Isso significa que um tipo deve herdar de ou implementar o outro.  
  
## Erros e falhas  
 `DirectCast` gera um erro do compilador se ele detectar que nenhuma relação de herança ou implementação existe.  Mas a falta de um erro do compilador não garante uma conversão bem\-sucedida.  Se a conversão desejada é de restrição, ele pode falhar em tempo de execução.  Se isso acontecer, o tempo de execução gera um erro <xref:System.InvalidCastException>.  
  
## Palavras\-chave conversão  
 Uma comparação entre as palavras\-chave conversão de tipos é a seguinte:  
  
|||||  
|-|-|-|-|  
|Keyword|Tipos de dados|Relacionamento de argumento|Falha em tempo de execução|  
|[Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)|Quaisquer tipos de dados|Expandir ou restringir a conversão deve ser definido entre os dois tipos de dados.|Gera <xref:System.InvalidCastException>|  
|`DirectCast`|Quaisquer tipos de dados|Um tipo deve herdar de ou implementar o outro tipo|Gera <xref:System.InvalidCastException>|  
|[Operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md)|Somente tipos de referência|Um tipo deve herdar de ou implementar o outro tipo|Retorna [nada](../../../visual-basic/language-reference/nothing.md)|  
  
## Exemplo  
 O exemplo a seguir demonstra dois usos do `DirectCast`, um que falha em tempo de execução e outro que é bem\-sucedido.  
  
 [!code-vb[VbVbalrKeywords#1](../../../visual-basic/language-reference/codesnippet/VisualBasic/directcast-operator_1.vb)]  
  
 No exemplo anterior, o tempo de execução digite de `q` é `Double`.  `CType`é bem\-sucedida pois `Double` pode ser convertido em `Integer`.  No entanto, o primeiro `DirectCast` falha no tempo de execução porque tem o tipo em tempo de execução de `Double` não tem relação de herança com `Integer`, mesmo que exista uma conversão.  O segundo `DirectCast` é bem\-sucedido pois ele converte do tipo <xref:System.Windows.Forms.Form> para o tipo <xref:System.Windows.Forms.Control>, do qual <xref:System.Windows.Forms.Form> herda.  
  
## Consulte também  
 <xref:System.Convert.ChangeType%2A?displayProperty=fullName>   
 [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Conversões implícitas e explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)