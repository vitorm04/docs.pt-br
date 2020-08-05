---
ms.openlocfilehash: 54ef49755dc0b9d1b821ae7999ab218626d455e1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556314"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="0f62f-101">Instâncias EncoderFallbackBuffer personalizadas não podem retornar recursivamente</span><span class="sxs-lookup"><span data-stu-id="0f62f-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="0f62f-102">As <xref:System.Text.EncoderFallbackBuffer> instâncias personalizadas não podem fazer fallback recursivamente.</span><span class="sxs-lookup"><span data-stu-id="0f62f-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="0f62f-103">A implementação de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> deve resultar em uma sequência de caracteres que é conversível para a codificação de destino.</span><span class="sxs-lookup"><span data-stu-id="0f62f-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="0f62f-104">Caso contrário, ocorrerá uma exceção.</span><span class="sxs-lookup"><span data-stu-id="0f62f-104">Otherwise, an exception occurs.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0f62f-105">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="0f62f-105">Change description</span></span>

<span data-ttu-id="0f62f-106">Durante uma operação de transcodificação de caractere para byte, o tempo de execução detecta sequências UTF-16 mal formadas ou não conversíveis e fornece esses caracteres para o <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="0f62f-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0f62f-107">O `Fallback` método determina quais caracteres devem ser substituídos pelos dados originais não conversíveis e esses caracteres são drenados chamando <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> em um loop.</span><span class="sxs-lookup"><span data-stu-id="0f62f-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="0f62f-108">Em seguida, o tempo de execução tenta transcodificar esses caracteres de substituição para a codificação de destino.</span><span class="sxs-lookup"><span data-stu-id="0f62f-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="0f62f-109">Se essa operação for realizada com sucesso, o tempo de execução continuará transcodificando de onde parou na cadeia de caracteres de entrada original.</span><span class="sxs-lookup"><span data-stu-id="0f62f-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="0f62f-110">Anteriormente, as implementações personalizadas do <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> podem retornar sequências de caracteres que não são conversíveis para a codificação de destino.</span><span class="sxs-lookup"><span data-stu-id="0f62f-110">Previously, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="0f62f-111">Se os caracteres substituídos não puderem ser transcodificados para a codificação de destino, o tempo de execução invocará o <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> método novamente com os caracteres de substituição, esperando que o <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> método retorne uma nova sequência de substituição.</span><span class="sxs-lookup"><span data-stu-id="0f62f-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="0f62f-112">Esse processo continua até que o tempo de execução eventualmente Veja uma substituição bem formada, conversível ou até que uma contagem de recursão máxima seja atingida.</span><span class="sxs-lookup"><span data-stu-id="0f62f-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="0f62f-113">A partir do .NET Core 3,0, implementações personalizadas do <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> devem retornar sequências de caracteres que são conversíveis para a codificação de destino.</span><span class="sxs-lookup"><span data-stu-id="0f62f-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="0f62f-114">Se os caracteres substituídos não puderem ser transcodificados para a codificação de destino, um <xref:System.ArgumentException> será lançado.</span><span class="sxs-lookup"><span data-stu-id="0f62f-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="0f62f-115">O tempo de execução não fará mais chamadas recursivas na <xref:System.Text.EncoderFallbackBuffer> instância.</span><span class="sxs-lookup"><span data-stu-id="0f62f-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="0f62f-116">Esse comportamento se aplica somente quando todas as três condições a seguir são atendidas:</span><span class="sxs-lookup"><span data-stu-id="0f62f-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="0f62f-117">O tempo de execução detecta uma sequência UTF-16 mal formada ou uma sequência UTF-16 que não pode ser convertida para a codificação de destino.</span><span class="sxs-lookup"><span data-stu-id="0f62f-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="0f62f-118">Um personalizado foi <xref:System.Text.EncoderFallback> especificado.</span><span class="sxs-lookup"><span data-stu-id="0f62f-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="0f62f-119">As tentativas personalizadas de <xref:System.Text.EncoderFallback> substituir uma nova sequência UTF-16 mal formada ou não conversível.</span><span class="sxs-lookup"><span data-stu-id="0f62f-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0f62f-120">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="0f62f-120">Version introduced</span></span>

<span data-ttu-id="0f62f-121">3.0</span><span class="sxs-lookup"><span data-stu-id="0f62f-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0f62f-122">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="0f62f-122">Recommended action</span></span>

<span data-ttu-id="0f62f-123">A maioria dos desenvolvedores não precisam realizar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="0f62f-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="0f62f-124">Se um aplicativo usar uma <xref:System.Text.EncoderFallback> classe e personalizada <xref:System.Text.EncoderFallbackBuffer> , verifique se a implementação de <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> popula o buffer de FALLBACK com dados UTF-16 bem formados que são conversíveis diretamente para a codificação de destino quando o <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> método é invocado pela primeira vez pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0f62f-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="0f62f-125">Categoria</span><span class="sxs-lookup"><span data-stu-id="0f62f-125">Category</span></span>

<span data-ttu-id="0f62f-126">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="0f62f-126">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0f62f-127">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0f62f-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
