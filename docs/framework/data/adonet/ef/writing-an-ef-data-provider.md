---
title: Escrevendo um provedor de dados do Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 29aa8cb1c6b31d9ada6b01860d76bcf03d37416c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854167"
---
# <a name="writing-an-entity-framework-data-provider"></a>Escrevendo um provedor de dados do Entity Framework
Esta seção discute como gravar um provedor de Entity Framework para dar suporte a uma fonte de dados diferente de SQL Server. O Entity Framework inclui um provedor que oferece suporte a SQL Server.  
  
## <a name="introducing-the-entity-framework-provider-model"></a>Introdução ao modelo de provedor de Entity Framework  
 O Entity Framework é independente de banco de dados e você pode escrever um provedor usando o modelo de provedor ADO.NET para se conectar a um conjunto diversificado de fontes de dados.  
  
 O provedor de dados do Entity Framework (compilado usando o modelo do provedor de dados do ADO.NET) executa as seguintes funções:  
  
- Mapeia tipos primitivos de EDM (Modelo de Dados de Entidade) para os tipos de provedor.  
  
- Expõe funções específicas do provedor.  
  
- Gera comandos específicos do provedor para um determinado DbQueryCommandTree para dar suporte a consultas Entity Framework.  
  
- Gera comandos de atualização específicos do provedor para um determinado DbModificationCommandTree para dar suporte a atualizações por meio do Entity Framework.  
  
- Expõe arquivos de mapeamento para a definição do esquema de armazenamento, para dar suporte à geração de um modelo baseado em um banco de dados.  
  
- Expõe metadados (tabelas e exibições, por exemplo) por meio de um modelo conceitual.  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")  
  
## <a name="sample"></a>Amostra  
 Consulte o [provedor de exemplo Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) para obter um exemplo de um provedor de Entity Framework que dá suporte a uma fonte de dados diferente de SQL Server.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Geração de SQL](sql-generation.md)  
  
 [Geração de SQL de modificação](modification-sql-generation.md)  
  
 [Especificação do manifesto do provedor](provider-manifest-specification.md)  
  
## <a name="see-also"></a>Consulte também

- [Trabalhando com Provedores de Dados](working-with-data-providers.md)
