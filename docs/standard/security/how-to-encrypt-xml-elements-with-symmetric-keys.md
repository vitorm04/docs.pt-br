---
title: Como criptografar elementos XML com chaves simétricas
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AES algorithm
- cryptography [.NET Framework], symmetric keys
- encryption [.NET Framework], symmetric keys
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Advanced Encryption Standard algorithm
- Rijndael
ms.assetid: d8461a44-aa2c-4ef4-b3e4-ab7cbaaee1b5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d9fa06ed0befd82a3efdd46deaa2362b1f10fa35
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a>Como criptografar elementos XML com chaves simétricas
Você pode usar as classes de <xref:System.Security.Cryptography.Xml> namespace para criptografar um elemento em um documento XML.  Criptografia XML permite armazenar ou transportar XML confidencial, sem se preocupar com os dados que estão sendo lidos facilmente.  Esse procedimento descriptografa um elemento XML usando o algoritmo de criptografia AES (Advanced Standard), também conhecido como Rijndael.  
  
 Para obter informações sobre como descriptografar um elemento XML que foi criptografado usando esse procedimento, consulte [como: descriptografar elementos XML com chaves simétricas](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).  
  
 Quando você usa um algoritmo simétrico, como AES para criptografar os dados XML, você deve usar a mesma chave para criptografar e descriptografar os dados XML.  O exemplo neste procedimento presume que o XML criptografado serão descriptografado usando a mesma chave, e que a criptografia e descriptografia de participantes concordam com o algoritmo e a chave a ser usado.  Este exemplo não armazena nem criptografar a chave AES dentro do XML criptografado.  
  
 Este exemplo é apropriado para situações em que um único aplicativo precisa criptografar dados com base em uma chave de sessão armazenados na memória ou baseada em uma chave forte criptograficamente derivada de uma senha.  Em situações em que dois ou mais aplicativos precisam compartilhar os dados criptografados do XML, considere o uso de um esquema de criptografia com base em um algoritmo assimétrico ou um certificado x. 509.  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a>Para criptografar um elemento XML com uma chave simétrica  
  
1.  Gerar uma chave simétrica usando o <xref:System.Security.Cryptography.RijndaelManaged> classe.  Essa chave será usada para criptografar o elemento XML.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2.  Criar um <xref:System.Xml.XmlDocument> objeto carregando um arquivo XML do disco.  O <xref:System.Xml.XmlDocument> objeto contém o elemento XML para criptografar.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3.  Localizar o elemento especificado no <xref:System.Xml.XmlDocument> de objeto e criar um novo <xref:System.Xml.XmlElement> objeto para representar o elemento que você deseja criptografar.  Neste exemplo, o `"creditcard"` elemento está criptografado.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4.  Criar uma nova instância do <xref:System.Security.Cryptography.Xml.EncryptedXml> classe e usá-la para criptografar o <xref:System.Xml.XmlElement> com a chave simétrica.  O <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> método retorna o elemento criptografado como uma matriz de bytes criptografados.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5.  Construir um <xref:System.Security.Cryptography.Xml.EncryptedData> de objeto e preenchê-lo com o identificador de URL do elemento XML criptografia.  Esse identificador de URL permite que um participante descriptografar o XML contém um elemento criptografado.  Você pode usar o <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> campo para especificar o identificador de URL.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6.  Criar um <xref:System.Security.Cryptography.Xml.EncryptionMethod> objeto que é inicializado para o identificador de URL do algoritmo de criptografia usado para gerar a chave.  Passar o <xref:System.Security.Cryptography.Xml.EncryptionMethod> o objeto para o <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> propriedade.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7.  Adicionar os dados criptografados do elemento para o <xref:System.Security.Cryptography.Xml.EncryptedData> objeto.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8.  Substitua o elemento do original <xref:System.Xml.XmlDocument> do objeto com o <xref:System.Security.Cryptography.Xml.EncryptedData> elemento.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a>Exemplo  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Para compilar este exemplo, você precisa incluir uma referência a `System.Security.dll`.  
  
-   Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, e <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Nunca armazenar uma chave de criptografia em texto não criptografado ou transferir uma chave entre máquinas em texto não criptografado.  Em vez disso, use um contêiner de chave seguro para armazenar chaves de criptografia.  
  
 Quando você terminar usando uma chave de criptografia, limpá-la da memória, definindo cada byte para zero ou chamando o <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> método da classe gerenciada de criptografia.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.Cryptography.Xml>  
 [Como descriptografar elementos XML com chaves simétricas](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md)
