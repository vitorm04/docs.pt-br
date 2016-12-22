---
title: "Compara&#231;&#227;o entre propriedades e indexadores (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "indexadores [C#], vs. propriedades"
  - "propriedades [C#], vs. indexadores"
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compara&#231;&#227;o entre propriedades e indexadores (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Os indexadores são como propriedades.  Exceto pelas diferenças mostradas na tabela a seguir, todas as regras que são definidas para os assessores da propriedade acessadores indexador também abordam.  
  
|Propriedade|Indexador|  
|-----------------|---------------|  
|Permite que os métodos sejam chamados como se fossem membros de dados pública.|Permite que os elementos de uma coleção interna de um objeto, sejam acessados usando a notação de matriz no próprio objeto.|  
|Acessado por meio de um nome simples.|Acessado por meio de um índice.|  
|Pode ser estático ou um membro de instância.|Deve ser um membro de instância.|  
|A  [obter](../../../csharp/language-reference/keywords/get.md) acessador de uma propriedade não tem parâmetros.|A `get` acessador de um indexador tem a mesma lista de parâmetros formal como o indexador.|  
|A  [set](../../../csharp/language-reference/keywords/set.md) acessador de uma propriedade contém o aspecto implícito `value` parâmetro.|A `set` acessador de um indexador tem a mesma lista de parâmetros formal, como o indexador e também para o  [valor](../../../csharp/language-reference/keywords/value.md) parâmetro.|  
|Suporta reduzido sintaxe com [Propriedades autoimplementadas](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).|Não oferece suporte a sintaxe abreviada.|  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Indexadores](../../../csharp/programming-guide/indexers/index.md)   
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)