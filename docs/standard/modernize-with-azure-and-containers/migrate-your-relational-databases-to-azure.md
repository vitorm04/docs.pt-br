---
title: Migrar seus bancos de dados relacionais para o azure
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | migrar seus bancos de dados relacionais para o azure
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 600c47b6b0ccaf704c8e7b638c759e990acaaacf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61812770"
---
# <a name="migrate-your-relational-databases-to-azure"></a>Migrar seus bancos de dados relacionais para o azure

Visão: O Azure oferece a migração de banco de dados mais abrangente.

No Azure, você pode migrar seus servidores de banco de dados diretamente para as VMs de IaaS (puro comparar e deslocar) ou você pode migrar para o banco de dados SQL Azure, para benefícios adicionais. Banco de dados SQL do Azure oferece a instância gerenciada e opções do completo banco de dados-como-um-serviço (DBaaS). Figura 3-1 mostra o banco de dados relacional de vários caminhos de migração disponíveis no Azure.

![Caminhos de migração de banco de dados no Azure](./media/image3-1.png)

> **Figura 3-1.** Caminhos de migração de banco de dados no Azure

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Quando migrar para o banco de dados de instância gerenciada do SQL

Na maioria dos casos, o banco de dados de instância gerenciada do SQL será a melhor opção a considerar ao migrar seus dados para o Azure. Se você estiver migrando bancos de dados do SQL Server e precisar quase 100% assurance que você não precisará refazer a arquitetura de seu aplicativo ou fazer alterações em seus dados ou o código de acesso a dados, escolha o recurso de instância gerenciada do banco de dados SQL.

Instância de gerenciada do banco de dados de SQL do Azure é a melhor opção se você tiver requisitos adicionais para a funcionalidade de nível de instância do SQL Server ou requisitos de isolamento além dos recursos fornecidos em um Azure SQL Database (modelo de banco de dados individual) padrão. Este último é a escolha mais orientado a PaaS, mas ele não oferece os mesmos recursos de um SQL server tradicional. Migração venham a surgir fricções.

Por exemplo, uma organização que já fez investimentos profundos em recursos do nível de instância do SQL Server pode se beneficiar da migração para a instância gerenciada do SQL. Exemplos de recursos do nível de instância do SQL Server incluem SQL integração common language runtime (CLR), SQL Server Agent e consultar bancos de dados. Suporte para esses recursos não está disponível no Azure SQL Database standard (um modelo de banco de dados único).

Uma organização que opera em um setor altamente controlado, e o que precisa manter o isolamento para fins de segurança, também pode se beneficiar escolhendo o modelo de instância gerenciada do SQL.

A instância gerenciada SQL do Azure tem as seguintes características:

- Isolamento de segurança por meio da rede Virtual do Azure

- Superfície compatibilidade de aplicativos, com esses recursos:

  - SQL Server Agent e o SQL Server Profiler

  - Referências e consultas de SQL CLR, a replicação entre bancos de dados, o change data capture (CDC) e o Service Broker

- Tamanhos de banco de dados de até 35 TB

- Migração para o tempo de inatividade mínimo, com esses recursos:

  - Serviço de migração de banco de dados do Azure

  - Envio de logs, restauração e backup nativo

Com esses recursos, ao migrar bancos de dados de aplicativo existente para o banco de dados SQL Azure, o modelo de instância gerenciada oferece quase 100% dos benefícios de PaaS para o SQL Server. Instância gerenciada é um ambiente do SQL Server no qual você continua usando os recursos de nível de instância sem alterar o design do aplicativo.

A instância gerenciada é provavelmente a melhor opção para empresas que atualmente estão usando o SQL Server e requerem a flexibilidade para sua segurança de rede na nuvem. É como ter uma rede virtual privada para seus bancos de dados SQL.

## <a name="when-to-migrate-to-azure-sql-database"></a>Quando migrar para o banco de dados SQL

Conforme mencionado, o banco de dados padrão do SQL Azure é um DBaaS relacional, totalmente gerenciado. Atualmente, o banco de dados SQL gerencia milhões de bancos de dados de produção, em 38 datacenters, em todo o mundo. Ele dá suporte a uma ampla gama de aplicativos e cargas de trabalho do gerenciamento de dados transacionais simples, orientando os aplicativos mais intensivo de dados de missão crítica que exigem processamento de dados avançado em escala global.

Devido a seus recursos de PaaS completos, melhor preço- e, por fim, reduzir o custo-você deve mover o banco de dados do SQL Azure padrão como sua escolha"por padrão" Se você tiver um aplicativo que usa básico, standard bancos de dados SQL e nenhum recurso de instância adicional. Recursos do SQL Server, como integração CLR do SQL, SQL Server Agent e consultar entre bancos de dados não têm suporte no banco de dados do SQL Azure padrão. Esses recursos estão disponíveis apenas no modelo de banco de dados instância gerenciada do SQL.

Banco de dados SQL do Azure é o serviço de banco de dados de nuvem apenas inteligente que é criado para desenvolvedores de aplicativos. Também é o único serviço de banco de dados de nuvem que pode ser dimensionado em imediatamente, sem tempo de inatividade, para ajudá-lo a entregar aplicativos multilocatários com eficiência. Por fim, o banco de dados do Azure SQL deixa mais tempo para inovar e ele reduz o tempo de colocação no mercado. Você pode criar aplicativos seguros e se conectar ao banco de dados SQL usando as linguagens e plataformas que preferir.

