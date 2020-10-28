---
title: Como verificar se cadeias de caracteres estão em um formato de email válido
description: Leia um exemplo de como uma expressão regular verifica se as cadeias de caracteres estão em um formato de email válido no .NET.
ms.date: 06/30/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- user input, examples
- Regex.IsMatch method
- regular expressions [.NET], examples
- examples [Visual Basic], strings
- IsValidEmail
- validation, email strings
- input, checking
- strings [.NET], examples [Visual Basic]
- email [.NET], validating
- IsMatch method
ms.assetid: 7536af08-4e86-4953-98a1-a8298623df92
ms.openlocfilehash: 07b8e31e4a0203b87492eb01ab686a1c56f5565d
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889069"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a><span data-ttu-id="c7086-103">Como verificar se cadeias de caracteres estão em um formato de email válido</span><span class="sxs-lookup"><span data-stu-id="c7086-103">How to verify that strings are in valid email format</span></span>

<span data-ttu-id="c7086-104">O exemplo a seguir usa uma expressão regular para verificar se uma cadeia de caracteres está no formato de email válido.</span><span class="sxs-lookup"><span data-stu-id="c7086-104">The following example uses a regular expression to verify that a string is in valid email format.</span></span>

<span data-ttu-id="c7086-105">Essa expressão regular é comparativamente simples para o que realmente pode ser usado como um email.</span><span class="sxs-lookup"><span data-stu-id="c7086-105">This regular expression is comparatively simple to what can actually be used as an email.</span></span> <span data-ttu-id="c7086-106">Usar uma expressão regular para validar um email é útil para verificar se a estrutura de um email está correta, mas não é uma substituição para verificar se o email realmente existe.</span><span class="sxs-lookup"><span data-stu-id="c7086-106">Using a regular expression to validate an email is useful to make sure the structure of an email is correct, but it isn't a substitution for verifying the email actually exists.</span></span>

<span data-ttu-id="c7086-107">✔️ usar uma pequena expressão regular para verificar a estrutura válida de um email.</span><span class="sxs-lookup"><span data-stu-id="c7086-107">✔️ DO use a small regular expression to check for the valid structure of an email.</span></span>

<span data-ttu-id="c7086-108">✔️ enviar um email de teste para o endereço fornecido por um usuário do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c7086-108">✔️ DO send a test email to the address provided by a user of your app.</span></span>

<span data-ttu-id="c7086-109">❌ Não use uma expressão regular como a única maneira de validar um email.</span><span class="sxs-lookup"><span data-stu-id="c7086-109">❌ DON'T use a regular expression as the only way you validate an email.</span></span>

<span data-ttu-id="c7086-110">Se você tentar criar a expressão regular _perfeita_ para validar que a estrutura de um email está correta, a expressão se torna tão complexa que é incrivelmente difícil de Depurar ou melhorar.</span><span class="sxs-lookup"><span data-stu-id="c7086-110">If you try to create the _perfect_ regular expression to validate that the structure of an email is correct, the expression becomes so complex that it's incredibly difficult to debug or improve.</span></span> <span data-ttu-id="c7086-111">As expressões regulares não podem validar um email existente, mesmo se ele estiver estruturado corretamente.</span><span class="sxs-lookup"><span data-stu-id="c7086-111">Regular expressions can't validate an email exists, even if it's structured correctly.</span></span> <span data-ttu-id="c7086-112">A melhor maneira de validar um email é enviar um email de teste para o endereço.</span><span class="sxs-lookup"><span data-stu-id="c7086-112">The best way to validate an email is to send a test email to the address.</span></span>

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a><span data-ttu-id="c7086-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c7086-113">Example</span></span>

<span data-ttu-id="c7086-114">O exemplo define um `IsValidEmail` método, que retorna `true` se a cadeia de caracteres contém um endereço de email válido e `false` , se não for, mas não executará nenhuma outra ação.</span><span class="sxs-lookup"><span data-stu-id="c7086-114">The example defines an `IsValidEmail` method, which returns `true` if the string contains a valid email address and `false` if it doesn't, but takes no other action.</span></span>

