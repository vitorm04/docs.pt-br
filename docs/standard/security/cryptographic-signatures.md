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
ms.openlocfilehash: 314c8b7268549380143a608bb423f849ad0bb64c
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583258"
---
# <a name="cryptographic-signatures"></a>Assinaturas criptográficas
<a name="top"></a> As assinaturas digitais de criptografia usam algoritmos de chave pública para fornecer integridade de dados. Quando você assina dados com uma assinatura digital, alguém pode verificar a assinatura e pode provar que os dados origem de você e não foi alterados depois que você assinou. Para obter mais informações sobre assinaturas digitais, consulte [serviços de criptografia](../../../docs/standard/security/cryptographic-services.md).  
  
 Este tópico explica como gerar e verificar assinaturas digitais usando classes no <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.  
  
-   [Geração de assinaturas](#generate)  
  
-   [Verificando assinaturas](#verify)  
  
<a name="generate"></a>   
## <a name="generating-signatures"></a>Geração de assinaturas  
 Assinaturas digitais geralmente são aplicadas aos valores de hash que representam dados maiores. O exemplo a seguir se aplica a uma assinatura digital a um valor de hash. Primeiro, uma nova instância do <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe é criada para gerar um par de chaves pública/privada. Em seguida, o <xref:System.Security.Cryptography.RSACryptoServiceProvider> é passado para uma nova instância do <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> classe. Isso transfere a chave privada para o <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, que, na verdade, executa a assinatura digital. Antes de poder assinar o código hash, você deve especificar um algoritmo de hash a ser usado. Este exemplo usa o algoritmo SHA1. Por fim, o <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> método é chamado para executar a assinatura.  
  
```vb  
Imports System  
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
  
using System;  
using System.Security.Cryptography;  
```  
  
```csharp  
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
  
### <a name="signing-xml-files"></a>Assinatura de arquivos XML  
 O .NET Framework fornece o <xref:System.Security.Cryptography.Xml> namespace, que permite que você entrar XML. Assinatura XML é importante quando você deseja verificar se o XML provém de uma fonte de determinadas. Por exemplo, se você estiver usando um serviço de cotação de ações que usa o XML, você pode verificar a origem do XML, se ele for assinado.  
  
 Siga as classes neste namespace de [recomendação de processamento e a sintaxe de assinatura XML](https://www.w3.org/TR/xmldsig-core/) da World Wide Web Consortium.  
  
 [Voltar ao início](#top)  
  
<a name="verify"></a>   
## <a name="verifying-signatures"></a>Verificando assinaturas  
 Para verificar se os dados foi assinados por uma pessoa específica, você deve ter as seguintes informações:  
  
-   A chave pública da parte que os dados assinados.  
  
-   A assinatura digital.  
  
-   Os dados que receberam um sinal.  
  
-   O algoritmo de hash usado pelo signatário.  
  
 Para verificar uma assinatura assinada pela <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> classe, use o <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> classe. O <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> classe deve ser fornecido a chave pública do assinante. Você precisará dos valores do módulo e o expoente para especificar a chave pública. (A parte que gerou o par de chaves pública/privada deve fornecer esses valores.) Primeiro crie uma <xref:System.Security.Cryptography.RSACryptoServiceProvider> objeto para conter a chave pública que verificam a assinatura e, em seguida, inicialize um <xref:System.Security.Cryptography.RSAParameters> estrutura para os valores de módulo e um expoente que especificam a chave pública.  
  
 O código a seguir mostra a criação de um <xref:System.Security.Cryptography.RSAParameters> estrutura. O `Modulus` estiver definida como o valor de uma matriz de bytes chamada `modulusData` e o `Exponent` estiver definida como o valor de uma matriz de bytes chamada `exponentData`.  
  
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
  
 Depois que você criou o <xref:System.Security.Cryptography.RSAParameters> do objeto, você pode inicializar uma nova instância dos <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe para os valores especificados na <xref:System.Security.Cryptography.RSAParameters>. O <xref:System.Security.Cryptography.RSACryptoServiceProvider> é, por sua vez, passado para o construtor de um <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> para transferir a chave.  
  
 O exemplo a seguir ilustra esse processo. Neste exemplo, `hashValue` e `signedHashValue` são matrizes de bytes fornecidas por uma parte remota. A parte remota tiver se conectado a `hashValue` usando o algoritmo SHA1, produzindo a assinatura digital `signedHashValue`. O  
  
 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> método verifica se a assinatura digital é válida e foi usada para assinar o `hashValue`.  
  
```vb  
Dim rsa As New RSACryptoServiceProvider()  
rsa.ImportParameters(rsaKeyInfo)  
Dim rsaDeformatter As New RSAPKCS1SignatureDeformatter(rsa)  
rsaDeformatter.SetHashAlgorithm("SHA1")  
If rsaDeformatter.VerifySignature(hashValue, signedHashValue) Then  
   Console.WriteLine("The signature is valid.")  
Else  
   Console.WriteLine("The signture is not valid.")  
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
  
 Este fragmento de código exibirá "`The signature is valid`" se a assinatura é válida e "`The signature is not valid`" se não for.  
  
## <a name="see-also"></a>Consulte também

- [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)
