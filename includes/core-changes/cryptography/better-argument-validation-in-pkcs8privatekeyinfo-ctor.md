---
ms.openlocfilehash: a9b6af31b68c25ab58c52757f48ed23cca3f5a35
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71263330"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="fe370-101">Melhor validação de argumento no Construtor Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="fe370-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="fe370-102">A partir do .NET Core 3,0 Preview 9, `Pkcs8PrivateKeyInfo` o Construtor valida o `algorithmParameters` parâmetro como um único valor codificado pelo ber.</span><span class="sxs-lookup"><span data-stu-id="fe370-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fe370-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="fe370-103">Change description</span></span>

<span data-ttu-id="fe370-104">Antes do .NET Core 3,0 Preview 9, o [ `Pkcs8PrivateKeyInfo` Construtor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) não validou `algorithmParameters` o argumento.</span><span class="sxs-lookup"><span data-stu-id="fe370-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="fe370-105">Quando esse argumento representasse um valor inválido, o Construtor teria sucesso, mas uma chamada para qualquer um <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>dos <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>métodos <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>,, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> ou geraria um <xref:System.ArgumentException> para um argumento que não aceitou (`preEncodedValue`) ou um <xref:System.Security.Cryptography.CryptographicException>.</span><span class="sxs-lookup"><span data-stu-id="fe370-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="fe370-106">Se executado com o .NET Core 3,0 antes da versão prévia 9, o código a seguir lançará <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> uma exceção somente quando o método for chamado:</span><span class="sxs-lookup"><span data-stu-id="fe370-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="fe370-107">A partir do .NET Core 3,0 Preview 9, o argumento é validado no construtor e um valor inválido resulta no método que gera um <xref:System.Security.Cryptography.CryptographicException>.</span><span class="sxs-lookup"><span data-stu-id="fe370-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="fe370-108">Essa alteração move a exceção mais perto da origem do erro de dados.</span><span class="sxs-lookup"><span data-stu-id="fe370-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="fe370-109">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="fe370-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="fe370-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="fe370-110">Version introduced</span></span>

<span data-ttu-id="fe370-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="fe370-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fe370-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="fe370-112">Recommended action</span></span>

<span data-ttu-id="fe370-113">Certifique-se de `algorithmParameters` que apenas valores válidos sejam fornecidos ou que chame `Pkcs8PrivateKeyInfo` para o teste de <xref:System.ArgumentException> Construtor <xref:System.Security.Cryptography.CryptographicException> para ambos e se a manipulação de exceção for desejada.</span><span class="sxs-lookup"><span data-stu-id="fe370-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

### <a name="category"></a><span data-ttu-id="fe370-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="fe370-114">Category</span></span>

<span data-ttu-id="fe370-115">Criptografia</span><span class="sxs-lookup"><span data-stu-id="fe370-115">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="fe370-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="fe370-116">Affected APIs</span></span>

- <span data-ttu-id="fe370-117">[Construtor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="fe370-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean))

-->
