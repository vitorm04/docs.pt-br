---
title: "sizeof (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "sizeof_CSharpKeyword"
  - "sizeof"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave sizeof [C#]"
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# sizeof (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Usado para obter o tamanho em bytes para um tipo não gerenciado.  Tipos não gerenciados incluem os tipos internos que estão listados na tabela a seguir e também o seguinte:  
  
-   Tipos de enum  
  
-   Tipos ponteiro  
  
-   Estruturas definidas pelo usuário que não contêm quaisquer campos ou propriedades que são tipos de referência  
  
 O exemplo a seguir mostra como recuperar o tamanho de um `int`:  
  
```c#  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## Comentários  
 Iniciando com a versão 2.0 do C\#, aplicando `sizeof` para tipos internos não exige que  [não seguros](../../../csharp/language-reference/keywords/unsafe.md) o modo de ser usado.  
  
 O `sizeof` operador não pode ser sobrecarregado.  Os valores retornados pela `sizeof` operador são do tipo `int`.  A tabela a seguir mostra os valores constantes que são substituídos por `sizeof` expressões que tenham determinados tipos internos como operandos.  
  
|Expression|Valor constante|  
|----------------|---------------------|  
|`sizeof(sbyte)`|1|  
|`sizeof(byte)`|1|  
|`sizeof(short)`|2|  
|`sizeof(ushort)`|2|  
|`sizeof(int)`|4|  
|`sizeof(uint)`|4|  
|`sizeof(long)`|8|  
|`sizeof(ulong)`|8|  
|`sizeof(char)`|2 \(Unicode\)|  
|`sizeof(float)`|4|  
|`sizeof(double)`|8|  
|`sizeof(decimal)`|16|  
|`sizeof(bool)`|1|  
  
 Para todos os outros tipos, incluindo structs, o `sizeof` pode ser usado somente em blocos de código não seguro.  Embora você possa usar o <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> método, o valor retornado por esse método nem sempre é o mesmo que o valor retornado por `sizeof`.  <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName>Retorna o tamanho após o tipo foi empacotado, enquanto `sizeof` retorna o tamanho conforme foi alocado pelo common language runtime, incluindo qualquer preenchimento.  
  
## Exemplo  
 [!code-cs[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Palavras\-chave do operador](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [enum](../../../csharp/language-reference/keywords/enum.md)   
 [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md)   
 [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md)