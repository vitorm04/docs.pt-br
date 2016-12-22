---
title: "string (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "string"
  - "string_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "cadeias de caracteres [c#], referência"
  - "literal de cadeia de caracteres @"
  - "literais String [C#]"
  - "palavra-chave string [C#]"
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
caps.latest.revision: 31
caps.handback.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# string (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O tipo de `string` representa uma sequência de zero ou mais caracteres Unicode.  `string` é um alias para <xref:System.String> no .NET Framework.  
  
 Embora `string` é um tipo de referência, os operadores de igualdade \(`==` e `!=`\) são definidos para comparar os valores de objetos de `string` , não referências.  Isso faz testes para igualdade de cadeia de caracteres mais intuitivos.  Por exemplo:  
  
```c#  
  
      string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 Isso exibe “true” e “false” porque o conteúdo de cadeias de caracteres são equivalentes, mas `a` e `b` não referem\-se à mesma instância de cadeia de caracteres.  
  
 O operador \+ concatena cadeias de caracteres:  
  
```c#  
  
string a = "good " + "morning";  
```  
  
 Isso cria um objeto de cadeia de caracteres que contém “\-” dia.  
  
 Cadeias de caracteres são *imutáveis*\-\-o conteúdo de um objeto de cadeia de caracteres não podem ser alterados após o objeto é criado, embora a sintaxe faça o parecer se você pode fazer isso.  Por exemplo, quando você escreve esse código, o compilador realmente criar um novo objeto de cadeia de caracteres para manter a nova sequência de caracteres, e esse novo objeto é atribuído ao B.  A cadeia de caracteres “h” é então qualificado para coleta de lixo.  
  
```c#  
  
      string b = "h";  
b += "ello";  
```  
  
 \[\] O operador pode ser usado para acesso readonly para caracteres individuais de `string`:  
  
```c#  
  
      string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 Literais de cadeia de caracteres são do tipo `string` e podem ser gravados em duas formas, ser entre aspas e @\-quoted.  Literais de cadeia de caracteres entre aspas são incluídos entre aspas duplas \("\):  
  
```c#  
"good morning"  // a string literal  
```  
  
 Literais de cadeia de caracteres podem conter qualquer caractere literal.  As sequências de escape são incluídas.  O exemplo a seguir usa a sequência de escape `\\` para a barra invertida, o `\u0066` para a letra f, e o `\n` para a nova linha.  
  
```  
  
      string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  O código de escape `\`EUA`dddd` \( `dddd` onde é um número de quatro dígitos\) representa o caractere U\+`dddd`Unicode.  Códigos de escape Unicode de Oito\- dígito também são reconhecidos: `\Udddddddd`.  
  
 O início textual de literais de cadeia de caracteres com @ e também estão incluídos entre aspas duplas.  Por exemplo:  
  
```c#  
@"good morning"  // a string literal  
```  
  
 A vantagem de cadeias de caracteres textuais é que as sequências de escape *não* são processadas, que facilitam gravar, por exemplo, um nome de arquivo totalmente qualificado:  
  
```c#  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 Para incluir aspas duplas em uma cadeia de caracteres @\-quoted, dobre\-a:  
  
```c#  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 Outro uso do símbolo @ é a identificadores referenciados uso de[\/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)\(\) que são palavras\-chave C\#.  
  
 Para obter mais informações sobre cadeias de caracteres em C\#, consulte [Cadeias de caracteres](../../../csharp/programming-guide/strings/index.md).  
  
## Exemplo  
 [!CODE [csrefKeywordsTypes#17](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#17)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Práticas recomendadas para o uso de cadeias de caracteres](../Topic/Best%20Practices%20for%20Using%20Strings%20in%20the%20.NET%20Framework.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Tipos de referência](../../../csharp/language-reference/keywords/reference-types.md)   
 [Tipos de valor](../../../csharp/language-reference/keywords/value-types.md)   
 [Operações básicas de cadeias de caracteres](../Topic/Basic%20String%20Operations%20in%20the%20.NET%20Framework.md)   
 [Criando novas cadeias de caracteres](../Topic/Creating%20New%20Strings%20in%20the%20.NET%20Framework.md)   
 [Tabela de formatação de resultados numéricos](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)