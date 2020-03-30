---
title: Práticas recomendadas de interoperabilidade nativa - .NET
description: Saiba mais sobre as práticas recomendadas para fazer interface com componentes nativos no .NET.
ms.date: 01/18/2019
ms.openlocfilehash: e5d96471e796dca712d25d2d9e2609508180d83f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391215"
---
# <a name="native-interoperability-best-practices"></a><span data-ttu-id="d7811-103">Práticas recomendadas de interoperabilidade nativa</span><span class="sxs-lookup"><span data-stu-id="d7811-103">Native interoperability best practices</span></span>

<span data-ttu-id="d7811-104">.NET oferece uma variedade maneiras de personalizar seu código de interoperabilidade nativa.</span><span class="sxs-lookup"><span data-stu-id="d7811-104">.NET gives you a variety of ways to customize your native interoperability code.</span></span> <span data-ttu-id="d7811-105">Este artigo inclui as diretrizes que as equipes .NET da Microsoft seguem para a interoperabilidade nativa.</span><span class="sxs-lookup"><span data-stu-id="d7811-105">This article includes the guidance that Microsoft's .NET teams follow for native interoperability.</span></span>

## <a name="general-guidance"></a><span data-ttu-id="d7811-106">Diretrizes gerais</span><span class="sxs-lookup"><span data-stu-id="d7811-106">General guidance</span></span>

<span data-ttu-id="d7811-107">As diretrizes nesta seção se aplicam a todos os cenários de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="d7811-107">The guidance in this section applies to all interop scenarios.</span></span>

- <span data-ttu-id="d7811-108">✔️ USE a mesma nomenclatura e uso de maiúsculas para seus métodos e parâmetros como o método nativo que você deseja chamar.</span><span class="sxs-lookup"><span data-stu-id="d7811-108">✔️ DO use the same naming and capitalization for your methods and parameters as the native method you want to call.</span></span>
- <span data-ttu-id="d7811-109">✔️ CONSIDERE usar a mesma nomenclatura e uso de maiúsculas para valores constantes.</span><span class="sxs-lookup"><span data-stu-id="d7811-109">✔️ CONSIDER using the same naming and capitalization for constant values.</span></span>
- <span data-ttu-id="d7811-110">✔️ USE tipos .NET com mapeamento mais próximo do tipo nativo.</span><span class="sxs-lookup"><span data-stu-id="d7811-110">✔️ DO use .NET types that map closest to the native type.</span></span> <span data-ttu-id="d7811-111">Por exemplo, no caso de C#, use `uint` quando o tipo nativo for `unsigned int`.</span><span class="sxs-lookup"><span data-stu-id="d7811-111">For example, in C#, use `uint` when the native type is `unsigned int`.</span></span>
- <span data-ttu-id="d7811-112">✔️ USE os atributos `[In]` e `[Out]` somente quando o comportamento desejado for diferente do comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="d7811-112">✔️ DO only use `[In]` and `[Out]` attributes when the behavior you want differs from the default behavior.</span></span>
- <span data-ttu-id="d7811-113">✔️ CONSIDERE usar <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> para agrupar seus buffers de matriz nativos.</span><span class="sxs-lookup"><span data-stu-id="d7811-113">✔️ CONSIDER using <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> to pool your native array buffers.</span></span>
- <span data-ttu-id="d7811-114">✔️ CONSIDERE encapsular suas declarações P/Invoke em uma classe com o mesmo nome e letras maiúsculas como sua biblioteca nativa.</span><span class="sxs-lookup"><span data-stu-id="d7811-114">✔️ CONSIDER wrapping your P/Invoke declarations in a class with the same name and capitalization as your native library.</span></span>
  - <span data-ttu-id="d7811-115">Isso permite que seus atributos `[DllImport]` usem o recurso de linguagem C# `nameof` para passar o nome da biblioteca nativa e garantir que você não tenha digitado errado o nome da biblioteca nativa.</span><span class="sxs-lookup"><span data-stu-id="d7811-115">This allows your `[DllImport]` attributes to use the C# `nameof` language feature to pass in the name of the native library and ensure that you didn't misspell the name of the native library.</span></span>

## <a name="dllimport-attribute-settings"></a><span data-ttu-id="d7811-116">Configurações de atributo DllImport</span><span class="sxs-lookup"><span data-stu-id="d7811-116">DllImport attribute settings</span></span>

