---
title: Cortando e removendo caracteres de cadeias de caracteres no .NET
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
- strings [.NET Framework], removing characters
- Remove method
- TrimEnd method
- Trim method
- trimming characters
- TrimStart method
- removing characters
ms.assetid: ab248dab-70d4-4413-81c6-542d153fd195
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fde24a97234d275d3d599f13bfc4063af939507b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a><span data-ttu-id="1cecd-102">Cortando e removendo caracteres de cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="1cecd-102">Trimming and Removing Characters from Strings in .NET</span></span>
<span data-ttu-id="1cecd-103">Se estiver analisando as palavras individuais de uma sentença, você poderá encontrar palavras com espaços em branco em ambas as extremidades da palavra.</span><span class="sxs-lookup"><span data-stu-id="1cecd-103">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="1cecd-104">Nessa situação, você pode usar um dos métodos de corte na classe **System.String** para remover qualquer número de espaços ou de outros caracteres de uma posição especificada na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1cecd-104">In this situation, you can use one of the trim methods in the **System.String** class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="1cecd-105">A tabela a seguir descreve os métodos de corte disponíveis.</span><span class="sxs-lookup"><span data-stu-id="1cecd-105">The following table describes the available trim methods.</span></span>  
  
|<span data-ttu-id="1cecd-106">Nome do método</span><span class="sxs-lookup"><span data-stu-id="1cecd-106">Method name</span></span>|<span data-ttu-id="1cecd-107">Use</span><span class="sxs-lookup"><span data-stu-id="1cecd-107">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|<span data-ttu-id="1cecd-108">Remove os espaços em branco ou caracteres especificados em uma matriz de caracteres do início e do final de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1cecd-108">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|<span data-ttu-id="1cecd-109">Remove os caracteres especificados em uma matriz de caracteres do final de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1cecd-109">Removes characters specified in an array of characters from the end of a string.</span></span>|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|<span data-ttu-id="1cecd-110">Remove os caracteres especificados em uma matriz de caracteres do início de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1cecd-110">Removes characters specified in an array of characters from the beginning of a string.</span></span>|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="1cecd-111">Remove um número especificado de caracteres de uma posição de índice especificada em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1cecd-111">Removes a specified number of characters from a specified index position in a string.</span></span>|  
  
## <a name="trim"></a><span data-ttu-id="1cecd-112">Trim</span><span class="sxs-lookup"><span data-stu-id="1cecd-112">Trim</span></span>  
 <span data-ttu-id="1cecd-113">Você pode facilmente remover espaços em branco de ambas as extremidades de uma cadeia de caracteres usando o <xref:System.String.Trim%2A?displayProperty=nameWithType> método, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1cecd-113">You can easily remove white spaces from both ends of a string by using the <xref:System.String.Trim%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 <span data-ttu-id="1cecd-114">Você também poderá remover os caracteres que especificar em uma matriz de caracteres do início e do final de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1cecd-114">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="1cecd-115">O exemplo a seguir remove caracteres de espaço em branco, pontos e asteriscos.</span><span class="sxs-lookup"><span data-stu-id="1cecd-115">The following example removes white-space characters, periods, and asterisks.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a><span data-ttu-id="1cecd-116">TrimEnd</span><span class="sxs-lookup"><span data-stu-id="1cecd-116">TrimEnd</span></span>  
 <span data-ttu-id="1cecd-117">O método **String.TrimEnd** remove os caracteres do final de uma cadeia de caracteres, criando um novo objeto de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1cecd-117">The **String.TrimEnd** method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="1cecd-118">Uma matriz de caracteres é passada para este método para especificar os caracteres a seres removidos.</span><span class="sxs-lookup"><span data-stu-id="1cecd-118">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="1cecd-119">A ordem dos elementos na matriz de caracteres não afeta a operação de corte.</span><span class="sxs-lookup"><span data-stu-id="1cecd-119">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="1cecd-120">O corte é interrompido quando um caractere não especificado na matriz é encontrado.</span><span class="sxs-lookup"><span data-stu-id="1cecd-120">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="1cecd-121">O exemplo a seguir remove as últimas letras de uma cadeia de caracteres usando o **TrimEnd** método.</span><span class="sxs-lookup"><span data-stu-id="1cecd-121">The following example removes the last letters of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="1cecd-122">Neste exemplo, as posições do caractere `'r'` e do caractere `'W'` estão invertidas para ilustrar que a ordem dos caracteres na matriz não importa.</span><span class="sxs-lookup"><span data-stu-id="1cecd-122">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="1cecd-123">Observe que este código remove a última palavra de `MyString` mais uma parte da primeira.</span><span class="sxs-lookup"><span data-stu-id="1cecd-123">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 <span data-ttu-id="1cecd-124">Esse código exibe `He` no console.</span><span class="sxs-lookup"><span data-stu-id="1cecd-124">This code displays `He` to the console.</span></span>  
  
 <span data-ttu-id="1cecd-125">O exemplo a seguir remove as últimas palavras de uma cadeia de caracteres usando o método **TrimEnd**.</span><span class="sxs-lookup"><span data-stu-id="1cecd-125">The following example removes the last word of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="1cecd-126">Nesse código, há uma vírgula após a palavra `Hello` e, como a vírgula não está especificada na matriz de caracteres para cortar, o corte termina na vírgula.</span><span class="sxs-lookup"><span data-stu-id="1cecd-126">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 <span data-ttu-id="1cecd-127">Esse código exibe `Hello,` no console.</span><span class="sxs-lookup"><span data-stu-id="1cecd-127">This code displays `Hello,` to the console.</span></span>  
  
