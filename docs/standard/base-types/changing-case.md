---
title: "Alterando a definição de maiúsculas e minúsculas"
description: "Alterando a definição de maiúsculas e minúsculas"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 646c5afd-8aec-4393-9c00-f68ad2580c68
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: f67c726b38657790deebb623dc44cb528fe404bc

---

# <a name="changing-case"></a>Alterando a definição de maiúsculas e minúsculas

Se você gravar um aplicativo que aceita a inserção de informações por um usuário, talvez você nunca tenha certeza se ele ou ela usará maiúsculas ou minúsculas para inserir os dados. Muitas vezes, você quer que as cadeias de caracteres tenham a grafia de maiúsculas e minúsculas consistente, especialmente se você estiver exibindo-as na interface do usuário. A tabela a seguir descreve dois métodos de alteração de maiúsculas e minúsculas.

Nome do método | Use
----------- | ---
[String.ToUpper](xref:System.String.ToUpper) | Converte todos os caracteres em uma cadeia de caracteres para maiúsculas.
[String.ToLower](xref:System.String.ToLower) | Converte todos os caracteres em uma cadeia de caracteres para minúsculas.

> [!WARNING]  
> Observe que os métodos `String.ToUpper` e `String.ToLower` não devem ser usados para converter cadeias de caracteres a fim de compará-las ou testá-las quanto à igualdade. 

## <a name="comparing-strings-of-mixed-case"></a>Comparando cadeias de caracteres em maiúsculas e minúsculas

Para comparar cadeias de caracteres em maiúsculas e minúsculas para determinar se eles são iguais, chame uma das sobrecargas do método [String](xref:System) `Equals` com um parâmetro *comparisonType* e forneça um valor [StringComparison.CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase) ou [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) para o argumento *comparisonType*. 

Para obter mais informações, consulte [Práticas recomendadas para o uso de cadeias de caracteres](best-practices.md). 

## <a name="toupper"></a>ToUpper

O método [String.ToUpper](xref:System.String.ToUpper) altera todos os caracteres em uma cadeia de caracteres para maiúsculas. O exemplo a seguir converte a cadeia de caracteres "Olá, mundo!" de maiúsculas e minúsculas para maiúsculas.

```csharp
string properString = "Hello World!";
Console.WriteLine(properString.ToUpper());
// This example displays the following output:
//       HELLO WORLD!
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.ToUpper())
' This example displays the following output:
'       HELLO WORLD!
```

## <a name="tolower"></a>ToLower

O método [String.ToLower](xref:System.String.ToLower) é semelhante ao método anterior, mas, em vez disso, ele converte todos os caracteres em uma cadeia de caracteres para minúsculas. O exemplo a seguir converte a cadeia de caracteres "Olá, mundo!" para minúsculas.

```csharp
string properString = "Hello World!";
Console.WriteLine(properString.ToLower());
// This example displays the following output:
//       hello world!
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.ToLower())
' This example displays the following output:
'       hello world!
```

## <a name="see-also"></a>Consulte também

[Operações básicas de cadeias de caracteres](basic-string-operations.md)



<!--HONumber=Nov16_HO5-->


