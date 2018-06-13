---
title: Migrar seus bancos de dados relacionais para o azure
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | migrar seus bancos de dados relacionais para o azure
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: fe1bf5820c2306beb380749b34d5a56964e016e4
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956079"
---
# <a name="migrate-your-relational-databases-to-azure"></a>Migrar seus bancos de dados relacionais para o azure

Visão: O Azure oferece a migração de banco de dados mais abrangente.

No Azure, você pode migrar os servidores de banco de dados diretamente para as VMs de IaaS (puro comparar e deslocar) ou você pode migrar para o banco de dados SQL Azure, para benefícios adicionais. Banco de dados do SQL Azure oferece as opções de (DBaaS) de completo banco de dados-como um serviço e instância gerenciada. Figura 3-1 mostra o banco de dados relacional vários caminhos de migração disponíveis no Azure.

![Caminhos de migração do banco de dados no Azure](./media/image3-1.png)

> **Figura 3-1.** Caminhos de migração do banco de dados no Azure

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Quando a migração para gerenciados instância do banco de dados do SQL Azure

Na maioria dos casos, a instância gerenciada do Azure SQL Database será a melhor opção deve ser considerado ao migrar seus dados para o Azure. Se você estiver migrando bancos de dados do SQL Server e precisar quase 100% garantia que você não precisará Refaça a arquitetura de seu aplicativo ou fazer alterações em seus dados ou o código de acesso a dados, escolha o recurso de instância gerenciada do banco de dados do SQL Azure.

Instância de gerenciados do banco de dados de SQL do Azure é a melhor opção se você tiver requisitos adicionais para a funcionalidade de nível de instância do SQL Server ou requisitos de isolamento, além dos recursos fornecidos em um padrão do Azure SQL Database (modelo de banco de dados único). Esse último é a escolha mais orientado a PaaS, mas ele não oferece os mesmos recursos que um SQL server tradicional. Migração pode superfície frictions.

Por exemplo, uma organização que investiu profundo de recursos de nível de instância do SQL Server pode se beneficiar da migração para a instância gerenciada do SQL. Exemplos de recursos do nível de instância do SQL Server incluem SQL integração common language runtime (CLR), SQL Server Agent e consultar dados. Suporte para esses recursos não está disponível no padrão do Azure SQL Database (um modelo de banco de dados único).

Uma organização que opera em um setor altamente regulamentado e que precisam manter o isolamento para fins de segurança, também pode se beneficiar escolhendo o modelo de instância gerenciada do SQL.

Instância gerenciada no banco de dados SQL tem as seguintes características:

- Isolamento de segurança por meio da rede Virtual do Azure

- Superfície compatibilidade de aplicativos, com estes recursos:

  - SQL Server Agent e o SQL Server Profiler

  - Replicação de referências e consultas de SQL CLR, bancos de dados, change data capture (CDC) e do Service Broker

- Até 35 TB de tamanho de banco de dados

- Migração de tempo de inatividade mínimo, com estes recursos:

  - Serviço de migração do banco de dados do Azure

  - Envio de logs, restauração e backup nativo

Com esses recursos, ao migrar bancos de dados de aplicativo existentes para o banco de dados SQL Azure, o modelo de instância gerenciada oferece quase 100% dos benefícios de Paas para o SQL Server. Instância gerenciada é um ambiente de SQL Server onde você continuar a usar os recursos de nível de instância sem alterar o design do aplicativo.

Instância gerenciada provavelmente é a melhor opção para empresas que atualmente estão usando o SQL Server e que necessitam de flexibilidade a segurança de rede na nuvem. É como ter uma rede virtual privada para bancos de dados SQL.

## <a name="when-to-migrate-to-azure-sql-database"></a>Quando a migração para o banco de dados do SQL Azure

Conforme mencionado, o banco de dados padrão do SQL Azure é um DBaaS totalmente gerenciado, relacionais. Banco de dados SQL no momento gerencia milhões de bancos de dados de produção, em data 38 centers, em todo o mundo. Ele dá suporte a uma ampla gama de aplicativos e cargas de trabalho do gerenciamento de dados transacionais simples, para direcionar os aplicativos com uso intensivo de dados de missão crítica que exigem processamento avançado de dados em uma escala global.

Devido a seus recursos completos de PaaS, melhor preços- e, finalmente, reduzir o custo-você deve mover o banco de dados do SQL Azure padrão sua escolha"por padrão" Se você tiver um aplicativo que usa basic, standard bancos de dados SQL e nenhum recurso de instância adicional. Não há suporte para recursos do SQL Server como a integração CLR do SQL, SQL Server Agent e consulta de bancos de dados no banco de dados padrão do SQL Azure. Esses recursos estão disponíveis apenas no modelo de instância gerenciada do Azure SQL Database.

Banco de dados do SQL Azure é o serviço de banco de dados de nuvem apenas inteligente que é criado para os desenvolvedores de aplicativos. Também é o único serviço de banco de dados de nuvem que pode ser expandido em rapidamente, sem tempo de inatividade, para ajudá-lo a fornecer com eficiência os aplicativos multilocatários. Por fim, o banco de dados do Azure SQL deixa mais tempo para inovar e ele reduz o tempo de mercado. Você pode criar aplicativos seguros e se conectar ao banco de dados SQL usando as linguagens e plataformas que você preferir.

Banco de dados do SQL Azure oferece os seguintes benefícios:

- Inteligência interna (aprendizado de máquina) que aprende e se adapta ao seu aplicativo

- Provisionamento do banco de dados sob demanda

- Um intervalo de ofertas para todas as cargas de trabalho

