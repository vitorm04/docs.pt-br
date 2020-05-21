---
ms.openlocfilehash: 32030698c12de87daef5e1d8851a0f55ec36d688
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721430"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="eeabe-101">Melhor validação de argumento no Construtor Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="eeabe-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="eeabe-102">A partir do .NET Core 3,0 Preview 9, o `Pkcs8PrivateKeyInfo` Construtor valida o `algorithmParameters` parâmetro como um único valor codificado pelo ber.</span><span class="sxs-lookup"><span data-stu-id="eeabe-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="eeabe-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="eeabe-103">Change description</span></span>

<span data-ttu-id="eeabe-104">Antes do .NET Core 3,0 Preview 9, o [ `Pkcs8PrivateKeyInfo` Construtor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) não validou o `algorithmParameters` argumento.</span><span class="sxs-lookup"><span data-stu-id="eeabe-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="eeabe-105">Quando esse argumento representasse um valor inválido, o Construtor teria sucesso, mas uma chamada para qualquer um <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> dos <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A> métodos,, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A> ou <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> geraria um <xref:System.ArgumentException> para um argumento que não aceitou ( `preEncodedValue` ) ou um <xref:System.Security.Cryptography.CryptographicException> .</span><span class="sxs-lookup"><span data-stu-id="eeabe-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="eeabe-106">Se executado com o .NET Core 3,0 antes da versão prévia 9, o código a seguir lançará uma exceção somente quando o <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> método for chamado:</span><span class="sxs-lookup"><span data-stu-id="eeabe-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="eeabe-107">A partir do .NET Core 3,0 Preview 9, o argumento é validado no construtor e um valor inválido resulta no método que gera um <xref:System.Security.Cryptography.CryptographicException> .</span><span class="sxs-lookup"><span data-stu-id="eeabe-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="eeabe-108">Essa alteração move a exceção mais perto da origem do erro de dados.</span><span class="sxs-lookup"><span data-stu-id="eeabe-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="eeabe-109">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="eeabe-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="eeabe-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="eeabe-110">Version introduced</span></span>

<span data-ttu-id="eeabe-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="eeabe-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="eeabe-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="eeabe-112">Recommended action</span></span>

<span data-ttu-id="eeabe-113">Certifique-se de que apenas `algorithmParameters` valores válidos sejam fornecidos ou que chame para o `Pkcs8PrivateKeyInfo` teste de construtor para ambos <xref:System.ArgumentException> e se a manipulação de <xref:System.Security.Cryptography.CryptographicException> exceção for desejada.</span><span class="sxs-lookup"><span data-stu-id="eeabe-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

#### <a name="category"></a><span data-ttu-id="eeabe-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="eeabe-114">Category</span></span>

<span data-ttu-id="eeabe-115">Criptografia</span><span class="sxs-lookup"><span data-stu-id="eeabe-115">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eeabe-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="eeabe-116">Affected APIs</span></span>

- <span data-ttu-id="eeabe-117">[Construtor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="eeabe-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
