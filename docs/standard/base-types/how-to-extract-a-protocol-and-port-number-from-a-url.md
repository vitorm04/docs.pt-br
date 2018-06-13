---
title: Como extrair um protocolo e um número de porta de uma URL
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffb31030a2e29458165ae6615a51685ed163fbac
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32768470"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="6a727-102">Como extrair um protocolo e um número de porta de uma URL</span><span class="sxs-lookup"><span data-stu-id="6a727-102">How to: Extract a Protocol and Port Number from a URL</span></span>
<span data-ttu-id="6a727-103">O exemplo a seguir extrai um protocolo e um número da porta de uma URL.</span><span class="sxs-lookup"><span data-stu-id="6a727-103">The following example extracts a protocol and port number from a URL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a727-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6a727-104">Example</span></span>  
 <span data-ttu-id="6a727-105">O exemplo usa o método <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> para retornar o protocolo seguido por dois-pontos e pelo número da porta.</span><span class="sxs-lookup"><span data-stu-id="6a727-105">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="6a727-106">O padrão de expressão regular `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` pode ser interpretado conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="6a727-106">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="6a727-107">Padrão</span><span class="sxs-lookup"><span data-stu-id="6a727-107">Pattern</span></span>|<span data-ttu-id="6a727-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="6a727-108">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="6a727-109">Comece a correspondência no início da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6a727-109">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="6a727-110">Corresponde a um ou mais caracteres de palavra.</span><span class="sxs-lookup"><span data-stu-id="6a727-110">Match one or more word characters.</span></span> <span data-ttu-id="6a727-111">Nomeie esse grupo como `proto`.</span><span class="sxs-lookup"><span data-stu-id="6a727-111">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="6a727-112">Fazer a correspondência de um sinal de dois-pontos seguido por duas barras "/".</span><span class="sxs-lookup"><span data-stu-id="6a727-112">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="6a727-113">Fazer a correspondência de uma ou mais ocorrências (mas o menor número possível) de qualquer caractere que não seja uma barra "/".</span><span class="sxs-lookup"><span data-stu-id="6a727-113">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="6a727-114">Fazer a correspondência de zero ou uma ocorrência de um sinal de dois-pontos seguido por um ou mais caracteres de dígito.</span><span class="sxs-lookup"><span data-stu-id="6a727-114">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="6a727-115">Nomeie esse grupo como `port`.</span><span class="sxs-lookup"><span data-stu-id="6a727-115">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="6a727-116">Fazer a correspondência de uma barra "/".</span><span class="sxs-lookup"><span data-stu-id="6a727-116">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="6a727-117">O método <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> expande a sequência de substituição `${proto}${port}`, que concatena o valor dos dois grupos nomeados capturados no padrão de expressão regular.</span><span class="sxs-lookup"><span data-stu-id="6a727-117">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="6a727-118">Essa é uma alternativa conveniente para concatenar explicitamente as cadeias de caracteres recuperadas do objeto da coleção retornado pela propriedade <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6a727-118">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="6a727-119">O exemplo usa o método <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> com duas substituições, `${proto}` e `${port}`, para incluir os grupos capturados na cadeia de caracteres de saída.</span><span class="sxs-lookup"><span data-stu-id="6a727-119">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="6a727-120">Você pode recuperar os grupos capturados do objeto <xref:System.Text.RegularExpressions.GroupCollection> da correspondência em vez disso, conforme mostra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="6a727-120">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6a727-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a727-121">See Also</span></span>  
 [<span data-ttu-id="6a727-122">Expressões regulares do .NET</span><span class="sxs-lookup"><span data-stu-id="6a727-122">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
