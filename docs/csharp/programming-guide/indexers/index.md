---
title: "Indexadores (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "cs.indexers"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Linguagem C#, indexadores"
  - "indexadores [C#]"
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
caps.latest.revision: 29
caps.handback.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Indexadores (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Indexadores permitem que instâncias de uma classe ou estrutura a ser indexado como matrizes.  Indexadores lembram [propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md) exceto que seus acessadores usam parâmetros.  
  
 No exemplo a seguir, uma classe genérica é definida e fornecida com simples [obter](../../../csharp/language-reference/keywords/get.md) e [definir](../../../csharp/language-reference/keywords/set.md) métodos acessadores como um meio de atribuir e recuperar valores.  O `Program` classe cria uma instância dessa classe para armazenar cadeias de caracteres.  
  
 [!code-cs[csProgGuideIndexers#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/index_1.cs)]  
  
> [!NOTE]
>  Para obter mais exemplos, consulte [Seções relacionadas](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).  
  
## Definições de corpo da expressão  
 É comum ter indexadores simplesmente retornam imediatamente com o resultado de uma expressão.  Existe um atalho de sintaxe para definir esses indexadores usando `=>`:  
  
```c#  
public Customer this[long id] => store.LookupCustomer(id);  
  
```  
  
 O indexador deve ser somente leitura e não usar o `get` palavra\-chave do acessador.  
  
## Visão Geral dos Indexadores  
  
-   Indexadores permitem a ser indexado de maneira semelhante às matrizes de objetos.  
  
-   Um `get` acessador retorna um valor.  Um `set` acessador atribui um valor.  
  
-   O [isso](../../../csharp/language-reference/keywords/this.md) palavra\-chave é usada para definir os indexadores.  
  
-   O [valor](../../../csharp/language-reference/keywords/value.md) palavra\-chave é usada para definir o valor que está sendo atribuído pelo `set` indexador.  
  
-   Indexadores não precisam ser indexado por um valor inteiro; cabe a você como definir o mecanismo de pesquisa específico.  
  
-   Indexadores podem ser sobrecarregados.  
  
-   Indexadores podem ter mais de um parâmetro formal, por exemplo, ao acessar uma matriz bidimensional.  
  
##  <a name="BKMK_RelatedSections"></a> Seções relacionadas  
  
-   [Usando indexadores](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [Indexadores em interfaces](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [Comparação entre propriedades e indexadores](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [Restringindo a acessibilidade aos acessadores](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## Especificação da Linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)