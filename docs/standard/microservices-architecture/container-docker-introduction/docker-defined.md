---
title: O que é o Docker?
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | O que é o Docker?
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: fadd2611283f0a7dadbf1734fe48f7d1a13096ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576180"
---
# <a name="what-is-docker"></a>O que é o Docker?

O [Docker](https://www.docker.com/) é um [projeto de software livre](https://github.com/docker/docker) para automatizar a implantação de aplicativos como contêineres autossuficientes portáteis que podem ser executados na nuvem ou localmente. O Docker é também um [empresa](https://www.docker.com/) que promove e evolui essa tecnologia. O Docker funciona em colaboração com a nuvem, o Linux e os fornecedores do Windows, incluindo a Microsoft.

![](./media/image2.png)

**Figura 2-2**. O Docker implanta contêineres em todas as camadas da nuvem híbrida

Os contêineres de imagem do Docker são executados nativamente no Linux e no Windows. As imagens do Windows são executadas somente em hosts do Windows, e as imagens do Linux são executadas apenas em hosts Linux. O host é um servidor ou uma VM.

É possível desenvolver no Windows, Linux ou macOS. O computador de desenvolvimento executa um host Docker em que as imagens do Docker são implantadas, incluindo o aplicativo e suas dependências. No Linux ou no macOS, você usa um host Docker que é baseado no Linux e pode criar imagens apenas para contêineres do Linux. (No macOS, é possível editar código ou executar a CLI do Docker, mas, no momento da redação deste artigo, os contêineres não são executados diretamente no macOS.) No Windows, é possível criar imagens para contêineres do Linux ou do Windows.

No Windows ou no macOS, o [Docker Community Edition (CE)](https://www.docker.com/community-edition) hospeda contêineres em um ambiente de desenvolvimento e fornece ferramentas para desenvolvedores adicionais. O [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition) é usado por equipes de TI que criam, enviam e executam grandes aplicativos críticos aos negócios. ~Os dois produtos instalam a VM necessária (o host Docker) para hospedar os contêineres.~ 

Os [contêineres do Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) funcionam com dois tipos de tempos de execução:

-   Os contêineres do Windows Server fornecem isolamento de aplicativos por meio da tecnologia de isolamento de processo e de namespace. Um contêiner do Windows Server compartilha um kernel com o host do contêiner e todos os contêineres em execução no host.

-   Os contêineres do Hyper-V expandem o isolamento fornecido pelos contêineres do Windows Server, executando cada contêiner em uma máquina virtual altamente otimizada. Nessa configuração, o kernel do host do contêiner não é compartilhado com os contêineres do Hyper-V, fornecendo melhor isolamento. Os contêineres do Hyper-V Containers permitem que aplicativos não confiáveis e *multilocatários hostis* sejam executados no mesmo host. Os contêineres do Hyper-V têm um pouco menos eficiência em tempos de inicialização e densidade do que os contêineres do Windows Server.

As imagens desses contêineres são criadas e funcionam da mesma maneira. Elas diferem na maneira como o contêiner é criado. Para obter detalhes, consulte [Contêineres do Hyper-V](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Comparando os contêineres do Docker com máquinas virtuais

A Figura 2-3 mostra uma comparação entre VMs e contêineres do Docker.

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Máquinas Virtuais**                                                                                                                                                                  **Contêineres do Docker**
                                                                                                                                                                                        
  ![](./media/image3.png)                                                                                                                                ![](./media/image4.png)
                                                                                                                                                                                        
  As máquinas virtuais incluem o aplicativo, as bibliotecas ou binários necessários e um sistema operacional convidado completo. A virtualização completa requer mais recursos do que a conteinerização. Os contêineres incluem o aplicativo e todas as suas dependências. No entanto, os contêineres compartilham o kernel do sistema operacional com outros contêineres. Os contêineres são executados como processos isolados no espaço do usuário no sistema operacional do host. Exceto em contêineres do Hyper-V, em que cada contêiner é executado dentro de uma máquina virtual especial por contêiner.
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Figura 2-3**. Comparação de máquinas virtuais tradicionais com contêineres do Docker

Como os contêineres requerem muito menos recursos (por exemplo, eles não precisam de um sistema operacional completo), eles iniciam rapidamente e são fáceis de implantar. A baixa utilização de recursos permite uma densidade mais alta. É possível executar mais serviços na mesma unidade de hardware e reduzir os custos.

A execução no mesmo kernel resulta em menos isolamento do que o que as VMs fornecem.

A meta principal de uma imagem é que ela torne o ambiente (dependências) o mesmo entre diferentes implantações. Isso significa que é possível depurá-la em seu computador e, em seguida, implantá-la em outro computador com o mesmo ambiente garantido.

Uma imagem de contêiner é uma maneira de empacotar um aplicativo ou serviço e implantá-lo de maneira confiável e reproduzível. Seria possível dizer que o Docker não é apenas uma tecnologia, mas também uma filosofia e um processo.

Os desenvolvedores do Docker não dizem "Funciona no meu computador, por que não em produção?" Eles dizem, "É executado no Docker". Os aplicativos empacotados pelo Docker podem ser executados em qualquer ambiente compatível do Docker. Os aplicativos empacotado do Docker são executados consistentemente em todos os destinos de implantação (desenvolvimento, garantia de qualidade, processo de preparo, produção).

>[!div class="step-by-step"]
[Anterior] (index.md) [Próximo] (docker-terminology.md)