Banco de dados SQL do Azure oferece os seguintes benefícios:

- Inteligência interna (aprendizado de máquina) que aprende e se adapta ao seu aplicativo

- Provisionamento de banco de dados sob demanda

- Uma variedade de ofertas para todas as cargas de trabalho

- disponibilidade de 99,99% SLA, manutenção zero

- Serviços de replicação geográfica e restauração para proteção de dados

- Ponto de banco de dados SQL do Azure no recurso de restauração pontual

- Compatibilidade com o SQL Server 2016, incluindo híbrida e migração

O banco de dados do SQL Azure standard é mais próximo do PaaS que banco de dados de instância gerenciada do SQL. Prefira o banco de dados do SQL Azure padrão porque você obterá mais benefícios de uma nuvem gerenciada. No entanto, o banco de dados do Azure SQL tem algumas das principais diferenças de regular e instâncias do SQL Server local. Dependendo de requisitos de banco de dados do seu aplicativo existente e seus requisitos empresariais e políticas, ele não pode ser a melhor opção quando você estiver planejando sua migração para a nuvem.

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>Quando mover seu RDBMS original para uma VM (IaaS)

Uma das suas opções de migração é mover seu original sistema de gerenciamento do banco de dados relacional (RDBMS), inclusive Oracle, IBM DB2, MySQL, PostgreSQL ou SQL Server, para um servidor semelhante que está em execução em uma VM do Azure. Se você tiver aplicativos existentes que requerem a migração mais rápida para a nuvem com alterações mínimas ou nenhuma alteração alguma, uma migração direta para o IaaS na nuvem pode ser uma opção razoável. Pode não ser a melhor maneira de tirar proveito dos benefícios de todos os da nuvem, mas provavelmente é o caminho inicial mais rápido.

Atualmente, o Microsoft Azure suporta até [servidores de banco de dados diferente 331](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/category/databases?page=1&subcategories=databases-all) implantadas como VMs de IaaS. Eles incluem RDBMS populares, como o SQL Server, Oracle, MySQL, PostgreSQL e IBM DB2 e muitos outros bancos de dados NoSQL como o MongoDB, Cassandra, DataStax, MariaDB e Cloudera.

> [!NOTE]
> Embora a movimentação de seu RDBMS para uma VM do Azure pode ser a maneira mais rápida para migrar seus dados para a nuvem (porque ele é IaaS), essa abordagem exige um investimento significativo em suas equipes de TI (administradores de banco de dados e os profissionais de TI). Equipes da empresa precisam ser capaz de configurar e gerenciar a alta disponibilidade, recuperação de desastres e aplicação de patch para o SQL Server. Nesse contexto também precisa de um ambiente personalizado, com direitos administrativos completos.

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>Quando migrar para o SQL Server como uma VM (IaaS)

Pode haver alguns casos em que você ainda precisará migrar para o SQL Server como uma VM regular. Um cenário de exemplo é se você precisa usar o SQL Server Reporting Services. Na maioria dos casos, no entanto, banco de dados de instância gerenciada do SQL pode fornecer tudo o que você precisa para migrar de servidores do SQL local, portanto, a migração para uma VM do SQL Server deve ser o último recurso para tentar.

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Usar o serviço de migração de banco de dados do Azure para migrar seus bancos de dados relacionais para o Azure 

Você pode usar o serviço de migração de banco de dados do Azure para migrar bancos de dados relacionais como SQL Server, Oracle e MySQL para o Azure, se seu banco de dados de destino é o banco de dados SQL, banco de dados de instância gerenciada do SQL ou SQL Server em uma VM do Azure.

O fluxo de trabalho automatizado com o relatório de avaliação, o orienta durante as alterações que você precisa fazer antes de migrar o banco de dados. Quando você estiver pronto, o serviço migra o banco de dados de origem para o Azure.

Sempre que você alterar um RDBMS original, você precisa testar novamente. Você também precisará alterar o código de mapeamento relacional de objeto (ORM) em seu aplicativo, dependendo dos resultados de testes ou frases SQL.

Se você tiver qualquer outro banco de dados (por exemplo, IBM DB2) e você optar por uma abordagem de lift- and -shift, você poderá continuar usando esses bancos de dados como VMs de IaaS no Azure, a menos que você está disposto a executar uma migração de dados mais complexa. Uma migração de dados mais complexa exigirão esforço adicional porque você poderia ser migrando para um tipo de banco de dados diferente com o novo esquema e as bibliotecas de programação diferentes.

Para saber como migrar bancos de dados usando o serviço de migração de banco de dados do Azure, consulte [chegar à nuvem mais rápido com o serviço de migração de banco de dados do Azure e o banco de dados de instância gerenciada do SQL](https://channel9.msdn.com/Events/Build/2017/P4008).

## <a name="additional-resources"></a>Recursos adicionais

- **Escolha uma opção do SQL Server de nuvem: Banco de dados SQL do Azure (PaaS) ou o SQL Server na VM do Azure (IaaS)**

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- **Introdução à nuvem mais rapidamente com a instância gerenciada do Azure SQL DB e o serviço de migração de banco de dados**

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- **Migração de banco de dados do SQL Server para o Banco de Dados SQL na nuvem**

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- **Banco de Dados SQL do Azure**

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- **SQL Server em máquinas virtuais**

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> [Anterior](lift-and-shift-existing-apps-azure-iaas.md)
> [Próximo](modernize-existing-apps-to-cloud-optimized/index.md)
