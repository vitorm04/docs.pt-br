---
title: "Chave (Visual Basic) | Microsoft Docs"
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
  - "vb.AnonymousKey"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "tipos anônimos [Visual Basic], key"
  - "Key [Visual Basic]"
  - "palavra-chave Key [Visual Basic]"
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Chave (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `Key` palavra\-chave permite que você especifique o comportamento para propriedades de tipos anônimos.  Somente as propriedades que você designar como propriedades de chave participarem de testes de igualdade entre instâncias do tipo anônimo ou o cálculo dos valores do código de hash.  No entanto, os valores das propriedades de chave não podem ser alterados.  
  
 Você designa uma propriedade de um tipo anônimo como uma propriedade\-chave colocando a palavra\-chave `Key` na frente de sua declaração na lista de inicialização.  No exemplo a seguir, `Airline` e `FlightNo` são propriedades\-chave, mas `Gate` não é.  
  
 [!CODE [VbVbalrAnonymousTypes#26](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#26)]  
  
 Quando um novo tipo anônimo é criado, ele herda diretamente de <xref:System.Object>.  O compilador desautoriza três membros herdados: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A> e <xref:System.Object.ToString%2A>.  O código de substituição é produzido para <xref:System.Object.Equals%2A> e <xref:System.Object.GetHashCode%2A> se baseia nas propriedades de chaves.  Se não há propriedades\-chave no tipo, <xref:System.Object.GetHashCode%2A> e <xref:System.Object.Equals%2A> não são desautorizados.  
  
## Igualdade  
 Duas instâncias de tipo anônimo são iguais se são instâncias do mesmo tipo e se os valores de suas propriedades\-chave são iguais.  Nos exemplos a seguir, `flight2` é igual a `flight1` do exemplo anterior porque elas são instâncias do mesmo anônimo tipo e eles com valores correspondentes para suas propriedades de chaves.  No entanto, `flight3` não é igual a `flight1` porque ele tem um valor diferente para uma propriedade de chave, `FlightNo`.  Instância `flight4` não é do mesmo tipo que `flight1` porque eles designar propriedades diferentes como propriedades de chave.  
  
 [!CODE [VbVbalrAnonymousTypes#27](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#27)]  
  
 Se duas instâncias de tipo são declaradas com apenas propriedades que não são chave, idênticas em nome, tipo, ordem e valor, as duas instâncias não são iguais.  Uma instância sem propriedades\-chave é igual somente a ela mesma.  
  
 Para obter mais informações sobre as condições sob as quais duas instâncias do tipo anônimo são instâncias do mesmo tipo anônimo, consulte [Tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## Cálculo Dividido de Código  
 Como <xref:System.Object.Equals%2A>, a função de hash é definida em <xref:System.Object.GetHashCode%2A> para um tipo anônimo é baseado nas propriedades principais do tipo.  Os exemplos a seguir mostram a interação entre propriedades de chave e hash de valores de código.  
  
 Instâncias de um tipo anônimo que têm os mesmos valores para todas as propriedades principais têm o mesmo valor de código hash, mesmo se as propriedades não\-chave não têm valores correspondentes.  A instrução seguinte retorna `True`.  
  
 [!CODE [VbVbalrAnonymousTypes#37](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#37)]  
  
 Instâncias de um tipo anônimo que possuem valores diferentes para um ou mais propriedades de chave têm valores de código de hash diferente.  A instrução seguinte retorna `False`.  
  
 [!CODE [VbVbalrAnonymousTypes#38](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#38)]  
  
 Instâncias de tipos anônimos que designar propriedades diferentes como propriedades de chave não são instâncias do mesmo tipo.  Mesmo quando os nomes e valores de todas as propriedades são os mesmos, eles têm valores de código hash diferente.  A instrução seguinte retorna `False`.  
  
 [!CODE [VbVbalrAnonymousTypes#39](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#39)]  
  
## Valores somente leitura  
 No entanto, os valores das propriedades de chave não podem ser alterados.  Por exemplo, em `flight1` nos exemplos anteriores, o `Airline` e `FlightNo` campos são somente leitura, mas `Gate` pode ser alterado.  
  
 [!CODE [VbVbalrAnonymousTypes#28](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#28)]  
  
## Consulte também  
 [Definição do tipo anônimo](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)   
 [Como inferir nomes e tipos de propriedade na declaração de tipo anônimo](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)   
 [Tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)