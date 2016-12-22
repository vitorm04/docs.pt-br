---
title: "Instru&#231;&#245;es passo a passo: criptografando e descriptografando cadeias de caracteres no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "descriptografia, cadeias de caracteres"
  - "criptografia, cadeias de caracteres"
  - "cadeias de caracteres {Visual Basic], descriptografando"
  - "cadeias de caracteres {Visual Basic], criptografando"
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: criptografando e descriptografando cadeias de caracteres no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Essa explicação passo a passo mostra como usar a classe <xref:System.Security.Cryptography.DESCryptoServiceProvider> para criptografar e descriptografar cadeias de caracteres usando a versão do provedor de serviços de criptografia \(CSP\) do algoritmo Triple Data Encryption Standard \(<xref:System.Security.Cryptography.TripleDES>\).  A primeira etapa é criar um classe wrapper simples que encapsula o algoritmo 3DES e armazena os dados criptografados como uma cadeia de caracteres codificada de base 64.  Em seguida, esse wrapper é usado para armazenar com segurança dados particulares do usuário em um arquivo de texto publicamente acessível.  
  
 Você pode usar a criptografia para proteger os segredos do usuário \(por exemplo, senhas\) e para tornar as credenciais ilegíveis por usuários não autorizados.  Isso pode proteger a identidade de um usuário autorizado de ser roubada, o que protege os ativos do usuário e fornece não\-repúdio.  A criptografia também pode proteger dados de um usuário de serem acessados por usuários não autorizados.  
  
 Para obter mais informações, consulte [Serviços criptográficos](../Topic/Cryptographic%20Services.md).  
  
> [!IMPORTANT]
>  O Rijndael \(agora conhecido como Advanced Encryption Standard \[AES\]\) e algoritmos Triple Data Encryption Standard \(3DES\) fornecem uma segurança maior que o DES porque são mais intensivos computacionalmente.  Para obter mais informações, consulte <xref:System.Security.Cryptography.DES> e <xref:System.Security.Cryptography.Rijndael>.  
  
### Para criar o wrapper de criptografia  
  
1.  Crie a classe de `Simple3Des` para encapsular os métodos de criptografia e descriptografia.  
  
     [!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  Adicionar uma importação do namespace de criptografia para o início do arquivo que contém a classe de `Simple3Des` .  
  
     [!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  Em a classe de `Simple3Des` , adicione um campo particular para armazenar o provedor de serviços de criptografia 3DES.  
  
     [!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  Adicione um método particular que cria um matriz de bytes de um comprimento especificado a partir do hash da chave especificada.  
  
     [!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  Adicione um construtor para inicializar o provedor de serviços de criptografia 3DES.  
  
     O parâmetro `key` controla os métodos `EncryptData` e `DecryptData`.  
  
     [!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  Adicione um método público que criptografa uma cadeia de caracteres.  
  
     [!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  Adicione um método público que descriptografa uma cadeia de caracteres.  
  
     [!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     A classe wrapper agora pode ser usada para proteger ativos do usuário.  Nesse exemplo, ela é usada para armazenar com segurança dados particulares do usuário em um arquivo de texto publicamente acessível.  
  
### Para testar o wrapper de criptografia  
  
1.  Em uma classe separada, adicione um método que usa o método `EncryptData` do wrapper para criptografar uma cadeia de caracteres e gravá\-la na pasta Meus Documentos do usuário.  
  
     [!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  Adicione um método que lê a cadeia de caracteres criptografada na pasta Meus Documentos do usuário e descriptografa a cadeia de caracteres com o método `DecryptData` do wrapper.  
  
     [!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  Adicione um código de interface do usuário para chamar os métodos `TestEncoding` e `TestDecoding`.  
  
4.  Execute o aplicativo.  
  
     Quando você testar o aplicativo, observe que ele não será descriptografar os dados se você fornecer a senha incorreta.  
  
## Consulte também  
 <xref:System.Security.Cryptography>   
 <xref:System.Security.Cryptography.DESCryptoServiceProvider>   
 <xref:System.Security.Cryptography.DES>   
 <xref:System.Security.Cryptography.TripleDES>   
 <xref:System.Security.Cryptography.Rijndael>   
 [Serviços criptográficos](../Topic/Cryptographic%20Services.md)