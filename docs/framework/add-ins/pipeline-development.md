---
title: Desenvolvimento de pipelines
ms.date: 03/30/2017
helpviewer_keywords:
- add-in pipeline [.NET Framework], segments
- activation path for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], activation path
- communication pipeline for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], pipeline development
ms.assetid: 932788f2-b87d-44cf-82f9-04492a8b2722
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f981d667f3cbf35ab010ac5bd26a9ecd5c2aae11
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50135422"
---
# <a name="pipeline-development"></a>Desenvolvimento de pipelines
O pipeline de suplemento é o caminho dos segmentos de pipeline que o aplicativo host e seu suplemento devem usar para se comunicar entre si.  
  
 A ilustração a seguir mostra o pipeline de comunicação e seus segmentos.  
  
 ![Adicionar&#45;no modelo de pipeline. ](../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
Suplemento do pipeline  
  
 O aplicativo host é um final do pipeline e o suplemento está na outra extremidade. Começando em cada extremidade e movendo em direção ao meio, o aplicativo host e o suplemento têm uma classe base abstrata que define um modo de exibição do modelo de objeto que ambas compartilham. Esses tipos (classes) compõem o segmento de pipeline de exibição do suplemento e a exibição de host do segmento de pipeline de suplemento. O segmento de pipeline de exibição de suplemento geralmente contém mais de uma classe abstrata, mas que o suplemento herda da classe é conhecida como a base de suplemento.  
  
 O segmento de pipeline do adaptador do lado do suplemento e a converter de segmento de pipeline do adaptador do lado do host o fluxo de tipos entre seus segmentos de pipeline de exibição e o segmento de pipeline de contrato. O segmento de central do pipeline é um contrato que é derivado de <xref:System.AddIn.Contract.IContract> interface. Este contrato define os métodos que o aplicativo host e seu suplemento serão usado.  
  
 Se você carregar o host e o suplemento em domínios de aplicativo separados, você tem um limite de isolamento que separa o escopo do aplicativo host do escopo do suplemento. O contrato é o único assembly é carregado no host e domínios de aplicativo do suplemento. O host e o suplemento cada referem-se somente ao modo de exibição dos métodos de contrato. Portanto, eles são separados por uma camada de abstração do contrato.  
  
 Para desenvolver os segmentos de pipeline, você deve criar uma estrutura de diretório que conterá a eles. Para obter mais informações sobre requisitos de desenvolvimento e as diretrizes de escopo, consulte [requisitos de desenvolvimento de Pipeline](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
 A ilustração a seguir mostra os tipos que compõem os segmentos de pipeline. Os nomes dos tipos mostrados na ilustração são arbitrários, mas todos os tipos, exceto para o host e o host de exibir os atributos de suplemento exigem para que possam ser descobertos por métodos que constroem um armazenamento de informações.  
  
 ![Adicionar&#45;no modelo com atributos necessários em tipos. ](../../../docs/framework/add-ins/media/addin-model.png "AddIn_Model")  
Suplemento do pipeline com tipos  
  
 A tabela a seguir descreve os segmentos de pipeline para ativar um suplemento. Para obter mais informações sobre esses segmentos, consulte [contratos, exibições e adaptadores](https://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c).  
  
|Segmento de pipeline|Descrição|  
|----------------------|-----------------|  
|Host|O assembly de aplicativo que cria uma instância de um suplemento.|  
|Exibição do suplemento do host|Representa a exibição do aplicativo host dos tipos de objeto e métodos usados para se comunicar com o suplemento. A exibição de host é uma interface ou classe base abstrata.|  
|Adaptador do lado do host|Um assembly com uma ou mais classes que se adapta a métodos de e para o contrato.<br /><br /> Este segmento de pipeline é identificado usando o <xref:System.AddIn.Pipeline.HostAdapterAttribute> atributo.<br /><br /> Não há suporte para vários assemblies de módulo.|  
|Contrato|Uma interface que deriva de <xref:System.AddIn.Contract.IContract> interface e que define o protocolo de comunicação de tipos entre o host e o seu suplemento.<br /><br /> Este segmento de pipeline é identificado, definindo o <xref:System.AddIn.Pipeline.AddInContractAttribute> atributo.|  
|Adicionar-adaptador no lado do|Um assembly com uma ou mais classes que se adapta a métodos de e para o contrato.<br /><br /> Este segmento de pipeline é identificado usando o <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atributo.<br /><br /> Cada assembly no diretório do adaptador do lado do suplemento que contém um tipo que tem um <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atributo é carregado no domínio de aplicativo do suplemento.<br /><br /> Cada assembly no diretório do lado do suplemento é carregado em seu próprio domínio de aplicativo.<br /><br /> Não há suporte para vários assemblies de módulo|  
|Exibição Add-in|Um assembly que representa a exibição do suplemento dos tipos de objeto e métodos que são usados para se comunicar com o host. O modo de exibição é uma interface ou classe base abstrata.<br /><br /> Este segmento de pipeline é identificado usando o <xref:System.AddIn.Pipeline.AddInBaseAttribute> atributo.<br /><br /> Cada assembly no diretório AddInViews que contém um tipo que tem um <xref:System.AddIn.Pipeline.AddInBaseAttribute> atributo é carregado no domínio de aplicativo do suplemento.|  
|suplemento|Um tipo instanciado que executa um serviço para o host.|  
  
## <a name="pipeline-activation-path"></a>Caminho de ativação de pipeline  
 A ilustração a seguir mostra a ativação de tipos quando um suplemento é ativado. Ele também mostra a passagem de objetos para o host, como os resultados de um cálculo ou uma coleção de objetos. Esse é o cenário mais comum.  
  
 ![Adicionar&#45;no modelo de caminho de ativação. ](../../../docs/framework/add-ins/media/addin6.png "AddIn6")  
Caminho de ativação do suplemento para o host  
  
 O caminho de ativação do pipeline ocorre da seguinte maneira:  
  
1.  O aplicativo host ativará o suplemento com o <xref:System.AddIn.Hosting.AddInToken.Activate%2A> método.  
  
2.  O modo de exibição do suplemento, add-in, o adaptador do lado do suplemento e os assemblies de contrato são carregados no domínio de aplicativo do suplemento.  
  
3.  Uma instância do adaptador do lado do suplemento é criada usando o modo de exibição (com a classe identificada pelo <xref:System.AddIn.Pipeline.AddInBaseAttribute> atributo) como seu construtor. Herda o adaptador do lado do suplemento do contrato.  
  
4.  O adaptador do lado do suplemento, o que é digitado como contrato, é passado pelo limite de isolamento (opcional) para o construtor do adaptador do lado do host.  
  
5.  O modo de host do adaptador de suplemento, do lado do host e os assemblies de contrato são carregados para o domínio do aplicativo host.  
  
6.  Uma instância do adaptador do host é criada usando o contrato como seu construtor. O adaptador do lado do host herda o modo de host do suplemento.  
  
7.  O host tem o suplemento, que é digitado como o host do modo de exibição de suplemento e pode continuar a chamar seus métodos.  
  
## <a name="walkthroughs"></a>Passo a passo  
 Há três tópicos de instruções passo a passo que descrevem como criar pipelines usando o Visual Studio:  
  
-   [Passo a passo: criando um aplicativo extensível](../../../docs/framework/add-ins/walkthrough-create-extensible-app.md)  
  
     Descreve um suplemento de calculadora que executa a adição, subtração, multiplicação e cálculos de divisão para o host.  
  
-   [Passo a passo: Habilitando a compatibilidade com versões anteriores como o Host é alterado](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
  
     Descreve um suplemento de calculadora com recursos de cálculo aprimorado e como manter a compatibilidade com o suplemento de calculadora primeiro.  
  
-   [Passo a passo: Passando coleções entre Hosts e suplementos](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
  
     Descreve como passar coleções de dados sobre o pipeline usando um cenário de repositório de livro.  
  
## <a name="see-also"></a>Consulte também  
- [Cenários de pipelines de suplemento](https://msdn.microsoft.com/library/feb70e0b-8734-494c-aeaf-b567f014043e)  
- [Suplementos e extensibilidade](../../../docs/framework/add-ins/index.md)
