---
ms.openlocfilehash: b4b49b55cda26ac9d9760f93e9758aab940ad135
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117257"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="68563-101">Instâncias EncoderFallbackBuffer personalizadas não podem retornar recursivamente</span><span class="sxs-lookup"><span data-stu-id="68563-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="68563-102">As <xref:System.Text.EncoderFallbackBuffer> instâncias personalizadas não podem fazer fallback recursivamente.</span><span class="sxs-lookup"><span data-stu-id="68563-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="68563-103">A implementação de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> deve resultar em uma sequência de caracteres que é conversível para a codificação de destino.</span><span class="sxs-lookup"><span data-stu-id="68563-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="68563-104">Caso contrário, ocorrerá uma exceção.</span><span class="sxs-lookup"><span data-stu-id="68563-104">Otherwise, an exception occurs.</span></span> 

#### <a name="details"></a><span data-ttu-id="68563-105">Detalhes</span><span class="sxs-lookup"><span data-stu-id="68563-105">Details</span></span>

<span data-ttu-id="68563-106">Durante uma operação de transcodificação de caractere para byte, o tempo de execução detecta sequências UTF-16 mal formadas ou não conversíveis e fornece <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> esses caracteres para o método.</span><span class="sxs-lookup"><span data-stu-id="68563-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="68563-107">O `Fallback` método determina quais caracteres devem ser substituídos pelos dados originais não conversíveis e esses caracteres são drenados chamando <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> em um loop.</span><span class="sxs-lookup"><span data-stu-id="68563-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="68563-108">Em seguida, o tempo de execução tenta transcodificar esses caracteres de substituição para a codificação de destino.</span><span class="sxs-lookup"><span data-stu-id="68563-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="68563-109">Se essa operação for realizada com sucesso, o tempo de execução continuará transcodificando de onde parou na cadeia de caracteres de entrada original.</span><span class="sxs-lookup"><span data-stu-id="68563-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span> 

<span data-ttu-id="68563-110">No .NET Core Preview 7 e versões anteriores, implementações personalizadas <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> do podem retornar sequências de caracteres que não são conversíveis para a codificação de destino.</span><span class="sxs-lookup"><span data-stu-id="68563-110">In .NET Core Preview 7 and earlier versions, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="68563-111">Se os caracteres substituídos não puderem ser transcodificados para a codificação de destino, o tempo <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> de execução invocará o método novamente com os caracteres <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> de substituição, esperando que o método retorne uma nova sequência de substituição.</span><span class="sxs-lookup"><span data-stu-id="68563-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="68563-112">Esse processo continua até que o tempo de execução eventualmente Veja uma substituição bem formada, conversível ou até que uma contagem de recursão máxima seja atingida.</span><span class="sxs-lookup"><span data-stu-id="68563-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="68563-113">A partir do .NET Core 3,0, implementações <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> personalizadas do devem retornar sequências de caracteres que são conversíveis para a codificação de destino.</span><span class="sxs-lookup"><span data-stu-id="68563-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="68563-114">Se os caracteres substituídos não puderem ser transcodificados para a codificação de <xref:System.ArgumentException> destino, um será lançado.</span><span class="sxs-lookup"><span data-stu-id="68563-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="68563-115">O tempo de execução não fará mais chamadas recursivas <xref:System.Text.EncoderFallbackBuffer> na instância.</span><span class="sxs-lookup"><span data-stu-id="68563-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span> 

<span data-ttu-id="68563-116">Esse comportamento se aplica somente quando todas as três condições a seguir são atendidas:</span><span class="sxs-lookup"><span data-stu-id="68563-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="68563-117">O tempo de execução detecta uma sequência UTF-16 mal formada ou uma sequência UTF-16 que não pode ser convertida para a codificação de destino.</span><span class="sxs-lookup"><span data-stu-id="68563-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="68563-118">Um personalizado <xref:System.Text.EncoderFallback> foi especificado.</span><span class="sxs-lookup"><span data-stu-id="68563-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="68563-119">As tentativas <xref:System.Text.EncoderFallback> personalizadas de substituir uma nova sequência UTF-16 mal formada ou não conversível.</span><span class="sxs-lookup"><span data-stu-id="68563-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="68563-120">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="68563-120">Version introduced</span></span>

<span data-ttu-id="68563-121">3.0</span><span class="sxs-lookup"><span data-stu-id="68563-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="68563-122">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="68563-122">Recommended action</span></span>

<span data-ttu-id="68563-123">A maioria dos desenvolvedores não precisam realizar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="68563-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="68563-124">Se um aplicativo usar uma classe <xref:System.Text.EncoderFallback> e <xref:System.Text.EncoderFallbackBuffer> personalizada, verifique se a implementação <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> de popula o buffer de fallback com dados UTF-16 bem formados que são conversíveis diretamente para a codificação de <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> destino quando o método é invocado pela primeira vez pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="68563-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="68563-125">Categoria</span><span class="sxs-lookup"><span data-stu-id="68563-125">Category</span></span>

<span data-ttu-id="68563-126">CoreFx</span><span class="sxs-lookup"><span data-stu-id="68563-126">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="68563-127">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="68563-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->