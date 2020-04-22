---
ms.openlocfilehash: 820825f0545aa78729414c388385b339225b1235
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021590"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="33ce5-101">As instâncias de EncoderFallbackBuffer personalizadas não podem recuar recursivamente</span><span class="sxs-lookup"><span data-stu-id="33ce5-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="33ce5-102">As <xref:System.Text.EncoderFallbackBuffer> instâncias personalizadas não podem recuar recursivamente.</span><span class="sxs-lookup"><span data-stu-id="33ce5-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="33ce5-103">A implementação de deve resultar em uma seqüência de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> caracteres conversível para a codificação de destino.</span><span class="sxs-lookup"><span data-stu-id="33ce5-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="33ce5-104">Caso contrário, ocorre uma exceção.</span><span class="sxs-lookup"><span data-stu-id="33ce5-104">Otherwise, an exception occurs.</span></span>

#### <a name="change-description"></a><span data-ttu-id="33ce5-105">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="33ce5-105">Change description</span></span>

<span data-ttu-id="33ce5-106">Durante uma operação de transcodificação de caracteres para bytes, o tempo de execução detecta <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> seqüências UTF-16 mal formadas ou não conversíveis e fornece esses caracteres para o método.</span><span class="sxs-lookup"><span data-stu-id="33ce5-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="33ce5-107">O `Fallback` método determina quais caracteres devem ser substituídos pelos dados originais <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> não conversíveis, e esses caracteres são drenados por chamada em um loop.</span><span class="sxs-lookup"><span data-stu-id="33ce5-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="33ce5-108">O tempo de execução, então, tenta transcodificar esses caracteres de substituição para a codificação de destino.</span><span class="sxs-lookup"><span data-stu-id="33ce5-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="33ce5-109">Se esta operação for bem sucedida, o tempo de execução continuará a transcodificação de onde parou na seqüência de entrada original.</span><span class="sxs-lookup"><span data-stu-id="33ce5-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="33ce5-110">Em .NET Core Preview 7 e versões anteriores, implementações personalizadas podem retornar seqüências de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> caracteres que não são conversíveis para a codificação de destino.</span><span class="sxs-lookup"><span data-stu-id="33ce5-110">In .NET Core Preview 7 and earlier versions, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="33ce5-111">Se os caracteres substituídos não puderem ser transcodificados para <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> a codificação de destino, <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> o tempo de execução invoca o método mais uma vez com os caracteres de substituição, esperando que o método retorne uma nova seqüência de substituição.</span><span class="sxs-lookup"><span data-stu-id="33ce5-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="33ce5-112">Este processo continua até que o tempo de execução eventualmente veja uma substituição bem formada e conversível, ou até que uma contagem máxima de recursão seja alcançada.</span><span class="sxs-lookup"><span data-stu-id="33ce5-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="33ce5-113">A partir do .NET Core 3.0, implementações personalizadas de sequências de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> caracteres devem retornar conversíveis para a codificação de destino.</span><span class="sxs-lookup"><span data-stu-id="33ce5-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="33ce5-114">Se os caracteres substituídos não puderem ser <xref:System.ArgumentException> transcodificados para a codificação do destino, um será jogado.</span><span class="sxs-lookup"><span data-stu-id="33ce5-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="33ce5-115">O tempo de execução não fará mais <xref:System.Text.EncoderFallbackBuffer> chamadas recursivas para a instância.</span><span class="sxs-lookup"><span data-stu-id="33ce5-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="33ce5-116">Esse comportamento só se aplica quando todas as três condições são atendidas:</span><span class="sxs-lookup"><span data-stu-id="33ce5-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="33ce5-117">O tempo de execução detecta uma seqüência UTF-16 mal formada ou uma seqüência UTF-16 que não pode ser convertida para a codificação de destino.</span><span class="sxs-lookup"><span data-stu-id="33ce5-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="33ce5-118">Um <xref:System.Text.EncoderFallback> costume foi especificado.</span><span class="sxs-lookup"><span data-stu-id="33ce5-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="33ce5-119">O <xref:System.Text.EncoderFallback> costume tenta substituir uma nova seqüência UTF-16 mal formada ou não conversível.</span><span class="sxs-lookup"><span data-stu-id="33ce5-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="33ce5-120">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="33ce5-120">Version introduced</span></span>

<span data-ttu-id="33ce5-121">3.0</span><span class="sxs-lookup"><span data-stu-id="33ce5-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="33ce5-122">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="33ce5-122">Recommended action</span></span>

<span data-ttu-id="33ce5-123">A maioria dos desenvolvedores não precisa tomar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="33ce5-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="33ce5-124">Se um aplicativo <xref:System.Text.EncoderFallback> usar <xref:System.Text.EncoderFallbackBuffer> um personalizado e <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> uma classe, assegure-se de que a implementação preencha o buffer de <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> recuo com dados UTF-16 bem formados que são diretamente conversíveis para a codificação de destino quando o método é invocado pela primeira vez pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="33ce5-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="33ce5-125">Categoria</span><span class="sxs-lookup"><span data-stu-id="33ce5-125">Category</span></span>

<span data-ttu-id="33ce5-126">Bibliotecas Core .NET</span><span class="sxs-lookup"><span data-stu-id="33ce5-126">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="33ce5-127">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="33ce5-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