| <span data-ttu-id="d7811-117">Configuração</span><span class="sxs-lookup"><span data-stu-id="d7811-117">Setting</span></span> | <span data-ttu-id="d7811-118">Padrão</span><span class="sxs-lookup"><span data-stu-id="d7811-118">Default</span></span> | <span data-ttu-id="d7811-119">Recomendação</span><span class="sxs-lookup"><span data-stu-id="d7811-119">Recommendation</span></span> | <span data-ttu-id="d7811-120">Detalhes</span><span class="sxs-lookup"><span data-stu-id="d7811-120">Details</span></span> |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  <span data-ttu-id="d7811-121">manter padrão</span><span class="sxs-lookup"><span data-stu-id="d7811-121">keep default</span></span>  | <span data-ttu-id="d7811-122">Quando esta configuração é definida como false, valores de retorno HRESULT com falha serão considerados exceções (e o valor de retorno na definição torna-se nulo).</span><span class="sxs-lookup"><span data-stu-id="d7811-122">When this is explicitly set to false, failed HRESULT return values will be turned into exceptions (and the return value in the definition becomes null as a result).</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | <span data-ttu-id="d7811-123">depende da API</span><span class="sxs-lookup"><span data-stu-id="d7811-123">depends on the API</span></span>  | <span data-ttu-id="d7811-124">Defina esta configuração como true se a API usa GetLastError e usa Marshal.GetLastWin32Error para obter o valor.</span><span class="sxs-lookup"><span data-stu-id="d7811-124">Set this to true if the API uses GetLastError and use Marshal.GetLastWin32Error to get the value.</span></span> <span data-ttu-id="d7811-125">Se a API definir uma condição que informa um erro, obtenha o erro antes de fazer outras chamadas para evitar que ele seja sobrescrito inadvertidamente.</span><span class="sxs-lookup"><span data-stu-id="d7811-125">If the API sets a condition that says it has an error, get the error before making other calls to avoid inadvertently having it overwritten.</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | <span data-ttu-id="d7811-126">`CharSet.None`, que reverte para o comportamento `CharSet.Ansi`</span><span class="sxs-lookup"><span data-stu-id="d7811-126">`CharSet.None`, which falls back to `CharSet.Ansi` behavior</span></span>  | <span data-ttu-id="d7811-127">Use explicitamente `CharSet.Unicode` ou `CharSet.Ansi` quando os caracteres ou cadeias de caracteres estiverem presentes na definição</span><span class="sxs-lookup"><span data-stu-id="d7811-127">Explicitly  use `CharSet.Unicode` or `CharSet.Ansi` when strings or characters are present in the definition</span></span> | <span data-ttu-id="d7811-128">Isso especifica o comportamento de marshaling de cadeias de caracteres e o que `ExactSpelling` faz quando `false`.</span><span class="sxs-lookup"><span data-stu-id="d7811-128">This specifies marshaling behavior of strings and what `ExactSpelling` does when `false`.</span></span> <span data-ttu-id="d7811-129">Note que `CharSet.Ansi` é na verdade UTF8 no Unix.</span><span class="sxs-lookup"><span data-stu-id="d7811-129">Note that `CharSet.Ansi` is actually UTF8 on Unix.</span></span> <span data-ttu-id="d7811-130">O Windows usa Unicode a _maior parte_ do tempo, enquanto o Unix usa UTF8.</span><span class="sxs-lookup"><span data-stu-id="d7811-130">_Most_ of the time Windows uses Unicode while Unix uses UTF8.</span></span> <span data-ttu-id="d7811-131">Veja mais informações na [documentação sobre conjuntos de caracteres](./charset.md).</span><span class="sxs-lookup"><span data-stu-id="d7811-131">See more information on the [documentation on charsets](./charset.md).</span></span> |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | <span data-ttu-id="d7811-132">Defina como true e obtenha um pequeno benefício de desempenho: o runtime não irá buscar por nomes de função alternativos com o sufixo "A" ou "W" dependendo do valor da configuração `CharSet` ("A" para `CharSet.Ansi` e "W" para `CharSet.Unicode`).</span><span class="sxs-lookup"><span data-stu-id="d7811-132">Set this to true and gain a slight perf benefit as the runtime will not look for alternate function names with either an "A" or "W" suffix depending on the value of the `CharSet` setting ("A" for `CharSet.Ansi` and "W" for `CharSet.Unicode`).</span></span> |

## <a name="string-parameters"></a><span data-ttu-id="d7811-133">Parâmetros de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="d7811-133">String parameters</span></span>

<span data-ttu-id="d7811-134">Quando o CharSet é Unicode ou o argumento é explicitamente marcado como `[MarshalAs(UnmanagedType.LPWSTR)]` _e_ a cadeia de caracteres é passada por valor (não `ref` ou `out`), a cadeia de caracteres será fixada e usada diretamente pelo código nativo (em vez de copiado).</span><span class="sxs-lookup"><span data-stu-id="d7811-134">When the CharSet is Unicode or the argument is explicitly marked as `[MarshalAs(UnmanagedType.LPWSTR)]` _and_ the string is passed by value (not `ref` or `out`), the string will be pinned and used directly by native code (rather than copied).</span></span>

<span data-ttu-id="d7811-135">Lembre-se de marcar `[DllImport]` como `Charset.Unicode`, a menos que você queira explicitamente o tratamento ANSI de suas cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d7811-135">Remember to mark the `[DllImport]` as `Charset.Unicode` unless you explicitly want ANSI treatment of your strings.</span></span>

<span data-ttu-id="d7811-136">❌NÃO use `[Out] string` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d7811-136">❌ DO NOT use `[Out] string` parameters.</span></span> <span data-ttu-id="d7811-137">Os parâmetros de cadeia de caracteres passados por valor com o atributo `[Out]` podem desestabilizar o runtime se a cadeia de caracteres for uma cadeia de caracteres internada.</span><span class="sxs-lookup"><span data-stu-id="d7811-137">String parameters passed by value with the `[Out]` attribute can destabilize the runtime if the string is an interned string.</span></span> <span data-ttu-id="d7811-138">Veja mais informações sobre a centralização da cadeia de caracteres na documentação do <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d7811-138">See more information about string interning in the documentation for <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d7811-139">❌EVITE `StringBuilder` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d7811-139">❌ AVOID `StringBuilder` parameters.</span></span> <span data-ttu-id="d7811-140">Marshaling de `StringBuilder`*sempre* cria uma cópia do buffer nativo.</span><span class="sxs-lookup"><span data-stu-id="d7811-140">`StringBuilder` marshaling *always* creates a native buffer copy.</span></span> <span data-ttu-id="d7811-141">Dessa forma, ele pode ser extremamente ineficiente.</span><span class="sxs-lookup"><span data-stu-id="d7811-141">As such, it can be extremely inefficient.</span></span> <span data-ttu-id="d7811-142">Veja o cenário típico da chamada de uma API do Windows que usa uma cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="d7811-142">Take the typical scenario of calling a Windows API that takes a string:</span></span>

