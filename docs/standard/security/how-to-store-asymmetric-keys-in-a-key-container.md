---
title: Como armazenar chaves assimétricas em um contêiner de chave
description: Saiba como armazenar chaves assimétricas em um contêiner de chave no .NET. Veja como criar uma chave assimétrica, salvá-la em um contêiner de chave e recuperar e excluir a chave.
ms.date: 05/26/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- storing asymmetric keys
- keys, asymmetric
- encryption keys
- keys, storing in key containers
- asymmetric keys [.NET Framework]
- encryption [.NET Framework], asymmetric keys
- decryption keys
ms.assetid: 0dbcbd8d-0dcf-40e9-9f0c-e3f162d35ccc
ms.openlocfilehash: a0fbde37491043cc1aab71e9733087bf410b997d
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769022"
---
# <a name="store-asymmetric-keys-in-a-key-container"></a><span data-ttu-id="5ac81-104">Armazenar chaves assimétricas em um contêiner de chave</span><span class="sxs-lookup"><span data-stu-id="5ac81-104">Store asymmetric keys in a key container</span></span>

<span data-ttu-id="5ac81-105">As chaves privadas assimétricas nunca devem ser armazenadas no formato textual nem como texto sem formatação no computador local.</span><span class="sxs-lookup"><span data-stu-id="5ac81-105">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="5ac81-106">Se você precisar armazenar uma chave privada, use um contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="5ac81-106">If you need to store a private key, use a key container.</span></span> <span data-ttu-id="5ac81-107">Para obter mais informações sobre contêineres de chave, consulte [noções básicas sobre contêineres de chave RSA no nível do computador e](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100))no nível do usuário.</span><span class="sxs-lookup"><span data-stu-id="5ac81-107">For more information on key containers, see [Understanding machine-level and user-level RSA key containers](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).</span></span>

## <a name="create-an-asymmetric-key-and-save-it-in-a-key-container"></a><span data-ttu-id="5ac81-108">Criar uma chave assimétrica e salvá-la em um contêiner de chave</span><span class="sxs-lookup"><span data-stu-id="5ac81-108">Create an asymmetric key and save it in a key container</span></span>

1. <span data-ttu-id="5ac81-109">Crie uma nova instância de uma <xref:System.Security.Cryptography.CspParameters> classe e passe o nome que você deseja chamar o contêiner de chave para o <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> campo.</span><span class="sxs-lookup"><span data-stu-id="5ac81-109">Create a new instance of a <xref:System.Security.Cryptography.CspParameters> class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>

1. <span data-ttu-id="5ac81-110">Crie uma nova instância de uma classe derivada da <xref:System.Security.Cryptography.AsymmetricAlgorithm> classe (geralmente <xref:System.Security.Cryptography.RSACryptoServiceProvider> ou <xref:System.Security.Cryptography.DSACryptoServiceProvider> ) e passe o objeto criado anteriormente `CspParameters` para seu construtor.</span><span class="sxs-lookup"><span data-stu-id="5ac81-110">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually <xref:System.Security.Cryptography.RSACryptoServiceProvider> or <xref:System.Security.Cryptography.DSACryptoServiceProvider>) and pass the previously created `CspParameters` object to its constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="5ac81-111">A criação e a recuperação de uma chave assimétrica são uma operação.</span><span class="sxs-lookup"><span data-stu-id="5ac81-111">The creation and retrieval of an asymmetric key is one operation.</span></span> <span data-ttu-id="5ac81-112">Se uma chave ainda não estiver no contêiner, ela será criada antes de ser retornada.</span><span class="sxs-lookup"><span data-stu-id="5ac81-112">If a key is not already in the container, it's created before being returned.</span></span>
>
> - <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType>
> - <xref:System.Security.Cryptography.DSA.ToXmlString%2A?displayProperty=nameWithType>

## <a name="delete-the-key-from-the-key-container"></a><span data-ttu-id="5ac81-113">Excluir a chave do contêiner de chave</span><span class="sxs-lookup"><span data-stu-id="5ac81-113">Delete the key from the key container</span></span>

1. <span data-ttu-id="5ac81-114">Crie uma nova instância de uma `CspParameters` classe e passe o nome que você deseja chamar o contêiner de chave para o <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> campo.</span><span class="sxs-lookup"><span data-stu-id="5ac81-114">Create a new instance of a `CspParameters` class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>

