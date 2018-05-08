---
title: Criptografando e descriptografando cadeias de caracteres no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: 96e56ab315a739fef9d5499b076a077f5294f39e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>Instruções passo a passo: criptografando e descriptografando cadeias de caracteres no Visual Basic
Este passo a passo mostra como usar o <xref:System.Security.Cryptography.DESCryptoServiceProvider> classe para criptografar e descriptografar cadeias de caracteres usando a versão CSP (provedor) de serviços de criptografia do padrão de criptografia de dados triplo (<xref:System.Security.Cryptography.TripleDES>) algoritmo. A primeira etapa é criar uma classe wrapper simples que encapsula o algoritmo 3DES e armazena os dados criptografados como uma cadeia de caracteres codificada de base 64. Em seguida, esse wrapper é usado para armazenar com segurança dados particulares do usuário em um arquivo de texto publicamente acessível.  
  
 Você pode usar criptografia para proteger segredos do usuário (por exemplo, senhas) e fazer com que as credenciais ilegível por usuários não autorizados. Isso pode proteger a identidade de um usuário autorizado de ser roubada, que protege os ativos do usuário e fornece não-repúdio. A criptografia também pode proteger dados de um usuário que está sendo acessado por usuários não autorizados.  
  
 Para obter mais informações, consulte [Serviços Criptográficos](../../../../standard/security/cryptographic-services.md).  
  
> [!IMPORTANT]
>  O Rijndael (agora conhecido como Advanced Encryption Standard [AES]) e algoritmos Triple Data Encryption Standard (3DES) fornecem maior segurança do que o DES porque eles são mais computação intensa. Para obter mais informações, consulte <xref:System.Security.Cryptography.DES> e <xref:System.Security.Cryptography.Rijndael>.  
  
### <a name="to-create-the-encryption-wrapper"></a>Para criar o wrapper de criptografia  
  
1.  Criar o `Simple3Des` classe para encapsular os métodos de criptografia e descriptografia.  
  
     [!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  Adicionar uma importação do namespace de criptografia para o início do arquivo que contém o `Simple3Des` classe.  
  
     [!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  No `Simple3Des` de classe, adicione um campo particular para armazenar o provedor de serviços de criptografia 3DES.  
  
     [!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  Adicione um método particular que cria uma matriz de bytes de um comprimento especificado do hash da chave especificada.  
  
     [!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  Adicione um construtor para inicializar o provedor de serviços de criptografia 3DES.  
  
     O `key` parâmetro controla o `EncryptData` e `DecryptData` métodos.  
  
     [!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  Adicione um método público que criptografa uma cadeia de caracteres.  
  
     [!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  Adicione um método público que descriptografa uma cadeia de caracteres.  
  
     [!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     A classe wrapper agora pode ser usada para proteger os ativos de usuário. Neste exemplo, ele é usado para armazenar com segurança dados particulares do usuário em um arquivo de texto publicamente acessível.  
  
### <a name="to-test-the-encryption-wrapper"></a>Para testar o wrapper de criptografia  
  
1.  Em uma classe separada, adicione um método que usa o wrapper `EncryptData` método para criptografar uma cadeia de caracteres e gravá-la para o usuário da pasta Meus documentos.  
  
     [!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  Adicione um método que lê a cadeia de caracteres criptografada do usuário da pasta Meus documentos e descriptografa a cadeia de caracteres com o wrapper `DecryptData` método.  
  
     [!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  Adicione código de interface do usuário chamar o `TestEncoding` e `TestDecoding` métodos.  
  
4.  Execute o aplicativo.  
  
     Quando você testar o aplicativo, observe que ele não será descriptografar os dados se você fornecer a senha incorreta.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.Cryptography>  
 <xref:System.Security.Cryptography.DESCryptoServiceProvider>  
 <xref:System.Security.Cryptography.DES>  
 <xref:System.Security.Cryptography.TripleDES>  
 <xref:System.Security.Cryptography.Rijndael>  
 [Serviços criptográficos](../../../../standard/security/cryptographic-services.md)
