---
title: Privacidade e segurança de dados
ms.date: 03/30/2017
ms.assetid: 46fa5839-adf7-4c7c-bce3-71e941fa7de9
ms.openlocfilehash: ed408cedbd686efd29472f6f7d19ec03390164f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662134"
---
# <a name="privacy-and-data-security"></a>Privacidade e segurança de dados
Protegendo e gerenciamento de informações confidenciais em um aplicativo ADO.NET depende de produtos e tecnologias usadas para criá-lo subjacentes. ADO.NET não fornece serviços para proteger ou criptografar dados diretamente.  
  
## <a name="cryptography-and-hash-codes"></a>Criptografia e códigos Hash  
 As classes no .NET Framework <xref:System.Security.Cryptography> namespace pode ser usado de seus aplicativos ADO.NET para evitar que dados que estão sendo lidos ou modificados por terceiros não autorizados. Algumas classes são wrappers para o Microsoft CryptoAPI não gerenciada, enquanto outras são implementações gerenciadas. O [serviços de criptografia](../../../../docs/standard/security/cryptographic-services.md) tópico fornece uma visão geral da criptografia no .NET Framework, descreve como cryptograph é implementada e como você pode executar tarefas específicas de criptografia.  
  
 Ao contrário da criptografia, que permite que os dados sejam criptografados e, em seguida, descriptografados, o hash de dados é um processo unidirecional. Hash de dados é útil quando você deseja evitar a violação, verificando os dados não foram alterados: dado cadeias de caracteres de entrada idênticas, algoritmos de hash sempre produzem valores de saída idêntica de curto que podem ser comparados facilmente. [Garantindo a integridade dos dados com códigos Hash](../../../../docs/standard/security/ensuring-data-integrity-with-hash-codes.md) descreve como você pode gerar e verificar os valores de hash.  
  
## <a name="encrypting-configuration-files"></a>Criptografando arquivos de configuração  
 A proteção do acesso à fonte de dados é essencial para a segurança do aplicativo. Uma cadeia de conexão apresenta uma vulnerabilidade potencial se não estiver protegida. Cadeias de Conexão salvas em arquivos de configuração são armazenadas em arquivos XML padrão para o qual o .NET Framework definiu um conjunto comum de elementos. Configuração protegida permite que você criptografe informações confidenciais em um arquivo de configuração. Embora projetado principalmente para aplicativos ASP.NET, configuração protegida também pode ser usada para criptografar seções do arquivo de configuração em aplicativos do Windows. Para obter mais informações, consulte [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="securing-string-values-in-memory"></a>Protegendo os valores de cadeia de caracteres na memória  
 Se um <xref:System.String> objeto contém informações confidenciais, como uma senha, o número de cartão de crédito ou dados pessoais, não há um risco de que as informações podem ser reveladas depois que ele é usado porque o aplicativo não é possível excluir os dados da memória do computador.  
  
 Um <xref:System.String> é imutável, seu valor não pode ser modificado depois de ele ter sido criado. As alterações que aparecem para modificar o valor de cadeia de caracteres, na verdade, criam uma nova instância de um <xref:System.String> objeto na memória, armazenamento de dados como texto sem formatação. Além disso, não é possível prever quando as instâncias de cadeia de caracteres serão excluídas da memória. Recuperação de memória com cadeias de caracteres não é determinística com coleta de lixo do .NET. Você deve evitar usar o <xref:System.String> e <xref:System.Text.StringBuilder> classes se seus dados forem realmente confidenciais.  
  
 O <xref:System.Security.SecureString> classe fornece métodos para criptografar o texto usando a API de proteção de dados (DPAPI) na memória. A cadeia de caracteres, em seguida, é excluída da memória quando ele não for mais necessário. Não há nenhuma `ToString` método para ler rapidamente o conteúdo de um <xref:System.Security.SecureString>. Você pode inicializar uma nova instância da `SecureString` sem nenhum valor ou ao passar um ponteiro para uma matriz de <xref:System.Char> objetos. Em seguida, você pode usar os vários métodos da classe para trabalhar com a cadeia de caracteres. Para obter mais informações, baixe o [aplicativo de exemplo de SecureString](https://go.microsoft.com/fwlink/?LinkId=120418), que demonstra como usar o `SecureString` classe.  
  
## <a name="see-also"></a>Consulte também
- [Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)
- [SQL Server Security](../../../../docs/framework/data/adonet/sql/sql-server-security.md) (Segurança do SQL Server)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
