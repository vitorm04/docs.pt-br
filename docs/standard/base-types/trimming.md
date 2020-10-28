---
title: Como cortar e remover caracteres das cadeias de caracteres no .NET
description: Saiba como cortar espaços em branco do início ou do fim de uma cadeia de caracteres ou remover qualquer número de espaços ou caracteres de uma posição especificada na cadeia de caracteres no .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET], removing characters
- Remove method
- TrimEnd method
- Trim method
- trimming characters
- TrimStart method
- removing characters
ms.assetid: ab248dab-70d4-4413-81c6-542d153fd195
ms.openlocfilehash: d0057d503474f3f6ff886acda3ce1d72fb3ebe21
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888588"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a><span data-ttu-id="185b3-103">Como cortar e remover caracteres das cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="185b3-103">Trimming and Removing Characters from Strings in .NET</span></span>
<span data-ttu-id="185b3-104">Se estiver analisando as palavras individuais de uma sentença, você poderá encontrar palavras com espaços em branco em ambas as extremidades da palavra.</span><span class="sxs-lookup"><span data-stu-id="185b3-104">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="185b3-105">Nessa situação, você pode usar um dos métodos de corte na classe **System.String** para remover qualquer número de espaços ou de outros caracteres de uma posição especificada na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="185b3-105">In this situation, you can use one of the trim methods in the **System.String** class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="185b3-106">A tabela a seguir descreve os métodos de corte disponíveis.</span><span class="sxs-lookup"><span data-stu-id="185b3-106">The following table describes the available trim methods.</span></span>  
  
|<span data-ttu-id="185b3-107">Nome do método</span><span class="sxs-lookup"><span data-stu-id="185b3-107">Method name</span></span>|<span data-ttu-id="185b3-108">Uso</span><span class="sxs-lookup"><span data-stu-id="185b3-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|<span data-ttu-id="185b3-109">Remove os espaços em branco ou caracteres especificados em uma matriz de caracteres do início e do final de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="185b3-109">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|<span data-ttu-id="185b3-110">Remove os caracteres especificados em uma matriz de caracteres do final de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="185b3-110">Removes characters specified in an array of characters from the end of a string.</span></span>|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|<span data-ttu-id="185b3-111">Remove os caracteres especificados em uma matriz de caracteres do início de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="185b3-111">Removes characters specified in an array of characters from the beginning of a string.</span></span>|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="185b3-112">Remove um número especificado de caracteres de uma posição de índice especificada em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="185b3-112">Removes a specified number of characters from a specified index position in a string.</span></span>|  
  
## <a name="trim"></a><span data-ttu-id="185b3-113">Trim</span><span class="sxs-lookup"><span data-stu-id="185b3-113">Trim</span></span>

 <span data-ttu-id="185b3-114">Você pode remover espaços em branco com facilidade de ambas as extremidades de uma cadeia de caracteres usando o método <xref:System.String.Trim%2A?displayProperty=nameWithType>, conforme é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="185b3-114">You can easily remove white spaces from both ends of a string by using the <xref:System.String.Trim%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 <span data-ttu-id="185b3-115">Você também poderá remover os caracteres que especificar em uma matriz de caracteres do início e do final de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="185b3-115">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="185b3-116">O exemplo a seguir remove caracteres de espaço em branco, pontos e asteriscos.</span><span class="sxs-lookup"><span data-stu-id="185b3-116">The following example removes white-space characters, periods, and asterisks.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a><span data-ttu-id="185b3-117">TrimEnd</span><span class="sxs-lookup"><span data-stu-id="185b3-117">TrimEnd</span></span>

 <span data-ttu-id="185b3-118">O método **String.TrimEnd** remove os caracteres do final de uma cadeia de caracteres, criando um novo objeto de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="185b3-118">The **String.TrimEnd** method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="185b3-119">Uma matriz de caracteres é passada para este método para especificar os caracteres a seres removidos.</span><span class="sxs-lookup"><span data-stu-id="185b3-119">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="185b3-120">A ordem dos elementos na matriz de caracteres não afeta a operação de corte.</span><span class="sxs-lookup"><span data-stu-id="185b3-120">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="185b3-121">O corte é interrompido quando um caractere não especificado na matriz é encontrado.</span><span class="sxs-lookup"><span data-stu-id="185b3-121">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="185b3-122">O exemplo a seguir remove as últimas letras de uma cadeia de caracteres usando o método **TrimEnd** .</span><span class="sxs-lookup"><span data-stu-id="185b3-122">The following example removes the last letters of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="185b3-123">Neste exemplo, as posições do caractere `'r'` e do caractere `'W'` estão invertidas para ilustrar que a ordem dos caracteres na matriz não importa.</span><span class="sxs-lookup"><span data-stu-id="185b3-123">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="185b3-124">Observe que este código remove a última palavra de `MyString` mais uma parte da primeira.</span><span class="sxs-lookup"><span data-stu-id="185b3-124">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 <span data-ttu-id="185b3-125">Esse código exibe `He` no console.</span><span class="sxs-lookup"><span data-stu-id="185b3-125">This code displays `He` to the console.</span></span>  
  
 <span data-ttu-id="185b3-126">O exemplo a seguir remove as últimas palavras de uma cadeia de caracteres usando o método **TrimEnd** .</span><span class="sxs-lookup"><span data-stu-id="185b3-126">The following example removes the last word of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="185b3-127">Nesse código, há uma vírgula após a palavra `Hello` e, como a vírgula não está especificada na matriz de caracteres para cortar, o corte termina na vírgula.</span><span class="sxs-lookup"><span data-stu-id="185b3-127">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 <span data-ttu-id="185b3-128">Esse código exibe `Hello,` no console.</span><span class="sxs-lookup"><span data-stu-id="185b3-128">This code displays `Hello,` to the console.</span></span>  
  
