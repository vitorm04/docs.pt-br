---
title: 'Como: Pesquisar dentro de uma cadeia de caracteres-Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: fe9e50dc5458fdf8546094e5f41c2f001f1d2791
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700071"
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="be321-102">Como: Pesquisar dentro de uma cadeia de caracteres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be321-102">How to: search within a string (Visual Basic)</span></span>

<span data-ttu-id="be321-103">Este artigo mostra um exemplo de como Pesquisar dentro de uma cadeia de caracteres em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="be321-103">This article shows an example of how to search within a string in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="be321-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="be321-104">Example</span></span>

<span data-ttu-id="be321-105">Este exemplo chama o método <xref:System.String.IndexOf%2A> em um objeto <xref:System.String> para relatar o índice da primeira ocorrência de uma subcadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="be321-105">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring:</span></span>

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a><span data-ttu-id="be321-106">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="be321-106">Robust programming</span></span>

<span data-ttu-id="be321-107">O método <xref:System.String.IndexOf%2A> retorna o local do primeiro caractere da primeira ocorrência da subcadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="be321-107">The <xref:System.String.IndexOf%2A> method returns the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="be321-108">O índice é baseado em 0, o que significa que o primeiro caractere de uma cadeia de caracteres tem um índice de 0.</span><span class="sxs-lookup"><span data-stu-id="be321-108">The index is 0-based, which means the first character of a string has an index of 0.</span></span>

<span data-ttu-id="be321-109">Se <xref:System.String.IndexOf%2A> não encontrar a subcadeia de caracteres, ela retornará-1.</span><span class="sxs-lookup"><span data-stu-id="be321-109">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>

<span data-ttu-id="be321-110">O método <xref:System.String.IndexOf%2A> diferencia maiúsculas de minúsculas e usa a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="be321-110">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>

<span data-ttu-id="be321-111">Para obter um controle de erro ideal, talvez você queira colocar a pesquisa de cadeia de caracteres no bloco `Try` de uma [tentativa... Capturar... Instrução Finally](../../../language-reference/statements/try-catch-finally-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="be321-111">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md) construction.</span></span>

## <a name="see-also"></a><span data-ttu-id="be321-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be321-112">See also</span></span>

- <xref:System.String.IndexOf%2A>
- [<span data-ttu-id="be321-113">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="be321-113">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="be321-114">Introdução às cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="be321-114">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
- [<span data-ttu-id="be321-115">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="be321-115">Strings</span></span>](index.md)
