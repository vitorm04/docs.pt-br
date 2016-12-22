---
title: "Tipos anul&#225;veis (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "Linguagem C#, tipos anuláveis"
  - "tipos anuláveis [C#]"
  - "tipos [C#], anulável"
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
caps.latest.revision: 44
caps.handback.revision: 44
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Tipos anul&#225;veis (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Os tipos anuláveis são instâncias de estrutura de <xref:System.Nullable%601?displayProperty=fullName> .  Um tipo anulável pode representar o intervalo de valores correto para seu tipo de valor subjacente, mais um valor adicional de `null` .  Por exemplo, `Nullable<Int32>`, pronunciado “anulável de Int32”, pode ser atribuído qualquer valor de \-2147483648 a 2147483647, ou pode ser atribuído o valor de `null` .  `Nullable<bool>` pode ser atribuído os valores [true](../../../csharp/language-reference/keywords/true.md)[false](../../../csharp/language-reference/keywords/false.md), ou [nulo](../../../csharp/language-reference/keywords/null.md).  A capacidade de atribuir `null` para tipos numéricos e booleanas é especialmente útil quando você está tratando os bancos de dados e outros tipos de dados que contêm elementos que não podem ser atribuído um valor.  Por exemplo, um campo booleano em um banco de dados pode armazenar os valores `true` ou `false`, ou pode ser indefinido.  
  
 [!code-cs[csProgGuideTypes#3](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_1.cs)]  
  
 O exemplo exibirá a saída:  
  
 `num = Null`  
  
 `Nullable object must have a value.`  
  
 Para obter mais exemplos, consulte [Usando tipos anuláveis](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
## Visão geral sobre anulável de tipos  
 Os tipos anuláveis têm as seguintes características:  
  
-   Os tipos anuláveis representam as variáveis do tipo de valor que podem ser atribuídos o valor de `null`.  Você não pode criar um tipo anulável com base em um tipo de referência.  \(Tipos de referência já têm suporte para o valor de `null` .\)  
  
-   A sintaxe `T?` é taquigrafia para <xref:System.Nullable%601>, onde `T` é um tipo de valor.  As duas formas intercambiáveis são.  
  
-   Atribua um valor para um tipo anulável exatamente como você faria para um tipo de valor comum, por exemplo `int? x = 10;`ou`double? d = 4.108`.  Um tipo anulável também pode ser atribuído o valor `null`:`int? x = null.`  
  
-   use o método de <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> para retornar o valor atribuído, ou o valor padrão para o tipo subjacente se o valor é `null`, por exemplo`int j = x.GetValueOrDefault();`  
  
-   Use <xref:System.Nullable%601.HasValue%2A> e propriedades somente leitura de <xref:System.Nullable%601.Value%2A> para testar o zero e recuperar o valor, conforme mostrado no exemplo o seguir: `if(x.HasValue) j = x.Value;`  
  
    -   A propriedade de `HasValue` retorna `true` se a variável contém um valor, ou `false` se é `null`.  
  
    -   A propriedade de `Value` retorna um valor se ele é atribuído.  Caso contrário, um <xref:System.InvalidOperationException?displayProperty=fullName> é lançado.  
  
    -   o valor padrão para `HasValue` é `false`.  A propriedade de `Value` não tem valor padrão.  
  
    -   Você também pode usar os operadores de `==` e de `!=` com um tipo anulável, conforme mostrado no exemplo o seguir: `if (x != null) y = x;`  
  
-   Use o operador de `??` para atribuir um valor padrão que é quando um tipo anulável cujo valor atual é `null` é atribuído a um tipo não\-nulo, por exemplo `int? x = null; int y = x ?? -1;`aplicado  
  
-   Os tipos anuláveis aninhados não são permitidos.  A seguinte linha não será compilado: `Nullable<Nullable<int>> n;`  
  
## Seções relacionadas  
 para mais informações:  
  
-   [Usando tipos anuláveis](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [Executando a conversão boxing de tipos anuláveis](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [Operador ??](../../../csharp/language-reference/operators/null-conditional-operator.md)  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 <xref:System.Nullable>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [C\#](../../../csharp/csharp.md)   
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Que faz exatamente meio levantado”? “](http://go.microsoft.com/fwlink/?LinkId=112382)