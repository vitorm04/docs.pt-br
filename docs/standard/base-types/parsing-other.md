---
title: Analisando outras cadeias de caracteres no .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Char data type, parsing strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- parsing strings, other strings
- Boolean data type, parsing strings
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
ms.openlocfilehash: 08e891501bbefcf8b32eff10dd7294af9d81adac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127566"
---
# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="ab75e-102">Analisando outras cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="ab75e-102">Parsing Other Strings in .NET</span></span>
<span data-ttu-id="ab75e-103">Além das cadeias de caracteres numéricas e <xref:System.DateTime>, também é possível analisar cadeias de caracteres que representam os tipos <xref:System.Char> <xref:System.Boolean> e<xref:System.Enum> em tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="ab75e-103">In addition to numeric and <xref:System.DateTime> strings, you can also parse strings that represent the types <xref:System.Char>, <xref:System.Boolean>, and <xref:System.Enum> into data types.</span></span>  
  
## <a name="char"></a><span data-ttu-id="ab75e-104">Char</span><span class="sxs-lookup"><span data-stu-id="ab75e-104">Char</span></span>  
 <span data-ttu-id="ab75e-105">O método de análise estática associado ao tipo de dados **Char** é útil para converter uma cadeia de caracteres que contém um único caractere em seu valor Unicode.</span><span class="sxs-lookup"><span data-stu-id="ab75e-105">The static parse method associated with the **Char** data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="ab75e-106">O exemplo de código a seguir analisa uma cadeia de caracteres em um caractere Unicode.</span><span class="sxs-lookup"><span data-stu-id="ab75e-106">The following code example parses a string into a Unicode character.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a><span data-ttu-id="ab75e-107">Booleano</span><span class="sxs-lookup"><span data-stu-id="ab75e-107">Boolean</span></span>  
 <span data-ttu-id="ab75e-108">O tipo de dados **Booliano** contém um método **Parse** que pode ser usado para converter uma cadeia de caracteres que representa um valor Booliano em um tipo **Booliano** real.</span><span class="sxs-lookup"><span data-stu-id="ab75e-108">The **Boolean** data type contains a **Parse** method that you can use to convert a string that represents a Boolean value into an actual **Boolean** type.</span></span> <span data-ttu-id="ab75e-109">Esse método não diferencia maiúsculas de minúsculas e consegue analisar com êxito uma cadeia de caracteres que contém “True” ou “False”.</span><span class="sxs-lookup"><span data-stu-id="ab75e-109">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="ab75e-110">O método **Parse** associado ao tipo **Booliano** também pode analisar cadeias de caracteres cercadas por espaços em branco.</span><span class="sxs-lookup"><span data-stu-id="ab75e-110">The **Parse** method associated with the **Boolean** type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="ab75e-111">Se qualquer outra cadeia de caracteres for passada, um <xref:System.FormatException> será gerado.</span><span class="sxs-lookup"><span data-stu-id="ab75e-111">If any other string is passed, a <xref:System.FormatException> is thrown.</span></span>  
  
 <span data-ttu-id="ab75e-112">O exemplo de código a seguir usa o método **Parse** para converter uma cadeia de caracteres em um valor Booliano.</span><span class="sxs-lookup"><span data-stu-id="ab75e-112">The following code example uses the **Parse** method to convert a string into a Boolean value.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a><span data-ttu-id="ab75e-113">Enumeração</span><span class="sxs-lookup"><span data-stu-id="ab75e-113">Enumeration</span></span>  
 <span data-ttu-id="ab75e-114">Você pode usar o método estático **Parse** para inicializar um tipo de enumeração para o valor de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ab75e-114">You can use the static **Parse** method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="ab75e-115">Esse método aceita o tipo de enumeração que você estiver analisando, a cadeia de caracteres a analisar e um sinalizador Booliano opcional que indica se a análise diferencia maiúsculas de minúsculas ou não.</span><span class="sxs-lookup"><span data-stu-id="ab75e-115">This method accepts the enumeration type you are parsing, the string to parse, and an optional Boolean flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="ab75e-116">A cadeia de caracteres que você está analisando pode conter diversos valores separados por vírgulas, que podem ser antecedidos ou seguidos por um ou mais espaços vazios (também chamados de espaços em branco).</span><span class="sxs-lookup"><span data-stu-id="ab75e-116">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="ab75e-117">Quando a cadeia de caracteres contém diversos valores, o valor do objeto retornado é o valor de todos os valores especificados combinado com uma operação OR bit a bit.</span><span class="sxs-lookup"><span data-stu-id="ab75e-117">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>  
  
 <span data-ttu-id="ab75e-118">O exemplo a seguir usa o método **Parse** para converter uma representação de cadeia de caracteres em um valor de enumeração.</span><span class="sxs-lookup"><span data-stu-id="ab75e-118">The following example uses the **Parse** method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="ab75e-119">A enumeração <xref:System.DayOfWeek> é inicializada para **Quinta-feira** de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ab75e-119">The <xref:System.DayOfWeek> enumeration is initialized to **Thursday** from a string.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="ab75e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab75e-120">See also</span></span>

- [<span data-ttu-id="ab75e-121">Análise de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="ab75e-121">Parsing Strings</span></span>](../../../docs/standard/base-types/parsing-strings.md)
- [<span data-ttu-id="ab75e-122">Formatando Tipos</span><span class="sxs-lookup"><span data-stu-id="ab75e-122">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)
- [<span data-ttu-id="ab75e-123">Conversão de tipo no .NET</span><span class="sxs-lookup"><span data-stu-id="ab75e-123">Type Conversion in the .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)
