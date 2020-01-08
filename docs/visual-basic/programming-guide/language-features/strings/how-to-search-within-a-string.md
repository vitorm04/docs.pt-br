---
title: 'Como: Pesquisar dentro de uma cadeia de caracteres'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: 655f746e4e496e1935afcd2a9f9fe36d9e3a2564
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348418"
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="e32ae-102">Como: Pesquisar dentro de uma cadeia de caracteres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e32ae-102">How to: search within a string (Visual Basic)</span></span>

<span data-ttu-id="e32ae-103">Este artigo mostra um exemplo de como Pesquisar dentro de uma cadeia de caracteres em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e32ae-103">This article shows an example of how to search within a string in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="e32ae-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e32ae-104">Example</span></span>

<span data-ttu-id="e32ae-105">Este exemplo chama o método <xref:System.String.IndexOf%2A> em um objeto <xref:System.String> para relatar o índice da primeira ocorrência de uma subcadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="e32ae-105">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring:</span></span>

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a><span data-ttu-id="e32ae-106">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="e32ae-106">Robust programming</span></span>

<span data-ttu-id="e32ae-107">O método <xref:System.String.IndexOf%2A> retorna o local do primeiro caractere da primeira ocorrência da subcadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e32ae-107">The <xref:System.String.IndexOf%2A> method returns the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="e32ae-108">O índice é baseado em 0, o que significa que o primeiro caractere de uma cadeia de caracteres tem um índice de 0.</span><span class="sxs-lookup"><span data-stu-id="e32ae-108">The index is 0-based, which means the first character of a string has an index of 0.</span></span>

<span data-ttu-id="e32ae-109">Se <xref:System.String.IndexOf%2A> não encontrar a subcadeia de caracteres, ela retornará-1.</span><span class="sxs-lookup"><span data-stu-id="e32ae-109">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>

<span data-ttu-id="e32ae-110">O método <xref:System.String.IndexOf%2A> diferencia maiúsculas de minúsculas e usa a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="e32ae-110">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>

<span data-ttu-id="e32ae-111">Para obter um controle de erro ideal, você pode desejar colocar a pesquisa de cadeia de caracteres no bloco de `Try` de uma [tentativa... Capturar... Instrução Finally](../../../language-reference/statements/try-catch-finally-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="e32ae-111">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md) construction.</span></span>

## <a name="see-also"></a><span data-ttu-id="e32ae-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="e32ae-112">See also</span></span>

- <xref:System.String.IndexOf%2A>
- [<span data-ttu-id="e32ae-113">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="e32ae-113">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="e32ae-114">Introdução às cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e32ae-114">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
- [<span data-ttu-id="e32ae-115">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e32ae-115">Strings</span></span>](index.md)
