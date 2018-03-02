---
title: "Exemplos de expressões regulares"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- regular expressions [.NET Framework], examples
- regular expressions [.NET Framework]
- strings [.NET Framework], regular expressions
ms.assetid: e9fd53f2-ed56-4b09-b2ea-e9bc9d65e6d6
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4d2d3aced78d2afed3f0d1396efe5e954ef84102
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="regular-expression-examples"></a><span data-ttu-id="b7ff5-102">Exemplos de expressões regulares</span><span class="sxs-lookup"><span data-stu-id="b7ff5-102">Regular Expression Examples</span></span>
<span data-ttu-id="b7ff5-103">Esta seção contém exemplos de código que mostram o uso de expressões regulares em aplicativos comuns.</span><span class="sxs-lookup"><span data-stu-id="b7ff5-103">This section contains code examples that illustrate the use of regular expressions in common applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7ff5-104">O namespace <xref:System.Web.RegularExpressions> contém vários objetos de expressão regular que implementam padrões predefinidos de expressão regular para analisar cadeias de caracteres de documentos HTML, XML e ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b7ff5-104">The <xref:System.Web.RegularExpressions> namespace contains a number of regular expression objects that implement predefined regular expression patterns for parsing strings from HTML, XML, and ASP.NET documents.</span></span> <span data-ttu-id="b7ff5-105">Por exemplo, a classe <xref:System.Web.RegularExpressions.TagRegex> identifica marcas de início em uma cadeia de caracteres e a classe <xref:System.Web.RegularExpressions.CommentRegex> identifica comentários ASP.NET em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b7ff5-105">For example, the <xref:System.Web.RegularExpressions.TagRegex> class identifies start tags in a string and the <xref:System.Web.RegularExpressions.CommentRegex> class identifies ASP.NET comments in a string.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b7ff5-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b7ff5-106">In This Section</span></span>  
 [<span data-ttu-id="b7ff5-107">Exemplo: Verificação de HREFs</span><span class="sxs-lookup"><span data-stu-id="b7ff5-107">Example: Scanning for HREFs</span></span>](../../../docs/standard/base-types/regular-expression-example-scanning-for-hrefs.md)  
 <span data-ttu-id="b7ff5-108">Fornece um exemplo que procura uma cadeia de caracteres de entrada e imprime todos os valores href = "…" e suas localizações na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b7ff5-108">Provides an example that searches an input string and prints out all the href="…" values and their locations in the string.</span></span>  
  
 [<span data-ttu-id="b7ff5-109">Exemplo: Alterando formatos de data</span><span class="sxs-lookup"><span data-stu-id="b7ff5-109">Example: Changing Date Formats</span></span>](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md)  
 <span data-ttu-id="b7ff5-110">Fornece um exemplo que substitui as datas no formato mm/dd/aa por datas no formato dd-mm-aa.</span><span class="sxs-lookup"><span data-stu-id="b7ff5-110">Provides an example that replaces dates in the form mm/dd/yy with dates in the form dd-mm-yy.</span></span>  
  
 [<span data-ttu-id="b7ff5-111">Como extrair um protocolo e um número da porta de uma URL</span><span class="sxs-lookup"><span data-stu-id="b7ff5-111">How to: Extract a Protocol and Port Number from a URL</span></span>](../../../docs/standard/base-types/how-to-extract-a-protocol-and-port-number-from-a-url.md)  
 <span data-ttu-id="b7ff5-112">Fornece um exemplo que extrai um protocolo e o número da porta de uma cadeia de caracteres que contém uma URL.</span><span class="sxs-lookup"><span data-stu-id="b7ff5-112">Provides an example that extracts a protocol and port number from a string that contains a URL.</span></span> <span data-ttu-id="b7ff5-113">Por exemplo, “http://www.contoso.com:8080/letters/readme.html” retorna “http:8080”.</span><span class="sxs-lookup"><span data-stu-id="b7ff5-113">For example, "http://www.contoso.com:8080/letters/readme.html" returns "http:8080".</span></span>  
  
 [<span data-ttu-id="b7ff5-114">Como retirar caracteres inválidos de uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b7ff5-114">How to: Strip Invalid Characters from a String</span></span>](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md)  
 <span data-ttu-id="b7ff5-115">Fornece um exemplo que retira caracteres não alfanuméricos inválidos de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b7ff5-115">Provides an example that strips invalid non-alphanumeric characters from a string.</span></span>  
  
 [<span data-ttu-id="b7ff5-116">Como verificar se cadeias de caracteres estão em um formato de email válido</span><span class="sxs-lookup"><span data-stu-id="b7ff5-116">How to: Verify that Strings Are in Valid Email Format</span></span>](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)  
 <span data-ttu-id="b7ff5-117">Fornece um exemplo que você pode usar para verificar se uma cadeia de caracteres está no formato de email válido.</span><span class="sxs-lookup"><span data-stu-id="b7ff5-117">Provides an example that you can use to verify that a string is in valid email format.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b7ff5-118">Referência</span><span class="sxs-lookup"><span data-stu-id="b7ff5-118">Reference</span></span>  
 <xref:System.Text.RegularExpressions>  
 <span data-ttu-id="b7ff5-119">Fornece informações de referência de biblioteca de classes para o namespace **System.Text.RegularExpressions** do .NET.</span><span class="sxs-lookup"><span data-stu-id="b7ff5-119">Provides class library reference information for the .NET **System.Text.RegularExpressions** namespace.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b7ff5-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="b7ff5-120">Related Sections</span></span>  
 [<span data-ttu-id="b7ff5-121">Expressões regulares do .NET</span><span class="sxs-lookup"><span data-stu-id="b7ff5-121">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)  
 <span data-ttu-id="b7ff5-122">Fornece uma visão geral sobre o aspecto de linguagem de programação das expressões regulares.</span><span class="sxs-lookup"><span data-stu-id="b7ff5-122">Provides an overview of the programming language aspect of regular expressions.</span></span>  
  
 [<span data-ttu-id="b7ff5-123">O modelo de objeto de expressão regular</span><span class="sxs-lookup"><span data-stu-id="b7ff5-123">The Regular Expression Object Model</span></span>](../../../docs/standard/base-types/the-regular-expression-object-model.md)  
 <span data-ttu-id="b7ff5-124">Descreve as classes de expressões regulares contidas no namespace `System.Text.RegularExpression` e fornece exemplos de uso.</span><span class="sxs-lookup"><span data-stu-id="b7ff5-124">Describes the regular expression classes contained in the `System.Text.RegularExpression` namespace and provides examples of their use.</span></span>  
  
 [<span data-ttu-id="b7ff5-125">Detalhes do comportamento da expressão regular</span><span class="sxs-lookup"><span data-stu-id="b7ff5-125">Details of Regular Expression Behavior</span></span>](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)  
 <span data-ttu-id="b7ff5-126">Oferece informações sobre os recursos e o comportamento das expressões regulares do .NET.</span><span class="sxs-lookup"><span data-stu-id="b7ff5-126">Provides information about the capabilities and behavior of .NET regular expressions.</span></span>  
  
 [<span data-ttu-id="b7ff5-127">Linguagem de expressão regular – referência rápida</span><span class="sxs-lookup"><span data-stu-id="b7ff5-127">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 <span data-ttu-id="b7ff5-128">Oferece informações sobre o conjunto de caracteres, operadores e constructos que você pode usar para definir expressões regulares.</span><span class="sxs-lookup"><span data-stu-id="b7ff5-128">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>
