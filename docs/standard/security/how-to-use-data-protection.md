---
title: Como usar proteção de dados
description: Saiba como usar a proteção de dados acessando a API de proteção de dados (DPAPI) no .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET Framework], data protection API
- data [.NET Framework], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET Framework], data protection API
- data protection API [.NET Framework]
- decryption
- data [.NET Framework], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: c7f88105727dfd33c87a815054aa317ac2052e83
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598587"
---
# <a name="how-to-use-data-protection"></a>Como usar proteção de dados
O .NET Framework fornece acesso à DPAPI (API de proteção de dados), que permite que você criptografe os dados usando as informações da conta de usuário atual ou do computador.  Ao usar o DPAPI, você alivia o problema difícil de gerar e armazenar explicitamente uma chave criptográfica.  
  
 Use a <xref:System.Security.Cryptography.ProtectedMemory> classe para criptografar uma matriz de bytes na memória.  Essa funcionalidade está disponível no Microsoft Windows XP e em sistemas operacionais posteriores.  Você pode especificar que a memória criptografada pelo processo atual só possa ser descriptografada pelo processo atual, por todos os processos ou pelo mesmo contexto de usuário.  Consulte a <xref:System.Security.Cryptography.MemoryProtectionScope> enumeração para obter uma descrição detalhada das <xref:System.Security.Cryptography.ProtectedMemory> opções.  
  
 Use a <xref:System.Security.Cryptography.ProtectedData> classe para criptografar uma cópia de uma matriz de bytes. Essa funcionalidade está disponível no Microsoft Windows 2000 e em sistemas operacionais posteriores.  Você pode especificar que os dados criptografados pela conta de usuário atual possam ser descriptografados somente pela mesma conta de usuário ou pode especificar que os dados criptografados pela conta de usuário atual possam ser descriptografados por qualquer conta no computador.  Consulte a <xref:System.Security.Cryptography.DataProtectionScope> enumeração para obter uma descrição detalhada das <xref:System.Security.Cryptography.ProtectedData> opções.  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a>Para criptografar dados na memória usando a proteção de dados  
  
1. Chame o <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> método estático ao passar uma matriz de bytes para criptografar, a entropia e o escopo de proteção de memória.  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a>Para descriptografar dados na memória usando a proteção de dados  
  
1. Chame o <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> método estático ao passar uma matriz de bytes para descriptografar e o escopo de proteção de memória.  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a>Para criptografar dados para um arquivo ou fluxo usando a proteção de dados  
  
1. Criar entropia aleatória.  
  
2. Chame o <xref:System.Security.Cryptography.ProtectedData.Protect%2A> método estático ao passar uma matriz de bytes para criptografar, a entropia e o escopo de proteção de dados.  
  
3. Grave os dados criptografados em um arquivo ou fluxo.  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a>Para descriptografar dados de um arquivo ou fluxo usando a proteção de dados  
  
1. Ler os dados criptografados de um arquivo ou fluxo.  
  
2. Chame o <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> método estático ao passar uma matriz de bytes para descriptografar e o escopo de proteção de dados.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra duas formas de criptografia e descriptografia.  Primeiro, o exemplo de código criptografa e, em seguida, descriptografa uma matriz de bytes na memória.  Em seguida, o exemplo de código criptografa uma cópia de uma matriz de bytes, salva-a em um arquivo, carrega os dados de volta do arquivo e, em seguida, descriptografa os dados.  O exemplo exibe os dados originais, os dados criptografados e os dados descriptografados.  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
- Inclua uma referência para `System.Security.dll` .  
  
- Inclua o <xref:System> namespace,, <xref:System.IO> <xref:System.Security.Cryptography> e <xref:System.Text> .  
  
## <a name="see-also"></a>Confira também

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
