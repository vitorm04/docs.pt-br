---
title: Desenvolvimento de pipelines
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- add-in pipeline [.NET Framework], segments
- activation path for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], activation path
- communication pipeline for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], pipeline development
ms.assetid: 932788f2-b87d-44cf-82f9-04492a8b2722
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ad577145c26b9c43e8b7fb3b61f27f374ff9298
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="pipeline-development"></a>Desenvolvimento de pipelines
O pipeline de suplemento é o caminho de segmentos de pipeline que o aplicativo de host e o suplemento devem usar para se comunicar entre si.  
  
 A ilustração a seguir mostra o canal de comunicação e seus segmentos.  
  
 ![Adicionar &#45; no modelo de pipeline. ] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
Pipeline de suplemento  
  
 O aplicativo host é um final do pipeline e o suplemento está na outra extremidade. A partir de cada extremidade e movendo no meio, o aplicativo de host e o suplemento tem uma classe base abstrata que define uma exibição do modelo de objeto que ambos compartilham. Esses tipos (classes) compõem o segmento de pipeline de suplemento do modo de exibição e o modo de host do segmento de pipeline de suplemento. O segmento de pipeline de suplemento exibição geralmente contém mais de uma classe abstrata, mas a classe que o suplemento herda é conhecida como a base de suplemento.  
  
 O segmento de pipeline do adaptador do lado do suplemento e a converter de segmento de pipeline do adaptador do host o fluxo de tipos entre seus segmentos de pipeline de exibição e o segmento de pipeline do contrato. O segmento central do pipeline é um contrato que é derivado de <xref:System.AddIn.Contract.IContract> interface. Esse contrato define os métodos que o aplicativo de host e o suplemento irá usar.  
  
 Se você carregar o host e o suplemento em domínios de aplicativo separados, você tem um limite de isolamento que separa o escopo do aplicativo host do escopo do suplemento. O contrato é o assembly só que é carregado no host e domínios de aplicativo do suplemento. O host e o suplemento cada referem-se apenas à sua exibição dos métodos de contrato. Portanto, eles serão separados por uma camada de abstração do contrato.  
  
 Para desenvolver os segmentos de pipeline, você deve criar uma estrutura de diretório que conterá a eles. Para obter mais informações sobre os requisitos de desenvolvimento e diretrizes de escopo, consulte [requisitos de desenvolvimento de Pipeline](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
 A ilustração a seguir mostra os tipos que compõem os segmentos de pipeline. Os nomes dos tipos mostrados na ilustração são arbitrários, mas todos os tipos, exceto para o host e o host de exibição dos atributos suplemento exigem para que possam ser descobertos por métodos que construir um armazenamento de informações.  
  
 ![Adicionar &#45; no modelo com atributos necessários em tipos. ] (../../../docs/framework/add-ins/media/addin-model.png "AddIn_Model")  
Pipeline de suplemento com tipos  
  
 A tabela a seguir descreve os segmentos de pipeline para ativar um suplemento. Para obter mais informações sobre esses segmentos, consulte [contratos, exibições e adaptadores](http://msdn.microsoft.com/en-us/a6460173-9507-4b87-8c07-d4ee245d715c).  
  
|Segmento de pipeline|Descrição|  
|----------------------|-----------------|  
|Host|O assembly de aplicativo que cria uma instância de um suplemento.|  
|Modo de host do suplemento|Representa a exibição do aplicativo host dos tipos de objetos e métodos usados para se comunicar com o suplemento. O modo de host é uma interface ou classe base abstrata.|  
|Adaptador do lado do host|Um assembly com uma ou mais classes que se adapta a métodos de e para o contrato.<br /><br /> Este segmento de pipeline é identificado usando o <xref:System.AddIn.Pipeline.HostAdapterAttribute> atributo.<br /><br /> Não há suporte para assemblies de vários módulos.|  
|Contrato|Uma interface que é derivada de <xref:System.AddIn.Contract.IContract> interface e que define o protocolo de comunicação de tipos entre o host e o suplemento.<br /><br /> Este segmento de pipeline é identificado, definindo o <xref:System.AddIn.Pipeline.AddInContractAttribute> atributo.|  
|Adicionar no lado adaptador|Um assembly com uma ou mais classes que se adapta a métodos de e para o contrato.<br /><br /> Este segmento de pipeline é identificado usando o <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atributo.<br /><br /> Cada assembly no diretório do adaptador do lado do suplemento que contém um tipo que tem um <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atributo é carregado no domínio de aplicativo do suplemento.<br /><br /> Cada assembly no diretório do lado do suplemento é carregado em seu próprio domínio de aplicativo.<br /><br /> Não há suporte para assemblies de vários módulos|  
|Adicionar em modo de exibição|Um assembly que representa a exibição do suplemento do tipos de objeto e os métodos que são usados para se comunicar com o host. O modo de exibição é uma interface ou classe base abstrata.<br /><br /> Este segmento de pipeline é identificado usando o <xref:System.AddIn.Pipeline.AddInBaseAttribute> atributo.<br /><br /> Cada assembly na pasta AddInViews que contém um tipo que tem um <xref:System.AddIn.Pipeline.AddInBaseAttribute> atributo é carregado no domínio de aplicativo do suplemento.|  
|suplemento|Um tipo instanciado que executa um serviço para o host.|  
  
## <a name="pipeline-activation-path"></a>Caminho de ativação de pipeline  
 A ilustração a seguir mostra a ativação de tipos, quando um suplemento é ativado. Ele também mostra a passagem de objetos para o host, como os resultados de um cálculo ou uma coleção de objetos. Este é o cenário mais comum.  
  
 ![Adicionar &#45; no modelo com caminho de ativação. ] (../../../docs/framework/add-ins/media/addin6.png "AddIn6")  
Caminho de ativação de suplemento para o host  
  
 O caminho de ativação do pipeline ocorre da seguinte maneira:  
  
1.  O aplicativo de host ativa o suplemento com o <xref:System.AddIn.Hosting.AddInToken.Activate%2A> método.  
  
2.  O modo de exibição do suplemento, add-in, adaptador do lado do suplemento e os assemblies de contrato são carregados no domínio de aplicativo do suplemento.  
  
3.  Uma instância do adaptador do lado do suplemento é criada usando o modo de exibição (com a classe identificada pelo <xref:System.AddIn.Pipeline.AddInBaseAttribute> atributo) como seu construtor. O adaptador do lado do suplemento herda do contrato.  
  
4.  O adaptador do lado do suplemento, que é digitado como o contrato, é passado através dos limites de isolamento (opcional) para o construtor do adaptador do host.  
  
5.  O modo de host do adaptador de suplemento, do lado do host e os assemblies de contrato são carregados no domínio do aplicativo do host.  
  
6.  Uma instância do adaptador do host é criada usando o contrato como seu construtor. O adaptador do lado do host herda o modo de host do suplemento.  
  
7.  O host tem o suplemento, que é digitado como o host de exibição do suplemento e pode continuar a chamar seus métodos.  
  
## <a name="walkthroughs"></a>Passo a passo  
 Há três tópicos de instruções passo a passo que descrevem como criar pipelines usando o Visual Studio:  
  
-   [Passo a passo: criando um aplicativo extensível](../../../docs/framework/add-ins/walkthrough-create-extensible-app.md)  
  
     Descreve um suplemento de cálculo que executa a adição, subtração, multiplicação e cálculos de divisão para o host.  
  
-   [Passo a passo: Habilitando a compatibilidade com versões anteriores, como as alterações de Host](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
  
     Descreve um suplemento de calculadora com recursos aprimorados de cálculo e como manter a compatibilidade com o suplemento de calculadora primeiro.  
  
-   [Passo a passo: Passando coleções entre Hosts e suplementos](http://msdn.microsoft.com/en-us/b532c604-548e-4fab-b11c-377257dd0ee5)  
  
     Descreve como passar conjuntos de dados pelo pipeline usando um cenário de armazenamento do catálogo.  
  
## <a name="see-also"></a>Consulte também  
 [Cenários de Pipeline do suplemento](http://msdn.microsoft.com/en-us/feb70e0b-8734-494c-aeaf-b567f014043e)  
 [Suplementos e extensibilidade](../../../docs/framework/add-ins/index.md)
