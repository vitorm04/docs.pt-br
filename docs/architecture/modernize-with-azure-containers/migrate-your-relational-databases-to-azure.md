---
title: Migre seus bancos de dados relacionais para o Azul
description: Modernizar aplicativos .NET existentes com contêineres Azure Cloud e Windows | migrar seus bancos de dados relacionais para o azul
ms.date: 04/28/2018
ms.openlocfilehash: efd1548c3f74fc27450f4949d71a1c4d61907ba5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73093621"
---
# <a name="migrate-your-relational-databases-to-azure"></a>Migre seus bancos de dados relacionais para o Azul

Visão: O Azure oferece a migração de banco de dados mais abrangente.

No Azure, você pode migrar seus servidores de banco de dados diretamente para VMs IaaS (elevador e turno puro), ou você pode migrar para o Banco de Dados SQL do Azure, para obter benefícios adicionais. O Azure SQL Database oferece opções de instância gerenciada e banco de dados completo como serviço (DBaaS). A Figura 3-1 mostra os múltiplos caminhos de migração de banco de dados relacionais disponíveis no Azure.

![Caminhos de migração de banco de dados no Azure](./media/image3-1.png)

**Figura 3-1.** Caminhos de migração de banco de dados no Azure

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Quando migrar para a instância gerenciada do banco de dados SQL do Azure

Na maioria dos casos, a instância gerenciada do banco de dados Azure SQL será a melhor opção a considerar quando você migrar seus dados para o Azure. Se você estiver migrando bancos de dados do SQL Server e precisar de quase 100% de garantia de que não precisará reprojetar seu aplicativo ou fazer alterações em seus dados ou código de acesso de dados, escolha o recurso Instância Gerenciada do Banco de Dados SQL do Azure.

A instância gerenciada do banco de dados Do Azure SQL é a melhor opção se você tiver requisitos adicionais para a funcionalidade de nível de instância do SQL Server ou requisitos de isolamento além dos recursos fornecidos em um banco de dados Azure SQL padrão (modelo de banco de dados único). Esta última é a escolha mais orientada para o PaaS, mas não oferece os mesmos recursos de um servidor SQL tradicional. A migração pode surgir atritos.

Por exemplo, uma organização que fez investimentos profundos em recursos de SQL Server de nível de instância se beneficiaria da migração para a Instância Gerenciada sql. Exemplos de recursos de SQL Server em nível de instância incluem integração clr (common language runtime) de idioma comum SQL, agente de servidor SQL e consulta entre bancos de dados. O suporte para esses recursos não está disponível no Banco de Dados SQL padrão do Azure (um modelo de banco de dados único).

Uma organização que opera em uma indústria altamente regulamentada e que precisa manter o isolamento para fins de segurança, também pode se beneficiar da escolha do modelo SQL Managed Instance.

Instance Gerenciado no Banco de Dados SQL do Azure tem as seguintes características:

- Isolamento de segurança através da Rede Virtual Azure

- Compatibilidade da superfície do aplicativo, com esses recursos:

  - Agente de servidor SQL e profiler do servidor SQL

  - Referências e consultas entre bancos de dados, SQL CLR, replicação, captura de dados de alteração (CDC) e Service Broker

- Tamanhos de banco de dados de até 35 TB

- Migração de tempo mínimo de inatividade, com essas características:

  - Serviço de Migração de Banco de Dados do Azure

  - Backup e restauração nativas e envio de log

Com esses recursos, quando você migra os bancos de dados de aplicativos existentes para o Azure SQL Database, o modelo Instância Gerenciada oferece quase 100% dos benefícios do PaaS para o SQL Server. Instance Managed é um ambiente SQL Server onde você continua usando recursos de nível de instância sem alterar o design do aplicativo.

A Instância Gerenciada é provavelmente a mais adequada para empresas que atualmente estão usando o SQL Server, e que requerem flexibilidade na segurança de sua rede na nuvem. É como ter uma rede virtual privada para seus bancos de dados SQL.

## <a name="when-to-migrate-to-azure-sql-database"></a>Quando migrar para o Banco de Dados SQL do Azure

Como mencionado, o Banco de Dados SQL padrão do Azure é um DBaaS totalmente gerenciado e relacional. O SQL Database atualmente gerencia milhões de bancos de dados de produção, em 38 data centers, em todo o mundo. Ele suporta uma ampla gama de aplicativos e cargas de trabalho, desde o gerenciamento de dados transacionais simples até a condução dos aplicativos mais intensivos em dados e de missão crítica que requerem processamento avançado de dados em escala global.

Devido aos seus recursos completos do PaaS, preços melhores e, finalmente, menores custos, você deve passar para o Banco de Dados SQL padrão como sua "escolha por padrão" se você tiver um aplicativo que usa bancos de dados SQL básicos e padrão e nenhum recurso de instância adicional. Os recursos do SQL Server, como integração SQL CLR, SQL Server Agent e consulta de banco de dados cruzado, não são suportados no banco de dados SQL padrão. Esses recursos estão disponíveis apenas no modelo Azure SQL Database Managed Instance.

O Azure SQL Database é o único serviço inteligente de banco de dados em nuvem que é construído para desenvolvedores de aplicativos. É também o único serviço de banco de dados em nuvem que escala em tempo real, sem tempo de inatividade, para ajudá-lo a fornecer aplicativos multilocatários com eficiência. Em última análise, o Banco de Dados SQL do Azure deixa mais tempo para inovar, e isso acelera seu tempo de mercado. Você pode criar aplicativos seguros e se conectar ao seu banco de dados SQL usando os idiomas e plataformas que preferir.