<span data-ttu-id="c7086-115">Para verificar se o endereço de email é válido, o método `IsValidEmail` chama o método <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> com o padrão da expressão regular `(@)(.+)$` para separar o nome de domínio do endereço de email.</span><span class="sxs-lookup"><span data-stu-id="c7086-115">To verify that the email address is valid, the `IsValidEmail` method calls the <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> method with the `(@)(.+)$` regular expression pattern to separate the domain name from the email address.</span></span> <span data-ttu-id="c7086-116">O terceiro parâmetro é um representante <xref:System.Text.RegularExpressions.MatchEvaluator>, que representa o método que processa e substitui o texto correspondente.</span><span class="sxs-lookup"><span data-stu-id="c7086-116">The third parameter is a <xref:System.Text.RegularExpressions.MatchEvaluator> delegate that represents the method that processes and replaces the matched text.</span></span> <span data-ttu-id="c7086-117">O padrão da expressão regular é interpretado da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="c7086-117">The regular expression pattern is interpreted as follows.</span></span>

| <span data-ttu-id="c7086-118">Padrão</span><span class="sxs-lookup"><span data-stu-id="c7086-118">Pattern</span></span> | <span data-ttu-id="c7086-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7086-119">Description</span></span>                                                                         |
|---------|-------------------------------------------------------------------------------------|
| `(@)`   | <span data-ttu-id="c7086-120">Coincida o caractere @.</span><span class="sxs-lookup"><span data-stu-id="c7086-120">Match the @ character.</span></span> <span data-ttu-id="c7086-121">Essa parte é o primeiro grupo de captura.</span><span class="sxs-lookup"><span data-stu-id="c7086-121">This part is the first capturing group.</span></span>                           |
| `(.+)`  | <span data-ttu-id="c7086-122">Coincida uma ou mais ocorrências de qualquer caractere.</span><span class="sxs-lookup"><span data-stu-id="c7086-122">Match one or more occurrences of any character.</span></span> <span data-ttu-id="c7086-123">Essa parte é o segundo grupo de captura.</span><span class="sxs-lookup"><span data-stu-id="c7086-123">This part is the second capturing group.</span></span> |
| `$`     | <span data-ttu-id="c7086-124">Encerrar a correspondência ao final da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c7086-124">End the match at the end of the string.</span></span>                                             |

<span data-ttu-id="c7086-125">O nome de domínio com o caractere @ é passado para o método `DomainMapper`, que usa a classe <xref:System.Globalization.IdnMapping> para converter caracteres Unicode fora do intervalo de caracteres US-ASCII em Punycode.</span><span class="sxs-lookup"><span data-stu-id="c7086-125">The domain name along with the @ character is passed to the `DomainMapper` method, which uses the <xref:System.Globalization.IdnMapping> class to translate Unicode characters that are outside the US-ASCII character range to Punycode.</span></span> <span data-ttu-id="c7086-126">O método também define o sinalizador `invalid` como `True`, caso o método <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> detecte algum caractere inválido no nome do domínio.</span><span class="sxs-lookup"><span data-stu-id="c7086-126">The method also sets the `invalid` flag to `True` if the <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> method detects any invalid characters in the domain name.</span></span> <span data-ttu-id="c7086-127">O método retorna o nome de domínio Punycode precedido pelo símbolo @ para o método `IsValidEmail`.</span><span class="sxs-lookup"><span data-stu-id="c7086-127">The method returns the Punycode domain name preceded by the @ symbol to the `IsValidEmail` method.</span></span>

> [!TIP]
> <span data-ttu-id="c7086-128">É recomendável que você use o padrão de `(@)(.+)$` expressão regular simples para normalizar o domínio e, em seguida, retornar um valor indicando que ele passou ou falhou.</span><span class="sxs-lookup"><span data-stu-id="c7086-128">It's recommended that you use use the simple `(@)(.+)$` regular expression pattern to normalize the domain and then return a value indicating that it passed or failed.</span></span> <span data-ttu-id="c7086-129">No entanto, o exemplo neste artigo descreve como usar uma expressão regular para validar o email.</span><span class="sxs-lookup"><span data-stu-id="c7086-129">However, the example in this article describes how to further use a regular expression to validate the email.</span></span> <span data-ttu-id="c7086-130">Independentemente de como você valida um email, você deve sempre enviar um email de teste para o endereço para verificar se ele existe.</span><span class="sxs-lookup"><span data-stu-id="c7086-130">Regardless of how you validate an email, you should always send a test email to the address to make sure it exists.</span></span>

<span data-ttu-id="c7086-131">Em seguida, o método `IsValidEmail` chama o método <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> para verificar se o endereço está adequado para um padrão de expressão regular.</span><span class="sxs-lookup"><span data-stu-id="c7086-131">The `IsValidEmail` method then calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> method to verify that the address conforms to a regular expression pattern.</span></span>