1. <span data-ttu-id="d7811-143">Criar um SB da capacidade desejada (aloca capacidade gerenciada)**{1}**</span><span class="sxs-lookup"><span data-stu-id="d7811-143">Create a SB of the desired capacity (allocates managed capacity) **{1}**</span></span>
2. <span data-ttu-id="d7811-144">Invoke</span><span class="sxs-lookup"><span data-stu-id="d7811-144">Invoke</span></span>
   1. <span data-ttu-id="d7811-145">Aloca um buffer nativo**{2}**</span><span class="sxs-lookup"><span data-stu-id="d7811-145">Allocates a native buffer **{2}**</span></span>
   2. <span data-ttu-id="d7811-146">Copia o conteúdo se `[In]` _(o padrão para um parâmetro `StringBuilder`)_</span><span class="sxs-lookup"><span data-stu-id="d7811-146">Copies the contents if `[In]` _(the default for a `StringBuilder` parameter)_</span></span>
   3. <span data-ttu-id="d7811-147">Copia o buffer nativo em uma matriz gerenciada recém-alocada se `[Out]` **{3}** _(também é o padrão para `StringBuilder`)_</span><span class="sxs-lookup"><span data-stu-id="d7811-147">Copies the native buffer into a newly allocated managed array if `[Out]` **{3}** _(also the default for `StringBuilder`)_</span></span>
3. <span data-ttu-id="d7811-148">`ToString()`aloca ainda outra matriz gerenciada**{4}**</span><span class="sxs-lookup"><span data-stu-id="d7811-148">`ToString()` allocates yet another managed array **{4}**</span></span>

<span data-ttu-id="d7811-149">Isso *{4}* são alocações para obter uma seqüência fora do código nativo.</span><span class="sxs-lookup"><span data-stu-id="d7811-149">That is *{4}* allocations to get a string out of native code.</span></span> <span data-ttu-id="d7811-150">O melhor que você pode fazer para limitar isso é reutilizar o `StringBuilder` em outra chamada, mas isso economiza apenas *1* alocação.</span><span class="sxs-lookup"><span data-stu-id="d7811-150">The best you can do to limit this is to reuse the `StringBuilder` in another call but this still only saves *1* allocation.</span></span> <span data-ttu-id="d7811-151">É muito melhor usar e armazenar em cache um buffer de caractere de `ArrayPool` - você pode então reduzir para apenas a alocação para `ToString()` nas chamadas subsequentes.</span><span class="sxs-lookup"><span data-stu-id="d7811-151">It's much better to use and cache a character buffer from `ArrayPool`- you can then get down to just the allocation for the `ToString()` on subsequent calls.</span></span>

<span data-ttu-id="d7811-152">O outro problema com `StringBuilder` é que esta configuração sempre copia o buffer de retorno de volta para o primeiro nulo.</span><span class="sxs-lookup"><span data-stu-id="d7811-152">The other issue with `StringBuilder` is that it always copies the return buffer back up to the first null.</span></span> <span data-ttu-id="d7811-153">Se a cadeia de caracteres transmitida não estiver terminada, ou terminar por dois caracteres nulos, na melhor das hipóteses, o recurso P/Invoke estará incorreto.</span><span class="sxs-lookup"><span data-stu-id="d7811-153">If the passed back string isn't terminated or is a double-null-terminated string, your P/Invoke is incorrect at best.</span></span>

<span data-ttu-id="d7811-154">Se você *usar* o `StringBuilder`, uma última pegadinha é que a capacidade **não** inclui um nulo oculto, que é sempre contabilizado na interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="d7811-154">If you *do* use `StringBuilder`, one last gotcha is that the capacity does **not** include a hidden null, which is always accounted for in interop.</span></span> <span data-ttu-id="d7811-155">É comum as pessoas entenderem errado, já que a maioria das APIs deseja o tamanho do buffer, *incluindo* o valor nulo.</span><span class="sxs-lookup"><span data-stu-id="d7811-155">It's common for people to get this wrong as most APIs want the size of the buffer *including* the null.</span></span> <span data-ttu-id="d7811-156">Isso pode resultar em alocações desnecessárias/desperdiçadas.</span><span class="sxs-lookup"><span data-stu-id="d7811-156">This can result in wasted/unnecessary allocations.</span></span> <span data-ttu-id="d7811-157">Além disso, esse problema impede que o runtime otimize o marshaling de `StringBuilder` para minimizar as cópias.</span><span class="sxs-lookup"><span data-stu-id="d7811-157">Additionally, this gotcha prevents the runtime from optimizing `StringBuilder` marshaling to minimize copies.</span></span>

<span data-ttu-id="d7811-158">✔️ CONSIDERE usar `char[]`s de um `ArrayPool`.</span><span class="sxs-lookup"><span data-stu-id="d7811-158">✔️ CONSIDER using `char[]`s from an `ArrayPool`.</span></span>

