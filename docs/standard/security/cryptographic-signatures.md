---
title: Assinaturas criptográficas
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- digital signatures
- cryptography [.NET Framework], signatures
- digital signatures, XML signing
- signatures, cryptographic
- digital signatures, generating
- verifying signatures
- generating signatures
- digital signatures, about
- encryption [.NET Framework], signatures
- security [.NET Framework], signatures
- XML signing
- digital signatures, verifying
- signing XML
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de64af1a4617af39b0ef8e054292a402d6a145e6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350464"
---
# <a name="cryptographic-signatures"></a>Assinaturas criptográficas

As assinaturas digitais de criptografia usam algoritmos de chave pública para fornecer integridade de dados. Quando você assina dados com uma assinatura digital, outra pessoa pode verificar a assinatura e pode provar que os dados foram originados de você e não foram alterados depois que você o assinou. Para obter mais informações sobre assinaturas digitais, consulte [serviços de criptografia](../../../docs/standard/security/cryptographic-services.md).

Este tópico explica como gerar e verificar assinaturas digitais usando classes no namespace <xref:System.Security.Cryptography?displayProperty=nameWithType>.

## <a name="generating-signatures"></a>Gerando assinaturas

Geralmente, as assinaturas digitais são aplicadas a valores de hash que representam dados maiores. O exemplo a seguir aplica uma assinatura digital a um valor de hash. Primeiro, uma nova instância da classe <xref:System.Security.Cryptography.RSACryptoServiceProvider> é criada para gerar um par de chaves pública/privada. Em seguida, o <xref:System.Security.Cryptography.RSACryptoServiceProvider> é passado para uma nova instância da classe <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>. Isso transfere a chave privada para o <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, que realmente executa a assinatura digital. Antes de poder assinar o código hash, você deve especificar um algoritmo de hash a ser usado. Este exemplo usa o algoritmo SHA1. Por fim, o método <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> é chamado para executar a assinatura.

Devido a problemas de colisão com o SHA1, a Microsoft recomenda SHA256 ou melhor.

```vb
Imports System.Security.Cryptography

Module Module1
    Sub Main()
        'The hash value to sign.
        Dim hashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}

        'The value to hold the signed value.
        Dim signedHashValue() As Byte

        'Generate a public/private key pair.
        Dim rsa As New RSACryptoServiceProvider()

        'Create an RSAPKCS1SignatureFormatter object and pass it
        'the RSACryptoServiceProvider to transfer the private key.
        Dim rsaFormatter As New RSAPKCS1SignatureFormatter(rsa)

        'Set the hash algorithm to SHA1.
        rsaFormatter.SetHashAlgorithm("SHA1")

        'Create a signature for hashValue and assign it to
        'signedHashValue.
        signedHashValue = rsaFormatter.CreateSignature(hashValue)
    End Sub
End Module
```

```csharp
using System;
using System.Security.Cryptography;

class Class1
{
   static void Main()
   {
      //The hash value to sign.
      byte[] hashValue = {59,4,248,102,77,97,142,201,210,12,224,93,25,41,100,197,213,134,130,135};

      //The value to hold the signed value.
      byte[] signedHashValue;

      //Generate a public/private key pair.
      RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();

      //Create an RSAPKCS1SignatureFormatter object and pass it the
      //RSACryptoServiceProvider to transfer the private key.
      RSAPKCS1SignatureFormatter rsaFormatter = new RSAPKCS1SignatureFormatter(rsa);

      //Set the hash algorithm to SHA1.
      rsaFormatter.SetHashAlgorithm("SHA1");

      //Create a signature for hashValue and assign it to
      //signedHashValue.
      signedHashValue = rsaFormatter.CreateSignature(hashValue);
   }
}
```

### <a name="signing-xml-files"></a>Assinando arquivos XML

