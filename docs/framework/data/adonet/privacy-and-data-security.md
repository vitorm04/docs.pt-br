---
title: Privacidade e segurança de dados
ms.date: 03/30/2017
ms.assetid: 46fa5839-adf7-4c7c-bce3-71e941fa7de9
ms.openlocfilehash: 04e405307d3aa42388c396cd69c465ba7ec70d35
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783232"
---
# <a name="privacy-and-data-security"></a>Privacidade e segurança de dados
Proteger e gerenciar informações confidenciais em um aplicativo ADO.NET depende dos produtos e tecnologias subjacentes usados para criá-lo. O ADO.NET não fornece diretamente serviços para proteger ou criptografar dados.  
  
## <a name="cryptography-and-hash-codes"></a>Criptografia e códigos de hash  
 As classes no namespace .NET Framework <xref:System.Security.Cryptography> podem ser usadas de seus aplicativos ADO.net para impedir que os dados sejam lidos ou modificados por terceiros não autorizados. Algumas classes são wrappers para o Microsoft CryptoAPI não gerenciado, enquanto outros são implementações gerenciadas. O tópico [serviços de criptografia](../../../standard/security/cryptographic-services.md) fornece uma visão geral da criptografia no .NET Framework, descreve como o cryptograph é implementado e como você pode executar tarefas de criptografia específicas.  
  
 Ao contrário da criptografia, que permite que os dados sejam criptografados e, em seguida, descriptografados, os dados de hash são um processo unidirecional. Os dados de hash são úteis quando você deseja impedir a adulteração verificando se os dados não foram alterados: dadas cadeias de caracteres de entrada idênticas, os algoritmos de hash sempre produzem valores de saída curtos idênticos que podem ser facilmente comparados. [Garantir a integridade dos dados com códigos de hash](../../../standard/security/ensuring-data-integrity-with-hash-codes.md) descreve como você pode gerar e verificar valores de hash.  
  
## <a name="encrypting-configuration-files"></a>Criptografando arquivos de configuração  
 A proteção do acesso à fonte de dados é essencial para a segurança do aplicativo. Uma cadeia de conexão apresenta uma vulnerabilidade potencial se não estiver protegida. As cadeias de conexão salvas em arquivos de configuração são armazenadas em arquivos XML padrão para os quais o .NET Framework definiu um conjunto comum de elementos. A configuração protegida permite que você criptografe informações confidenciais em um arquivo de configuração. Embora projetado principalmente para aplicativos ASP.NET, a configuração protegida também pode ser usada para criptografar seções de arquivo de configuração em aplicativos do Windows. Para obter mais informações, consulte [Protegendo informações de conexão](protecting-connection-information.md).  
  
## <a name="securing-string-values-in-memory"></a>Protegendo valores de cadeia de caracteres na memória  
 Se um <xref:System.String> objeto contiver informações confidenciais, como uma senha, um número de cartão de crédito ou dados pessoais, haverá um risco de que as informações possam ser reveladas após serem usadas porque o aplicativo não pode excluir os dados da memória do computador.  
  
 Um <xref:System.String> é imutável; seu valor não pode ser modificado depois de ser criado. As alterações que parecem modificar o valor da cadeia de caracteres realmente criam uma nova <xref:System.String> instância de um objeto na memória, armazenando os dados como texto sem formatação. Além disso, não é possível prever quando as instâncias de cadeia de caracteres serão excluídas da memória. A recuperação de memória com cadeias de caracteres não é determinística com a coleta de lixo do .NET. Você deve evitar usar as <xref:System.String> classes <xref:System.Text.StringBuilder> e se seus dados forem verdadeiramente confidenciais.  
  
 A <xref:System.Security.SecureString> classe fornece métodos para criptografar texto usando a DPAPI (API de proteção de dados) na memória. A cadeia de caracteres é excluída da memória quando ela não é mais necessária. Não há nenhum `ToString` método para ler rapidamente o conteúdo de um <xref:System.Security.SecureString>. Você pode inicializar uma nova instância do `SecureString` sem valor ou passando um ponteiro para uma matriz de <xref:System.Char> objetos. Em seguida, você pode usar os vários métodos da classe para trabalhar com a cadeia de caracteres. Para obter mais informações, baixe o [aplicativo de exemplo SecureString](https://go.microsoft.com/fwlink/?LinkId=120418), que demonstra como usar `SecureString` a classe de.  
  
## <a name="see-also"></a>Consulte também

- [Securing ADO.NET Applications](securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)
- [SQL Server Security](./sql/sql-server-security.md) (Segurança do SQL Server)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
