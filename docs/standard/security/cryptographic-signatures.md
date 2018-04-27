---
title: Assinaturas criptográficas
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 17
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 596625f229c4031b681755d538bf0a3d7b6674c8
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="cryptographic-signatures"></a>Assinaturas criptográficas
<a name="top"></a> Assinaturas digitais criptográficas usam algoritmos de chave pública para fornecer a integridade dos dados. Quando você assinar dados com uma assinatura digital, alguém pode verificar a assinatura e pode provar que os dados origem de você e não foi alterados depois que você assinou. Para obter mais informações sobre assinaturas digitais, consulte [serviços criptográficos](../../../docs/standard/security/cryptographic-services.md).  
  
 Este tópico explica como gerar e verificar assinaturas digitais usando classes no <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.  
  
-   [Gerando assinaturas](#generate)  
  
-   [Verificando assinaturas](#verify)  
  
<a name="generate"></a>   
## <a name="generating-signatures"></a>Gerando assinaturas  
 Assinaturas digitais geralmente são aplicadas aos valores de hash que representam dados maiores. O exemplo a seguir se aplica a uma assinatura digital a um valor de hash. Primeiro, uma nova instância do <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe é criada para gerar um par de chaves pública/privada. Em seguida, o <xref:System.Security.Cryptography.RSACryptoServiceProvider> é passado para uma nova instância do <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> classe. Isso transfere a chave privada para o <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, que realmente executa a assinatura digital. Antes de poder assinar o código de hash, você deve especificar um algoritmo de hash a ser usado. Este exemplo usa o algoritmo SHA1. Por fim, o <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> método é chamado para executar a assinatura.  
  
```vb  
Imports System  
Imports System.Security.Cryptography  
  
Module Module1  
    Sub Main()  
        'The hash value to sign.  
        Dim HashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}  
  
        'The value to hold the signed value.  
        Dim SignedHashValue() As Byte  
  
        'Generate a public/private key pair.  
        Dim RSA As New RSACryptoServiceProvider()  
  
        'Create an RSAPKCS1SignatureFormatter object and pass it   
        'the RSACryptoServiceProvider to transfer the private key.  
        Dim RSAFormatter As New RSAPKCS1SignatureFormatter(RSA)  
  
        'Set the hash algorithm to SHA1.  
        RSAFormatter.SetHashAlgorithm("SHA1")  
  
        'Create a signature for HashValue and assign it to   
        'SignedHashValue.  
        SignedHashValue = RSAFormatter.CreateSignature(HashValue)  
    End Sub  
End Module  
  
using System;  
using System.Security.Cryptography;  
```  
  
```csharp  
class Class1  
{  
   static void Main()  
   {  
      //The hash value to sign.  
      byte[] HashValue = {59,4,248,102,77,97,142,201,210,12,224,93,25,41,100,197,213,134,130,135};  
  
      //The value to hold the signed value.  
      byte[] SignedHashValue;  
  
      //Generate a public/private key pair.  
      RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
  
      //Create an RSAPKCS1SignatureFormatter object and pass it the   
      //RSACryptoServiceProvider to transfer the private key.  
      RSAPKCS1SignatureFormatter RSAFormatter = new RSAPKCS1SignatureFormatter(RSA);  
  
      //Set the hash algorithm to SHA1.  
      RSAFormatter.SetHashAlgorithm("SHA1");  
  
      //Create a signature for HashValue and assign it to   
      //SignedHashValue.  
      SignedHashValue = RSAFormatter.CreateSignature(HashValue);  
   }  
}  
```  
  
### <a name="signing-xml-files"></a>Assinatura de arquivos XML  
 O .NET Framework fornece o <xref:System.Security.Cryptography.Xml> namespace, que permite que você assinar XML. Assinatura XML é importante quando você deseja verificar se o XML provém de uma fonte de determinados. Por exemplo, se você estiver usando um serviço de cotação de ações que usa o XML, você pode verificar a origem do XML se ele está assinado.  
  
 Siga as classes nesse namespace o [recomendação de processamento e a sintaxe de assinatura XML](https://www.w3.org/TR/xmldsig-core/) da World Wide Web Consortium.  
  
 [Voltar ao início](#top)  
  
<a name="verify"></a>   
## <a name="verifying-signatures"></a>Verificando assinaturas  
 Para verificar se dados foi assinados por uma pessoa específica, você deve ter as seguintes informações:  
  
-   A chave pública da parte que os dados assinados.  
  
-   A assinatura digital.  
  
-   Os dados que receberam um sinal.  
  
-   O algoritmo de hash usado pelo assinante.  
  
 Para verificar uma assinatura assinada pelo <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> classe, use o <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> classe. O <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> classe deve ser fornecido a chave pública do assinante. Você precisará dos valores do módulo e o expoente para especificar a chave pública. (A parte que gerou o par de chaves pública/privada deve fornecer esses valores). Primeiro crie um <xref:System.Security.Cryptography.RSACryptoServiceProvider> objeto para armazenar a chave pública que verificam a assinatura e, em seguida, inicializar um <xref:System.Security.Cryptography.RSAParameters> estrutura para os valores de módulo e o expoente que especifique a chave pública.  
  
 O código a seguir mostra a criação de um <xref:System.Security.Cryptography.RSAParameters> estrutura. O `Modulus` propriedade é definida como o valor de uma matriz de bytes chamada `ModulusData` e `Exponent` propriedade é definida como o valor de uma matriz de bytes chamada `ExponentData`.  
  
```vb  
Dim RSAKeyInfo As RSAParameters  
RSAKeyInfo.Modulus = ModulusData  
RSAKeyInfo.Exponent = ExponentData  
```  
  
```csharp  
RSAParameters RSAKeyInfo;  
RSAKeyInfo.Modulus = ModulusData;  
RSAKeyInfo.Exponent = ExponentData;  
```  
  
 Depois que você criou o <xref:System.Security.Cryptography.RSAParameters> do objeto, você pode inicializar uma nova instância do <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe com os valores especificados no <xref:System.Security.Cryptography.RSAParameters>. O <xref:System.Security.Cryptography.RSACryptoServiceProvider> é, por sua vez, passado para o construtor de um <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> para transferir a chave.  
  
 O exemplo a seguir ilustra esse processo. Neste exemplo, `HashValue` e `SignedHashValue` são matrizes de bytes fornecidos por um participante remoto. A parte remota tenha assinado a `HashValue` usando o algoritmo SHA1, produzindo a assinatura digital `SignedHashValue`. O  
  
 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> método verifica se a assinatura digital é válida e foi usada para assinar o `HashValue`.  
  
```vb  
Dim RSA As New RSACryptoServiceProvider()  
RSA.ImportParameters(RSAKeyInfo)  
Dim RSADeformatter As New RSAPKCS1SignatureDeformatter(RSA)  
RSADeformatter.SetHashAlgorithm("SHA1")  
If RSADeformatter.VerifySignature(HashValue, SignedHashValue) Then  
   Console.WriteLine("The signature is valid.")  
Else  
   Console.WriteLine("The signture is not valid.")  
End If  
```  
  
```csharp  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
RSA.ImportParameters(RSAKeyInfo);  
RSAPKCS1SignatureDeformatter RSADeformatter = new RSAPKCS1SignatureDeformatter(RSA);  
RSADeformatter.SetHashAlgorithm("SHA1");  
if(RSADeformatter.VerifySignature(HashValue, SignedHashValue))  
{  
   Console.WriteLine("The signature is valid.");  
}  
else  
{  
   Console.WriteLine("The signature is not valid.");  
}  
```  
  
 Este fragmento de código exibirá "`The signature is valid`" se a assinatura é válida e "`The signature is not valid`" se não for.  
  
## <a name="see-also"></a>Consulte também  
 [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)
