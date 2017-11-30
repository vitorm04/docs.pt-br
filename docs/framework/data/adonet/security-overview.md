---
title: "Segurança 2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33e09965-61d5-48cc-9e8c-3b047cc4f194
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d7288eeffeb642d1e897e11153802633d71747bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="security-overview"></a>Visão geral de segurança
Proteger um aplicativo é um processo contínuo. Nunca será um ponto em que um desenvolvedor pode garantir que um aplicativo é seguro de todos os ataques, porque é impossível prever quais tipos de novas tecnologias de ataques futuros causará. Por outro lado, só porque ninguém tem falhas de segurança ainda descobertos (ou publicado) em um sistema não significa que nenhum existem ou podem existir. Você precisa planejar a segurança durante a fase de design do projeto, bem como para planejar como segurança será mantida durante o tempo de vida do aplicativo.  
  
## <a name="design-for-security"></a>Design de segurança  
 Um dos maiores problemas no desenvolvimento de aplicativos seguros é que a segurança é geralmente prioridade, algo implemente depois de um projeto é a conclusão de código. Não criar segurança em um aplicativo desde o início leva a aplicativos não seguros porque tem pouco a que torna um aplicativo seguro.  
  
 Implementação de segurança do último minuto leva a mais bugs, como quebras de software em novas restrições ou precisa ser reescrito para acomodar a funcionalidade inesperada. Cada linha de código revisado contém a possibilidade de introduzir um novo bug. Por esse motivo, você deve considerar a segurança no início do processo de desenvolvimento, para que ele possa continuar em conjunto com o desenvolvimento de novos recursos.  
  
### <a name="threat-modeling"></a>Modelagem de ameaças  
 Você não pode proteger o sistema contra ataques a menos que você compreenda todos os ataques potenciais que está exposta a. O processo de avaliação de ameaças de segurança, denominado *a modelagem de ameaças*, é necessário para determinar a probabilidade e ramificações de violações de segurança em seu aplicativo ADO.NET.  
  
 Modelagem de ameaças é composta de três etapas de alto nível: Noções básicas sobre o modo de exibição do adversário, que caracterizam a segurança do sistema e determinar as ameaças.  
  
 Modelagem de ameaças é uma abordagem iterativa para avaliação de vulnerabilidades em seu aplicativo encontrar aquelas que são mais perigoso, pois expõem os dados mais confidenciais. Depois que você identificar as vulnerabilidades, você classificá-las em ordem de gravidade e cria um conjunto de prioridade de contramedidas para as ameaças do contador.  
  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|O [modelagem de ameaça](http://go.microsoft.com/fwlink/?LinkId=98353) site MSDN Security Developer Center|Os recursos nesta página ajudarão você a entender a processo de modelagem de ameaças e criar modelos de ameaças que você pode usar para proteger seus aplicativos|  
  
## <a name="the-principle-of-least-privilege"></a>O princípio de privilégios mínimos  
 Quando você projeta, cria e implanta seu aplicativo, você deve supor que seu aplicativo será atacado. Geralmente, esses ataques provenientes código mal-intencionado que é executado com as permissões do usuário que executa o código. Outros podem ser obtidos com o código bem intencionado que tenha sido explorado por um invasor. Ao planejar a segurança, sempre assuma o que pior cenário ocorrerá.  
  
 É uma medida de contador, que você pode usar tentar colocar tantas proteções ao seu código possível executando com privilégios mínimos. O princípio de menos privilégios diz que qualquer privilégio deve ser concedido para a quantidade mínima de código necessário para a duração mais curta de tempo que é necessário para realizar o trabalho.  
  
 A prática recomendada para a criação de aplicativos seguros é iniciar com nenhuma permissão e, em seguida, adicionar as permissões mais restrito para a tarefa específica que está sendo executada. Por outro lado, começando com todas as permissões e, em seguida, negando individuais que leva a aplicativos não seguros que são difíceis de testar e manter como falhas de segurança podem existir acidentalmente conceda mais permissões do que o necessário.  
  
 Para obter mais informações sobre como proteger seus aplicativos, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Protegendo aplicativos](/visualstudio/ide/securing-applications)|Contém links para tópicos gerais de segurança. Também contém links para tópicos para proteger aplicativos distribuídos, aplicativos Web, aplicativos móveis e aplicativos de desktop.|  
  
