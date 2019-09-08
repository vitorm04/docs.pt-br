---
title: Assinando procedimentos armazenados no SQL Server
ms.date: 01/05/2018
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
ms.openlocfilehash: 8dc62527be7273d3ce3222d4d261b81bc40b1e19
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791803"
---
# <a name="signing-stored-procedures-in-sql-server"></a>Assinando procedimentos armazenados no SQL Server

Uma assinatura digital é um resumo dos dados criptografados com a chave privada do assinante. A chave privada garante que a assinatura digital seja exclusiva de seu portador ou proprietário. Você pode assinar procedimentos armazenados, funções (exceto para funções com valor de tabela embutida), gatilhos e assemblies.

Você pode assinar um procedimento armazenado com um certificado ou uma chave assimétrica. Isso é criado para cenários quando as permissões não podem ser herdadas pelo encadeamento de propriedade ou quando a cadeia de propriedade é quebrada, como SQL dinâmico. Em seguida, você pode criar um usuário mapeado para o certificado, concedendo permissões de usuário de certificado nos objetos que o procedimento armazenado precisa acessar.

Você também pode criar um logon mapeado para o mesmo certificado e, em seguida, conceder permissões de nível de servidor necessárias para esse logon ou adicionar o logon a uma ou mais das funções de servidor fixas. Isso é projetado para evitar a habilitação da configuração do `TRUSTWORTHY` banco de dados para cenários nos quais são necessárias permissões de nível superior.

Quando o procedimento armazenado é executado, SQL Server combina as permissões do usuário do certificado e/ou o logon com aqueles do chamador. Ao contrário `EXECUTE AS` da cláusula, ele não altera o contexto de execução do procedimento. As funções internas que retornam o logon e os nomes de usuário retornam o nome do chamador, não o nome do usuário do certificado.

## <a name="creating-certificates"></a>Criando certificados

Quando você assina um procedimento armazenado com um certificado ou uma chave assimétrica, um resumo de dados que consiste no hash criptografado do código de procedimento armazenado, juntamente com o usuário execute-as, é criado usando a chave privada. Em tempo de execução, o resumo dos dados é criptografado com a chave pública e comparado com o valor de hash do procedimento armazenado. Alterar o usuário executar como invalida o valor de hash para que a assinatura digital não corresponda mais. A modificação do procedimento armazenado descarta totalmente a assinatura, o que impede que alguém que não tenha acesso à chave privada altere o código do procedimento armazenado. Em ambos os casos, você deve assinar novamente o procedimento sempre que alterar o código ou o usuário executar como.

Há duas etapas necessárias envolvidas na assinatura de um módulo:

1. Criar um certificado usando a instrução Transact-SQL `CREATE CERTIFICATE [certificateName]`. Essa instrução tem várias opções para definir uma data inicial e final e uma senha. A data de validade padrão é de um ano.

1. Assinar o procedimento armazenado com o certificado usando a instrução Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]`.

Depois que o módulo tiver sido assinado, uma ou mais entidades de segurança precisarão ser criadas para manter as permissões adicionais que devem ser associadas ao certificado.

Se o módulo precisar de permissões adicionais no nível do banco de dados:

1. Crie um usuário de banco de dados associado ao certificado usando a instrução Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]`. Esse usuário existe somente no banco de dados e não está associado a um logon, a menos que um logon também tenha sido criado a partir desse mesmo certificado.

1. Conceda ao usuário do certificado as permissões de nível de banco de dados necessárias.

Se o módulo precisar de permissões adicionais no nível do servidor:

1. Copie o certificado no banco `master` de dados.

1. Crie um logon associado a esse certificado usando a instrução Transact- `CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]` SQL.

1. Conceda ao certificado logon as permissões necessárias no nível do servidor.

> [!NOTE]
> Um certificado não pode conceder permissões a um usuário que tem permissões revogadas usando a instrução DENY. DENY sempre terá precedência sobre GRANT, impedindo que o chamador herde as permissões concedidas ao usuário do certificado.

## <a name="external-resources"></a>Recursos externos

Para obter mais informações, consulte os seguintes recursos.

|Recurso|Descrição|
|--------------|-----------------|
|Manuais Online do SQL Server de [entrada de módulo](https://go.microsoft.com/fwlink/?LinkId=98590)|Descreve a assinatura do módulo, fornecendo um cenário de exemplo e links para tópicos relevantes do Transact-SQL.|
|[Assinando procedimentos armazenados com um certificado](/sql/relational-databases/tutorial-signing-stored-procedures-with-a-certificate) no manuais online do SQL Server|Fornece um tutorial para assinar um procedimento armazenado com um certificado.|

## <a name="see-also"></a>Consulte também

- [Securing ADO.NET Applications](../securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)
- [Visão geral de segurança do SQL Server](overview-of-sql-server-security.md)
- [Cenários de segurança do aplicativo no SQL Server](application-security-scenarios-in-sql-server.md)
- [Gerenciando permissões com procedimentos armazenados no SQL Server](managing-permissions-with-stored-procedures-in-sql-server.md)
- [Escrevendo SQL dinâmico seguro no SQL Server](writing-secure-dynamic-sql-in-sql-server.md)
- [Personalizando permissões com representação no SQL Server](customizing-permissions-with-impersonation-in-sql-server.md)
- [Modificando dados com procedimentos armazenados](../modifying-data-with-stored-procedures.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