## <a name="trimstart"></a><span data-ttu-id="185b3-129">TrimStart</span><span class="sxs-lookup"><span data-stu-id="185b3-129">TrimStart</span></span>

 <span data-ttu-id="185b3-130">O método **String.TrimStart** é semelhante ao método **String.TrimEnd** , exceto que ele cria uma nova cadeia de caracteres removendo caracteres do início de um objeto de cadeia de caracteres existente.</span><span class="sxs-lookup"><span data-stu-id="185b3-130">The **String.TrimStart** method is similar to the **String.TrimEnd** method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="185b3-131">Uma matriz de caracteres é passada para o método **TrimStart** para especificar os caracteres a serem removidos.</span><span class="sxs-lookup"><span data-stu-id="185b3-131">An array of characters is passed to the **TrimStart** method to specify the characters to be removed.</span></span> <span data-ttu-id="185b3-132">Assim como acontece com o método **TrimEnd** , a ordem dos elementos na matriz de caracteres não afeta a operação de corte.</span><span class="sxs-lookup"><span data-stu-id="185b3-132">As with the **TrimEnd** method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="185b3-133">O corte é interrompido quando um caractere não especificado na matriz é encontrado.</span><span class="sxs-lookup"><span data-stu-id="185b3-133">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="185b3-134">O exemplo a seguir remove a primeira palavra de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="185b3-134">The following example removes the first word of a string.</span></span> <span data-ttu-id="185b3-135">Neste exemplo, as posições do caractere `'l'` e do caractere `'H'` estão invertidas para ilustrar que a ordem dos caracteres na matriz não importa.</span><span class="sxs-lookup"><span data-stu-id="185b3-135">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 <span data-ttu-id="185b3-136">Esse código exibe `World!` no console.</span><span class="sxs-lookup"><span data-stu-id="185b3-136">This code displays `World!` to the console.</span></span>  
  
## <a name="remove"></a><span data-ttu-id="185b3-137">Remover</span><span class="sxs-lookup"><span data-stu-id="185b3-137">Remove</span></span>

 <span data-ttu-id="185b3-138">O método <xref:System.String.Remove%2A?displayProperty=nameWithType> remove um número especificado de caracteres que começam em uma posição especificada em uma cadeia de caracteres existente.</span><span class="sxs-lookup"><span data-stu-id="185b3-138">The <xref:System.String.Remove%2A?displayProperty=nameWithType> method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="185b3-139">Este método assume um índice baseado em zero.</span><span class="sxs-lookup"><span data-stu-id="185b3-139">This method assumes a zero-based index.</span></span>  
  
 <span data-ttu-id="185b3-140">O exemplo a seguir remove dez caracteres de uma cadeia de caracteres começando na posição cinco de um índice baseado em zero da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="185b3-140">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
## <a name="replace"></a><span data-ttu-id="185b3-141">Substitua</span><span class="sxs-lookup"><span data-stu-id="185b3-141">Replace</span></span>

 <span data-ttu-id="185b3-142">Você também pode remover um caractere ou uma subcadeia de caracteres especificada de uma cadeia de caracteres chamando o método <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> e especificando uma cadeia de caracteres vazia (<xref:System.String.Empty?displayProperty=nameWithType>) como a substituição.</span><span class="sxs-lookup"><span data-stu-id="185b3-142">You can also remove a specified character or substring from a string by calling the <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> method and specifying an empty string (<xref:System.String.Empty?displayProperty=nameWithType>) as the replacement.</span></span> <span data-ttu-id="185b3-143">O exemplo a seguir remove todas as vírgulas de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="185b3-143">The following example removes all commas from a string.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="185b3-144">Veja também</span><span class="sxs-lookup"><span data-stu-id="185b3-144">See also</span></span>

- [<span data-ttu-id="185b3-145">Operações básicas de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="185b3-145">Basic String Operations</span></span>](basic-string-operations.md)
