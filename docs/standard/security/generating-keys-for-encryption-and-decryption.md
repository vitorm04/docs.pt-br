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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb506ee4e9dde8fcc58e92dfcecd9b896a78401e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="generating-keys-for-encryption-and-decryption"></a>Gerando chaves para criptografia e descriptografia
Criação e gerenciamento de chaves é uma parte importante do processo de criptografia. Algoritmos simétricos exigem a criação de uma chave e um vetor de inicialização (IV). A chave deve ser mantida em segredo de qualquer pessoa que não deve descriptografar os dados. O IV não precisa ser secreta, mas deve ser alterado para cada sessão. Algoritmos assimétricos exigem a criação de uma chave pública e uma chave privada. A chave pública pode ser publicada para qualquer pessoa, enquanto a chave privada deve conhecida somente pela parte que descriptografa os dados criptografados com a chave pública. Esta seção descreve como gerar e gerenciar chaves simétricas e assimétricas algoritmos.  
  
## <a name="symmetric-keys"></a>Chaves Simétricas  
 As classes de criptografia simétrica fornecidas pelo .NET Framework exigem uma chave e um vetor de inicialização (IV) para criptografar e descriptografar dados novos. Sempre que você cria uma nova instância de uma das classes de criptografia simétricas gerenciadas usando o construtor padrão, uma nova chave e IV são criados automaticamente. Qualquer pessoa que permitem a você para descriptografar os dados deve ter a mesma chave e IV e usam o mesmo algoritmo. Geralmente, uma nova chave e IV devem ser criado para cada sessão e a chave nem IV deve ser armazenado para uso em uma sessão posterior.  
  
 Para comunicar uma chave simétrica e IV para a parte remota, você normalmente deve criptografar a chave simétrica usando a criptografia assimétrica. Enviar a chave através de uma rede insegura sem criptografia não é segura, pois qualquer pessoa que intercepta a chave e o IV, em seguida, pode descriptografar os dados. Para obter mais informações sobre a troca de dados usando a criptografia, consulte [criando um esquema de criptografia](../../../docs/standard/security/creating-a-cryptographic-scheme.md).  
  
 O exemplo a seguir mostra a criação de uma nova instância do <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> classe que implementa o algoritmo TripleDES.  
  
```vb  
Dim TDES As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider TDES = new TripleDESCryptoServiceProvider();  
```  
  
 Quando o código anterior for executado, uma nova chave e IV são gerados e colocada no **chave** e **IV** propriedades, respectivamente.  
  
 Às vezes, talvez seja necessário gerar várias chaves. Nessa situação, você pode criar uma nova instância de uma classe que implementa um algoritmo simétrico e, em seguida, crie uma nova chave e IV chamando o **GenerateKey** e **GenerateIV** métodos. O exemplo de código a seguir ilustra como criar novas chaves e IVs depois que uma nova instância da classe de criptografia assimétrica é estabelecida.  
  
```vb  
Dim TDES As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
TDES.GenerateIV()  
TDES.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider TDES = new TripleDESCryptoServiceProvider();  
TDES.GenerateIV();  
TDES.GenerateKey();  
```  
  
 Quando o código anterior for executado, uma chave e IV são gerados quando a nova instância do **TripleDESCryptoServiceProvider** é feita. Outra chave e IV são criados quando o **GenerateKey** e **GenerateIV** métodos são chamados.  
  
## <a name="asymmetric-keys"></a>Chaves Assimétricas  
 O .NET Framework fornece o <xref:System.Security.Cryptography.RSACryptoServiceProvider> e <xref:System.Security.Cryptography.DSACryptoServiceProvider> classes para criptografia assimétrica. Essas classes de criar um par de chaves pública/privada quando você usa o construtor padrão para criar uma nova instância. Chaves assimétricas podem ser armazenadas para uso em várias sessões ou geradas para apenas uma sessão. Enquanto a chave pública pode ser disponibilizada, a chave privada deve ser bastante protegida.  
  
 Um par de chaves pública/privada é gerado sempre que uma nova instância de uma classe de algoritmo assimétrico é criada. Depois que uma nova instância da classe é criada, as informações de chave podem ser extraídas usando um destes dois métodos:  
  
-   O <xref:System.Security.Cryptography.RSA.ToXmlString%2A> método, que retorna uma representação XML das informações de chave.  
  
-   O <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> método, que retorna um <xref:System.Security.Cryptography.RSAParameters> estrutura que contém as informações de chave.  
  
 Ambos os métodos aceitam um valor booliano que indica se deve retornar apenas as informações de chave públicas ou para retornar a chave pública e as informações de chave privada. Um **RSACryptoServiceProvider** classe pode ser inicializada com o valor de um **RSAParameters** estrutura usando o <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> método.  
  
 As chaves privadas assimétricas nunca devem ser armazenadas no formato textual nem como texto sem formatação no computador local. Se precisar armazenar uma chave privada, você deverá usar um contêiner de chave. Para obter mais informações sobre como armazenar uma chave privada em um contêiner de chave, consulte [como: armazenar chaves assimétricas em um contêiner de chave](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).  
  
 O exemplo de código a seguir cria uma nova instância do **RSACryptoServiceProvider** classe, criando um par de chaves pública/privada e salva as informações de chave públicas para um **RSAParameters** estrutura.  
  
```vb  
'Generate a public/private key pair.  
Dim RSA as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim RSAKeyInfo As RSAParameters = RSA.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters RSAKeyInfo = RSA.ExportParameters(false);  
```  
  
## <a name="see-also"></a>Consulte também  
 [Criptografando dados](../../../docs/standard/security/encrypting-data.md)  
 [Descriptografando dados](../../../docs/standard/security/decrypting-data.md)  
 [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)  
 [Como armazenar chaves assimétricas em um contêiner de chaves](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md)