<span data-ttu-id="c7086-132">O `IsValidEmail` método simplesmente determina se o formato de email é válido para um endereço de email, ele não valida se o email existe.</span><span class="sxs-lookup"><span data-stu-id="c7086-132">The `IsValidEmail` method merely determines whether the email format is valid for an email address, it doesn't validate that the email exists.</span></span> <span data-ttu-id="c7086-133">Além disso, o `IsValidEmail` método não verifica se o nome de domínio de nível superior é um nome de domínio válido listado no [banco de dados da zona raiz IANA](https://www.iana.org/domains/root/db), o que exigiria uma operação de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c7086-133">Also, the `IsValidEmail` method doesn't verify that the top-level domain name is a valid domain name listed at the [IANA Root Zone Database](https://www.iana.org/domains/root/db), which would require a look-up operation.</span></span>

:::code language="csharp" source="snippets/how-to-verify-that-strings-are-in-valid-email-format/csharp/RegexUtilities.cs":::

:::code language="vb" source="snippets/how-to-verify-that-strings-are-in-valid-email-format/vb/RegexUtilities.vb":::

<span data-ttu-id="c7086-134">Neste exemplo, o padrão de expressão regular `^[^@\s]+@[^@\s]+\.[^@\s]+$` é interpretado conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="c7086-134">In this example, the regular expression pattern `^[^@\s]+@[^@\s]+\.[^@\s]+$` is interpreted as shown in the following table.</span></span> <span data-ttu-id="c7086-135">A expressão regular é compilada usando o <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> sinalizador.</span><span class="sxs-lookup"><span data-stu-id="c7086-135">The regular expression is compiled using the <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> flag.</span></span>

| <span data-ttu-id="c7086-136">Padrão</span><span class="sxs-lookup"><span data-stu-id="c7086-136">Pattern</span></span>   | <span data-ttu-id="c7086-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7086-137">Description</span></span>                                                                              |
|-----------|------------------------------------------------------------------------------------------|
| `^`       | <span data-ttu-id="c7086-138">Comece a correspondência no início da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c7086-138">Begin the match at the start of the string.</span></span>                                              |
| `[^@\s]+` | <span data-ttu-id="c7086-139">Corresponder uma ou mais ocorrências de qualquer caractere além do caractere @ ou espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="c7086-139">Match one or more occurrences of any character other than the @ character or whitespace.</span></span> |
| `@`       | <span data-ttu-id="c7086-140">Coincida o caractere @.</span><span class="sxs-lookup"><span data-stu-id="c7086-140">Match the @ character.</span></span>                                                                   |
| `[^@\s]+` | <span data-ttu-id="c7086-141">Corresponder uma ou mais ocorrências de qualquer caractere além do caractere @ ou espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="c7086-141">Match one or more occurrences of any character other than the @ character or whitespace.</span></span> |
| `\.`      | <span data-ttu-id="c7086-142">Corresponder a um único caractere de ponto.</span><span class="sxs-lookup"><span data-stu-id="c7086-142">Match a single period character.</span></span>                                                         |
| `[^@\s]+` | <span data-ttu-id="c7086-143">Corresponder uma ou mais ocorrências de qualquer caractere além do caractere @ ou espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="c7086-143">Match one or more occurrences of any character other than the @ character or whitespace.</span></span> |
| `$`       | <span data-ttu-id="c7086-144">Encerrar a correspondência ao final da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c7086-144">End the match at the end of the string.</span></span>                                                  |

> [!IMPORTANT]
> <span data-ttu-id="c7086-145">Esta expressão regular não se destina a abranger todos os aspectos de um endereço de email válido.</span><span class="sxs-lookup"><span data-stu-id="c7086-145">This regular expression is not intended to cover every aspect of a valid email address.</span></span> <span data-ttu-id="c7086-146">Ele é fornecido como um exemplo para você estender conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="c7086-146">It's provided as an example for you to extend as needed.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7086-147">Veja também</span><span class="sxs-lookup"><span data-stu-id="c7086-147">See also</span></span>

- [<span data-ttu-id="c7086-148">Expressões regulares do .NET</span><span class="sxs-lookup"><span data-stu-id="c7086-148">.NET Regular Expressions</span></span>](regular-expressions.md)
- [<span data-ttu-id="c7086-149">Com que distância uma validação de endereço de email deve ser tomada?</span><span class="sxs-lookup"><span data-stu-id="c7086-149">How far should one take e-mail address validation?</span></span>](https://softwareengineering.stackexchange.com/questions/78353/how-far-should-one-take-e-mail-address-validation#78363)
