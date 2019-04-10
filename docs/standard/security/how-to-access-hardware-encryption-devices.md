---
title: 'Como: acessar dispositivos de criptografia de hardware'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 33af618ac3971df76683fd64346e1aa1e5977177
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334608"
---
# <a name="how-to-access-hardware-encryption-devices"></a>Como: acessar dispositivos de criptografia de hardware
Você pode usar o <xref:System.Security.Cryptography.CspParameters> classe para dispositivos de criptografia de hardware de acesso. Por exemplo, você pode usar essa classe para integrar seu aplicativo com um cartão inteligente, um gerador de número aleatório de hardware ou uma implementação de hardware de um determinado algoritmo criptográfico.  
  
 O <xref:System.Security.Cryptography.CspParameters> classe cria um provedor de serviços de criptografia (CSP) que acessa um dispositivo de criptografia de hardware instalado corretamente.  Você pode verificar a disponibilidade de um CSP inspecionando a seguinte chave do registro usando o Editor do registro (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.  
  
### <a name="to-sign-data-using-a-key-card"></a>Para assinar dados usando um cartão de chave  
  
1. Criar uma nova instância do <xref:System.Security.Cryptography.CspParameters> classe, passando o tipo de provedor de inteiro e o nome do provedor para o construtor.  
  
2. Passar os sinalizadores adequados para o <xref:System.Security.Cryptography.CspParameters.Flags%2A> propriedade de recém-criado <xref:System.Security.Cryptography.CspParameters> objeto.  Por exemplo, passar o <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> sinalizador.  
  
3. Criar uma nova instância de um <xref:System.Security.Cryptography.AsymmetricAlgorithm> classe (por exemplo, o <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe), passando o <xref:System.Security.Cryptography.CspParameters> objeto para o construtor.  
  
4. Assinar seus dados usando um dos `Sign` métodos e verifique se seus dados usando um do `Verify` métodos.  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a>Para gerar um número aleatório usando um gerador de número aleatório de hardware  
  
1. Criar uma nova instância do <xref:System.Security.Cryptography.CspParameters> classe, passando o tipo de provedor de inteiro e o nome do provedor para o construtor.  
  
2. Criar uma nova instância dos <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passando o <xref:System.Security.Cryptography.CspParameters> objeto para o construtor.  
  
3. Criar um valor aleatório usando o <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> ou <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> método.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como assinar dados usando um cartão inteligente.  O exemplo de código cria um <xref:System.Security.Cryptography.CspParameters> objeto que expõe um cartão inteligente e, em seguida, inicializa um <xref:System.Security.Cryptography.RSACryptoServiceProvider> usando o CSP do objeto.  O exemplo de código e em seguida, assina e verifica alguns dados.  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Incluir o <xref:System> e <xref:System.Security.Cryptography> namespaces.  
  
-   Você deve ter um leitor de cartão inteligente e os drivers instalados em seu computador.  
  
-   Você deve inicializar o <xref:System.Security.Cryptography.CspParameters> usando informações específicas para seu leitor de cartão de objeto.  Para obter mais informações, consulte a documentação de seu leitor de cartão.
