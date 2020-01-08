---
title: Privacidade e segurança de dados
ms.date: 03/30/2017
ms.assetid: 46fa5839-adf7-4c7c-bce3-71e941fa7de9
ms.openlocfilehash: a8d7ae2ece966b4649c9c988c123304fe3f1b4d9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348131"
---
# <a name="privacy-and-data-security"></a>Privacidade e segurança de dados
Proteger e gerenciar informações confidenciais em um aplicativo ADO.NET depende dos produtos e tecnologias subjacentes usados para criá-lo. O ADO.NET não fornece diretamente serviços para proteger ou criptografar dados.  
  
## <a name="cryptography-and-hash-codes"></a>Criptografia e códigos de hash  
 As classes no namespace do .NET Framework <xref:System.Security.Cryptography> podem ser usadas em seus aplicativos ADO.NET para impedir que os dados sejam lidos ou modificados por terceiros não autorizados. Algumas classes são wrappers para o Microsoft CryptoAPI não gerenciado, enquanto outros são implementações gerenciadas. O tópico [serviços de criptografia](../../../standard/security/cryptographic-services.md) fornece uma visão geral da criptografia no .NET Framework, descreve como o cryptograph é implementado e como você pode executar tarefas de criptografia específicas.  
  
 Ao contrário da criptografia, que permite que os dados sejam criptografados e, em seguida, descriptografados, os dados de hash são um processo unidirecional. Os dados de hash são úteis quando você deseja impedir a adulteração verificando se os dados não foram alterados: dadas cadeias de caracteres de entrada idênticas, os algoritmos de hash sempre produzem valores de saída curtos idênticos que podem ser facilmente comparados. [Garantir a integridade dos dados com códigos de hash](../../../standard/security/ensuring-data-integrity-with-hash-codes.md) descreve como você pode gerar e verificar valores de hash.  
  
## <a name="encrypting-configuration-files"></a>Criptografando arquivos de configuração  
 A proteção do acesso à fonte de dados é essencial para a segurança do aplicativo. Uma cadeia de conexão apresentará uma vulnerabilidade potencial se não for protegida. As cadeias de conexão salvas em arquivos de configuração são armazenadas em arquivos XML padrão para os quais o .NET Framework definiu um conjunto comum de elementos. A configuração protegida permite que você criptografe informações confidenciais em um arquivo de configuração. Embora projetado principalmente para aplicativos ASP.NET, a configuração protegida também pode ser usada para criptografar seções de arquivo de configuração em aplicativos do Windows. Para obter mais informações, consulte [Protegendo informações de conexão](protecting-connection-information.md).  
  
## <a name="securing-string-values-in-memory"></a>Protegendo valores de cadeia de caracteres na memória  
 Se um objeto de <xref:System.String> contiver informações confidenciais, como uma senha, um número de cartão de crédito ou dados pessoais, haverá um risco de que as informações possam ser reveladas após serem usadas porque o aplicativo não pode excluir os dados da memória do computador.  
  
 Um <xref:System.String> é imutável; seu valor não pode ser modificado após ter sido criado. As alterações que parecem modificar o valor da cadeia de caracteres realmente criam uma nova instância de um objeto <xref:System.String> na memória, armazenando os dados como texto sem formatação. Além disso, não é possível prever quando as instâncias de cadeia de caracteres serão excluídas da memória. A recuperação de memória com cadeias de caracteres não é determinística com a coleta de lixo do .NET. Você deve evitar usar as classes <xref:System.String> e <xref:System.Text.StringBuilder> se seus dados forem verdadeiramente confidenciais.  
  
 A classe <xref:System.Security.SecureString> fornece métodos para criptografar texto usando a DPAPI (API de proteção de dados) na memória. A cadeia de caracteres é excluída da memória quando ela não é mais necessária. Não há nenhum método `ToString` para ler rapidamente o conteúdo de um <xref:System.Security.SecureString>. Você pode inicializar uma nova instância do `SecureString` sem valor ou passando um ponteiro para uma matriz de objetos <xref:System.Char>. Em seguida, você pode usar os vários métodos da classe para trabalhar com a cadeia de caracteres.
  
## <a name="see-also"></a>Veja também

- [Securing ADO.NET Applications](securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)
- [SQL Server Security](./sql/sql-server-security.md) (Segurança do SQL Server)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
