---
title: Segurança 2
ms.date: 03/30/2017
ms.assetid: 33e09965-61d5-48cc-9e8c-3b047cc4f194
ms.openlocfilehash: 0b5b86aad2365c76351ff748228826ba703223dc
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56091793"
---
# <a name="security-overview"></a>Visão geral de segurança
Proteger um aplicativo é um processo contínuo. Nunca haverá um ponto em que um desenvolvedor pode garantir que um aplicativo está protegido contra todos os ataques, porque é impossível prever quais tipos de novas tecnologias de ataques futuros trará. Por outro lado, apenas porque ninguém tem falhas de segurança ainda descobertos (ou publicado) em um sistema não significa que nenhum existir ou podem existir. Você precisa planejar a segurança durante a fase de design do projeto, bem como para planejar como segurança será mantida durante a vida útil do aplicativo.  
  
## <a name="design-for-security"></a>Design de segurança  
 Um dos maiores problemas no desenvolvimento de aplicativos seguros é que a segurança muitas vezes é uma consideração posterior, algo para implementar depois que um projeto é o código concluído. Não criar segurança em um aplicativo desde o início resulta em aplicativos inseguros porque tem pouca atenção a que torna um aplicativo seguro.  
  
 Implementação de segurança de última hora leva a mais bugs, como quebras de software sob as novas restrições ou precisará ser reescrito para acomodar a funcionalidade imprevista. Todas as linhas de código revisado contém a possibilidade de introduzir um novo bug. Por esse motivo, você deve considerar a segurança no início do processo de desenvolvimento para que ele possa continuar em tandem com o desenvolvimento de novos recursos.  
  
### <a name="threat-modeling"></a>Modelagem de ameaças  
 Você não pode proteger um sistema contra ataques, a menos que você compreenda todos os ataques potenciais que ele é exposto ao. O processo de avaliação de ameaças à segurança, chamado *a modelagem de ameaças*, é necessário para determinar a probabilidade e ramificações de violações de segurança em seu aplicativo ADO.NET.  
  
 A modelagem de ameaças é composta de três etapas de alto nível: Noções básicas sobre o modo de exibição do adversário, caracterizar a segurança do sistema e determinar as ameaças.  
  
 A modelagem de ameaças é uma abordagem iterativa para avaliação de vulnerabilidades em seu aplicativo para encontrar aqueles que são o mais perigoso, pois expõem os dados mais confidenciais. Depois de identificar as vulnerabilidades, você classificá-las em ordem de gravidade e cria um conjunto priorizado de contramedidas para combater as ameaças.  
  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|O [Threat Modeling](https://go.microsoft.com/fwlink/?LinkId=98353) site do MSDN Security Developer Center|Os recursos desta página ajudarão você a entender a processo de modelagem de ameaças e criar modelos de ameaça que você pode usar para proteger seus próprios aplicativos|  
  
## <a name="the-principle-of-least-privilege"></a>O princípio de privilégios mínimos  
 Quando você projeta, compila e implanta seu aplicativo, você deve supor que seu aplicativo será ser atacado. Geralmente esses ataques provenientes de um código mal-intencionado que é executado com as permissões do usuário que executa o código. Outras pessoas podem se originar com código bem-intencionado que tenha sido explorado por um invasor. Ao planejar a segurança, sempre presuma que o pior cenário ocorrerá.  
  
 É uma medida de contador, que você pode empregar tentar erguer muros tantos em torno de seu código possível, executando com privilégios mínimos. O princípio de privilégios mínimos diz que qualquer privilégio oferecido deve ser concedido para a quantidade mínima de código necessária para a menor duração de tempo que é necessário para realizar o trabalho.  
  
 A prática recomendada para criar aplicativos seguros é iniciar com nenhuma permissão em todos os e, em seguida, adicione as permissões mais restritas para a tarefa específica que está sendo executada. Por outro lado, começando com todas as permissões e, em seguida, negando memorandos individuais resulta em aplicativos inseguros que são difíceis de testar e manter porque brechas de segurança podem existir de acidentalmente conceder mais permissões do que o necessário.  
  
 Para obter mais informações sobre como proteger seus aplicativos, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Protegendo aplicativos](/visualstudio/ide/securing-applications)|Contém links para tópicos gerais de segurança. Também contém links para tópicos para proteger aplicativos distribuídos, aplicativos Web, aplicativos móveis e aplicativos da área de trabalho.|  
  
