---
title: "O que é o Docker?"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | O que é o Docker?"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: aa9cb379628fa91e5dc5b1b529f92db98fa59305
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="what-is-docker"></a>O que é o Docker?

[Docker](https://www.docker.com/) é um [projeto de código-fonte aberto](https://github.com/docker/docker) para automatizar a implantação de aplicativos como contêineres auto-suficiente, portáteis que podem ser executados na nuvem ou local. A docker é também um [empresa](https://www.docker.com/) que promove e evolui essa tecnologia. Docker funciona em colaboração com a nuvem, Linux e fornecedores do Windows, incluindo Microsoft.

![](./media/image2.png)

**Figura 2-2**. Docker implanta contêineres em todas as camadas da nuvem híbrida

Contêineres de imagem do docker executam nativamente no Linux e Windows. Imagens do Windows executado somente em hosts do Windows e imagens Linux executar apenas em hosts Linux. O host é um servidor ou em uma VM.

Você pode desenvolver no Windows, Linux ou macOS. O computador de desenvolvimento executa um host Docker onde as imagens do Docker são implantadas, incluindo o aplicativo e suas dependências. No Linux ou macOS, você deve usar um host Docker Linux com base e pode criar imagens apenas para contêineres do Linux. (Em macOS, você pode editar o código ou executar a CLI do Docker, mas a partir do momento da redação deste artigo, os contêineres não são executadas diretamente em macOS.) No Windows, você pode criar imagens de contêineres do Windows ou Linux.

No Windows ou macOS, [Docker Community Edition (CE)](https://www.docker.com/community-edition) hospeda contêineres em um ambiente de desenvolvimento e fornece ferramentas de desenvolvimento adicionais. [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition) é usado por equipes de TI que criarem, enviar e executam grandes aplicativos essenciais aos negócios. ~ Ambos os produtos de instalam o VM necessário (o host do Docker) para hospedar os contêineres. ~ 

[Contêineres do Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) funcionam com dois tipos de tempos de execução:

-   Contêineres do Windows Server fornecem isolamento de aplicativos por meio da tecnologia de isolamento de processo e de namespace. Um contêiner do Windows Server compartilha um kernel com o host do contêiner e todos os contêineres em execução no host.

-   Contêineres do Hyper-V expandem o isolamento fornecido pelos contêineres do Windows Server, executando cada contêiner em uma máquina virtual altamente otimizada. Nessa configuração, o kernel do host do contêiner não é compartilhado com os contêineres do Hyper-V, fornece melhor isolamento. Permitir a contêineres do Hyper-V não confiáveis e *hostil multilocatário* aplicativos sejam executados no mesmo host. Contêineres do Hyper-V tem um pouco menos eficiência em tempos de inicialização e a densidade de contêineres do Windows Server.

As imagens para esses contêineres são criadas e funcionam da mesma maneira. Elas diferem em como o contêiner é criado. Para obter detalhes, consulte [contêineres do Hyper-V](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Comparando os contêineres do Docker com máquinas virtuais

Figura 2-3 mostra uma comparação entre VMs e Docker contêineres.

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Máquinas virtuais****contêineres do Docker** 
                                                                                                                                                                                        
  ![](./media/image3.png)                                                                                                                                ![](./media/image4.png)
                                                                                                                                                                                        
  Máquinas virtuais incluem o aplicativo, as bibliotecas necessárias ou binários e um sistema operacional convidado completo. A virtualização completa requer mais recursos que enormemente. Contêineres incluem o aplicativo e todas as suas dependências. No entanto, contêineres de compartilham o kernel do sistema operacional com outros contêineres. Contêineres são executados como processos isolados no espaço do usuário no sistema operacional do host. Exceto em contêineres do Hyper-V, onde cada contêiner é executado dentro de uma máquina virtual especial por contêiner.
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Figura 2-3**. Comparação de máquinas virtuais tradicionais para contêineres do Docker

Como contêineres exigem muito menos recursos (por exemplo, eles não é necessário um SO completo), eles início rápido e são fáceis de implantar. Baixa utilização de recursos permite que a densidade mais alta. Você pode executar mais serviços na mesma unidade de hardware e reduzir os custos.

Os mesmos resultados de kernel menos isoladamente que fornecem VMs em execução.

O objetivo principal de uma imagem é que ele faz o ambiente (dependências) os mesmos entre diferentes implantações. Isso significa que você pode depurá-lo em seu computador e, em seguida, implantá-lo para outro computador com o mesmo ambiente de garantia.

Uma imagem de contêiner é uma maneira para empacotar um aplicativo ou serviço e implantá-lo de forma confiável e reproduzível. Você pode dizer que o Docker é não apenas uma tecnologia, mas também uma filosofia e um processo.

Os desenvolvedores de docker não diga "Funciona no meu computador, por que não em produção?" Diz, "Executa no Docker". Aplicativos empacotados docker podem ser executados em qualquer ambiente Docker. Aplicativos empacotado de docker executados consistentemente em todos os destinos de implantação (desenvolvimento, QA, preparo, produção).

>[!div class="step-by-step"]
[Anterior] (index.md) [Avançar] (docker-terminology.md)
