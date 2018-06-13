---
title: '@ (Referência de C#)'
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdf8735894594acab31586e539f90e426db97f24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289172"
---
# <a name="-c-reference"></a><span data-ttu-id="d65c9-102">@ (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d65c9-102">@ (C# Reference)</span></span>

<span data-ttu-id="d65c9-103">O caractere especial `@` serve como um identificador textual.</span><span class="sxs-lookup"><span data-stu-id="d65c9-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="d65c9-104">Ele pode ser usado das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="d65c9-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="d65c9-105">Para habilitar palavras-chave de C# a serem usadas como identificadores.</span><span class="sxs-lookup"><span data-stu-id="d65c9-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="d65c9-106">O caractere `@` atua como prefixo de um elemento de código que o compilador deve interpretar como um identificador e não como uma palavra-chave de C#.</span><span class="sxs-lookup"><span data-stu-id="d65c9-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="d65c9-107">O exemplo a seguir usa o caractere `@` para definir um identificador chamado `for` que usa em um loop `for`.</span><span class="sxs-lookup"><span data-stu-id="d65c9-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="d65c9-108">Para indicar que um literal de cadeia de caracteres é interpretado de forma textual.</span><span class="sxs-lookup"><span data-stu-id="d65c9-108">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="d65c9-109">O caractere `@` neste exemplo define um *literal de cadeia de caracteres textual*.</span><span class="sxs-lookup"><span data-stu-id="d65c9-109">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="d65c9-110">Sequências de escape simples (como `"\\"` para uma barra invertida), sequências de escape hexadecimais (como um `"\x0041"` para um A maiúsculo) e sequências de escape Unicode (como `"\u0041"` para um A maiúsculo) são interpretadas de forma textual.</span><span class="sxs-lookup"><span data-stu-id="d65c9-110">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A), and Unicode escape sequences (such as `"\u0041"` for an uppercase A) are interpreted literally.</span></span> <span data-ttu-id="d65c9-111">Somente uma sequência de escape de aspas (`""`) não é interpretada literalmente; ela produz aspas simples.</span><span class="sxs-lookup"><span data-stu-id="d65c9-111">Only a quote escape sequence (`""`) is not interpreted literally; it produces a single quotation mark.</span></span> <span data-ttu-id="d65c9-112">Além disso, no caso de uma [cadeia de caracteres interpolada](interpolated.md) textual, as sequências de escape de chave (`{{` e `}}`) não são interpretadas de forma textual; elas geram caracteres de chave única.</span><span class="sxs-lookup"><span data-stu-id="d65c9-112">Additionally, in case of a verbatim [interpolated string](interpolated.md) brace escape sequences (`{{` and `}}`) are not interpreted literally; they produce single brace characters.</span></span> <span data-ttu-id="d65c9-113">O exemplo a seguir define dois caminhos de arquivo idênticos, um usando um literal de cadeia de caracteres regular e o outro usando um literal de cadeia de caracteres textual.</span><span class="sxs-lookup"><span data-stu-id="d65c9-113">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="d65c9-114">Este é um dos usos mais comuns de literais de cadeias de caracteres textuais.</span><span class="sxs-lookup"><span data-stu-id="d65c9-114">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="d65c9-115">O exemplo a seguir ilustra o efeito de definir um literal de cadeia de caracteres regular e um literal de cadeia de caracteres textual que contêm sequências de caracteres idênticas.</span><span class="sxs-lookup"><span data-stu-id="d65c9-115">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="d65c9-116">Para habilitar o compilador a distinguir entre os atributos em caso de um conflito de nomenclatura.</span><span class="sxs-lookup"><span data-stu-id="d65c9-116">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="d65c9-117">Um atributo é um tipo que deriva de <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="d65c9-117">An attribute is a type that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="d65c9-118">Seu nome de tipo normalmente inclui o sufixo **Attribute**, embora o compilador não imponha essa convenção.</span><span class="sxs-lookup"><span data-stu-id="d65c9-118">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="d65c9-119">O atributo pode, então, ser referenciado no código por seu nome de tipo completo (por exemplo, `[InfoAttribute]` ou pelo nome abreviado (por exemplo, `[Info]`).</span><span class="sxs-lookup"><span data-stu-id="d65c9-119">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="d65c9-120">No entanto, um conflito de nomenclatura ocorre se dois nomes de tipo abreviados forem idênticos e um nome de tipo incluir o sufixo **Attribute** e o outro não incluir.</span><span class="sxs-lookup"><span data-stu-id="d65c9-120">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="d65c9-121">Por exemplo, o código a seguir não é compilado porque o compilador não consegue determinar se o atributo `Info` ou `InfoAttribute` é aplicado à classe `Example`.</span><span class="sxs-lookup"><span data-stu-id="d65c9-121">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span>

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

   <span data-ttu-id="d65c9-122">Se o identificador textual for usado para identificar o atributo `Info`, o exemplo será compilado com êxito.</span><span class="sxs-lookup"><span data-stu-id="d65c9-122">If the verbatim identifier is used to identify the `Info` attribute, the example compiles successfully.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]

## <a name="see-also"></a><span data-ttu-id="d65c9-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d65c9-123">See Also</span></span>  
 [<span data-ttu-id="d65c9-124">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d65c9-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d65c9-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d65c9-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d65c9-126">Caracteres especiais de C#</span><span class="sxs-lookup"><span data-stu-id="d65c9-126">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)
