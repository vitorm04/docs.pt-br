---
title: Como usar proteção de dados
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b043c5a2173cff9eb82497f6d4ee8b7c0aa3f14c
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46325398"
---
# <a name="how-to-use-data-protection"></a>Como usar proteção de dados
O .NET Framework fornece acesso para a proteção de dados DPAPI (API), que lhe permite criptografar dados usando as informações de conta de usuário atual ou do computador.  Quando você usa a DPAPI, você aliviar o problema difícil de explicitamente gerar e armazenar uma chave de criptografia.  
  
 Use o <xref:System.Security.Cryptography.ProtectedMemory> classe para criptografar uma matriz de bytes na memória.  Essa funcionalidade está disponível no Microsoft Windows XP e sistemas operacionais posteriores.  Você pode especificar que a memória criptografada pelo atual processo pode ser descriptografado pelo processo atual, por todos os processos ou no mesmo contexto de usuário.  Consulte a <xref:System.Security.Cryptography.MemoryProtectionScope> enumeração para uma descrição detalhada do <xref:System.Security.Cryptography.ProtectedMemory> opções.  
  
 Use o <xref:System.Security.Cryptography.ProtectedData> classe a cópia de uma matriz de bytes. Essa funcionalidade está disponível no Microsoft Windows 2000 e sistemas operacionais posteriores.  Você pode especificar que os dados criptografados pela conta do usuário atual podem ser descriptografados somente pela mesma conta de usuário, ou você pode especificar que os dados criptografados pela conta de usuário atual podem ser descriptografados por qualquer conta no computador.  Consulte a <xref:System.Security.Cryptography.DataProtectionScope> enumeração para uma descrição detalhada do <xref:System.Security.Cryptography.ProtectedData> opções.  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a>Para criptografar os dados na memória usando a proteção de dados  
  
1.  Chamar estático <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> método passando uma matriz de bytes para criptografar a entropia e o escopo de proteção de memória.  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a>Para descriptografar os dados na memória usando a proteção de dados  
  
1.  Chamar estático <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> método passando uma matriz de bytes para descriptografar e o escopo de proteção de memória.  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a>Para criptografar dados em um arquivo ou fluxo usando a proteção de dados  
  
1.  Crie entropia aleatória.  
  
2.  Chamar estático <xref:System.Security.Cryptography.ProtectedData.Protect%2A> método passando uma matriz de bytes para criptografar a entropia e o escopo de proteção de dados.  
  
3.  Gravar os dados criptografados em um arquivo ou fluxo.  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a>Para descriptografar os dados de um arquivo ou fluxo usando a proteção de dados  
  
1.  Ler os dados criptografados de um arquivo ou fluxo.  
  
2.  Chamar estático <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> método passando uma matriz de bytes para descriptografar e o escopo de proteção de dados.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra duas formas de criptografia e descriptografia.  Primeiro, o exemplo de código criptografa e descriptografa uma matriz na memória de bytes.  Em seguida, o exemplo de código criptografa uma cópia de uma matriz de bytes, salva em um arquivo, carrega os dados de volta do arquivo e, em seguida, descriptografa os dados.  O exemplo exibe os dados originais, os dados criptografados e os dados descriptografados.  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Incluir uma referência a `System.Security.dll`.  
  
-   Incluir o <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, e <xref:System.Text> namespace.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Security.Cryptography.ProtectedMemory>  
- <xref:System.Security.Cryptography.ProtectedData>