## <a name="code-access-security-cas"></a>CAS (Segurança de Acesso do Código)  
 Segurança de acesso do código (CAS) é um mecanismo que ajuda a limitar o acesso de código tem a recursos e operações protegidos. No .NET Framework, o CAS executa as seguintes funções:  
  
-   Define as permissões e os conjuntos de permissões que representam o direito de acessar vários recursos do sistema.  
  
-   Permite aos administradores configurar política de segurança, associando os conjuntos de permissões a grupos de código (grupos de códigos).  
  
-   Permite que o código solicitar as permissões necessárias para executar, bem como as permissões que seriam útil ter e especifica quais permissões o código nunca deve ter.  
  
-   Concede permissões para cada assembly que é carregado, com base nas permissões solicitadas pelo código e as operações permitidas pela política de segurança.  
  
-   Permite que o código para que os chamadores têm permissões específicas à demanda.  
  
-   Permite que o código para que os chamadores possuem uma assinatura digital, permitindo que somente os chamadores de uma organização específica ou um site chamar o código protegido à demanda.  
  
-   Impõe restrições em código em tempo de execução, comparando as permissões concedidas de todos os chamadores na pilha de chamadas para as permissões que os chamadores devem ter.  
  
 Para minimizar a quantidade de danos que podem ocorrer se um ataque for bem-sucedida, escolha um contexto de segurança de seu código que concede acesso apenas os recursos necessários para executar seu trabalho concluído e nada mais.  
  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Segurança de acesso do código e o ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)|Descreve as interações entre ambientes parcialmente confiáveis da perspectiva de um aplicativo ADO.NET, segurança baseada em função e segurança de acesso do código.|  
|[Segurança de acesso do código](../../../../docs/framework/misc/code-access-security.md)|Contém links para tópicos adicionais que descrevem o CAS no .NET Framework.|  
  
## <a name="database-security"></a>Segurança de banco de dados  
 O princípio de privilégios mínimos também se aplica à sua fonte de dados. Algumas diretrizes gerais para segurança de banco de dados incluem:  
  
-   Crie contas com os privilégios mais baixos possíveis.  
  
-   Não permitir que os usuários acesso a contas administrativas apenas para obter o código em funcionamento.  
  
-   Não retornam mensagens de erro do lado do servidor para aplicativos cliente.  
  
-   Valide todas as entradas no cliente e no servidor.  
  
-   Usar comandos parametrizados e evitar instruções SQL dinâmicas.  
  
-   Habilite a auditoria de segurança e registro em log para o banco de dados que você está usando para que você será alertado de qualquer violações de segurança.  
  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[SQL Server Security](../../../../docs/framework/data/adonet/sql/sql-server-security.md) (Segurança do SQL Server)|Fornece uma visão geral de segurança do SQL Server com cenários de aplicativos que fornecem diretrizes para criar aplicativos ADO.NET seguros que direcionam SQL Server.|  
|[Recomendações para estratégias de acesso a dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))|Fornece recomendações para acessar dados e executar operações de banco de dados.|  
  
## <a name="security-policy-and-administration"></a>Diretiva de segurança e administração  
 Administrar incorretamente a política de CAS (segurança) de acesso do código potencialmente poderá criar vulnerabilidades de segurança. Depois que um aplicativo é implantado, técnicas para monitorar a segurança devem ser usadas e os riscos avaliados como novas ameaças surgem.  
  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Gerenciamento de política de segurança](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100))|Fornece informações sobre como criar e administrar a política de segurança.|  
|[Práticas recomendadas de política de segurança](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100))|Fornece links que descrevem como administrar a política de segurança.|  
  
## <a name="see-also"></a>Consulte também
- [Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)
- [Segurança no .NET](../../../standard/security/index.md)
- [SQL Server Security](../../../../docs/framework/data/adonet/sql/sql-server-security.md) (Segurança do SQL Server)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
