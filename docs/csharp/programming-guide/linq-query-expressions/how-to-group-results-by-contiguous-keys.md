---
title: "Como agrupar resultados por chaves cont&#237;guas (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "chaves contíguas [LINQ em C#]"
ms.assetid: 0f0f48a8-e13b-4274-8903-3b73f68cd18e
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como agrupar resultados por chaves cont&#237;guas (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O exemplo a seguir mostra como agrupar elementos em blocos que representam as subseqüências de chaves contíguas.  Por exemplo, suponha que você recebe a seguinte seqüência de pares chave\-valor:  
  
|Chave|Valor|  
|-----------|-----------|  
|A|Podemos|  
|A|Pense|  
|A|que|  
|B|LINQ|  
|C|é|  
|A|realmente|  
|B|legal|  
|B|\!|  
  
 Os seguintes grupos serão criados nesta ordem:  
  
1.  Acreditamos que  
  
2.  LINQ  
  
3.  é  
  
4.  realmente  
  
5.  legal\!  
  
 A solução é implementada como um método de extensão que é thread\-safe e que retorna os seus resultados de uma maneira de fluxo contínuo.  Em outras palavras, ele produz seus grupos de medida que percorre a seqüência de origem.  Ao contrário do `group` ou `orderby` operadores, ele pode começar retornando grupos para o chamador antes de todas a seqüência foi lido.  
  
 Segurança do thread é realizada pela cópia de cada grupo ou bloco como a seqüência de origem é iterada, conforme explicado nos comentários de código fonte.  Se a seqüência de origem tiver uma seqüência grande de itens adjacentes, o common language runtime pode lançar uma <xref:System.OutOfMemoryException>.  
  
## Exemplo  
 O exemplo a seguir mostra o método de extensão e o código do cliente que o utiliza.  
  
 [!code-cs[cscsrefContiguousGroups#1](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/how-to-group-results-by-contiguous-keys_1.cs)]  
  
 Para usar o método de extensão em seu projeto, copie o `MyExtensions` arquivo de código de classe estática para uma fonte de nova ou existente e se necessário, adicione um `using` diretriz para o namespace onde está localizado.  
  
## Consulte também  
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Classificação de operadores de consulta padrão por meio da execução](../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)