<span data-ttu-id="d7811-159">Para obter mais informações sobre o marshaling de cadeia de caracteres, veja [Marshaling padrão para cadeias de caracteres](../../framework/interop/default-marshaling-for-strings.md) e [Personalizando marshaling de cadeia de caracteres](customize-parameter-marshaling.md#customizing-string-parameters).</span><span class="sxs-lookup"><span data-stu-id="d7811-159">For more information on string marshaling, see [Default Marshaling for Strings](../../framework/interop/default-marshaling-for-strings.md) and [Customizing string marshaling](customize-parameter-marshaling.md#customizing-string-parameters).</span></span>

> <span data-ttu-id="d7811-160">__Específico do Windows__ Para `[Out]` strings, a `CoTaskMemFree` CLR usará por `SysStringFree` padrão para liberar strings ou para strings marcadas como `UnmanagedType.BSTR`.</span><span class="sxs-lookup"><span data-stu-id="d7811-160">__Windows Specific__ For `[Out]` strings the CLR will use `CoTaskMemFree` by default to free strings or `SysStringFree` for strings that are marked as `UnmanagedType.BSTR`.</span></span>
> <span data-ttu-id="d7811-161">**Para a maioria das APIs com um buffer de seqüência de saída:** A contagem de caracteres aprovada deve incluir o nulo.</span><span class="sxs-lookup"><span data-stu-id="d7811-161">**For most APIs with an output string buffer:** The passed in character count must include the null.</span></span> <span data-ttu-id="d7811-162">Se o valor retornado for menor que a contagem de caracteres transmitidos, a chamada foi bem-sucedida e o valor consiste no número de caracteres *sem* o nulo à direita.</span><span class="sxs-lookup"><span data-stu-id="d7811-162">If the returned value is less than the passed in character count the call has succeeded and the value is the number of characters *without* the trailing null.</span></span> <span data-ttu-id="d7811-163">Caso contrário, a contagem consiste no tamanho necessário do buffer *incluindo* o caractere nulo.</span><span class="sxs-lookup"><span data-stu-id="d7811-163">Otherwise the count is the required size of the buffer *including* the null character.</span></span>
>
> - <span data-ttu-id="d7811-164">Passe em 5, pegue 4: A seqüência tem 4 caracteres longos com um nulo.</span><span class="sxs-lookup"><span data-stu-id="d7811-164">Pass in 5, get 4: The string is 4 characters long with a trailing null.</span></span>
> - <span data-ttu-id="d7811-165">Passe em 5, obtenha 6: A seqüência tem 5 caracteres de comprimento, precisa de um buffer de 6 caracteres para segurar o nulo.</span><span class="sxs-lookup"><span data-stu-id="d7811-165">Pass in 5, get 6: The string is 5 characters long, need a 6 character buffer to hold the null.</span></span>
> [<span data-ttu-id="d7811-166">Tipos de dados do Windows para cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="d7811-166">Windows Data Types for Strings</span></span>](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a><span data-ttu-id="d7811-167">Parâmetros e campos boolianos</span><span class="sxs-lookup"><span data-stu-id="d7811-167">Boolean parameters and fields</span></span>

<span data-ttu-id="d7811-168">É fácil cometer erros com boolianos.</span><span class="sxs-lookup"><span data-stu-id="d7811-168">Booleans are easy to mess up.</span></span> <span data-ttu-id="d7811-169">Por padrão, o marshaling de um `bool` .NET é realizado para um Windows `BOOL`, em que é um valor de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="d7811-169">By default, a .NET `bool` is marshaled to a Windows `BOOL`, where it's a 4-byte value.</span></span> <span data-ttu-id="d7811-170">No entanto, os tipos `_Bool` e `bool` em C e C++ são um byte *único*.</span><span class="sxs-lookup"><span data-stu-id="d7811-170">However, the `_Bool`, and `bool` types in C and C++ are a *single* byte.</span></span> <span data-ttu-id="d7811-171">Isso pode dificultar o rastreamento de bugs, já que metade do valor de retorno será descartado, o que só *potencialmente* alterará o resultado.</span><span class="sxs-lookup"><span data-stu-id="d7811-171">This can lead to hard to track down bugs as half the return value will be discarded, which will only *potentially* change the result.</span></span> <span data-ttu-id="d7811-172">Para obter mais informações sobre o marshaling de valores do `bool` .NET para tipos `bool` C ou C++, veja a documentação sobre como [personalizar marshaling de campo booliano](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span><span class="sxs-lookup"><span data-stu-id="d7811-172">For more for information on marshaling .NET `bool` values to C or C++ `bool` types, see the documentation on [customizing boolean field marshaling](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span></span>

## <a name="guids"></a><span data-ttu-id="d7811-173">GUIDs</span><span class="sxs-lookup"><span data-stu-id="d7811-173">GUIDs</span></span>

<span data-ttu-id="d7811-174">Os GUIDs podem ser usados diretamente em assinaturas.</span><span class="sxs-lookup"><span data-stu-id="d7811-174">GUIDs are usable directly in signatures.</span></span> <span data-ttu-id="d7811-175">Muitas APIs do Windows usam aliases do tipo `GUID&` como `REFIID`.</span><span class="sxs-lookup"><span data-stu-id="d7811-175">Many Windows APIs take `GUID&` type aliases like `REFIID`.</span></span> <span data-ttu-id="d7811-176">Quando passadas por ref, elas podem ser passadas por `ref` ou pelo atributo `[MarshalAs(UnmanagedType.LPStruct)]`.</span><span class="sxs-lookup"><span data-stu-id="d7811-176">When passed by ref, they can either be passed by `ref` or with the `[MarshalAs(UnmanagedType.LPStruct)]` attribute.</span></span>

| <span data-ttu-id="d7811-177">GUID</span><span class="sxs-lookup"><span data-stu-id="d7811-177">GUID</span></span> | <span data-ttu-id="d7811-178">GUID by-ref</span><span class="sxs-lookup"><span data-stu-id="d7811-178">By-ref GUID</span></span> |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

<span data-ttu-id="d7811-179">❌NÃO Use `[MarshalAs(UnmanagedType.LPStruct)]` para nada `ref` além de parâmetros GUID.</span><span class="sxs-lookup"><span data-stu-id="d7811-179">❌ DO NOT Use `[MarshalAs(UnmanagedType.LPStruct)]` for anything other than `ref` GUID parameters.</span></span>

## <a name="blittable-types"></a><span data-ttu-id="d7811-180">Tipos blittable</span><span class="sxs-lookup"><span data-stu-id="d7811-180">Blittable types</span></span>

<span data-ttu-id="d7811-181">Os tipos blittable são tipos que têm a mesma representação em nível de bits no código gerenciado e nativo.</span><span class="sxs-lookup"><span data-stu-id="d7811-181">Blittable types are types that have the same bit-level representation in managed and native code.</span></span> <span data-ttu-id="d7811-182">Como tal, eles não precisam ser convertidos em outro formato para serem empacotados para e do código nativo e, uma vez que isso melhora o desempenho, eles devem ter preferência.</span><span class="sxs-lookup"><span data-stu-id="d7811-182">As such they do not need to be converted to another format to be marshaled to and from native code, and as this improves performance they should be preferred.</span></span>

<span data-ttu-id="d7811-183">**Tipos blittable:**</span><span class="sxs-lookup"><span data-stu-id="d7811-183">**Blittable types:**</span></span>

- <span data-ttu-id="d7811-184">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span><span class="sxs-lookup"><span data-stu-id="d7811-184">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span></span>
- <span data-ttu-id="d7811-185">matrizes unidimensionais não aninhadas de tipos blittable (por exemplo, `int[]`)</span><span class="sxs-lookup"><span data-stu-id="d7811-185">non-nested one-dimensional arrays of blittable types (for example, `int[]`)</span></span>
- <span data-ttu-id="d7811-186">estruturas e classes com layout fixo que só têm tipos de valor blittable para campos de instância</span><span class="sxs-lookup"><span data-stu-id="d7811-186">structs and classes with fixed layout that only have blittable value types for instance fields</span></span>
  - <span data-ttu-id="d7811-187">layout fixo requer `[StructLayout(LayoutKind.Sequential)]` ou `[StructLayout(LayoutKind.Explicit)]`</span><span class="sxs-lookup"><span data-stu-id="d7811-187">fixed layout requires `[StructLayout(LayoutKind.Sequential)]` or `[StructLayout(LayoutKind.Explicit)]`</span></span>
  - <span data-ttu-id="d7811-188">structs são `LayoutKind.Sequential` por padrão, classes são `LayoutKind.Auto`</span><span class="sxs-lookup"><span data-stu-id="d7811-188">structs are `LayoutKind.Sequential` by default, classes are `LayoutKind.Auto`</span></span>

<span data-ttu-id="d7811-189">**NÃO blittable:**</span><span class="sxs-lookup"><span data-stu-id="d7811-189">**NOT blittable:**</span></span>

- `bool`

<span data-ttu-id="d7811-190">**ÀS VEZES blittable:**</span><span class="sxs-lookup"><span data-stu-id="d7811-190">**SOMETIMES blittable:**</span></span>

- <span data-ttu-id="d7811-191">`char`, `string`</span><span class="sxs-lookup"><span data-stu-id="d7811-191">`char`, `string`</span></span>

<span data-ttu-id="d7811-192">Quando tipos blittable são passados por referência, eles são simplesmente fixados pelo marshaller em vez de serem copiados para um buffer intermediário.</span><span class="sxs-lookup"><span data-stu-id="d7811-192">When blittable types are passed by reference, they're simply pinned by the marshaller instead of being copied to an intermediate buffer.</span></span> <span data-ttu-id="d7811-193">(As classes são inerentemente passadas por referência, structs são passadas por referência quando usadas com `ref` ou `out`).</span><span class="sxs-lookup"><span data-stu-id="d7811-193">(Classes are inherently passed by reference, structs are passed by reference when used with `ref` or `out`.)</span></span>

<span data-ttu-id="d7811-194">`char` é blittable em uma matriz unidimensional **ou** se for parte de um tipo que é explicitamente marcado com `[StructLayout]` com `CharSet = CharSet.Unicode`.</span><span class="sxs-lookup"><span data-stu-id="d7811-194">`char` is blittable in a one-dimensional array **or** if it's part of a type that contains it's explicitly marked with `[StructLayout]` with `CharSet = CharSet.Unicode`.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

<span data-ttu-id="d7811-195">`string` é blittable se não está contido em outro tipo e está sendo passado como um argumento marcado com `[MarshalAs(UnmanagedType.LPWStr)]` ou o `[DllImport]` tem `CharSet = CharSet.Unicode` definido.</span><span class="sxs-lookup"><span data-stu-id="d7811-195">`string` is blittable if it isn't contained in another type and it's being passed as an argument that is marked with `[MarshalAs(UnmanagedType.LPWStr)]` or the `[DllImport]` has `CharSet = CharSet.Unicode` set.</span></span>

<span data-ttu-id="d7811-196">Você pode verificar se um tipo é blittable pela tentativa de criar um `GCHandle` fixado.</span><span class="sxs-lookup"><span data-stu-id="d7811-196">You can see if a type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="d7811-197">Se o tipo não for uma cadeia de caracteres ou considerado blittable, `GCHandle.Alloc` lançará um `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="d7811-197">If the type isn't a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="d7811-198">✔️ TORNE suas estruturas mais blittable quando possível.</span><span class="sxs-lookup"><span data-stu-id="d7811-198">✔️ DO make your structures blittable when possible.</span></span>

<span data-ttu-id="d7811-199">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="d7811-199">For more information, see:</span></span>

- [<span data-ttu-id="d7811-200">Tipos blittable e não blittable</span><span class="sxs-lookup"><span data-stu-id="d7811-200">Blittable and Non-Blittable Types</span></span>](../../framework/interop/blittable-and-non-blittable-types.md)
- [<span data-ttu-id="d7811-201">Marshaling de Tipo</span><span class="sxs-lookup"><span data-stu-id="d7811-201">Type Marshaling</span></span>](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a><span data-ttu-id="d7811-202">Manter objetos gerenciados ativos</span><span class="sxs-lookup"><span data-stu-id="d7811-202">Keeping managed objects alive</span></span>

<span data-ttu-id="d7811-203">`GC.KeepAlive()` garantirá que um objeto permaneça no escopo até que o método KeepAlive seja alcançado.</span><span class="sxs-lookup"><span data-stu-id="d7811-203">`GC.KeepAlive()` will ensure an object stays in scope until the KeepAlive method is hit.</span></span>

<span data-ttu-id="d7811-204">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef)permite que o marshaller mantenha um objeto vivo durante a duração de um P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="d7811-204">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) allows the marshaller to keep an object alive for the duration of a P/Invoke.</span></span> <span data-ttu-id="d7811-205">Ele pode ser usado em vez de `IntPtr` em assinaturas de métodos.</span><span class="sxs-lookup"><span data-stu-id="d7811-205">It can be used instead of `IntPtr` in method signatures.</span></span> <span data-ttu-id="d7811-206">`SafeHandle` substitui efetivamente essa classe e deve ser usado em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="d7811-206">`SafeHandle` effectively replaces this class and should be used instead.</span></span>

<span data-ttu-id="d7811-207">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle)permite fixar um objeto gerenciado e obter o ponteiro nativo para ele.</span><span class="sxs-lookup"><span data-stu-id="d7811-207">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) allows pinning a managed object and getting the native pointer to it.</span></span> <span data-ttu-id="d7811-208">O padrão básico é:</span><span class="sxs-lookup"><span data-stu-id="d7811-208">The basic pattern is:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

<span data-ttu-id="d7811-209">Fixar não é o padrão para `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="d7811-209">Pinning isn't the default for `GCHandle`.</span></span> <span data-ttu-id="d7811-210">O outro padrão principal é passar uma referência a um objeto gerenciado por meio do código nativo e voltar ao código gerenciado, geralmente com um retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="d7811-210">The other major pattern is for passing a reference to a managed object through native code and back to managed code, usually with a callback.</span></span> <span data-ttu-id="d7811-211">Aqui está o padrão:</span><span class="sxs-lookup"><span data-stu-id="d7811-211">Here is the pattern:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

<span data-ttu-id="d7811-212">Não se esqueça que `GCHandle` precisa ser explicitamente liberado para evitar perda de memória.</span><span class="sxs-lookup"><span data-stu-id="d7811-212">Don't forget that `GCHandle` needs to be explicitly freed to avoid memory leaks.</span></span>

## <a name="common-windows-data-types"></a><span data-ttu-id="d7811-213">Tipos de dados comuns do Windows</span><span class="sxs-lookup"><span data-stu-id="d7811-213">Common Windows data types</span></span>

<span data-ttu-id="d7811-214">Veja a seguir uma lista dos tipos de dados comumente usados em APIs do Windows e quais tipos C# devem ser usados ao chamar o código do Windows.</span><span class="sxs-lookup"><span data-stu-id="d7811-214">Here is a list of data types commonly used in Windows APIs and which C# types to use when calling into the Windows code.</span></span>

<span data-ttu-id="d7811-215">Os tipos a seguir são do mesmo tamanho no Windows de 32 e 64 bits, apesar de seus nomes.</span><span class="sxs-lookup"><span data-stu-id="d7811-215">The following types are the same size on 32-bit and 64-bit Windows, despite their names.</span></span>

| <span data-ttu-id="d7811-216">Largura</span><span class="sxs-lookup"><span data-stu-id="d7811-216">Width</span></span> | <span data-ttu-id="d7811-217">Windows</span><span class="sxs-lookup"><span data-stu-id="d7811-217">Windows</span></span>          | <span data-ttu-id="d7811-218">C (Windows)</span><span class="sxs-lookup"><span data-stu-id="d7811-218">C (Windows)</span></span>          | <span data-ttu-id="d7811-219">C#</span><span class="sxs-lookup"><span data-stu-id="d7811-219">C#</span></span>       | <span data-ttu-id="d7811-220">Alternativa</span><span class="sxs-lookup"><span data-stu-id="d7811-220">Alternative</span></span>                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| <span data-ttu-id="d7811-221">32</span><span class="sxs-lookup"><span data-stu-id="d7811-221">32</span></span>    | `BOOL`           | `int`                | `int`    | `bool`                               |
| <span data-ttu-id="d7811-222">8</span><span class="sxs-lookup"><span data-stu-id="d7811-222">8</span></span>     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| <span data-ttu-id="d7811-223">8</span><span class="sxs-lookup"><span data-stu-id="d7811-223">8</span></span>     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="d7811-224">8</span><span class="sxs-lookup"><span data-stu-id="d7811-224">8</span></span>     | `CHAR`           | `char`               | `sbyte`  |                                      |
| <span data-ttu-id="d7811-225">8</span><span class="sxs-lookup"><span data-stu-id="d7811-225">8</span></span>     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="d7811-226">16</span><span class="sxs-lookup"><span data-stu-id="d7811-226">16</span></span>    | `SHORT`          | `short`              | `short`  |                                      |
| <span data-ttu-id="d7811-227">16</span><span class="sxs-lookup"><span data-stu-id="d7811-227">16</span></span>    | `CSHORT`         | `short`              | `short`  |                                      |
| <span data-ttu-id="d7811-228">16</span><span class="sxs-lookup"><span data-stu-id="d7811-228">16</span></span>    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="d7811-229">16</span><span class="sxs-lookup"><span data-stu-id="d7811-229">16</span></span>    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="d7811-230">16</span><span class="sxs-lookup"><span data-stu-id="d7811-230">16</span></span>    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="d7811-231">32</span><span class="sxs-lookup"><span data-stu-id="d7811-231">32</span></span>    | `INT`            | `int`                | `int`    |                                      |
| <span data-ttu-id="d7811-232">32</span><span class="sxs-lookup"><span data-stu-id="d7811-232">32</span></span>    | `LONG`           | `long`               | `int`    |                                      |
| <span data-ttu-id="d7811-233">32</span><span class="sxs-lookup"><span data-stu-id="d7811-233">32</span></span>    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="d7811-234">32</span><span class="sxs-lookup"><span data-stu-id="d7811-234">32</span></span>    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="d7811-235">64</span><span class="sxs-lookup"><span data-stu-id="d7811-235">64</span></span>    | `QWORD`          | `long long`          | `long`   |                                      |
| <span data-ttu-id="d7811-236">64</span><span class="sxs-lookup"><span data-stu-id="d7811-236">64</span></span>    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| <span data-ttu-id="d7811-237">64</span><span class="sxs-lookup"><span data-stu-id="d7811-237">64</span></span>    | `LONGLONG`       | `long long`          | `long`   |                                      |
| <span data-ttu-id="d7811-238">64</span><span class="sxs-lookup"><span data-stu-id="d7811-238">64</span></span>    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="d7811-239">64</span><span class="sxs-lookup"><span data-stu-id="d7811-239">64</span></span>    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="d7811-240">32</span><span class="sxs-lookup"><span data-stu-id="d7811-240">32</span></span>    | `HRESULT`        | `long`               | `int`    |                                      |
| <span data-ttu-id="d7811-241">32</span><span class="sxs-lookup"><span data-stu-id="d7811-241">32</span></span>    | `NTSTATUS`       | `long`               | `int`    |                                      |

<span data-ttu-id="d7811-242">Os tipos a seguir, sendo ponteiros, seguem a largura da plataforma.</span><span class="sxs-lookup"><span data-stu-id="d7811-242">The following types, being pointers, do follow the width of the platform.</span></span> <span data-ttu-id="d7811-243">Use `IntPtr`/`UIntPtr` para eles.</span><span class="sxs-lookup"><span data-stu-id="d7811-243">Use `IntPtr`/`UIntPtr` for these.</span></span>

| <span data-ttu-id="d7811-244">Tipos de ponteiros assinados (use `IntPtr`)</span><span class="sxs-lookup"><span data-stu-id="d7811-244">Signed Pointer Types (use `IntPtr`)</span></span> | <span data-ttu-id="d7811-245">Tipos de ponteiros não assinados (use `UIntPtr`)</span><span class="sxs-lookup"><span data-stu-id="d7811-245">Unsigned Pointer Types (use `UIntPtr`)</span></span> |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

<span data-ttu-id="d7811-246">Um `PVOID`Windows que é um `void*` C pode passar por marshalling como `IntPtr` ou `UIntPtr`, mas prefere `void*` quando possível.</span><span class="sxs-lookup"><span data-stu-id="d7811-246">A Windows `PVOID` which is a C `void*` can be marshaled as either `IntPtr` or `UIntPtr`, but prefer `void*` when possible.</span></span>

[<span data-ttu-id="d7811-247">Tipos de dados do Windows</span><span class="sxs-lookup"><span data-stu-id="d7811-247">Windows Data Types</span></span>](/windows/desktop/WinProg/windows-data-types)

[<span data-ttu-id="d7811-248">Intervalos de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="d7811-248">Data Type Ranges</span></span>](/cpp/cpp/data-type-ranges)

## <a name="structs"></a><span data-ttu-id="d7811-249">Structs</span><span class="sxs-lookup"><span data-stu-id="d7811-249">Structs</span></span>

<span data-ttu-id="d7811-250">As structs gerenciadas são criadas e não são removidas até o método retornar.</span><span class="sxs-lookup"><span data-stu-id="d7811-250">Managed structs are created on the stack and aren't removed until the method returns.</span></span> <span data-ttu-id="d7811-251">Por definição, elas são "fixadas" (não serão movidas pelo GC).</span><span class="sxs-lookup"><span data-stu-id="d7811-251">By definition then, they are "pinned" (it won't get moved by the GC).</span></span> <span data-ttu-id="d7811-252">Você também pode simplesmente pegar o endereço em blocos de código não seguros se o código nativo não usar o ponteiro após o final do método atual.</span><span class="sxs-lookup"><span data-stu-id="d7811-252">You can also simply take the address in unsafe code blocks if native code won't use the pointer past the end of the current method.</span></span>

<span data-ttu-id="d7811-253">Structs blittable são muito mais eficazes, pois simplesmente podem ser usados de modo direto pela camada de marshaling.</span><span class="sxs-lookup"><span data-stu-id="d7811-253">Blittable structs are much more performant as they can simply be used directly by the marshaling layer.</span></span> <span data-ttu-id="d7811-254">Tente tornar structs blittable (por exemplo, evite `bool`).</span><span class="sxs-lookup"><span data-stu-id="d7811-254">Try to make structs blittable (for example, avoid `bool`).</span></span> <span data-ttu-id="d7811-255">Para saber mais, veja a seção [Tipos blittable](#blittable-types).</span><span class="sxs-lookup"><span data-stu-id="d7811-255">For more information, see the [Blittable Types](#blittable-types) section.</span></span>

<span data-ttu-id="d7811-256">*Se* a struct é blittable, use `sizeof()` em vez de `Marshal.SizeOf<MyStruct>()` para melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="d7811-256">*If* the struct is blittable, use `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for better performance.</span></span> <span data-ttu-id="d7811-257">Como mencionado acima, você pode validar que o tipo é blittable ao tentar criar um `GCHandle` fixado.</span><span class="sxs-lookup"><span data-stu-id="d7811-257">As mentioned above, you can validate that the type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="d7811-258">Se o tipo não for uma cadeia de caracteres ou considerado blittable, `GCHandle.Alloc` lançara `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="d7811-258">If the type is not a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="d7811-259">Os ponteiros para structs nas definições devem ser transmitidos por `ref` ou usar `unsafe` e `*`.</span><span class="sxs-lookup"><span data-stu-id="d7811-259">Pointers to structs in definitions must either be passed by `ref` or use `unsafe` and `*`.</span></span>

<span data-ttu-id="d7811-260">✔️ BUSQUE a struct gerenciada o mais próximo possível da forma e dos nomes usados na documentação ou no cabeçalho da plataforma oficial.</span><span class="sxs-lookup"><span data-stu-id="d7811-260">✔️ DO match the managed struct as closely as possible to the shape and names that are used in the official platform documentation or header.</span></span>

<span data-ttu-id="d7811-261">✔️ USE`sizeof()` C# em vez de `Marshal.SizeOf<MyStruct>()` para estruturas blittable a fim de melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="d7811-261">✔️ DO use the C# `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for blittable structures to improve performance.</span></span>

<span data-ttu-id="d7811-262">❌EVITE `System.Delegate` usar `System.MulticastDelegate` ou campos para representar campos de ponteiro de função em estruturas.</span><span class="sxs-lookup"><span data-stu-id="d7811-262">❌ AVOID using `System.Delegate` or `System.MulticastDelegate` fields to represent function pointer fields in structures.</span></span>

<span data-ttu-id="d7811-263">Uma <xref:System.Delegate?displayProperty=fullName> <xref:System.MulticastDelegate?displayProperty=fullName> vez que e não tem uma assinatura necessária, eles não garantem que o delegado aprovado corresponderá à assinatura que o código nativo espera.</span><span class="sxs-lookup"><span data-stu-id="d7811-263">Since <xref:System.Delegate?displayProperty=fullName> and <xref:System.MulticastDelegate?displayProperty=fullName> don't have a required signature, they don't guarantee that the delegate passed in will match the signature the native code expects.</span></span> <span data-ttu-id="d7811-264">Além disso, no .NET Framework e no .NET Core, `System.Delegate` `System.MulticastDelegate` o marshaling de uma estrutura contendo uma ou de sua representação nativa para um objeto gerenciado pode desestabilizar o tempo de execução se o valor do campo na representação nativa não for um ponteiro de função que envolva um delegado gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d7811-264">Additionally, in .NET Framework and .NET Core, marshaling a struct containing a `System.Delegate` or `System.MulticastDelegate` from its native representation to a managed object can destabilize the runtime if the value of the field in the native representation isn't a function pointer that wraps a managed delegate.</span></span> <span data-ttu-id="d7811-265">Nas versões .NET 5 `System.Delegate` e `System.MulticastDelegate` posteriores, não é suportado o empacotamento de um ou campo de uma representação nativa para um objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d7811-265">In .NET 5 and later versions, marshaling a `System.Delegate` or `System.MulticastDelegate` field from a native representation to a managed object is not supported.</span></span> <span data-ttu-id="d7811-266">Use um tipo de `System.Delegate` `System.MulticastDelegate`delegado específico em vez de ou .</span><span class="sxs-lookup"><span data-stu-id="d7811-266">Use a specific delegate type instead of `System.Delegate` or `System.MulticastDelegate`.</span></span>

### <a name="fixed-buffers"></a><span data-ttu-id="d7811-267">Buffers fixos</span><span class="sxs-lookup"><span data-stu-id="d7811-267">Fixed Buffers</span></span>

<span data-ttu-id="d7811-268">Uma matriz como `INT_PTR Reserved1[2]` precisa ser empacotada para dois campos `IntPtr`, `Reserved1a` e `Reserved1b`.</span><span class="sxs-lookup"><span data-stu-id="d7811-268">An array like `INT_PTR Reserved1[2]` has to be marshaled to two `IntPtr` fields, `Reserved1a` and `Reserved1b`.</span></span> <span data-ttu-id="d7811-269">Quando a matriz nativa é um tipo primitivo, podemos usar a palavra-chave `fixed` para escrevê-la um pouco mais limpa.</span><span class="sxs-lookup"><span data-stu-id="d7811-269">When the native array is a primitive type, we can use the `fixed` keyword to write it a little more cleanly.</span></span> <span data-ttu-id="d7811-270">Por exemplo, `SYSTEM_PROCESS_INFORMATION` se parece com isso no cabeçalho nativo:</span><span class="sxs-lookup"><span data-stu-id="d7811-270">For example, `SYSTEM_PROCESS_INFORMATION` looks like this in the native header:</span></span>

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

<span data-ttu-id="d7811-271">Em C#, podemos escrevê-lo assim:</span><span class="sxs-lookup"><span data-stu-id="d7811-271">In C#, we can write it like this:</span></span>

```csharp
internal unsafe struct SYSTEM_PROCESS_INFORMATION
{
    internal uint NextEntryOffset;
    internal uint NumberOfThreads;
    private fixed byte Reserved1[48];
    internal Interop.UNICODE_STRING ImageName;
    ...
}
```

<span data-ttu-id="d7811-272">No entanto, existem algumas armadilhas com buffers fixos.</span><span class="sxs-lookup"><span data-stu-id="d7811-272">However, there are some gotchas with fixed buffers.</span></span> <span data-ttu-id="d7811-273">Buffers fixos de tipos não blittable não serão empacotados corretamente, portanto, a matriz no local precisa ser expandida para vários campos individuais.</span><span class="sxs-lookup"><span data-stu-id="d7811-273">Fixed buffers of non-blittable types won't be correctly marshaled, so the in-place array needs to be expanded out to multiple individual fields.</span></span> <span data-ttu-id="d7811-274">Além disso, no .NET Framework e no .NET Core antes da versão 3.0, se um struct contendo um campo de buffer fixo for aninhado dentro de um struct não blittable, não será realizado o marshaling correto do campo de buffer fixo para código nativo.</span><span class="sxs-lookup"><span data-stu-id="d7811-274">Additionally, in .NET Framework and .NET Core before 3.0, if a struct containing a fixed buffer field is nested within a non-blittable struct, the fixed buffer field won't be correctly marshaled to native code.</span></span>
