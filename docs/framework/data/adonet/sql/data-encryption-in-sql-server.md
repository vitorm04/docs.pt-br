---
title: Criptografia de dados no SQL Server
ms.date: 03/30/2017
ms.assetid: 83b992f7-b351-4678-b4b9-f4ffd58134cc
ms.openlocfilehash: 1acb720b8a4f8beb27bb1a5236efdb6f2bb44383
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102161"
---
# <a name="data-encryption-in-sql-server"></a>Criptografia de dados no SQL Server
O SQL Server fornece funções para criptografar e descriptografar dados usando um certificado, uma chave assimétrica ou uma chave simétrica. Ele gerencia todos eles em um repositório de certificados interno. O repositório usa uma hierarquia de criptografia que protege os certificados e as chaves em um nível com a camada acima deles na hierarquia. Essa área de recurso do SQL Server é chamada Armazenamento Secreto.  
  
 O modo mais rápido de criptografia suportado por funções de criptografia é criptografia de chave simétrica. Este modo é apropriado para tratar grandes volumes de dados. As chaves simétricas podem ser criptografadas por certificados, senhas ou outras chaves simétricas.  
  
## <a name="keys-and-algorithms"></a>Chaves e algoritmos  
 O SQL Server oferece suporte a vários algoritmos de criptografia de chave simétrica, incluindo DES, Triple DES, RC2, RC4, RC4 de 128 bits, DESX, AES de 128 bits, AES de 192 bits e AES de 256 bits. Os algoritmos são implementados usando a API de criptografia do Windows.  
  
 No escopo de uma conexão de banco de dados, o SQL Server pode manter várias chaves simétricas abertas. Uma chave aberta é recuperada do repositório e está disponível para descriptografar dados. Quando uma parte de dados é descriptografada, não há necessidade de especificar a chave simétrica a ser usada. Cada valor criptografado contém o identificador da chave (GUID) da chave usada para criptografa. O mecanismo corresponde ao fluxo de bytes criptografado com uma chave simétrica aberta, se a chave correta tiver sido descriptografada e estiver aberta. Essa chave é usada para executar a descriptografia e retornar os dados. Se a chave correta não estiver aberta, NULL será retornado.  
  
 Para obter um exemplo que mostra como trabalhar com dados criptografados em um banco de dados, consulte [criptografar uma coluna de dados](/sql/relational-databases/security/encryption/encrypt-a-column-of-data).
  
## <a name="external-resources"></a>Recursos externos  
 Para obter mais informações sobre criptografia de dados, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|-|-|  
|[Criptografia do SQL Server](/sql/relational-databases/security/encryption/sql-server-encryption)|Fornece uma visão geral de criptografia no SQL Server. Este tópico inclui links para artigos adicionais.|  
|[Hierarquia de criptografia](/sql/relational-databases/security/encryption/encryption-hierarchy)|Fornece uma visão geral de criptografia no SQL Server. Este tópico fornece links para artigos adicionais.|  
  
## <a name="see-also"></a>Consulte também

- [Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)
- [Cenários de segurança do aplicativo no SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Autenticação no SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)
- [Servidor e funções de banco de dados no SQL Server](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)
- [Propriedade e separação do esquema de usuário no SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)
- [Autorização e permissões no SQL Server](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
