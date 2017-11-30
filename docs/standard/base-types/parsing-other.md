---
title: Analisando outras cadeias de caracteres no .NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: edd48993f50ec8b91ba7941a682d7de9f22aa12e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="4fa69-102">Analisando outras cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="4fa69-102">Parsing Other Strings in .NET</span></span>
<span data-ttu-id="4fa69-103">Além de numeric e <xref:System.DateTime> cadeias de caracteres, você também pode analisar cadeias de caracteres que representam os tipos de <xref:System.Char>, <xref:System.Boolean>, e <xref:System.Enum> em tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="4fa69-103">In addition to numeric and <xref:System.DateTime> strings, you can also parse strings that represent the types <xref:System.Char>, <xref:System.Boolean>, and <xref:System.Enum> into data types.</span></span>  
  
## <a name="char"></a><span data-ttu-id="4fa69-104">Char</span><span class="sxs-lookup"><span data-stu-id="4fa69-104">Char</span></span>  
 <span data-ttu-id="4fa69-105">O método de análise estática associado ao tipo de dados **Char** é útil para converter uma cadeia de caracteres que contém um único caractere em seu valor Unicode.</span><span class="sxs-lookup"><span data-stu-id="4fa69-105">The static parse method associated with the **Char** data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="4fa69-106">O exemplo de código a seguir analisa uma cadeia de caracteres em um caractere Unicode.</span><span class="sxs-lookup"><span data-stu-id="4fa69-106">The following code example parses a string into a Unicode character.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a><span data-ttu-id="4fa69-107">Boolean</span><span class="sxs-lookup"><span data-stu-id="4fa69-107">Boolean</span></span>  
 <span data-ttu-id="4fa69-108">O **booliano** tipo de dados contém um **analisar** método que você pode usar para converter uma cadeia de caracteres que representa um valor booliano em um real **booliano** tipo.</span><span class="sxs-lookup"><span data-stu-id="4fa69-108">The **Boolean** data type contains a **Parse** method that you can use to convert a string that represents a Boolean value into an actual **Boolean** type.</span></span> <span data-ttu-id="4fa69-109">Esse método não diferencia maiúsculas de minúsculas e consegue analisar com êxito uma cadeia de caracteres que contém “True” ou “False”.</span><span class="sxs-lookup"><span data-stu-id="4fa69-109">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="4fa69-110">O **analisar** método associado com o **booliano** tipo também pode analisar cadeias de caracteres que são cercadas por espaços em branco.</span><span class="sxs-lookup"><span data-stu-id="4fa69-110">The **Parse** method associated with the **Boolean** type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="4fa69-111">Se qualquer outra cadeia de caracteres for passada, um <xref:System.FormatException> é gerada.</span><span class="sxs-lookup"><span data-stu-id="4fa69-111">If any other string is passed, a <xref:System.FormatException> is thrown.</span></span>  
  
 <span data-ttu-id="4fa69-112">O seguinte exemplo de código usa o **analisar** método para converter uma cadeia de caracteres em um valor booleano.</span><span class="sxs-lookup"><span data-stu-id="4fa69-112">The following code example uses the **Parse** method to convert a string into a Boolean value.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a><span data-ttu-id="4fa69-113">Enumeração</span><span class="sxs-lookup"><span data-stu-id="4fa69-113">Enumeration</span></span>  
 <span data-ttu-id="4fa69-114">Você pode usar o método estático **Parse** para inicializar um tipo de enumeração para o valor de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4fa69-114">You can use the static **Parse** method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="4fa69-115">Esse método aceita o tipo de enumeração que você estiver analisando, a cadeia de caracteres para analisar e um sinalizador booleano opcional que indica se a análise diferencia maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="4fa69-115">This method accepts the enumeration type you are parsing, the string to parse, and an optional Boolean flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="4fa69-116">A cadeia de caracteres que você está analisando pode conter diversos valores separados por vírgulas, que podem ser antecedidos ou seguidos por um ou mais espaços vazios (também chamados de espaços em branco).</span><span class="sxs-lookup"><span data-stu-id="4fa69-116">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="4fa69-117">Quando a cadeia de caracteres contém diversos valores, o valor do objeto retornado é o valor de todos os valores especificados combinado com uma operação OR bit a bit.</span><span class="sxs-lookup"><span data-stu-id="4fa69-117">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>  
  
 <span data-ttu-id="4fa69-118">O exemplo a seguir usa o **analisar** método para converter uma representação de cadeia de caracteres em um valor de enumeração.</span><span class="sxs-lookup"><span data-stu-id="4fa69-118">The following example uses the **Parse** method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="4fa69-119">O <xref:System.DayOfWeek> enumeração é inicializada como **quinta-feira** de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4fa69-119">The <xref:System.DayOfWeek> enumeration is initialized to **Thursday** from a string.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="4fa69-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4fa69-120">See Also</span></span>  
 [<span data-ttu-id="4fa69-121">Análise de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="4fa69-121">Parsing Strings</span></span>](../../../docs/standard/base-types/parsing-strings.md)  
 [<span data-ttu-id="4fa69-122">Formatando Tipos</span><span class="sxs-lookup"><span data-stu-id="4fa69-122">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 [<span data-ttu-id="4fa69-123">Conversão de tipo no .NET</span><span class="sxs-lookup"><span data-stu-id="4fa69-123">Type Conversion in the .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)