O .NET Framework fornece o namespace <xref:System.Security.Cryptography.Xml>, que permite que você assine o XML. A assinatura de XML é importante quando você deseja verificar se o XML provém de uma determinada fonte. Por exemplo, se você estiver usando um serviço de cotação de ações que usa XML, poderá verificar a origem do XML se ele estiver assinado.

As classes neste namespace seguem a [sintaxe de assinatura XML e a recomendação de processamento](https://www.w3.org/TR/xmldsig-core/) do World Wide Web Consortium.

## <a name="verifying-signatures"></a>Verificando assinaturas

Para verificar se os dados foram assinados por uma entidade específica, você deve ter as seguintes informações:

- A chave pública da entidade que assinou os dados.

- A assinatura digital.

- Os dados que receberam um sinal.

- O algoritmo de hash usado pelo assinante.

Para verificar uma assinatura assinada pela classe <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, use a classe <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter>. A classe de <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> deve ser fornecida à chave pública do Assinante. Você precisará dos valores do módulo e do expoente para especificar a chave pública. (A parte que gerou o par de chaves pública/privada deve fornecer esses valores.) Primeiro, crie um objeto <xref:System.Security.Cryptography.RSACryptoServiceProvider> para manter a chave pública que verificará a assinatura e, em seguida, inicialize uma estrutura de <xref:System.Security.Cryptography.RSAParameters> para os valores de módulo e expoente que especificam a chave pública.

O código a seguir mostra a criação de uma estrutura de <xref:System.Security.Cryptography.RSAParameters>. A propriedade `Modulus` é definida como o valor de uma matriz de bytes chamada `modulusData` e a propriedade `Exponent` é definida como o valor de uma matriz de bytes chamada `exponentData`.

```vb
Dim rsaKeyInfo As RSAParameters
rsaKeyInfo.Modulus = modulusData
rsaKeyInfo.Exponent = exponentData
```

```csharp
RSAParameters rsaKeyInfo;
rsaKeyInfo.Modulus = modulusData;
rsaKeyInfo.Exponent = exponentData;
```

Depois de criar o objeto <xref:System.Security.Cryptography.RSAParameters>, você pode inicializar uma nova instância da classe <xref:System.Security.Cryptography.RSACryptoServiceProvider> para os valores especificados em <xref:System.Security.Cryptography.RSAParameters>. O <xref:System.Security.Cryptography.RSACryptoServiceProvider> é, por sua vez, passado para o construtor de um <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> para transferir a chave.

O exemplo a seguir ilustra esse processo. Neste exemplo, `hashValue` e `signedHashValue` são matrizes de bytes fornecidos por uma parte remota. A parte remota assinou o `hashValue` usando o algoritmo SHA1, produzindo a `signedHashValue`de assinatura digital. O método <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> verifica se a assinatura digital é válida e se foi usada para assinar o `hashValue`.

```vb
Dim rsa As New RSACryptoServiceProvider()
rsa.ImportParameters(rsaKeyInfo)
Dim rsaDeformatter As New RSAPKCS1SignatureDeformatter(rsa)
rsaDeformatter.SetHashAlgorithm("SHA1")
If rsaDeformatter.VerifySignature(hashValue, signedHashValue) Then
   Console.WriteLine("The signature is valid.")
Else
   Console.WriteLine("The signature is not valid.")
End If
```

```csharp
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();
rsa.ImportParameters(rsaKeyInfo);
RSAPKCS1SignatureDeformatter rsaDeformatter = new RSAPKCS1SignatureDeformatter(rsa);
rsaDeformatter.SetHashAlgorithm("SHA1");
if(rsaDeformatter.VerifySignature(hashValue, signedHashValue))
{
   Console.WriteLine("The signature is valid.");
}
else
{
   Console.WriteLine("The signature is not valid.");
}
```

Esse fragmento de código exibirá "`The signature is valid`" se a assinatura for válida e "`The signature is not valid`" se não for.

## <a name="see-also"></a>Consulte também

- [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)
