---
title: "Tipos de valor (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.valuetypes
dev_langs:
- CSharp
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7500426846562dd7f3bbb8ea99f300a3e8a26546
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="value-types-c-reference"></a>Tipos de valor (Referência de C#)
Os tipos de valor consistem em duas categorias principais:  
  
-   [Estruturas](../../../csharp/language-reference/keywords/struct.md)  
  
-   [Enumerações](../../../csharp/language-reference/keywords/enum.md)  
  
 Os structs se enquadram nestas categorias:  
  
-   Tipos numéricos  
  
    -   [Tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [Tipos de ponto flutuante](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
    -   [decimal](../../../csharp/language-reference/keywords/decimal.md)  
  
-   [bool](../../../csharp/language-reference/keywords/bool.md)  
  
-   Structs definidos pelo usuário.  
  
## <a name="main-features-of-value-types"></a>Principais recursos dos tipos de valor  
 As variáveis que são baseadas diretamente em tipos de valor contêm valores. Atribuir uma variável de tipo de valor à outra, copia o valor contido. Isso difere da atribuição de variáveis de tipo de referência, que copiam uma referência para o objeto, mas não o próprio objeto.  
  
 Todos os tipos de valor são derivados implicitamente da <xref:System.ValueType?displayProperty=fullName>.  
  
 Ao contrário do que acontece com tipos de referência, você não pode derivar um novo tipo de um tipo de valor. No entanto, assim como com tipos de referência, os structs podem implementar interfaces.  
  
 Ao contrário dos tipos de referência, um tipo de valor não pode conter o valor `null`. No entanto, o recurso [tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md) permite que os tipos de valor sejam atribuídos como `null`.  
  
 Cada tipo de valor tem um construtor padrão implícito que inicializa o valor padrão desse tipo. Para obter informações sobre valores padrão de tipos de valor, consulte [Tabela de valores padrão](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## <a name="main-features-of-simple-types"></a>Principais recursos dos tipos simples  
 Todos os tipos simples – os integrantes à linguagem C# – são aliases dos tipos de sistema do .NET Framework. Por exemplo, [int](../../../csharp/language-reference/keywords/int.md) é um alias de <xref:System.Int32?displayProperty=fullName>. Para obter uma lista completa de aliases, consulte [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md).  
  
 As expressões constantes, cujos operandos são todos constantes de tipo simples, são avaliadas em tempo de compilação.  
  
 Os tipos simples podem ser inicializados com o uso de literais. Por exemplo, 'A' é um literal do tipo `char` e 2001 é um literal do tipo `int`.  
  
## <a name="initializing-value-types"></a>Inicializando tipos de valor  
 As variáveis locais no C# devem ser inicializadas antes de serem usadas. Por exemplo, você pode declarar uma variável local sem inicialização, como no exemplo a seguir:  
  
```  
int myInt;  
```  
  
 Você não pode usá-la antes de inicializá-la. Você pode inicializar a variável usando a instrução a seguir:  
  
```  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 Essa instrução é equivalente à instrução a seguir:  
  
```  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 É claro que a declaração e a inicialização podem ser feitas na mesma instrução, como nos exemplos a seguir:  
  
```  
int myInt = new int();  
```  
  
 – ou –  
  
```  
int myInt = 0;  
```  
  
 Usando o operador [new](../../../csharp/language-reference/keywords/new.md), chama o construtor padrão do tipo específico e atribui o valor padrão à variável. No exemplo anterior, o construtor padrão atribuiu o valor `0` para `myInt`. Para obter mais informações sobre valores atribuídos ao chamar construtores padrão, consulte [Tabela de valores padrão](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 Com tipos definidos pelo usuário, use [new](../../../csharp/language-reference/keywords/new.md) para invocar o construtor padrão. Por exemplo, a instrução a seguir invoca o construtor padrão do struct `Point`:  
  
```  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 Após esta chamada, o struct é considerado para ser definitivamente atribuído, ou seja, todos os seus membros são inicializados com seus valores padrão.  
  
 Para obter mais informações sobre o operador new, consulte [new](../../../csharp/language-reference/keywords/new.md).  
  
 Para obter informações sobre a formatação da saída de tipos numéricos, consulte [Tabela de formatação de resultados numéricos](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Tipos](../../../csharp/language-reference/keywords/types.md)   
 [Tabelas de Referência de Tipos](../../../csharp/language-reference/keywords/reference-tables-for-types.md)   
 [Tipos de referência](../../../csharp/language-reference/keywords/reference-types.md)

