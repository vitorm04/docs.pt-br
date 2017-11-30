---
title: "Como extrair um protocolo e um número de porta de uma URL"
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
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 10ab05ac8b24c0658be2f27809137c6b0bd4834f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="7b6d7-102">Como extrair um protocolo e um número de porta de uma URL</span><span class="sxs-lookup"><span data-stu-id="7b6d7-102">How to: Extract a Protocol and Port Number from a URL</span></span>
<span data-ttu-id="7b6d7-103">O exemplo a seguir extrai um protocolo e um número da porta de uma URL.</span><span class="sxs-lookup"><span data-stu-id="7b6d7-103">The following example extracts a protocol and port number from a URL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b6d7-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b6d7-104">Example</span></span>  
 <span data-ttu-id="7b6d7-105">O exemplo usa o <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> método para retornar o protocolo seguido por dois-pontos seguido pelo número da porta.</span><span class="sxs-lookup"><span data-stu-id="7b6d7-105">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="7b6d7-106">O padrão de expressão regular `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` pode ser interpretado conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="7b6d7-106">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="7b6d7-107">Padrão</span><span class="sxs-lookup"><span data-stu-id="7b6d7-107">Pattern</span></span>|<span data-ttu-id="7b6d7-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b6d7-108">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="7b6d7-109">Comece a correspondência no início da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7b6d7-109">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="7b6d7-110">Corresponde a um ou mais caracteres de palavra.</span><span class="sxs-lookup"><span data-stu-id="7b6d7-110">Match one or more word characters.</span></span> <span data-ttu-id="7b6d7-111">Este grupo `proto`.</span><span class="sxs-lookup"><span data-stu-id="7b6d7-111">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="7b6d7-112">Fazer a correspondência de um sinal de dois-pontos seguido por duas barras "/".</span><span class="sxs-lookup"><span data-stu-id="7b6d7-112">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="7b6d7-113">Fazer a correspondência de uma ou mais ocorrências (mas o menor número possível) de qualquer caractere que não seja uma barra "/".</span><span class="sxs-lookup"><span data-stu-id="7b6d7-113">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="7b6d7-114">Fazer a correspondência de zero ou uma ocorrência de um sinal de dois-pontos seguido por um ou mais caracteres de dígito.</span><span class="sxs-lookup"><span data-stu-id="7b6d7-114">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="7b6d7-115">Este grupo `port`.</span><span class="sxs-lookup"><span data-stu-id="7b6d7-115">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="7b6d7-116">Fazer a correspondência de uma barra "/".</span><span class="sxs-lookup"><span data-stu-id="7b6d7-116">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="7b6d7-117">O <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> método expande o `${proto}${port}` sequência de substituição, que concatena o valor dos dois grupos nomeados capturados no padrão de expressão regular.</span><span class="sxs-lookup"><span data-stu-id="7b6d7-117">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="7b6d7-118">É uma alternativa conveniente para concatenar explicitamente as cadeias de caracteres recuperadas do objeto de coleção retornado pelo <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="7b6d7-118">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="7b6d7-119">O exemplo usa o <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> método com duas substituições, `${proto}` e `${port}`, para incluir os grupos capturados na cadeia de saída.</span><span class="sxs-lookup"><span data-stu-id="7b6d7-119">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="7b6d7-120">Você pode recuperar os grupos capturados a correspondência de <xref:System.Text.RegularExpressions.GroupCollection> em vez disso, como mostra o seguinte código do objeto.</span><span class="sxs-lookup"><span data-stu-id="7b6d7-120">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7b6d7-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b6d7-121">See Also</span></span>  
 [<span data-ttu-id="7b6d7-122">Expressões regulares do .NET</span><span class="sxs-lookup"><span data-stu-id="7b6d7-122">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
