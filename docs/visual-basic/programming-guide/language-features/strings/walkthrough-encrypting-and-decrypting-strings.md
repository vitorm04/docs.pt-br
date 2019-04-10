---
title: Criptografando e descriptografando cadeias de caracteres no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: 1d003df87327e14a6cbd65222f86c3dc4df169ff
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334036"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>Passo a passo: Criptografando e descriptografando cadeias de caracteres no Visual Basic
Este passo a passo mostra como usar o <xref:System.Security.Cryptography.DESCryptoServiceProvider> classe para criptografar e descriptografar cadeias de caracteres usando a versão do CSP (provedor) de serviço criptográfico do Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algoritmo. A primeira etapa é criar uma classe de invólucro simples que encapsula o algoritmo 3DES e armazena os dados criptografados como uma cadeia de caracteres codificado em base 64. Em seguida, esse wrapper é usado para armazenar com segurança dados particulares do usuário em um arquivo de texto publicamente acessível.  
  
 Você pode usar criptografia para proteger segredos do usuário (por exemplo, senhas) e fazer com que as credenciais não pode ser lido por usuários não autorizados. Isso pode proteger a identidade de um usuário autorizado seja roubada, qual protege os ativos do usuário e fornece não-repúdio. A criptografia também pode proteger dados de um usuário que está sendo acessado por usuários não autorizados.  
  
 Para obter mais informações, consulte [Serviços Criptográficos](../../../../standard/security/cryptographic-services.md).  
  
> [!IMPORTANT]
>  O Rijndael (agora conhecido como criptografia AES [AES]) e algoritmos DES triplo (3DES) fornecem uma segurança maior do que o DES porque eles são mais intensos de computação. Para obter mais informações, consulte <xref:System.Security.Cryptography.DES> e <xref:System.Security.Cryptography.Rijndael>.  
  
### <a name="to-create-the-encryption-wrapper"></a>Para criar o wrapper de criptografia  
  
1. Criar o `Simple3Des` classe para encapsular os métodos de criptografia e descriptografia.  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. Adicionar uma importação do namespace de criptografia para o início do arquivo que contém o `Simple3Des` classe.  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. No `Simple3Des` de classe, adicione um campo particular para armazenar o provedor de serviços de criptografia 3DES.  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. Adicione um método particular que cria uma matriz de bytes de um comprimento especificado do hash da chave especificada.  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. Adicione um construtor para inicializar o provedor de serviços de criptografia 3DES.  
  
     O `key` parâmetro controla a `EncryptData` e `DecryptData` métodos.  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. Adicione um método público que criptografa uma cadeia de caracteres.  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. Adicione um método público que descriptografa uma cadeia de caracteres.  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     A classe de wrapper agora pode ser usada para proteger os ativos do usuário. Neste exemplo, ele é usado para armazenar com segurança dados particulares do usuário em um arquivo de texto publicamente acessível.  
  
### <a name="to-test-the-encryption-wrapper"></a>Para testar o wrapper de criptografia  
  
1. Em uma classe separada, adicione um método que usa o wrapper `EncryptData` método para criptografar uma cadeia de caracteres e gravá-lo para o usuário da pasta Meus documentos.  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. Adicione um método que lê a cadeia de caracteres criptografada do usuário da pasta Meus documentos e descriptografa a cadeia de caracteres com o wrapper `DecryptData` método.  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. Adicionar código de interface do usuário para chamar o `TestEncoding` e `TestDecoding` métodos.  
  
4. Execute o aplicativo.  
  
     Quando você testar o aplicativo, observe que ele não descriptografa os dados se você fornecer a senha incorreta.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [Serviços criptográficos](../../../../standard/security/cryptographic-services.md)