## <a name="trimstart"></a><span data-ttu-id="1cecd-128">TrimStart</span><span class="sxs-lookup"><span data-stu-id="1cecd-128">TrimStart</span></span>  
 <span data-ttu-id="1cecd-129">O método **String.TrimStart** é semelhante ao método **String.TrimEnd**, exceto que ele cria uma nova cadeia de caracteres removendo caracteres do início de um objeto de cadeia de caracteres existente.</span><span class="sxs-lookup"><span data-stu-id="1cecd-129">The **String.TrimStart** method is similar to the **String.TrimEnd** method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="1cecd-130">Uma matriz de caracteres é passada para o método **TrimStart** para especificar os caracteres a serem removidos.</span><span class="sxs-lookup"><span data-stu-id="1cecd-130">An array of characters is passed to the **TrimStart** method to specify the characters to be removed.</span></span> <span data-ttu-id="1cecd-131">Assim como acontece com o método **TrimEnd**, a ordem dos elementos na matriz de caracteres não afeta a operação de corte.</span><span class="sxs-lookup"><span data-stu-id="1cecd-131">As with the **TrimEnd** method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="1cecd-132">O corte é interrompido quando um caractere não especificado na matriz é encontrado.</span><span class="sxs-lookup"><span data-stu-id="1cecd-132">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="1cecd-133">O exemplo a seguir remove a primeira palavra de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1cecd-133">The following example removes the first word of a string.</span></span> <span data-ttu-id="1cecd-134">Neste exemplo, as posições do caractere `'l'` e do caractere `'H'` estão invertidas para ilustrar que a ordem dos caracteres na matriz não importa.</span><span class="sxs-lookup"><span data-stu-id="1cecd-134">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 <span data-ttu-id="1cecd-135">Esse código exibe `World!` no console.</span><span class="sxs-lookup"><span data-stu-id="1cecd-135">This code displays `World!` to the console.</span></span>  
  
## <a name="remove"></a><span data-ttu-id="1cecd-136">Remover</span><span class="sxs-lookup"><span data-stu-id="1cecd-136">Remove</span></span>  
 <span data-ttu-id="1cecd-137">O <xref:System.String.Remove%2A?displayProperty=nameWithType> método Remove um número especificado de caracteres que começam com uma posição especificada em uma cadeia de caracteres existente.</span><span class="sxs-lookup"><span data-stu-id="1cecd-137">The <xref:System.String.Remove%2A?displayProperty=nameWithType> method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="1cecd-138">Este método assume um índice baseado em zero.</span><span class="sxs-lookup"><span data-stu-id="1cecd-138">This method assumes a zero-based index.</span></span>  
  
 <span data-ttu-id="1cecd-139">O exemplo a seguir remove dez caracteres de uma cadeia de caracteres começando na posição cinco de um índice baseado em zero da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1cecd-139">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
 <span data-ttu-id="1cecd-140">Você também pode remover um caractere especificado ou uma subcadeia de caracteres de uma cadeia de caracteres chamando o <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> método e especificando uma cadeia de caracteres vazia (<xref:System.String.Empty?displayProperty=nameWithType>) como a substituição.</span><span class="sxs-lookup"><span data-stu-id="1cecd-140">You can also remove a specified character or substring from a string by calling the <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> method and specifying an empty string (<xref:System.String.Empty?displayProperty=nameWithType>) as the replacement.</span></span> <span data-ttu-id="1cecd-141">O exemplo a seguir remove todas as vírgulas de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1cecd-141">The following example removes all commas from a string.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="1cecd-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cecd-142">See Also</span></span>  
 [<span data-ttu-id="1cecd-143">Operações básicas de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="1cecd-143">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
