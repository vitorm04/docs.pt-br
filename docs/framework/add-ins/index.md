---
title: Suplementos e extensibilidade
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "42"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7e4d336992be216178b1237c9f43bffb3de61fba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="add-ins-and-extensibility"></a>Suplementos e extensibilidade
<a name="top"></a>Os suplementos fornecem recursos estendidos ou serviços para um aplicativo host. O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] fornece um modelo de programação que os desenvolvedores podem usar para desenvolver os complementos e ativá-los em seus aplicativos de host. O modelo realiza isso criando um pipeline de comunicação entre o host e o suplemento. O modelo é implementado usando os tipos no <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, e <xref:System.AddIn.Contract> namespaces.  
  
 Esta visão geral contém as seguintes seções:  
  
-   [Modelo de suplemento](#addin_model)  
  
-   [Fazer distinção entre Hosts e suplementos](#distinguishing_between_addins_and_hosts)  
  
-   [Tópicos relacionados](#related_topics)  
  
-   [Referência](#reference)  
  
> [!NOTE]
>  Você pode encontrar exemplos adicionais de código e prévias de tecnologia de cliente de ferramentas para construção suplemento pipelines no [site gerenciado extensibilidade e suplemento do Framework no CodePlex](http://go.microsoft.com/fwlink/?LinkId=121190).  
  
<a name="addin_model"></a>   
## <a name="add-in-model"></a>Modelo de suplemento  
 O modelo de suplemento consiste em uma série de segmentos que compõem o pipeline de suplementos (também conhecido como o pipeline de comunicação), que é responsável por toda a comunicação entre o suplemento e o host. O pipeline é um modelo de comunicação simétrico de segmentos que trocar dados entre um suplemento e seu host. Desenvolver esses segmentos entre o host e o suplemento fornece isolamento do suplemento e as camadas necessárias de abstração que oferecem suporte a controle de versão.  
  
 A ilustração a seguir mostra o pipeline.  
  
 ![Adicionar &#45; no modelo de pipeline. ] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
Pipeline de suplemento  
  
 Os assemblies para esses segmentos não são necessários para estar no mesmo domínio do aplicativo. Você pode carregar um suplemento em seu próprio domínio de aplicativo nova, em um domínio de aplicativo existente ou até mesmo para o domínio de aplicativo do host. Você pode carregar vários suplementos no mesmo domínio do aplicativo, que permite que os suplementos compartilhar recursos e contextos de segurança.  
  
 Modelo de suplemento dá suporte a e recomenda um limite opcional entre o host e o suplemento, que é chamado o limite de isolamento (também conhecido como um limite de comunicação remota). Esse limite pode ser um limite de domínio ou de processo do aplicativo.  
  
 O segmento de contrato no meio do pipeline é carregado no domínio do aplicativo do host e domínio de aplicativo do suplemento. O contrato define os métodos virtuais que o host e o uso de adicionar a troca de tipos entre si.  
  
 Para passar o limite de isolamento, os tipos devem ser contratos ou tipos serializáveis. Tipos não contratos ou tipos serializáveis devem ser convertidos para contratos por segmentos de adaptador no pipeline.  
  
 Os segmentos de modo de exibição do pipeline são classes base abstratas ou interfaces que fornecem o host e o suplemento com uma exibição dos métodos que compartilham, conforme definido pelo contrato.  
  
 Para obter mais informações sobre o desenvolvimento de segmentos de pipeline, consulte [desenvolvimento de Pipeline](../../../docs/framework/add-ins/pipeline-development.md).  
  
 As seções a seguir descrevem os recursos do modelo de suplemento.  
  
### <a name="independent-versioning"></a>Controle de versão independente  
 O modelo de suplemento permite que hosts e suplementos para versão independentemente. Como resultado, o modelo de suplemento permite os seguintes cenários:  
  
-   Criar um adaptador que permite que um host usar um suplemento criado para uma versão anterior do host.  
  
-   Criar um adaptador que permite que um host usar um suplemento criado para uma versão posterior do host.  
  
-   Criação de um adaptador que permite que um host usar os suplementos criados para um host diferente.  
  
### <a name="discovery-and-activation"></a>Detecção e ativação  
 Você pode ativar um suplemento usando um token de uma coleção que representa os suplementos encontrados em um armazenamento de informações. Complementos são encontrados por meio de pesquisa para o tipo que define a exibição do host do suplemento. Você também pode encontrar um add-in específico pelo tipo que define o suplemento. O armazenamento de informações consiste em dois arquivos de cache: o repositório de pipeline e o repositório de suplementos.  
  
 Para obter informações sobre como atualizar e recompilar o armazenamento de informações, consulte [suplemento descoberta](http://msdn.microsoft.com/en-us/5d268dde-11df-4c4d-a022-f58d88bbc421). Para obter informações sobre como ativar suplementos, consulte [suplemento ativação](http://msdn.microsoft.com/en-us/bedcbcdf-5964-4215-b5f3-3299798b2b3f) e [como: ativar suplementos com segurança e isolamento diferentes](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).  
  
### <a name="isolation-levels-and-external-processes"></a>Níveis de isolamento e processos externos  
 O modelo dá suporte a vários níveis de isolamento entre um suplemento e seu host ou suplementos. A partir de menos isolado, esses níveis são os seguintes:  
  
-   O suplemento é executado no mesmo domínio do aplicativo como o host. Isso não é recomendado porque você perderá o isolamento e recursos de descarregamento que você obtém ao usar diferentes domínios de aplicativo.  
  
-   Vários suplementos são carregados no mesmo domínio do aplicativo que é diferente do domínio de aplicativo usado pelo host.  
  
-   Cada suplemento é carregado exclusivamente em seu próprio domínio de aplicativo. Este é o nível mais comuns de isolamento.  
  
-   Vários suplementos são carregados no mesmo domínio do aplicativo em um processo externo.  
  
-   Cada suplemento é carregado exclusivamente em seu próprio domínio de aplicativo em um processo externo. Esse é o cenário mais isolado.  
  
 Para obter mais informações sobre o uso de processos externos, consulte [como: ativar suplementos com segurança e isolamento diferentes](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).  
  
### <a name="lifetime-management"></a>Gerenciamento do tempo de vida  
 Porque o modelo de suplemento ultrapassa os limites de domínio e o processo do aplicativo, a coleta de lixo por si só não é suficiente para liberar e recuperar os objetos. O modelo fornece um mecanismo de gerenciamento do ciclo de vida que usa tokens e contagem de referência e geralmente não requer programação adicional. Para obter mais informações, consulte [gerenciamento de vida útil](http://msdn.microsoft.com/en-us/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).  
  
 [Voltar ao início](#top)  
  
<a name="distinguishing_between_addins_and_hosts"></a>   
## <a name="distinguishing-between-add-ins-and-hosts"></a>Fazer distinção entre Hosts e suplementos  
 A diferença entre um suplemento e um host é simplesmente que o host é o que ativa o suplemento. O host pode ter mais de dois, como um aplicativo de processamento de texto e seu verificadores ortográficos; ou o host pode ser o menor dos dois, como um cliente de mensagens instantâneo que incorpora um reprodutor de mídia. O modelo dá suporte a suplementos em cenários de cliente e servidor. Exemplos de suplementos do servidor incluem suplementos que fornecem os servidores de email com a verificação de vírus, filtros de spam e proteção de IP. Cliente suplemento exemplos suplementos de referência para processadores de texto, recursos especializados para programas gráficos e jogos e verificação de vírus de clientes de email local.  
  
 [Voltar ao início](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Desenvolvimento de pipeline](../../../docs/framework/add-ins/pipeline-development.md)|Descreve o canal de comunicação de segmentos do aplicativo host para o suplemento. Fornece exemplos de código nos tópicos de instruções passo a passo que descrevem como construir o pipeline e como implantar segmentos para o pipeline em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].|  
|[Domínios do aplicativo e assemblies](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346)|Descreve a relação entre os domínios de aplicativo, que fornecem um limite de isolamento de segurança, confiabilidade e controle de versão e assemblies.|  
  
 [Voltar ao início](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a>Referência  
 <xref:System.AddIn?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Contract?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Hosting?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Pipeline?displayProperty=nameWithType>  
  
 [Voltar ao início](#top)