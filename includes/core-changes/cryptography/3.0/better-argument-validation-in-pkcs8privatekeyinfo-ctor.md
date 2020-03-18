---
ms.openlocfilehash: 8d3a8712528d2d35c706cc26b8c388b65d6ad506
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449200"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="a3fc0-101">Melhor validação de argumentos no construtor Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="a3fc0-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="a3fc0-102">Começando com a visualização .NET `Pkcs8PrivateKeyInfo` Core 3.0 `algorithmParameters` 9, o construtor valida o parâmetro como um único valor codificado por BER.</span><span class="sxs-lookup"><span data-stu-id="a3fc0-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a3fc0-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="a3fc0-103">Change description</span></span>

<span data-ttu-id="a3fc0-104">Antes do .NET Core 3.0 Preview 9, `algorithmParameters` o [ `Pkcs8PrivateKeyInfo` construtor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) não validou o argumento.</span><span class="sxs-lookup"><span data-stu-id="a3fc0-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="a3fc0-105">Quando este argumento representava um valor inválido, o construtor teria <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>sucesso, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>mas <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> uma chamada para <xref:System.ArgumentException> qualquer um dos <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>métodos, <xref:System.Security.Cryptography.CryptographicException>ou métodos jogaria ma ou um argumento que eles não aceitassem (`preEncodedValue`) ou um .</span><span class="sxs-lookup"><span data-stu-id="a3fc0-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="a3fc0-106">Se for executado com o .NET Core 3.0 antes da <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> visualização 9, o código a seguir será executado apenas quando o método for chamado:</span><span class="sxs-lookup"><span data-stu-id="a3fc0-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="a3fc0-107">A partir do .NET Core 3.0 Preview 9, o argumento é validado na <xref:System.Security.Cryptography.CryptographicException>construtora, e um valor inválido resulta no método de lançamento de um .</span><span class="sxs-lookup"><span data-stu-id="a3fc0-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="a3fc0-108">Essa alteração move a exceção mais perto da fonte do erro de dados.</span><span class="sxs-lookup"><span data-stu-id="a3fc0-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="a3fc0-109">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="a3fc0-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="a3fc0-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="a3fc0-110">Version introduced</span></span>

<span data-ttu-id="a3fc0-111">3.0 Visualização 9</span><span class="sxs-lookup"><span data-stu-id="a3fc0-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a3fc0-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="a3fc0-112">Recommended action</span></span>

<span data-ttu-id="a3fc0-113">Certifique-se `algorithmParameters` de que apenas valores válidos são fornecidos ou que chamadas para o `Pkcs8PrivateKeyInfo` teste de construtor para ambos <xref:System.ArgumentException> e <xref:System.Security.Cryptography.CryptographicException> se o manuseio de exceção for desejado.</span><span class="sxs-lookup"><span data-stu-id="a3fc0-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

### <a name="category"></a><span data-ttu-id="a3fc0-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="a3fc0-114">Category</span></span>

<span data-ttu-id="a3fc0-115">Criptografia</span><span class="sxs-lookup"><span data-stu-id="a3fc0-115">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="a3fc0-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="a3fc0-116">Affected APIs</span></span>

- <span data-ttu-id="a3fc0-117">[Construtor pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="a3fc0-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
