---
title: Gerando chaves para criptografia e descriptografia
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET Framework], keys
- symmetric keys
- asymmetric keys [.NET Framework]
- cryptography [.NET Framework], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
ms.openlocfilehash: 88d8dac83c3d5bf267ed90ffb313cd9e24b42dea
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706182"
---
# <a name="generating-keys-for-encryption-and-decryption"></a>Gerando chaves para criptografia e descriptografia
A criação e o gerenciamento de chaves é uma parte importante do processo criptográfico. Os algoritmos simétricos exigem a criação de uma chave e um vetor de inicialização (IV). A chave deve ser mantida em segredo de qualquer pessoa que não deva descriptografar seus dados. O IV não precisa ser secreto, mas deve ser alterado para cada sessão. Algoritmos assimétricos exigem a criação de uma chave pública e uma chave privada. A chave pública pode se tornar pública para qualquer pessoa, enquanto a chave privada deve ser conhecida somente pela parte que descriptografará os dados criptografados com a chave pública. Esta seção descreve como gerar e gerenciar chaves para algoritmos simétricos e assimétricos.  
  
## <a name="symmetric-keys"></a>Chaves Simétricas  
 As classes de criptografia simétrica fornecidas pelo .NET Framework exigem uma chave e um novo vetor de inicialização (IV) para criptografar e descriptografar dados. Sempre que você cria uma nova instância de uma das classes criptográficas simétricas gerenciadas usando o construtor sem parâmetros, uma nova chave e IV são criadas automaticamente. Qualquer pessoa que você permita descriptografar seus dados deve ter a mesma chave e IV e usar o mesmo algoritmo. Em geral, uma nova chave e IV devem ser criadas para cada sessão e nem a chave nem o IV devem ser armazenados para uso em uma sessão posterior.  
  
 Para comunicar uma chave simétrica e um IV a uma parte remota, você normalmente criptografaria a chave simétrica usando a criptografia assimétrica. Enviar a chave por meio de uma rede insegura sem criptografá-la não é seguro, pois qualquer pessoa que intercepta a chave e o IV pode então descriptografar seus dados. Para obter mais informações sobre como trocar dados usando a criptografia, consulte [criando um esquema criptográfico](../../../docs/standard/security/creating-a-cryptographic-scheme.md).  
  
 O exemplo a seguir mostra a criação de uma nova instância da classe <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> que implementa o algoritmo TripleDES.  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
```  
  
 Quando o código anterior é executado, uma nova chave e IV são gerados e colocados nas propriedades **Key** e **IV** , respectivamente.  
  
 Às vezes, talvez seja necessário gerar várias chaves. Nessa situação, você pode criar uma nova instância de uma classe que implementa um algoritmo simétrico e, em seguida, criar uma nova chave e IV chamando os métodos **GenerateKey** e **GenerateIV** . O exemplo de código a seguir ilustra como criar novas chaves e IVs após uma nova instância da classe de criptografia simétrica ter sido feita.  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
tdes.GenerateIV()  
tdes.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
tdes.GenerateIV();  
tdes.GenerateKey();  
```  
  
 Quando o código anterior é executado, uma chave e IV são gerados quando a nova instância de **TripleDESCryptoServiceProvider** é feita. Outra chave e IV são criados quando os métodos **GenerateKey** e **GenerateIV** são chamados.  
  
## <a name="asymmetric-keys"></a>Chaves Assimétricas  
 O .NET Framework fornece as classes <xref:System.Security.Cryptography.RSACryptoServiceProvider> e <xref:System.Security.Cryptography.DSACryptoServiceProvider> para a criptografia assimétrica. Essas classes criam um par de chaves pública/privada quando você usa o construtor sem parâmetros para criar uma nova instância. Chaves assimétricas podem ser armazenadas para uso em várias sessões ou geradas apenas para uma sessão. Embora a chave pública possa ser disponibilizada para o público geral, a chave privada deve ser bastante protegida.  
  
 Um par de chaves pública/privada é gerado sempre que uma nova instância de uma classe de algoritmo assimétrico é criada. Depois que uma nova instância da classe é criada, as informações de chave podem ser extraídas usando um dos dois métodos:  
  
- O método <xref:System.Security.Cryptography.RSA.ToXmlString%2A>, que retorna uma representação XML das informações de chave.  
  
- O método <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A>, que retorna uma estrutura de <xref:System.Security.Cryptography.RSAParameters> que contém as informações de chave.  
  
 Os dois métodos aceitam um valor booliano que indica se deve retornar apenas as informações de chave pública ou para retornar as informações de chave pública e de chave privada. Uma classe **RSACryptoServiceProvider** pode ser inicializada para o valor de uma estrutura **RSAParameters** usando o método <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A>.  
  
 As chaves privadas assimétricas nunca devem ser armazenadas no formato textual nem como texto sem formatação no computador local. Se precisar armazenar uma chave privada, você deverá usar um contêiner de chave. Para obter mais informações sobre como armazenar uma chave privada em um contêiner de chave, consulte [como armazenar chaves assimétricas em um contêiner de chave](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).  
  
 O exemplo de código a seguir cria uma nova instância da classe **RSACryptoServiceProvider** , criando um par de chaves pública/privada e salva as informações de chave pública em uma estrutura **RSAParameters** .  
  
```vb  
'Generate a public/private key pair.  
Dim rsa as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim rsaKeyInfo As RSAParameters = rsa.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters rsaKeyInfo = rsa.ExportParameters(false);  
```  
  
## <a name="see-also"></a>Veja também

- [Criptografando dados](../../../docs/standard/security/encrypting-data.md)
- [Descriptografando dados](../../../docs/standard/security/decrypting-data.md)
- [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)
- [Como armazenar chaves assimétricas em um contêiner de chaves](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md)