## <a name="code-access-security-cas"></a>CAS (Segurança de Acesso do Código)  
 Segurança de acesso ao código (CAS) é um mecanismo que ajuda a limitar o acesso ao código tem a recursos protegidos e operações. No .NET Framework, o ACS executa as seguintes funções:  
  
-   Define as permissões e os conjuntos de permissões que representam o direito de acesso a vários recursos do sistema.  
  
-   Permite aos administradores configurar política de segurança, associando os conjuntos de permissões a grupos de código (grupos de código).  
  
-   Permite que o código solicitar as permissões requeridas para executar, bem como as permissões que seriam úteis para ter e especifica que o código nunca deve ter as permissões.  
  
-   Concede permissões para cada assembly carregado, com base nas permissões solicitadas pelo código e as operações permitidas pela política de segurança.  
  
-   Permite que o código que os chamadores têm permissões específicas de demanda.  
  
-   Permite que o código que os chamadores tenha uma assinatura digital, permitindo que somente os chamadores de uma determinada organização ou um site chamar o código protegido de demanda.  
  
-   Impõe restrições no código em tempo de execução, comparando as permissões concedidas de todos os chamadores na pilha de chamadas para as permissões que os chamadores devem ter.  
  
 Para minimizar a quantidade de danos que podem ocorrer se um ataque tiver êxito, escolha um contexto de segurança de seu código que concede acesso apenas os recursos necessários para executar seu trabalho concluído e não mais.  
  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Segurança de acesso do código e o ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)|Descreve as interações entre ambientes parcialmente confiáveis da perspectiva de um aplicativo ADO.NET, segurança baseada em função e segurança de acesso ao código.|  
|[Segurança de acesso do código](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03)|Contém links para tópicos adicionais que descrevem o CAS no .NET Framework.|  
  
## <a name="database-security"></a>Segurança de banco de dados  
 O princípio de menos privilégios também se aplica à fonte de dados. Algumas diretrizes gerais para segurança de banco de dados incluem:  
  
-   Crie contas com os privilégios mais baixos possíveis.  
  
-   Não permitir que usuários acessem contas administrativas para obter o código em funcionamento.  
  
-   Não retornam mensagens de erro do lado do servidor para aplicativos cliente.  
  
-   Valide todas as entradas no cliente e o servidor.  
  
-   Use comandos parametrizados e evitar instruções SQL dinâmicas.  
  
-   Habilite a segurança de auditoria e log do banco de dados que você está usando para que você será alertado de quaisquer violações de segurança.  
  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[SQL Server Security](../../../../docs/framework/data/adonet/sql/sql-server-security.md) (Segurança do SQL Server)|Fornece uma visão geral de segurança do SQL Server com cenários de aplicativos que fornecem orientação para a criação de aplicativos seguros do ADO.NET destino do SQL Server.|  
|[Recomendações para estratégias de acesso de dados](http://msdn.microsoft.com/en-us/72411f32-d12a-4de8-b961-e54fca7faaf5)|Fornece recomendações para acessar dados e executar operações de banco de dados.|  
  
## <a name="security-policy-and-administration"></a>Diretiva de segurança e administração  
 Administrar incorretamente a política de CAS (segurança) de acesso do código pode criar vulnerabilidades de segurança. Quando um aplicativo é implantado, técnicas para monitorar a segurança devem ser usadas e riscos avaliados como novas ameaças surgem.  
  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[PONTA: Gerenciamento de política de segurança](http://msdn.microsoft.com/en-us/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9)|Fornece informações sobre como criar e administrar a política de segurança.|  
|[PONTA: Práticas recomendadas de política de segurança](http://msdn.microsoft.com/en-us/d49bc4d5-efb7-4caa-a2fe-e4d3cec63c05)|Fornece links que descrevem como administrar a política de segurança.|  
  
## <a name="see-also"></a>Consulte também  
 [Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 [PAVE Security in Native and .NET Framework Code](http://msdn.microsoft.com/en-us/bd61be84-c143-409a-a75a-44253724f784) (PAVE Segurança no código nativo e do .NET Framework)  
 [SQL Server Security](../../../../docs/framework/data/adonet/sql/sql-server-security.md) (Segurança do SQL Server)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
