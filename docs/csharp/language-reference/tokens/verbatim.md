---
title: "@ (Referência de C#)"
ms.date: 02/09/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30f937951557ba65971a752b414cce6b485149be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-c-reference"></a>@ (Referência de C#)

O caractere especial `@` serve como um identificador textual. Ele pode ser usado das seguintes maneiras:

1. Para habilitar palavras-chave de C# a serem usadas como identificadores. O caractere `@` atua como prefixo de um elemento de código que o compilador deve interpretar como um identificador e não como uma palavra-chave de C#. O exemplo a seguir usa o caractere `@` para definir um identificador chamado `for` que usa em um loop `for`.

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Para indicar que um literal de cadeia de caracteres é interpretado de forma textual. O caractere `@` neste exemplo define um *literal de cadeia de caracteres textual*. Sequências de escape simples (como `"\\"` para uma barra invertida), sequências de escape hexadecimais (como um `"\x0041"` para um A maiúsculo) e sequências de escape Unicode, como `"\u0041"` para um A maiúsculo, são interpretadas de forma textual. Somente uma sequência de escape de aspas (`""`) não é interpretada literalmente; ela produz aspas simples. O exemplo a seguir define dois caminhos de arquivo idênticos, um usando um literal de cadeia de caracteres regular e o outro usando um literal de cadeia de caracteres textual. Este é um dos usos mais comuns de literais de cadeias de caracteres textuais.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   O exemplo a seguir ilustra o efeito de definir um literal de cadeia de caracteres regular e um literal de cadeia de caracteres textual que contêm sequências de caracteres idênticas.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Para habilitar o compilador a distinguir entre os atributos em caso de um conflito de nomenclatura. Um atributo é um tipo que deriva de <xref:System.Attribute>. Seu nome de tipo normalmente inclui o sufixo **Attribute**, embora o compilador não imponha essa convenção. O atributo pode, então, ser referenciado no código por seu nome de tipo completo (por exemplo, `[InfoAttribute]` ou pelo nome abreviado (por exemplo, `[Info]`). No entanto, um conflito de nomenclatura ocorre se dois nomes de tipo abreviados forem idênticos e um nome de tipo incluir o sufixo **Attribute** e o outro não incluir. Por exemplo, o código a seguir não é compilado porque o compilador não pode determinar se o atributo `Info` ou `InfoAttribute` é aplicado ao método `Main`.

   ```csharp
   using System;

   [AttributeUsage(AttributeTargets.Class)]
   public class Info : Attribute
   {
      private string information;
      
      public Info(string info)
      {
          information = info;
      }
   }

   [AttributeUsage(AttributeTargets.Method)]
   public class InfoAttribute : Attribute
   {
      private string information;
      
      public InfoAttribute(string info)
      {
          information = info;
      }
   }

   [Info("A simple executable.")]
   public class Example
   {
      [InfoAttribute("The entry point.")]
      public static void Main()
      {
      }
   }
   ```  

   Se o identificador textual for usado para identificar o atributo `Info`, o exemplo será compilado com êxito.

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]

## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Caracteres especiais de C#](../../../csharp/language-reference/tokens/index.md)
