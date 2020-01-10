---
title: Como acessar dispositivos de criptografia de hardware
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encryption
- key card
- cryptography
- hardware encryption
- CspParameters
ms.assetid: b0e734df-6eb4-4b16-b48c-6f0fe82d5f17
ms.openlocfilehash: d6ee22fd9fb0c11e22ac01ff83b3269e37e37763
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706169"
---
# <a name="how-to-access-hardware-encryption-devices"></a>Como acessar dispositivos de criptografia de hardware
Você pode usar a classe <xref:System.Security.Cryptography.CspParameters> para acessar dispositivos de criptografia de hardware. Por exemplo, você pode usar essa classe para integrar seu aplicativo a um cartão inteligente, um gerador de números aleatórios de hardware ou uma implementação de hardware de um algoritmo criptográfico específico.  
  
 A classe <xref:System.Security.Cryptography.CspParameters> cria um CSP (provedor de serviços de criptografia) que acessa um dispositivo de criptografia de hardware instalado corretamente.  Você pode verificar a disponibilidade de um CSP inspecionando a seguinte chave do registro usando o editor do registro (regedit. exe): HKEY_LOCAL_MACHINE \Software\Microsoft\Cryptography\Defaults\Provider.  
  
### <a name="to-sign-data-using-a-key-card"></a>Para assinar dados usando um cartão-chave  
  
1. Crie uma nova instância da classe <xref:System.Security.Cryptography.CspParameters>, passando o tipo de provedor inteiro e o nome do provedor para o construtor.  
  
2. Passe os sinalizadores apropriados para a propriedade <xref:System.Security.Cryptography.CspParameters.Flags%2A> do objeto de <xref:System.Security.Cryptography.CspParameters> recém-criado.  Por exemplo, passe o sinalizador <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer>.  
  
3. Crie uma nova instância de uma classe de <xref:System.Security.Cryptography.AsymmetricAlgorithm> (por exemplo, a classe <xref:System.Security.Cryptography.RSACryptoServiceProvider>), passando o objeto <xref:System.Security.Cryptography.CspParameters> para o construtor.  
  
4. Assine seus dados usando um dos métodos de `Sign` e verifique seus dados usando um dos métodos `Verify`.  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a>Para gerar um número aleatório usando um gerador de número aleatório de hardware  
  
1. Crie uma nova instância da classe <xref:System.Security.Cryptography.CspParameters>, passando o tipo de provedor inteiro e o nome do provedor para o construtor.  
  
2. Crie uma nova instância do <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passando o objeto <xref:System.Security.Cryptography.CspParameters> para o construtor.  
  
3. Crie um valor aleatório usando o método <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> ou <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A>.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como assinar dados usando um cartão inteligente.  O exemplo de código cria um objeto <xref:System.Security.Cryptography.CspParameters> que expõe um cartão inteligente e inicializa um objeto <xref:System.Security.Cryptography.RSACryptoServiceProvider> usando o CSP.  O exemplo de código, em seguida, assina e verifica alguns dados.  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
  
- Inclua os namespaces <xref:System> e <xref:System.Security.Cryptography>.  
  
- Você deve ter um leitor de cartão inteligente e drivers instalados no seu computador.  
  
- Você deve inicializar o objeto <xref:System.Security.Cryptography.CspParameters> usando informações específicas para o leitor de cartão.  Para obter mais informações, consulte a documentação do leitor de cartão.
