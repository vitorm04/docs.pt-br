---
title: Criptografando e descriptografando cadeias de caracteres no Visual Basic | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- encryption, strings
- strings [Visual Basic], encrypting
- decryption, strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ae3d599f7173162c07fbaeda60435615f101b10d
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>Instruções passo a passo: criptografando e descriptografando cadeias de caracteres no Visual Basic
Este passo a passo mostra como usar o <xref:System.Security.Cryptography.DESCryptoServiceProvider>classe para criptografar e descriptografar as cadeias de caracteres usando a versão CSP (provedor) de serviços de criptografia do Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algoritmo.</xref:System.Security.Cryptography.TripleDES> </xref:System.Security.Cryptography.DESCryptoServiceProvider> A primeira etapa é criar uma classe de invólucro simples que encapsula o algoritmo 3DES e armazena os dados criptografados como uma cadeia de caracteres codificada em base 64. Em seguida, esse wrapper é usado para armazenar com segurança dados particulares do usuário em um arquivo de texto publicamente acessível.  
  
 Você pode usar criptografia para proteger segredos do usuário (por exemplo, senhas) e fazer com que as credenciais ilegível por usuários não autorizados. Isso pode proteger a identidade de um usuário autorizado de ser roubada, que protege os ativos do usuário e fornece não-repúdio. A criptografia também pode proteger dados do usuário que está sendo acessado por usuários não autorizados.  
  
 Para obter mais informações, consulte [serviços criptográficos](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8).  
  
> [!IMPORTANT]
>  O Rijndael (agora conhecido como Advanced Encryption Standard [AES]) e algoritmos Triple Data Encryption Standard (3DES) fornecem maior segurança do que o DES porque eles são mais intensos de computação. Para obter mais informações, consulte <xref:System.Security.Cryptography.DES>e <xref:System.Security.Cryptography.Rijndael>.</xref:System.Security.Cryptography.Rijndael> </xref:System.Security.Cryptography.DES>  
  
### <a name="to-create-the-encryption-wrapper"></a>Para criar o wrapper de criptografia  
  
1.  Crie o `Simple3Des` classe para encapsular os métodos de criptografia e descriptografia.  
  
     [!code-vb[VbVbalrStrings&38;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  Adicionar uma importação do namespace de criptografia ao início do arquivo que contém o `Simple3Des` classe.  
  
     [!code-vb[VbVbalrStrings&#77;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  No `Simple3Des` da classe, adicione um campo particular para armazenar o provedor de serviços de criptografia 3DES.  
  
     [!code-vb[VbVbalrStrings&#39;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  Adicione um método particular que cria uma matriz de bytes de um comprimento especificado a partir do hash da chave especificada.  
  
     [!code-vb[41 VbVbalrStrings](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  Adicione um construtor para inicializar o provedor de serviços de criptografia 3DES.  
  
     O `key` parâmetro controla a `EncryptData` e `DecryptData` métodos.  
  
     [!code-vb[40 VbVbalrStrings](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  Adicione um método público que criptografa uma cadeia de caracteres.  
  
     [!code-vb[VbVbalrStrings&42;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  Adicione um método público que descriptografa uma cadeia de caracteres.  
  
     [!code-vb[VbVbalrStrings&#43;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     A classe wrapper agora pode ser usada para proteger ativos do usuário. Neste exemplo, ele é usado para armazenar com segurança dados particulares do usuário em um arquivo de texto publicamente acessível.  
  
### <a name="to-test-the-encryption-wrapper"></a>Para testar o wrapper de criptografia  
  
1.  Em uma classe separada, adicione um método que usa o wrapper `EncryptData` método criptografar uma cadeia de caracteres e gravá-los para o usuário da pasta Meus documentos.  
  
     [!code-vb[VbVbalrStrings&#78;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  Adicione um método que lê a cadeia de caracteres criptografada do usuário da pasta Meus documentos e descriptografa a cadeia de caracteres com o wrapper `DecryptData` método.  
  
     [!code-vb[VbVbalrStrings&#79;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  Adicionar código de interface do usuário chamar o `TestEncoding` e `TestDecoding` métodos.  
  
4.  Execute o aplicativo.  
  
     Quando você testar o aplicativo, observe que ele não será descriptografar os dados se você fornecer a senha incorreta.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.Cryptography></xref:System.Security.Cryptography>   
 <xref:System.Security.Cryptography.DESCryptoServiceProvider></xref:System.Security.Cryptography.DESCryptoServiceProvider>   
 <xref:System.Security.Cryptography.DES></xref:System.Security.Cryptography.DES>   
 <xref:System.Security.Cryptography.TripleDES></xref:System.Security.Cryptography.TripleDES>   
 <xref:System.Security.Cryptography.Rijndael></xref:System.Security.Cryptography.Rijndael>   
 [Serviços de criptografia](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8)