O Banco de Dados SQL do Azure oferece os seguintes benefícios:

- Inteligência incorporada (aprendizado de máquina) que aprende e se adapta ao seu aplicativo

- Provisionamento de banco de dados demanda

- Uma gama de ofertas, para todas as cargas de trabalho

- 99,99% de disponibilidade SLA, manutenção zero

- Serviços de replicação e restauração de geo-replicação para proteção de dados

- Recurso de restauração de tempo do Azure SQL Database Point in Time

- Compatibilidade com o SQL Server 2016, incluindo híbrido e migração

O banco de dados Azure SQL padrão está mais próximo do PaaS do que o Azure SQL Database Managed Instance. Prefira o banco de dados SQL padrão do Azure porque você terá mais benefícios de uma nuvem gerenciada. No entanto, o Banco de Dados SQL do Azure tem algumas diferenças importantes em relação às instâncias regulares e locais do SQL Server. Dependendo dos requisitos de banco de dados do aplicativo existentes e dos requisitos e políticas da empresa, pode não ser a melhor escolha quando você está planejando sua migração para a nuvem.

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>Quando mover seu RDBMS original para um VM (IaaS)

Uma de suas opções de migração é mover seu sistema de gerenciamento de banco de dados relacional original (RDBMS), incluindo Oracle, IBM DB2, MySQL, PostgreSQL ou SQL Server, para um servidor semelhante que está sendo executado em um VM do Azure. Se você tiver aplicativos existentes que requerem a migração mais rápida para a nuvem com alterações mínimas ou nenhuma alteração, uma migração direta para IaaS na nuvem pode ser uma opção justa. Pode não ser a melhor maneira de aproveitar todos os benefícios da nuvem, mas provavelmente é o caminho inicial mais rápido.

Atualmente, o Microsoft Azure suporta até [331 servidores de banco de dados diferentes implantados](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all) como VMs IaaS. Estes incluem rdbms populares como SQL Server, Oracle, MySQL, PostgreSQL e IBM DB2, e muitos outros bancos de dados NoSQL como MongoDB, Cassandra, DataStax, MariaDB e Cloudera.

> [!NOTE]
> Embora mover seu RDBMS para uma VM do Azure possa ser a maneira mais rápida de migrar seus dados para a nuvem (por ser IaaS), essa abordagem requer um investimento significativo em suas equipes de TI (administradores de banco de dados e profissionais de TI). As equipes corporativas precisam ser capazes de configurar e gerenciar alta disponibilidade, recuperação de desastres e patches para o SQL Server. Esse contexto também precisa de um ambiente personalizado, com plenos direitos administrativos.

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>Quando migrar para o SQL Server como Um VM (IaaS)

Pode haver alguns casos em que você ainda precisa migrar para o SQL Server como uma VM regular. Um cenário de exemplo é se você precisar usar os Serviços de Relatórios do Servidor SQL. Na maioria dos casos, porém, a Instância Gerenciada do Banco de Dados SQL do Azure pode fornecer tudo o que você precisa para migrar de servidores SQL no local, de modo que a migração para um VM do SQL Server deve ser seu último recurso para tentar.

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Use o Serviço de Migração de Banco de Dados do Azure para migrar seus bancos de dados relacionais para o Azure

Você pode usar o Azure Database Migration Service para migrar bancos de dados relacionais como SQL Server, Oracle e MySQL para o Azure, quer seu banco de dados de destino seja o Banco de Dados Azure SQL, a instância gerenciada do banco de dados Do Azure SQL ou o SQL Server em um VM do Azure.

O fluxo de trabalho automatizado, com relatórios de avaliação, orienta você sobre as alterações que você precisa fazer antes de migrar o banco de dados. Quando você estiver pronto, o serviço migra o banco de dados de origem para o Azure.

Sempre que você mudar um RDBMS original, você pode precisar testar novamente. Você também pode precisar alterar as sentenças SQL ou o código ORM (Object-Relational Mapping, mapeamento de objeto-relacional) em seu aplicativo, dependendo dos resultados dos testes.

Se você tiver qualquer outro banco de dados (por exemplo, IBM DB2) e optar por uma abordagem de elevação e mudança, você pode querer continuar usando esses bancos de dados como VMs IaaS no Azure, a menos que você esteja disposto a realizar uma migração de dados mais complexa. Uma migração de dados mais complexa exigirá esforço adicional porque você estaria migrando para um tipo de banco de dados diferente com novos esquemas e diferentes bibliotecas de programação.

Para saber como migrar bancos de dados usando o Azure Database Migration Service, consulte [Chegar à nuvem mais rapidamente com a instância gerenciada do banco de dados Azure SQL e o Serviço de Migração de Banco de Dados Do Azure.](https://channel9.msdn.com/Events/Build/2017/P4008)

## <a name="additional-resources"></a>Recursos adicionais

- **Escolha uma opção de SQL Server em nuvem: Banco de dados SQL (PaaS) ou SQL Server no Azure VM (IaaS)**

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- **Chegar à nuvem mais rápido com o Azure SQL DB Managed Instance and Database Migration Service**

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- **Migração de banco de dados do SQL Server para o Banco de Dados SQL na nuvem**

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- **Banco de dados SQL do Azure**

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- **SQL Server em máquinas virtuais**

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> [Próximo](lift-and-shift-existing-apps-azure-iaas.md)
> [anterior](modernize-existing-apps-to-cloud-optimized/index.md) <!-- Next Chapter -->
