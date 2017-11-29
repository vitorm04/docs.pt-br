---
title: Conjunto de caracteres de entrada (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 691f29a04b1b1f997be501330ec887d6815d7531
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="input-character-set-entity-sql"></a><span data-ttu-id="0ad21-102">Conjunto de caracteres de entrada (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0ad21-102">Input Character Set (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="0ad21-103"> aceita os caracteres de UNICODE codificados em UTF-16.</span><span class="sxs-lookup"><span data-stu-id="0ad21-103"> accepts UNICODE characters encoded in UTF-16.</span></span>  
  
 <span data-ttu-id="0ad21-104">Literais de cadeia de caracteres podem conter qualquer caractere UTF-16 colocado entre aspas simples.</span><span class="sxs-lookup"><span data-stu-id="0ad21-104">String literals can contain any UTF-16 character enclosed in single quotes.</span></span> <span data-ttu-id="0ad21-105">Por exemplo, N'文字列リテラル.</span><span class="sxs-lookup"><span data-stu-id="0ad21-105">For example, N'文字列リテラル'.</span></span> <span data-ttu-id="0ad21-106">Quando os literais de cadeia de caracteres são comparados, os valores de original UTF-16 são usados.</span><span class="sxs-lookup"><span data-stu-id="0ad21-106">When string literals are compared, the original UTF-16 values are used.</span></span> <span data-ttu-id="0ad21-107">Por exemplo, N'ABC é diferente em páginas de código japonesas e latinos.</span><span class="sxs-lookup"><span data-stu-id="0ad21-107">For example, N'ABC' is different in Japanese and Latin codepages.</span></span>  
  
 <span data-ttu-id="0ad21-108">Comentários podem conter qualquer caractere UTF-16.</span><span class="sxs-lookup"><span data-stu-id="0ad21-108">Comments can contain any UTF-16 character.</span></span>  
  
 <span data-ttu-id="0ad21-109">Os identificadores escapados podem conter qualquer caractere UTF-16 entre colchetes.</span><span class="sxs-lookup"><span data-stu-id="0ad21-109">Escaped identifiers can contain any UTF-16 character enclosed in square brackets.</span></span> <span data-ttu-id="0ad21-110">Por exemplo, エスケープされた識別子 [].</span><span class="sxs-lookup"><span data-stu-id="0ad21-110">For example, [エスケープされた識別子].</span></span> <span data-ttu-id="0ad21-111">A comparação de identificadores escapados UTF-16 não difere maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="0ad21-111">The comparison of UTF-16 escaped identifiers is case insensitive.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="0ad21-112"> trata versões de letras que aparecem o mesmo mas é páginas diferentes de código como caracteres diferentes.</span><span class="sxs-lookup"><span data-stu-id="0ad21-112"> treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="0ad21-113">Por exemplo, [ABC] é equivalente a [abc] se os caracteres correspondentes são da mesma página de código.</span><span class="sxs-lookup"><span data-stu-id="0ad21-113">For example, [ABC] is equivalent to [abc] if the corresponding characters are from the same code page.</span></span> <span data-ttu-id="0ad21-114">No entanto, se os mesmos dois identificadores são de páginas de código diferentes, eles não são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="0ad21-114">However, if the same two identifiers are from different code pages, they are not equivalent.</span></span>  
  
 <span data-ttu-id="0ad21-115">Espaço em branco é qualquer caractere de espaço em branco UTF-16.</span><span class="sxs-lookup"><span data-stu-id="0ad21-115">White space is any UTF-16 white space character.</span></span>  
  
 <span data-ttu-id="0ad21-116">Uma nova linha é qualquer caractere de nova linha UTF-16 normalizado.</span><span class="sxs-lookup"><span data-stu-id="0ad21-116">A newline is any normalized UTF-16 newline character.</span></span> <span data-ttu-id="0ad21-117">Por exemplo, “\ n” e “\ \ r em” é considerado caracteres de nova linha, mas “\ r” não é um caractere de nova linha.</span><span class="sxs-lookup"><span data-stu-id="0ad21-117">For example, '\n' and '\r\n' are considered newline characters, but '\r' is not a newline character.</span></span>  
  
 <span data-ttu-id="0ad21-118">Palavras-chave, as expressões, e pontuação podem ser qualquer caractere UTF-16 que normalizar ao latim.</span><span class="sxs-lookup"><span data-stu-id="0ad21-118">Keywords, expressions, and punctuation can be any UTF-16 character that normalizes to Latin.</span></span> <span data-ttu-id="0ad21-119">Por exemplo, SELECT em uma página de código japonesa é uma palavra-chave válida.</span><span class="sxs-lookup"><span data-stu-id="0ad21-119">For example, SELECT in a Japanese codepage is a valid keyword.</span></span>  
  
 <span data-ttu-id="0ad21-120">Palavras-chave, as expressões, e pontuação só podem ser caracteres latinos.</span><span class="sxs-lookup"><span data-stu-id="0ad21-120">Keywords, expressions, and punctuation can only be Latin characters.</span></span> <span data-ttu-id="0ad21-121">`SELECT` em uma página de código japonesa não é uma palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="0ad21-121">`SELECT` in a Japanese codepage is not a keyword.</span></span> <span data-ttu-id="0ad21-122">+, -, *,/, =, (,), o ', [], e qualquer outra construção de linguagem não citada aqui só podem ser caracteres latinos.</span><span class="sxs-lookup"><span data-stu-id="0ad21-122">+, -, *, /, =, (, ), ‘, [, ] and any other language construct not quoted here can only be Latin characters.</span></span>  
  
 <span data-ttu-id="0ad21-123">Os identificadores simples só podem ser caracteres latinos.</span><span class="sxs-lookup"><span data-stu-id="0ad21-123">Simple identifiers can only be Latin characters.</span></span> <span data-ttu-id="0ad21-124">Isso evita a ambiguidade durante a comparação, porque os valores originais são comparados.</span><span class="sxs-lookup"><span data-stu-id="0ad21-124">This avoids ambiguity during comparison, because original values are compared.</span></span> <span data-ttu-id="0ad21-125">Por exemplo, ABC deve ser diferente em páginas de código japonesas e latinos.</span><span class="sxs-lookup"><span data-stu-id="0ad21-125">For example, ABC would be different in in Japanese and Latin codepages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ad21-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ad21-126">See Also</span></span>  
 [<span data-ttu-id="0ad21-127">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0ad21-127">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