1. <span data-ttu-id="5ac81-115">Crie uma nova instância de uma classe derivada da <xref:System.Security.Cryptography.AsymmetricAlgorithm> classe (geralmente `RSACryptoServiceProvider` ou `DSACryptoServiceProvider` ) e passe o objeto criado anteriormente `CspParameters` para seu construtor.</span><span class="sxs-lookup"><span data-stu-id="5ac81-115">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually `RSACryptoServiceProvider` or `DSACryptoServiceProvider`) and pass the previously created `CspParameters` object to its constructor.</span></span>

1. <span data-ttu-id="5ac81-116">Defina a <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> propriedade ou <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> da classe que deriva de `AsymmetricAlgorithm` para `false` ( `False` em Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5ac81-116">Set the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> or the <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> property of the class that derives from `AsymmetricAlgorithm` to `false` (`False` in Visual Basic).</span></span>

1. <span data-ttu-id="5ac81-117">Chame o `Clear` método da classe derivada de `AsymmetricAlgorithm` .</span><span class="sxs-lookup"><span data-stu-id="5ac81-117">Call the `Clear` method of the class that derives from `AsymmetricAlgorithm`.</span></span> <span data-ttu-id="5ac81-118">Esse método libera todos os recursos da classe e limpa o contêiner de chaves.</span><span class="sxs-lookup"><span data-stu-id="5ac81-118">This method releases all resources of the class and clears the key container.</span></span>

## <a name="example"></a><span data-ttu-id="5ac81-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ac81-119">Example</span></span>

<span data-ttu-id="5ac81-120">O exemplo a seguir mostra como criar uma chave assimétrica, salvá-la em um contêiner de chaves, recuperar a chave posteriormente e excluir a chave do contêiner.</span><span class="sxs-lookup"><span data-stu-id="5ac81-120">The following example demonstrates how to create an asymmetric key, save it in a key container, retrieve the key at a later time, and delete the key from the container.</span></span>

<span data-ttu-id="5ac81-121">Observe que o código no `GenKey_SaveInContainer` método e o `GetKeyFromContainer` método são semelhantes.</span><span class="sxs-lookup"><span data-stu-id="5ac81-121">Notice that code in the `GenKey_SaveInContainer` method and the `GetKeyFromContainer` method is similar.</span></span> <span data-ttu-id="5ac81-122">Quando você especifica um nome de contêiner de chave para um <xref:System.Security.Cryptography.CspParameters> objeto e o passa para um <xref:System.Security.Cryptography.AsymmetricAlgorithm> objeto com a <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> propriedade ou <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> propriedade definida como `true` , o comportamento é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5ac81-122">When you specify a key container name for a <xref:System.Security.Cryptography.CspParameters> object and pass it to an <xref:System.Security.Cryptography.AsymmetricAlgorithm> object with the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> property or <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> property set to `true`, the behavior is as follows:</span></span>

- <span data-ttu-id="5ac81-123">se o contêiner de chaves com o nome especificado não existir, ele será criado e a chave persistirá.</span><span class="sxs-lookup"><span data-stu-id="5ac81-123">If a key container with the specified name does not exist, then one is created and the key is persisted.</span></span>
- <span data-ttu-id="5ac81-124">Se o contêiner de chaves com o nome especificado existir, a chave será carregada automaticamente no objeto <xref:System.Security.Cryptography.AsymmetricAlgorithm> atual.</span><span class="sxs-lookup"><span data-stu-id="5ac81-124">If a key container with the specified name does exist, then the key in the container is automatically loaded into the current <xref:System.Security.Cryptography.AsymmetricAlgorithm> object.</span></span>

<span data-ttu-id="5ac81-125">Portanto, o código no `GenKey_SaveInContainer` método persiste a chave porque ela é executada primeiro, enquanto o código no `GetKeyFromContainer` método carrega a chave porque ela é executada em segundo lugar.</span><span class="sxs-lookup"><span data-stu-id="5ac81-125">Therefore, the code in the `GenKey_SaveInContainer` method persists the key because it is run first, while the code in the `GetKeyFromContainer` method loads the key because it's run second.</span></span>

```vb
Imports System
Imports System.Security.Cryptography

Public Class StoreKey

    Public Shared Sub Main()
        Try
            ' Create a key and save it in a container.
            GenKey_SaveInContainer("MyKeyContainer")

            ' Retrieve the key from the container.
            GetKeyFromContainer("MyKeyContainer")

            ' Delete the key from the container.
            DeleteKeyFromContainer("MyKeyContainer")

            ' Create a key and save it in a container.
            GenKey_SaveInContainer("MyKeyContainer")

            ' Delete the key from the container.
            DeleteKeyFromContainer("MyKeyContainer")
        Catch e As CryptographicException
            Console.WriteLine(e.Message)
        End Try
    End Sub

    Private Shared Sub GenKey_SaveInContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        ' name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container MyKeyContainerName.
        Using rsa As New RSACryptoServiceProvider(parameters)
            ' Display the key information to the console.
            Console.WriteLine($"Key added to container:  {rsa.ToXmlString(True)}")
        End Using
    End Sub

    Private Shared Sub GetKeyFromContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        '  name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container MyKeyContainerName.
        Using rsa As New RSACryptoServiceProvider(parameters)
            ' Display the key information to the console.
            Console.WriteLine($"Key retrieved from container : {rsa.ToXmlString(True)}")
        End Using
    End Sub

    Private Shared Sub DeleteKeyFromContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        '  name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container.
        ' Delete the key entry in the container.
        Dim rsa As New RSACryptoServiceProvider(parameters) With {
            .PersistKeyInCsp = False
        }

        ' Call Clear to release resources and delete the key from the container.
        rsa.Clear()

        Console.WriteLine("Key deleted.")
    End Sub
End Class
```

```csharp
using System;
using System.Security.Cryptography;

public class StoreKey
{
    public static void Main()
    {
        try
        {
            // Create a key and save it in a container.
            GenKey_SaveInContainer("MyKeyContainer");

            // Retrieve the key from the container.
            GetKeyFromContainer("MyKeyContainer");

            // Delete the key from the container.
            DeleteKeyFromContainer("MyKeyContainer");

            // Create a key and save it in a container.
            GenKey_SaveInContainer("MyKeyContainer");

            // Delete the key from the container.
            DeleteKeyFromContainer("MyKeyContainer");
        }
        catch (CryptographicException e)
        {
            Console.WriteLine(e.Message);
        }
    }

    private static void GenKey_SaveInContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container MyKeyContainerName.
        using var rsa = new RSACryptoServiceProvider(parameters);

        // Display the key information to the console.
        Console.WriteLine($"Key added to container: \n  {rsa.ToXmlString(true)}");
    }

    private static void GetKeyFromContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container MyKeyContainerName.
        using var rsa = new RSACryptoServiceProvider(parameters);

        // Display the key information to the console.
        Console.WriteLine($"Key retrieved from container : \n {rsa.ToXmlString(true)}");
    }

    private static void DeleteKeyFromContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container.
        using var rsa = new RSACryptoServiceProvider(parameters)
        {
            // Delete the key entry in the container.
            PersistKeyInCsp = false
        };

        // Call Clear to release resources and delete the key from the container.
        rsa.Clear();

        Console.WriteLine("Key deleted.");
    }
}
```

<span data-ttu-id="5ac81-126">A saída é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="5ac81-126">The output is as follows:</span></span>

```console
Key added to container:
<RSAKeyValue> Key Information A</RSAKeyValue>
Key retrieved from container :
<RSAKeyValue> Key Information A</RSAKeyValue>
Key deleted.
Key added to container:
<RSAKeyValue> Key Information B</RSAKeyValue>
Key deleted.
```

## <a name="see-also"></a><span data-ttu-id="5ac81-127">Veja também</span><span class="sxs-lookup"><span data-stu-id="5ac81-127">See also</span></span>

- [<span data-ttu-id="5ac81-128">Gerando chaves para criptografia e descriptografia</span><span class="sxs-lookup"><span data-stu-id="5ac81-128">Generating keys for encryption and decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="5ac81-129">Criptografando dados</span><span class="sxs-lookup"><span data-stu-id="5ac81-129">Encrypting data</span></span>](encrypting-data.md)
- [<span data-ttu-id="5ac81-130">Descriptografando dados</span><span class="sxs-lookup"><span data-stu-id="5ac81-130">Decrypting data</span></span>](decrypting-data.md)
- [<span data-ttu-id="5ac81-131">Serviços de criptografia</span><span class="sxs-lookup"><span data-stu-id="5ac81-131">Cryptographic services</span></span>](cryptographic-services.md)
