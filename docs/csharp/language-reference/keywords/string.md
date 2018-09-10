---
title: string (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- string
- string_CSharpKeyword
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
ms.openlocfilehash: 8b70f1c1dcb39dcdde6ba24a1bdcdfc3084cfc97
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513094"
---
# <a name="string-c-reference"></a><span data-ttu-id="c3a84-102">string (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="c3a84-102">string (C# Reference)</span></span>
<span data-ttu-id="c3a84-103">O tipo `string` representa uma sequência de zero ou mais caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="c3a84-103">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="c3a84-104">`string` é um alias de <xref:System.String> no .NET.</span><span class="sxs-lookup"><span data-stu-id="c3a84-104">`string` is an alias for <xref:System.String> in .NET.</span></span>  
  
 <span data-ttu-id="c3a84-105">Embora `string` seja um tipo de referência, os operadores de igualdade (`==` e `!=`) são definidos para comparar os valores dos objetos `string`, não referências.</span><span class="sxs-lookup"><span data-stu-id="c3a84-105">Although `string` is a reference type, the equality operators (`==` and `!=`) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="c3a84-106">Isso torna o teste de igualdade de cadeia de caracteres mais intuitivo.</span><span class="sxs-lookup"><span data-stu-id="c3a84-106">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="c3a84-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c3a84-107">For example:</span></span>  
  
```csharp  
string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 <span data-ttu-id="c3a84-108">Isso exibe "True" e, em seguida, "False" porque os conteúdos das cadeias de caracteres são equivalentes, mas `a` e `b` não fazem referência à mesma instância da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c3a84-108">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>  
  
 <span data-ttu-id="c3a84-109">O operador + concatena as cadeias de caracteres:</span><span class="sxs-lookup"><span data-stu-id="c3a84-109">The + operator concatenates strings:</span></span>  
  
```csharp  
string a = "good " + "morning";  
```  
  
 <span data-ttu-id="c3a84-110">Isso cria um objeto de cadeia de caracteres que contém “good morning”.</span><span class="sxs-lookup"><span data-stu-id="c3a84-110">This creates a string object that contains "good morning".</span></span>  
  
 <span data-ttu-id="c3a84-111">Cadeias de caracteres são *imutável* – o conteúdo de um objeto de cadeia de caracteres não pode ser alterado depois que o objeto é criado, embora a sintaxe faça com que pareça que você pode fazer isso.</span><span class="sxs-lookup"><span data-stu-id="c3a84-111">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="c3a84-112">Por exemplo, quando você escreve esse código, o compilador na verdade cria um novo objeto de cadeia de caracteres para manter a nova sequência de caracteres e esse novo objeto é atribuído a b.</span><span class="sxs-lookup"><span data-stu-id="c3a84-112">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to b.</span></span> <span data-ttu-id="c3a84-113">A cadeia de caracteres "h" é então qualificada para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c3a84-113">The string "h" is then eligible for garbage collection.</span></span>  
  
```csharp
string b = "h";  
b += "ello";  
```  
  
 <span data-ttu-id="c3a84-114">O operador [] pode ser usado para o acesso somente leitura a caracteres individuais de uma `string`:</span><span class="sxs-lookup"><span data-stu-id="c3a84-114">The [] operator can be used for readonly access to individual characters of a `string`:</span></span>  
  
```csharp  
string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 <span data-ttu-id="c3a84-115">Literais de cadeia de caracteres são do tipo `string` e podem ser escritos de duas formas, entre aspas e @-quoted.</span><span class="sxs-lookup"><span data-stu-id="c3a84-115">String literals are of type `string` and can be written in two forms, quoted and @-quoted.</span></span> <span data-ttu-id="c3a84-116">Os literais de cadeia de caracteres entre aspas são colocados entre aspas duplas ("):</span><span class="sxs-lookup"><span data-stu-id="c3a84-116">Quoted string literals are enclosed in double quotation marks ("):</span></span>  
  
```csharp  
"good morning"  // a string literal  
```  
  
 <span data-ttu-id="c3a84-117">Os literais de cadeia de caracteres podem conter qualquer literal de caractere.</span><span class="sxs-lookup"><span data-stu-id="c3a84-117">String literals can contain any character literal.</span></span> <span data-ttu-id="c3a84-118">Sequências de escape são incluídas.</span><span class="sxs-lookup"><span data-stu-id="c3a84-118">Escape sequences are included.</span></span> <span data-ttu-id="c3a84-119">O exemplo a seguir usa a sequência de escape `\\` de barra invertida, `\u0066` para a letra f e `\n` para a nova linha.</span><span class="sxs-lookup"><span data-stu-id="c3a84-119">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>  
  
```csharp  
string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  <span data-ttu-id="c3a84-120">O código de escape `\udddd` (em que `dddd` é um número de quatro dígitos) representa o caractere Unicode U+`dddd`.</span><span class="sxs-lookup"><span data-stu-id="c3a84-120">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="c3a84-121">Os códigos de escape Unicode de oito dígitos também são reconhecidos: `\Udddddddd`.</span><span class="sxs-lookup"><span data-stu-id="c3a84-121">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>  
  
 <span data-ttu-id="c3a84-122">Os literais de cadeia de caracteres textuais começam com `@` e também são colocados entre aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="c3a84-122">Verbatim string literals start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="c3a84-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c3a84-123">For example:</span></span>  
  
```csharp  
@"good morning"  // a string literal  
```  
  
 <span data-ttu-id="c3a84-124">A vantagem das cadeias de caracteres textuais é que as sequências de escape *não* são processadas, o que torna mais fácil escrever, por exemplo, um nome de arquivo totalmente qualificado:</span><span class="sxs-lookup"><span data-stu-id="c3a84-124">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified file name:</span></span>  
  
```csharp  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 <span data-ttu-id="c3a84-125">Para incluir aspas duplas em uma cadeia de caracteres @-quoted, dobre-a:</span><span class="sxs-lookup"><span data-stu-id="c3a84-125">To include a double quotation mark in an @-quoted string, double it:</span></span>  
  
```csharp  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 <span data-ttu-id="c3a84-126">Para saber outras formas de usar o caractere especial `@`, confira [@ – identificador textual](../tokens/verbatim.md).</span><span class="sxs-lookup"><span data-stu-id="c3a84-126">For other uses of the `@` special character, see [@ -- verbatim identifier](../tokens/verbatim.md).</span></span>  
  
 <span data-ttu-id="c3a84-127">Para obter mais informações sobre cadeias de caracteres, consulte [Cadeias de caracteres](../../../csharp/programming-guide/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="c3a84-127">For more information about strings in C#, see [Strings](../../../csharp/programming-guide/strings/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3a84-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3a84-128">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="c3a84-129">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="c3a84-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c3a84-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3a84-130">See Also</span></span>

- [<span data-ttu-id="c3a84-131">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="c3a84-131">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="c3a84-132">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="c3a84-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c3a84-133">Melhores práticas para o uso de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="c3a84-133">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)  
- [<span data-ttu-id="c3a84-134">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="c3a84-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="c3a84-135">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="c3a84-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c3a84-136">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="c3a84-136">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
- [<span data-ttu-id="c3a84-137">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="c3a84-137">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
- [<span data-ttu-id="c3a84-138">Operações básicas de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="c3a84-138">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)  
- [<span data-ttu-id="c3a84-139">Criando novas cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="c3a84-139">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)  
- [<span data-ttu-id="c3a84-140">Tabela de formatação de resultados numéricos</span><span class="sxs-lookup"><span data-stu-id="c3a84-140">Formatting Numeric Results Table</span></span>](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)
