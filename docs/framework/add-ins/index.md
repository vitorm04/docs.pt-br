---
title: Suplementos e extensibilidade
ms.date: 03/30/2017
helpviewer_keywords:
- extensibility [.NET Framework], add-ins
- add-ins [.NET Framework]
- add-ins [.NET Framework], about
- hosts [.NET Framework], compared to add-ins
- .NET Framework, add-ins
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], compared to hosts
- .NET Framework, extensibility
- versioning [.NET Framework], add-ins
ms.assetid: 8dd45b02-7218-40f9-857d-40d7b98b850b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb2485f2ecf0426360dba80d443500a92b5a7af6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510048"
---
# <a name="add-ins-and-extensibility"></a>Suplementos e extensibilidade
<a name="top"></a> Suplementos fornecem recursos estendidos ou serviços para um aplicativo host. O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] fornece um modelo de programação que os desenvolvedores podem usar para desenvolver suplementos e ativá-los em seus aplicativos de host. O modelo realiza isso criando um pipeline de comunicação entre o host e o suplemento. O modelo é implementado usando os tipos na <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, e <xref:System.AddIn.Contract> namespaces.  
  
 Esta visão geral contém as seguintes seções:  
  
-   [Modelo de suplemento](#addin_model)  
  
-   [Fazer a distinção entre Hosts e suplementos](#distinguishing_between_addins_and_hosts)  
  
-   [Tópicos relacionados](#related_topics)  
  
-   [Referência](#reference)  
  
> [!NOTE]
>  Você pode encontrar exemplos adicionais de código e visualizações de tecnologia de cliente de ferramentas para construção suplemento pipelines na [extensibilidade gerenciada e Add-In Framework site CodePlex](https://go.microsoft.com/fwlink/?LinkId=121190).  
  
<a name="addin_model"></a>   
## <a name="add-in-model"></a>Modelo de suplemento  
 O modelo de suplemento consiste em uma série de segmentos que compõem o suplemento do pipeline (também conhecido como pipeline de comunicação), que é responsável por toda a comunicação entre o suplemento e o host. O pipeline é um modelo de comunicação simétrico de segmentos que trocar dados entre um suplemento e seu host. Desenvolver esses segmentos entre o host e o suplemento fornece isolamento de suplemento e as camadas necessárias de abstração que dão suporte a controle de versão.  
  
 A ilustração a seguir mostra o pipeline.  
  
 ![Adicionar&#45;no modelo de pipeline. ](../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
Suplemento do pipeline  
  
 Os assemblies para esses segmentos não são necessários para estar no mesmo domínio do aplicativo. Você pode carregar um suplemento em seu próprio domínio de aplicativo novo, em um domínio de aplicativo existente ou até mesmo para o domínio do aplicativo host. Você pode carregar vários suplementos no mesmo domínio do aplicativo, que permite que os suplementos compartilhar recursos e contextos de segurança.  
  
 O modelo de suplemento oferece suporte à e recomenda, um limite opcional entre o host e o suplemento, que é chamado o limite de isolamento (também conhecido como um limite de comunicação remota). Esse limite pode ser um limite de domínio ou processo do aplicativo.  
  
 O segmento de contrato no meio do pipeline é carregado no domínio de aplicativo do host e o domínio de aplicativo do suplemento. O contrato define os métodos virtuais que o host e o uso de adicionar a troca de tipos entre si.  
  
 Para passar o limite de isolamento, os tipos devem ser contratos ou tipos serializáveis. Tipos que não contratos ou tipos serializáveis devem ser convertidos para contratos pelos segmentos de adaptador no pipeline.  
  
 Os segmentos de modo de exibição do pipeline são classes base abstratas ou interfaces que fornecem o host e o suplemento com uma exibição dos métodos que eles compartilham, conforme definido pelo contrato.  
  
 Para obter mais informações sobre o desenvolvimento de segmentos de pipeline, consulte [desenvolvimento de Pipeline](../../../docs/framework/add-ins/pipeline-development.md).  
  
 As seções a seguir descrevem os recursos do modelo de suplemento.  
  
### <a name="independent-versioning"></a>Controle de versão independente  
 O modelo de suplemento permite que hosts e suplementos para a versão independentemente. Como resultado, o modelo de suplemento permite os seguintes cenários:  
  
-   Criação de um adaptador que permite que um host usar um suplemento criado para uma versão anterior do host.  
  
-   Criação de um adaptador que permite que um host usar um suplemento criado para uma versão posterior do host.  
  
-   Criação de um adaptador que permite que um host usar os suplementos criados para um host diferente.  
  
### <a name="discovery-and-activation"></a>Detecção e ativação  
 Você pode ativar um suplemento usando um token de uma coleção que representa os suplementos encontrados a partir de um armazenamento de informações. Suplementos são encontrados por meio de pesquisa para o tipo que define a exibição do host do suplemento. Você também pode encontrar um add-in específico pelo tipo que define o suplemento. O armazenamento de informações consiste em dois arquivos de cache: o repositório de pipeline e o armazenamento de suplemento.  
  
 Para obter informações sobre como atualizar e recompilar o armazenamento de informações, consulte [Add-in descoberta](https://msdn.microsoft.com/library/5d268dde-11df-4c4d-a022-f58d88bbc421). Para obter informações sobre como ativar suplementos, consulte [ativação de suplementos](https://msdn.microsoft.com/library/bedcbcdf-5964-4215-b5f3-3299798b2b3f) e [como: ativar suplementos com isolamento e segurança diferentes](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).  
  
### <a name="isolation-levels-and-external-processes"></a>Níveis de isolamento e processos externos  
 O modelo de suplemento oferece suporte a vários níveis de isolamento entre um suplemento e seu host ou suplementos. A partir da menos isolado, esses níveis são da seguinte maneira:  
  
-   O suplemento é executado no mesmo domínio do aplicativo como o host. Isso não é recomendado porque você perde os recursos de isolamento e descarregando que você obtém ao usar domínios de aplicativo diferentes.  
  
-   Vários suplementos são carregados no mesmo domínio do aplicativo que é diferente do domínio de aplicativo usado pelo host.  
  
-   Cada suplemento é carregado exclusivamente em seu próprio domínio de aplicativo. Este é o nível mais comuns de isolamento.  
  
-   Vários suplementos são carregados no mesmo domínio do aplicativo em um processo externo.  
  
-   Cada suplemento é carregado exclusivamente em seu próprio domínio de aplicativo em um processo externo. Esse é o cenário mais isolado.  
  
 Para obter mais informações sobre o uso de processos externos, consulte [como: ativar suplementos com isolamento e segurança diferentes](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).  
  
### <a name="lifetime-management"></a>Gerenciamento do tempo de vida  
 Porque o modelo de suplemento abrange os limites de processo e de domínio de aplicativo, a coleta de lixo por si só não é suficiente para liberar e recuperar objetos. O modelo de suplemento fornece um mecanismo de gerenciamento de tempo de vida que usa tokens e a contagem de referência e geralmente não requer programação adicional. Para obter mais informações, consulte [gerenciamento de tempo de vida](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).  
  
 [Voltar ao início](#top)  
  
<a name="distinguishing_between_addins_and_hosts"></a>   
## <a name="distinguishing-between-add-ins-and-hosts"></a>Fazer a distinção entre Hosts e suplementos  
 A diferença entre um suplemento e um host é simplesmente que o host é o que ativa o suplemento. O host pode ser o maior dos dois, como um aplicativo de processamento de texto e seu verificadores ortográficos; ou o host pode ser o menor dos dois, como um cliente de mensagens instantâneas que incorpora um player de mídia. O modelo de suplemento oferece suporte a suplementos em cenários de cliente e servidor. Exemplos de suplementos do servidor incluem suplementos que fornecem os servidores de email com verificação de vírus, filtros de spam e proteção de IP. Exemplos de suplemento do cliente incluem suplementos de referência para processadores de texto, recursos especializados para programas gráficos e jogos e verificação de vírus de clientes de email local.  
  
 [Voltar ao início](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Desenvolvimento de pipeline](../../../docs/framework/add-ins/pipeline-development.md)|Descreve o pipeline de comunicação de segmentos do aplicativo host para o suplemento. Fornece exemplos de código nos tópicos de instruções passo a passo que descrevem como construir o pipeline e como implantar os segmentos de pipeline no Visual Studio.|  
|[Domínios do aplicativo e assemblies](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)|Descreve o relacionamento entre domínios de aplicativo, que fornecem um limite de isolamento de segurança, confiabilidade e controle de versão e assemblies.|  
  
 [Voltar ao início](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a>Referência  
 <xref:System.AddIn?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Contract?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Hosting?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Pipeline?displayProperty=nameWithType>  
  
 [Voltar ao início](#top)