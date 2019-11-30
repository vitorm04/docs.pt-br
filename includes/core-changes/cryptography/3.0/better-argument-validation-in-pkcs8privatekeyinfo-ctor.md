---
ms.openlocfilehash: a9b6af31b68c25ab58c52757f48ed23cca3f5a35
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567976"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="adc11-101">Melhor validação de argumento no Construtor Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="adc11-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="adc11-102">A partir do .NET Core 3,0 Preview 9, o construtor de `Pkcs8PrivateKeyInfo` valida o parâmetro `algorithmParameters` como um único valor codificado por BER.</span><span class="sxs-lookup"><span data-stu-id="adc11-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="adc11-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="adc11-103">Change description</span></span>

<span data-ttu-id="adc11-104">Antes do .NET Core 3,0 Preview 9, o [Construtor de`Pkcs8PrivateKeyInfo`](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) não validou o argumento `algorithmParameters`.</span><span class="sxs-lookup"><span data-stu-id="adc11-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="adc11-105">Quando esse argumento representasse um valor inválido, o Construtor teria sucesso, mas uma chamada para qualquer um dos métodos <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>ou <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> geraria um <xref:System.ArgumentException> para um argumento que ele não aceitou (`preEncodedValue`) ou um <xref:System.Security.Cryptography.CryptographicException>.</span><span class="sxs-lookup"><span data-stu-id="adc11-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="adc11-106">Se executado com o .NET Core 3,0 antes da versão prévia 9, o código a seguir lançará uma exceção somente quando o método <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> for chamado:</span><span class="sxs-lookup"><span data-stu-id="adc11-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="adc11-107">A partir do .NET Core 3,0 Preview 9, o argumento é validado no construtor e um valor inválido resulta no método que gera um <xref:System.Security.Cryptography.CryptographicException>.</span><span class="sxs-lookup"><span data-stu-id="adc11-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="adc11-108">Essa alteração move a exceção mais perto da origem do erro de dados.</span><span class="sxs-lookup"><span data-stu-id="adc11-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="adc11-109">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="adc11-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="adc11-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="adc11-110">Version introduced</span></span>

<span data-ttu-id="adc11-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="adc11-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="adc11-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="adc11-112">Recommended action</span></span>

<span data-ttu-id="adc11-113">Certifique-se de que apenas valores de `algorithmParameters` válidos sejam fornecidos ou que chamem para o teste de Construtor `Pkcs8PrivateKeyInfo` para <xref:System.ArgumentException> e <xref:System.Security.Cryptography.CryptographicException> se o tratamento de exceção for desejado.</span><span class="sxs-lookup"><span data-stu-id="adc11-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

### <a name="category"></a><span data-ttu-id="adc11-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="adc11-114">Category</span></span>

<span data-ttu-id="adc11-115">Criptografia</span><span class="sxs-lookup"><span data-stu-id="adc11-115">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="adc11-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="adc11-116">Affected APIs</span></span>

- <span data-ttu-id="adc11-117">[Construtor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="adc11-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean))

-->