- disponibilidade de 99,99% SLA, zero manutenção

- Serviços de replicação geográfica e restauração para proteção de dados

- Ponto de banco de dados do SQL Azure no recurso de restauração pontual

- Compatibilidade com o SQL Server 2016, incluindo híbrida e migração

Banco de dados padrão do SQL Azure está mais próximo PaaS de gerenciado instância do banco de dados do SQL Azure. Preferir banco de dados padrão do SQL Azure, porque você terá mais benefícios de uma nuvem gerenciada. No entanto, o banco de dados do Azure SQL tem algumas das principais diferenças de regular e instâncias do SQL Server local. Dependendo de requisitos de banco de dados do seu aplicativo existente e seus requisitos de empresa e políticas, talvez não seja a melhor opção quando você estiver planejando a migração para a nuvem.

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>Ao mover o RDBMS original para uma VM (IaaS)

Uma das suas opções de migração é mover seu original sistema de gerenciamento do banco de dados relacional (RDBMS), inclusive Oracle, IBM DB2, MySQL, PostgreSQL ou SQL Server, para um servidor semelhante que está em execução em uma VM do Azure. Se você tiver aplicativos existentes que exigem a migração mais rápida para a nuvem com alterações mínimas ou nenhuma alteração em todos os, uma migração direta para IaaS na nuvem pode ser uma opção razoável. Ele não pode ser a melhor maneira de aproveitar os benefícios de todos os da nuvem, mas provavelmente é o caminho inicial mais rápido.

Atualmente, o Microsoft Azure suporta até [331 servidores de banco de dados diferente](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/category/databases?page=1&subcategories=databases-all) implantadas como VMs de IaaS. Isso inclui RDBMS populares como o SQL Server, Oracle, MySQL, PostgreSQL e IBM DB2 e muitos outros bancos de dados NoSQL como MongoDB, Cassandra, DataStax, MariaDB e Cloudera.

> [!NOTE]
> Embora mover seu RDBMS para uma VM do Azure pode ser a maneira mais rápida para migrar seus dados para a nuvem (porque IaaS), essa abordagem requer um investimento significativo em suas equipes de TI (administradores de banco de dados e os profissionais de TI). Equipes de empresa precisam ser capaz de configurar e gerenciar a alta disponibilidade, recuperação de desastres e a aplicação de patch do SQL Server. Esse contexto também precisa de um ambiente personalizado, com direitos administrativos completos.

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>Quando migrar para o SQL Server como uma VM (IaaS)

Pode haver alguns casos em que você ainda precisa migrar para o SQL Server como uma VM regular. Um cenário de exemplo é se você precisa usar o SQL Server Reporting Services. Na maioria dos casos, porém, gerenciados instância do banco de dados do SQL Azure pode fornecer tudo o que você precisa para migrar dos servidores do SQL local, para a migração para uma VM do SQL Server deve ser o último recurso para experimentar.

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Use o serviço de migração de banco de dados do Azure para migrar seus bancos de dados relacionais para o Azure 

Você pode usar o serviço de migração de banco de dados do Azure para migrar bancos de dados relacionais, como o SQL Server, Oracle e MySQL para o Azure, se seu banco de dados de destino é o banco de dados do SQL Azure, gerenciados instância do banco de dados do SQL Azure ou SQL Server em uma VM do Azure.

O fluxo de trabalho automatizado, com os relatórios de avaliação, orientará você durante as alterações que você precisa fazer antes de migrar o banco de dados. Quando você estiver pronto, o serviço migra o banco de dados de origem para o Azure.

Sempre que alterar um RDBMS original, você precisará testar novamente. Você também pode precisar alterar a frases SQL ou código de mapeamento relacional de objeto (ORM) em seu aplicativo, dependendo dos resultados de testes.

Se você tiver qualquer outro banco de dados (por exemplo, IBM DB2) e você optar por uma abordagem de comparar e deslocar, deseja continuar usando esses bancos de dados como VMs de IaaS no Azure, a menos que você pretende executar uma migração de dados mais complexa. Migração de dados mais complexa exige esforço adicional, pois você poderia ser migrando para um tipo de banco de dados diferente com o novo esquema e as bibliotecas de programação diferentes.

Para saber como migrar bancos de dados usando o serviço de migração de banco de dados do Azure, consulte [Get para a nuvem mais rápida com gerenciado instância do banco de dados do SQL Azure e o serviço de migração de banco de dados do Azure](https://channel9.msdn.com/Events/Build/2017/P4008).

## <a name="additional-resources"></a>Recursos adicionais

- **Escolha uma opção do SQL Server de nuvem: banco de dados do SQL do Azure (PaaS) ou o SQL Server na VM do Azure (IaaS)**

    [https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas)

- **Obter para a nuvem mais rápida com o serviço de migração do banco de dados e instância gerenciada do Azure SQL DB**

    [https://channel9.msdn.com/Events/Build/2017/P4008](https://channel9.msdn.com/Events/Build/2017/P4008)

- **Migração de banco de dados do SQL Server para o banco de dados SQL na nuvem**

    [https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate](https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate)

- **Banco de Dados SQL do Azure**

    [https://azure.microsoft.com/services/sql-database/?v=16.50](https://azure.microsoft.com/services/sql-database/?v=16.50)

- **SQL Server em máquinas virtuais**

    [https://azure.microsoft.com/services/virtual-machines/sql-server/](https://azure.microsoft.com/services/virtual-machines/sql-server/)

>[!div class="step-by-step"]
[Anterior](lift-and-shift-existing-apps-azure-iaas.md)
[Próximo](modernize-existing-apps-to-cloud-optimized/index.md)