---
title: "@ (Referência de C#)"
ms.date: 2017-02-09
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '@_CSharpKeyword'
- '@'
dev_langs:
- CSharp
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
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
ms.openlocfilehash: 08e3da6aaeee037d7272ea8cddc4382a436b683b
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="-c-reference"></a><span data-ttu-id="c57d3-102">@ (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="c57d3-102">@ (C# Reference)</span></span>

<span data-ttu-id="c57d3-103">O caractere especial `@` serve como um identificador textual.</span><span class="sxs-lookup"><span data-stu-id="c57d3-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="c57d3-104">Ele pode ser usado das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="c57d3-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="c57d3-105">Para habilitar palavras-chave de C# a serem usadas como identificadores.</span><span class="sxs-lookup"><span data-stu-id="c57d3-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="c57d3-106">O caractere `@` atua como prefixo de um elemento de código que o compilador deve interpretar como um identificador e não como uma palavra-chave de C#.</span><span class="sxs-lookup"><span data-stu-id="c57d3-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="c57d3-107">O exemplo a seguir usa o caractere `@` para definir um identificador chamado `for` que usa em um loop `for`.</span><span class="sxs-lookup"><span data-stu-id="c57d3-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   <span data-ttu-id="c57d3-108">[!code-cs[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="c57d3-108">[!code-cs[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]</span></span>

1. <span data-ttu-id="c57d3-109">Para indicar que um literal de cadeia de caracteres é interpretado de forma textual.</span><span class="sxs-lookup"><span data-stu-id="c57d3-109">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="c57d3-110">O caractere `@` neste exemplo define um *literal de cadeia de caracteres textual*.</span><span class="sxs-lookup"><span data-stu-id="c57d3-110">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="c57d3-111">Sequências de escape simples (como `"\\"` para uma barra invertida), sequências de escape hexadecimais (como um `"\x0041"` para um A maiúsculo) e sequências de escape Unicode, como `"\u0041"` para um A maiúsculo, são interpretadas de forma textual.</span><span class="sxs-lookup"><span data-stu-id="c57d3-111">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A, and Unicode escape sequences, such as `"\u0041"` for an uppercase A, are interpreted literally.</span></span> <span data-ttu-id="c57d3-112">Somente uma sequência de escape de aspas (`""`) não é interpretada literalmente; ela produz aspas simples.</span><span class="sxs-lookup"><span data-stu-id="c57d3-112">Only a quote escape sequence (`""`) is not interpreted literally; it produces a single quotation mark.</span></span> <span data-ttu-id="c57d3-113">O exemplo a seguir define dois caminhos de arquivo idênticos, um usando um literal de cadeia de caracteres regular e o outro usando um literal de cadeia de caracteres textual.</span><span class="sxs-lookup"><span data-stu-id="c57d3-113">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="c57d3-114">Este é um dos usos mais comuns de literais de cadeias de caracteres textuais.</span><span class="sxs-lookup"><span data-stu-id="c57d3-114">This is one of the more common uses of verbatim string literals.</span></span>

   <span data-ttu-id="c57d3-115">[!code-cs[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]</span><span class="sxs-lookup"><span data-stu-id="c57d3-115">[!code-cs[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]</span></span>

   <span data-ttu-id="c57d3-116">O exemplo a seguir ilustra o efeito de definir um literal de cadeia de caracteres regular e um literal de cadeia de caracteres textual que contêm sequências de caracteres idênticas.</span><span class="sxs-lookup"><span data-stu-id="c57d3-116">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   <span data-ttu-id="c57d3-117">[!code-cs[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]</span><span class="sxs-lookup"><span data-stu-id="c57d3-117">[!code-cs[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]</span></span>

1. <span data-ttu-id="c57d3-118">Para habilitar o compilador a distinguir entre os atributos em caso de um conflito de nomenclatura.</span><span class="sxs-lookup"><span data-stu-id="c57d3-118">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="c57d3-119">Um atributo é um tipo que deriva de @System.Attribute.</span><span class="sxs-lookup"><span data-stu-id="c57d3-119">An attribute is a type that derives from @System.Attribute.</span></span> <span data-ttu-id="c57d3-120">Seu nome de tipo normalmente inclui o sufixo **Attribute**, embora o compilador não imponha essa convenção.</span><span class="sxs-lookup"><span data-stu-id="c57d3-120">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="c57d3-121">O atributo pode, então, ser referenciado no código por seu nome de tipo completo (por exemplo, `[InfoAttribute]` ou pelo nome abreviado (por exemplo, `[Info]`).</span><span class="sxs-lookup"><span data-stu-id="c57d3-121">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="c57d3-122">No entanto, um conflito de nomenclatura ocorre se dois nomes de tipo abreviados forem idênticos e um nome de tipo incluir o sufixo **Attribute** e o outro não incluir.</span><span class="sxs-lookup"><span data-stu-id="c57d3-122">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="c57d3-123">Por exemplo, o código a seguir não é compilado porque o compilador não pode determinar se o atributo `Info` ou `InfoAttribute` é aplicado ao método `Main`.</span><span class="sxs-lookup"><span data-stu-id="c57d3-123">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Main` method.</span></span>

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

   <span data-ttu-id="c57d3-124">Se o identificador textual for usado para identificar o atributo `Info`, o exemplo será compilado com êxito.</span><span class="sxs-lookup"><span data-stu-id="c57d3-124">If the verbatim identifier is used to identify the `Info` attribute, the example compiles successfully.</span></span>

   <span data-ttu-id="c57d3-125">[!code-cs[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="c57d3-125">[!code-cs[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c57d3-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c57d3-126">See Also</span></span>  
 <span data-ttu-id="c57d3-127">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="c57d3-127">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="c57d3-128">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c57d3-128">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="c57d3-129">Caracteres especiais de C#</span><span class="sxs-lookup"><span data-stu-id="c57d3-129">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)

